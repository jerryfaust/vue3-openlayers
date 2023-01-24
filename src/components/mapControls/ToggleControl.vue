<template lang="">
<div v-if="false">

</div>
</template>

<script>
import Toggle from 'ol-ext/control/Toggle'

import useControl from '@/composables/useControl'
export default {
    name: 'ol-control-toggle',
    setup(props,context) {
        // activate or deactivate control
        const setActive = (b) => control.value.setActive(b);
        // disable or enable the control
        const setDisable = (b) => control.value.setDisable(b);
        // toggle control state
        const toggle = () => control.value.toggle();

        const {
            control
        } = useControl(Toggle, props,context);

        return {
            control,
            setActive,
            setDisable,
            toggle
        }

    },
    props: {
        html: {
            type: String,
        },
        interaction: {
            type: Object,
        },
        className: {
            type: String,
        },
        title: {
            type: String,
        },
        onToggle: {
            type: Function,
        },
    }
}
</script>

<style lang="">

</style>
