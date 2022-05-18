<template>
    <div class="custom-chart-tooltip">
        <div class="apexcharts-tooltip-title">
            {{ config.title }}
        </div>
        <div
            class="apexcharts-tooltip-series-group apexcharts-active"
            v-for="(element, index) in config.elements"
            :key="index"
        >
            <span
                class="apexcharts-tooltip-marker"
                :style="{ backgroundColor: element.markerColor }"
            />
            <div class="apexcharts-tooltip-text">
                <div class="apexcharts-tooltip-y-group">
                    <a
                        v-if="element.link.length > 0"
                        :href="element.link"
                        target="_blank"
                        class="apexcharts-tooltip-text-y-label"
                    >
                        <span>{{ element.label }}</span>
                    </a>
                    <span v-else class="apexcharts-tooltip-text-y-label">
                        {{ element.label }}
                    </span>
                    <span>: </span>
                    <span class="apexcharts-tooltip-text-y-value"
                        >{{ element.value }}
                    </span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "CustomChartTooltip",
    props: {
        config: Object,
    },
};
</script>

<style lang="scss" scoped>
.apexcharts-tooltip-title {
    font-family: Helvetica, Arial, sans-serif;
    font-size: 12px;
}

.apexcharts-tooltip-series-group {
    order: 1;
    display: flex;
}

.apexcharts-tooltip-text {
    font-family: Helvetica, Arial, sans-serif;
    font-size: 12px;
}

.apexcharts-tooltip-y-group > a:hover {
    text-decoration: underline;
    cursor: pointer;
}
</style>