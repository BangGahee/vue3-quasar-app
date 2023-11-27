<template>
  <q-page padding>
    <div class="row q-col-gutter-x-lg">
      <PostLeftBar class="col-grow" />
      <section class="col-7">
        <!-- <q-card v-for="id in 100" :key="id" @click="goPostDetails(id)">
        <q-card-section>{{ id }}번 게시글</q-card-section>
      </q-card> -->

        <!-- <q-card v-for="id in 100" :key="id">
        <router-link :to="`/posts/${id}`">
          <q-card-section>{{ id }}번 게시글</q-card-section>
        </router-link>
      </q-card> -->
        <PostHeader />
        <PostList :items="posts" />
      </section>
      <PostRightBar class="col-3" @open-write-dialog="openWriteDialog" />
    </div>
    <PostWriteDialog v-model="postDialog" />
  </q-page>
</template>

<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import PostList from 'src/components/apps/post/PostList.vue';
import PostHeader from './components/PostHeader.vue';
import PostLeftBar from './components/PostLeftBar.vue';
import PostRightBar from './components/PostRightBar.vue';
import PostWriteDialog from 'src/components/apps/post/PostWriteDialog.vue';
const router = useRouter();
// const goPostDetails = id => router.push(`/posts/${id}`);
const posts = Array.from(Array(20), (_, index) => ({
  id: 'A' + index,
  title: 'Vue3 Firebase 강의 ' + index,
  content:
    'Lorem ipsum dolor sit amet consectetur adipisicing elit. Adipisci at corrupti quia itaque odit aliquid sapiente praesentium sunt, officia eligendi sequi, voluptatem commodi voluptate suscipit tenetur non explicabo. Eligendi, voluptas.',
  readCount: 1,
  commentCount: 2,
  likeCount: 3,
  bookmarkCount: 4,
  tags: ['html', 'css', 'javascript'],
  uid: 'uid',
  category: '카테고리' + index,
}));

const postDialog = ref(false);
const openWriteDialog = () => {
  postDialog.value = true;
};
</script>

<style lang="scss" scoped></style>
