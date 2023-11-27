<script setup>
import { computed } from "@vue/reactivity";
import { ref } from "vue";

const activeStep = ref(0);

const items = ref([
    {
        label: 'Personal Info'
    },
    {
        label: 'Reservation'
    },
    {
        label: 'Review'
    }
]);

const items2 = ref([
    {
        icon: 'pi pi-user'
    },
    {
        icon: 'pi pi-calendar'
    },
    {
        icon: 'pi pi-check'
    }
]);

let show = computed(() => {
    return items.value[activeStep.value]?.label || "";
})

</script>
<template>
    <div>
    <div class="card">
        <Steps v-model:activeStep="activeStep" :model="items" :readonly="false"/>
        TabContent: {{ show }}
    </div>
    <div class="card">
        
        <Steps :model="items2" v-model:activeStep="activeStep" class="custom-steps" :readonly="false">
            <template #item="{ item, active }">
                    <div :class="['h-1rem w-5rem', { 'bg-primary': active, 'border-primary-500 surface-overlay border-3': !active }]"></div>
            </template>
        </Steps>
    </div>
    </div>
    
</template>