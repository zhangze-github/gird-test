<template>
    <grid-layout :layout.sync="layout"
                 :col-num="12"
                 :row-height="100"
                 :is-draggable="draggable"
                 :is-resizable="resizable"
                 :vertical-compact="true"
                 :use-css-transforms="true"
    >
    <grid-item v-for="item in layout"
                   :static="item.static"
                   :x="item.x"
                   :y="item.y"
                   :w="item.w"
                   :h="item.h"
                   :i="item.i"
        >
            <iframe src="https://feishu.cn" frameborder="0" class="iframe"></iframe>
        </grid-item>
        <!-- <grid-item v-for="item in layout"
                   :static="item.static"
                   :x="item.x"
                   :y="item.y"
                   :w="item.w"
                   :h="item.h"
                   :i="item.i"
        >
            <span class="text">{{itemTitle(item)}}</span>
        </grid-item> -->
    </grid-layout>
</template>

<script>
import { GridLayout, GridItem } from "vue-grid-layout"

export default {
    components: {
        GridLayout,
        GridItem
    },
    data() {
        return {
            layout: [
                // {"x":0,"y":0,"w":6,"h":6,"i":"0", static: false},
                // {"x":2,"y":0,"w":2,"h":4,"i":"1", static: true},
                {"x":4,"y":0,"w":1,"h":1,"i":"2", static: false},
                {"x":6,"y":0,"w":4,"h":8,"i":"3", static: false},
                {"x":8,"y":0,"w":4,"h":6,"i":"1", static: false},
                // {"x":10,"y":0,"w":2,"h":3,"i":"5", static: false},
                // {"x":0,"y":5,"w":2,"h":5,"i":"6", static: false},
                // {"x":2,"y":5,"w":2,"h":5,"i":"7", static: false},
                // {"x":4,"y":5,"w":2,"h":5,"i":"8", static: false},
                // {"x":6,"y":3,"w":2,"h":4,"i":"9", static: true},
                // {"x":8,"y":4,"w":2,"h":4,"i":"10", static: false},
                // {"x":10,"y":4,"w":2,"h":4,"i":"11", static: false},
                // {"x":0,"y":10,"w":2,"h":5,"i":"12", static: false},
                // {"x":2,"y":10,"w":2,"h":5,"i":"13", static: false},
                // {"x":4,"y":8,"w":2,"h":4,"i":"14", static: false},
                // {"x":6,"y":8,"w":2,"h":4,"i":"15", static: false},
                // {"x":8,"y":10,"w":2,"h":5,"i":"16", static: false},
                // {"x":10,"y":4,"w":2,"h":2,"i":"17", static: false},
                // {"x":0,"y":9,"w":2,"h":3,"i":"18", static: false},
                // {"x":2,"y":6,"w":2,"h":2,"i":"19", static: false}
            ],
            draggable: true,
            resizable: true,
            index: 0
        }
    },
    methods: {
        itemTitle(item) {
            let result = item.i;
            if (item.static) {
                result += " - Static";
            }
            return result;
        }
    }
}
</script>

<style scoped>

iframe{
    width: 100%;
    height: calc(100% - 30px);

    /* border: 1px solid #fff; */
    /* border-radius: 6px; */
    border-top: 30px solid blue;
}
.vue-grid-layout {
    background: #ccc;
    background-position: 10px 10px;
    background-size: calc((100% - 10px) / 12) 110px;
    background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAFsAAABlCAYAAAAiRp9EAAAAAXNSR0IArs4c6QAAAmZJREFUeF7t3FFKw0AYReHGdShYXIi4M3cmLkQq6Dqs5KGlD7bk3AuDJMdX/5NpP4fgROr0cfh63d34eto/3Pz+ZbrVay01mg6f328z2M/x+P6X+dILze3WsO+m6Xl+3/vH+5dbG/b0vekERFCXXHgLM9RO7GJXiF3g0VRsKlbMi13g0VRsKlbMi13g0RRj0wWczwWmPLWkAmJTsWJe7AKPpmJTsWJe7AKPpmJTsWJe7AKPpmJTsWLeR6wFHj5B0qB4batLqZ07u9gCYhd4NBWbihXzYhd4NBWbihXzYhd4NMXYdAHncwFPkLkdLsXGZHkgdm6HS7ExWR6IndvhUmxMlgdi53a4FBuT5YGPWHO78yctln6QQGyxC4GBKX42QoOB7+XfL0XtvI0UP1KxCzyaik3FinmxCzyaYmy6gPO5gCfI3A6XYmOyPBA7t8Ol2JgsD8TO7XApNibLA7FzO1yKjcnywAdRuZ1/PCjscIqP6zTAr2jFAbXzNlJsBrELPJqKTcWKebELPJqKTcWKeYxdrGUKBTxBQrBmXOxGD7ZiQ7BmXOxGD7ZiQ7BmXOxGD7ZiQ7BmXOxGD7Y+9YNgl+P4BEmD4rWtLqV27uxiC4hd4NFUbCpWzItd4NFUbCpWzItd4NEUY9MFnM8FPEHmdrgUG5Plgdi5HS7FxmR5IHZuh0uxMVkeiJ3b4VJsTJYHPmLN7fzkQWGHU3xcpwF+RSsOqN35NnLNZOl/9pr70+Jbu9ZSI7F3u91SrGsbamnvbyMDb3Niiz1QYOBS7myxBwoMXMqdLfZAgYFLubPFHigwcCl39kDsX53rpHXjm3V4AAAAAElFTkSuQmCC);
}

.vue-grid-item:not(.vue-grid-placeholder) {
    background: #eee;
    /* border: 1px solid black; */
}

.vue-grid-item .resizing {
    opacity: 0.9;
}

.vue-grid-item .static {
    background: #cce;
}

.vue-grid-item .text {
    font-size: 24px;
    text-align: center;
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    margin: auto;
    height: 100%;
    width: 100%;
}

.vue-grid-item .no-drag {
    height: 100%;
    width: 100%;
}

.vue-grid-item .minMax {
    font-size: 12px;
}

.vue-grid-item .add {
    cursor: pointer;
}

.vue-draggable-handle {
    position: absolute;
    width: 20px;
    height: 20px;
    top: 0;
    left: 0;
    background: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='10' height='10'><circle cx='5' cy='5' r='5' fill='#999999'/></svg>") no-repeat;
    background-position: bottom right;
    padding: 0 8px 8px 0;
    background-repeat: no-repeat;
    background-origin: content-box;
    box-sizing: border-box;
    cursor: pointer;
}


</style>