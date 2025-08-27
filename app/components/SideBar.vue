<template>
  <div class="fixed top-0 left-0 h-screen w-16 m-0 flex flex-col items-center" style="background-color: var(--bg-light);">
    <div class="flex flex-col items-center justify-center flex-grow px-6">
      <LinkButton link="/" icon="material-symbols:home" class="scale-125"/>
      <LinkButton link="/projects" icon="eos-icons:project" class="scale-125"/>
      <LinkButton link="/contact" icon="material-symbols:contacts" class="scale-125"/>
    </div>

  </div>
</template>
<ChangeThemeButton class="mb-6 scale-125" />
