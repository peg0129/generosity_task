<script setup>
console.log(import.meta.env.VITE_API_KEY)

const resasApiKey = import.meta.env.VITE_API_KEY;

const getResasApi = async () => {
  try {
    const response = await fetch('https://opendata.resas-portal.go.jp/api/v1/prefectures', {headers: {"x-api-key": `${resasApiKey}`}});
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Error fetching posts:', error);
    throw error;
  }
}

const init = async () => {
  const result = await getResasApi()
  console.log(result)
}

init()
</script>

<template>

</template>

<style scoped>

</style>
