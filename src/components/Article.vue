<template>
  <article>
    <div>Default:
      <slot />
    </div>
    <div>Title:
      <slot name="title" />
    </div>
    <div>Excerpt:
      <slot name="excerpt" />
    </div>
  </article>
</template>