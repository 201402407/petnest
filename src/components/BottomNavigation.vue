<template>
    <div class="bottom-navigation">
        <h2>Bottom Navigation Bar</h2>
        <div :class="{ active: isActive('test') }">
            <a @click="moveMenu('test')">test</a>
        </div>
        <div :class="{ active: isActive('main') }">
            <a @click="moveMenu('main')">main</a>
        </div>
        <div :class="{ active: isActive('home') }">
            <a @click="moveMenu('home')">home</a>
        </div>
        <div :class="{ active: isActive('trail') }">
            <a @click="moveMenu('trail')">trail</a>
        </div>
    </div>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator'

@Component
export default class BottomNavigation extends Vue {
    private actived = 'main'

    isActive(selectMenu: string): boolean {
        // console.log("[BottomNavigation.vue] isActive Called!")
        return this.actived === selectMenu
    }

    moveMenu(menu: string) {
        console.log('[BottomNavigation.vue] moveMenu Called!')
        this.actived = menu
        const currentPath = this.$router.currentRoute.query?.menu // TEST 필요
        console.log(currentPath)
        if (currentPath !== menu) {
            this.$emit('selected', menu)
        }
    }
}
</script>
<style>
.bottom-navigation {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
    background-color: aquamarine;
}
</style>
