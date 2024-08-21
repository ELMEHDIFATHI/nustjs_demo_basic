<template>
       
    
      <div v-if="product">
        <Head>
      <Title>Nuxt Dojo | {{ product.title }}</Title>
      <Meta name="description" :content="product.description" />
    </Head>
    <ProductDetails :product="product" />
  </div>
  </template>
  
  <script setup>
  const { id } = useRoute().params
  
  definePageMeta({
    layout: 'products',
  });
  
  const uri = 'https://fakestoreapi.com/products/' + id
  
   //  fetch the products
   const { data: product, error } = await useFetch(uri, { key: id });

   if (error.value || !product.value) {
  throw createError({ statusCode: 404, statusMessage: 'Product not found' });
}
  </script>
  
  <style scoped>
  /* Add your styles here */
  </style>
  