<template>
  <main class="lightmode">
    <AppHeader />

    <section>
      <SignatureStats />
      <SignatureDetail />

      <ChecksStream :refresh-key="refreshKey" />

      <CreateSignature @signed="refreshKey ++" />
    </section>
  </main>
</template>

<script setup>
import '~/styles/index.css'
const { load } = useSignatures()

const refreshKey = ref(1)

onMounted(() => load())
</script>


<style lang="postcss" scoped>
main {
  min-height: 100dvh;
  display: flex;
  flex-direction: column;
}

main > section {
  display: flex;
  flex-direction: column;
  height: 100%;
  width: 100%;
  width: var(--main-content-width);
  max-width: var(--main-content-max-width);
  flex-grow: 1;
  background: var(--gray-z-0);
  box-shadow: var(--shadow);
  margin: 0 auto;

  :deep(> aside) {
    &:first-of-type {
      @media (--lg) {
        margin-top: 0;
      }
    }

    &:last-of-type {
      margin-bottom: var(--padding-lg);
    }
  }
}
</style>
