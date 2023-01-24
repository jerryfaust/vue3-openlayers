<template lang="">
<slot></slot>
</template>

<script>

import Bar from 'ol-ext/control/Bar'

import useControl from '@/composables/useControl'
import {provide} from "vue"
export default {
    name: 'ol-control-bar',
    setup(props,context) {

        const getControls = () => control.value.getControls();
        const getControlsByName = (n) => control.value.getControlsByName(n);

        const {
            control
        } = useControl(Bar, props,context);

        provide('controlBar',control)

        return {
            control,
            getControls,
            getControlsByName
        }

    },
    props: {
        toggleOne: {
            type: Boolean,
            default:true
        },
        group: {
             type: Boolean,
            default:true
        },

    }
}
</script>

<style lang="">

</style>
