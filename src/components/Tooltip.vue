<template>
    <div>
        <button data-tooltip-target="tooltip-info-general"
                @mouseover="showTooltipInfoGeneral"
                @mouseleave="hideTooltipInfoGeneral"
                data-tooltip-placement="bottom">Elemento</button>

        <div id="tooltip-info-general"
             style="display: none;"
             class="absolute z-10 mt-2 p-4 text-xs text-black rounded shadow-md text-left space-y-2">
            <div>Mesa de trabajo: <span class="font-bold">Hospital/Dictamen médico</span></div>
            <div>Dictaminador: <span class="font-bold">Luis Medina</span></div>
            <div>Actividad pendiente: <span class="font-bold">Pendiente de dictamen</span></div>
            <div>Días expirado: <span class="font-bold">2</span></div>
            <div>Fecha de captura de admisión hospitalaria: <span class="font-bold">12/02/2023</span></div>
        </div>

    </div>
</template>

<script>
export default {
    methods: {
        showTooltipInfoGeneral() {
            document.querySelector('#tooltip-info-general').style.display = 'block';
        },
        hideTooltipInfoGeneral() {
            document.querySelector('#tooltip-info-general').style.display = 'none';
        },
    },
};
</script>