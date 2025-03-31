<!--
  - Copyright (c) 2024 LangChat. TyCoding All Rights Reserved.
  -
  - Licensed under the GNU Affero General Public License, Version 3 (the "License");
  - you may not use this file except in compliance with the License.
  - You may obtain a copy of the License at
  -
  -     https://www.gnu.org/licenses/agpl-3.0.html
  -
  - Unless required by applicable law or agreed to in writing, software
  - distributed under the License is distributed on an "AS IS" BASIS,
  - WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  - See the License for the specific language governing permissions and
  - limitations under the License.
  -->

<script lang="ts" setup>
  import { DownloadOutline } from '@vicons/ionicons5';
  import { useRouter } from 'vue-router';
  import { UploadCustomRequestOptions, useMessage } from 'naive-ui';
  import { embeddingDocs } from '@/api/aigc/embedding';
  import { ref } from 'vue';

  const router = useRouter();
  const message = useMessage();
  const fileList = ref<any[]>([]);
  const uploading = ref(false);
  const uploadQueue = ref<any[]>([]);
  const currentUploading = ref(false);

  // 处理上传队列
  const processUploadQueue = async () => {
    if (currentUploading.value || uploadQueue.value.length === 0) return;
    
    currentUploading.value = true;
    const file = uploadQueue.value[0];
    
    try {
      await embeddingDocs(
        String(router.currentRoute.value.params.id),
        {
          file: file.file,
        },
        (progressEvent) => {
          // 更新进度
          file.progress = Math.round((progressEvent.loaded * 100) / Number(progressEvent.total));
        }
      );
      
      fileList.value.push(file);
      message.success(`${file.name} 上传成功，文档解析中...`);
      file.status = 'success';
    } catch (err) {
      console.error(err);
      message.error(`${file.name} 上传失败`);
      file.status = 'error';
    } finally {
      // 从队列中移除当前文件
      uploadQueue.value.shift();
      currentUploading.value = false;
      
      // 如果队列中还有文件，继续处理
      if (uploadQueue.value.length > 0) {
        processUploadQueue();
      } else {
        // 所有文件处理完成，重置状态
        uploading.value = false;
        message.success('所有文件上传完成');
      }
    }
  };

  const handleImport = async ({ file, onFinish, onError, onProgress }: UploadCustomRequestOptions) => {
    const kbId = router.currentRoute.value.params.id;
    uploading.value = true;
    
    // 将文件添加到上传队列
    uploadQueue.value.push({
      ...file,
      status: 'pending',
      progress: 0
    });
    
    // 开始处理队列
    processUploadQueue();
    
    // 立即完成上传组件的回调
    onFinish();
  };

  // 重置上传状态
  const resetUpload = () => {
    fileList.value = [];
    uploadQueue.value = [];
    uploading.value = false;
    currentUploading.value = false;
  };
</script>

<template>
  <n-space vertical>
    <n-upload
      :custom-request="handleImport"
      directory-dnd
      multiple
      :max="200"
      :disabled="uploading"
      accept=".doc,.docx,application/msword,application/vnd.openxmlformats-officedocument.wordprocessingml.document,.pdf,.txt,.md"
    >
      <n-upload-dragger>
        <div style="margin-bottom: 12px">
          <n-icon :depth="3" size="48">
            <DownloadOutline />
          </n-icon>
        </div>
        <n-text style="font-size: 16px"> 点击或者拖动文件到该区域来上传</n-text>
        <n-p depth="3" style="margin: 8px 0 0 0">
          请上传文档文本类型的文件，文本类型文件将被单独处理和向量化，支持的文件格式有：.txt、 .md、
          .docx、 .doc、.pdf
        </n-p>
        <n-p depth="3" style="margin: 8px 0 0 0">
          支持批量上传，最多可同时上传200个文件
        </n-p>
      </n-upload-dragger>
    </n-upload>

    <n-list v-if="fileList.length > 0" bordered>
      <n-list-item v-for="file in fileList" :key="file.name">
        <div class="flex items-center justify-between">
          <div class="flex items-center gap-2">
            <SvgIcon icon="flat-color-icons:document" />
            <span>{{ file.name }}</span>
          </div>
          <div class="flex items-center gap-2">
            <n-progress
              v-if="file.status === 'pending'"
              type="line"
              :percentage="file.progress"
              :processing="true"
              :width="100"
            />
            <n-tag v-else-if="file.status === 'success'" type="success">上传成功</n-tag>
            <n-tag v-else type="error">上传失败</n-tag>
          </div>
        </div>
      </n-list-item>
    </n-list>

    <div v-if="fileList.length > 0" class="flex justify-end">
      <n-button @click="resetUpload">重置上传</n-button>
    </div>
  </n-space>
</template>

<style lang="less" scoped></style>
