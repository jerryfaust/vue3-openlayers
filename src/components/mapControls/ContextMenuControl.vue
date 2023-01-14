<template lang="">
<div v-if="false">

</div>
</template>

<script>

import ContextMenu from 'ol-contextmenu'

import useControl from '@/composables/useControl'

export default {
    name: 'ol-context-menu',
    // expose the built-in events
    emits: ['beforeopen', 'open', 'close', 'add-menu-entry'],
    setup(props,context) {
        // methods existing in the ol-contextmenu control
        // that should be reachable via ol-context-menu
        const clear = () => control.value.clear();
        const close = () => control.value.close();
        const extend = (arr) => control.value.extend(arr);
        const push = (item) => control.value.push(item);
        const shift = () => control.value.shift();
        const pop = () => control.value.pop();
        const getDefaultItems = () => control.value.getDefaultItems();
        const isOpen = () => control.value.isOpen();
        const updatePosition = (pixel) => control.value.updatePosition(pixel);
        const {
            control
        } = useControl(ContextMenu, props, context);

        // forward events from the ol-contextmenu control
        control.value.on("beforeopen", (event) => {
            context.emit('beforeopen', event)
        })
        control.value.on("open", (event) => {
            context.emit('open', event)
        })
        control.value.on("close", (event) => {
            context.emit('close', event)
        })
        control.value.on("add-menu-entry", (event) => {
            context.emit('add-menu-entry', event)
        })

        return {
            control,
            clear, close, extend, push, shift, pop, getDefaultItems, isOpen, updatePosition
        }

    },
    props: {
        eventType: {
            type: String,
            default: 'contextmenu'
        },
        defaultItems: {
            type: Boolean,
            default:true
        },
        width: {
            type: Number,
            default:150
        },
        items: {
            type: Array,
            default: ()=>[]
        }
    }
}
</script>

<style lang="">

</style>
