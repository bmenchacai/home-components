<script setup>
import { ref } from 'vue'
import { defineProps } from 'vue'

defineProps({
    msg: String,
})

const count = ref(0)
</script>

<template>
    <Head :title="'Vista estática'" />
    <section name="filtro" class="hidden lg:block">
        <div class="flex gap-8 p-4 m-4 rounded-lg shadow-md hide-on-small">
            <form class="flex-grow max-w-sm">
                <label for="filtros" class="block mb-2 text-sm font-medium text-gray-900">Seleccione un filtro</label>
                <select id="filtros" class="custom-input-field border-red-500">
                    <option value="0" selected="">Seleccione</option>
                </select>
            </form>
            <div class="flex-grow">
                <label for="criterio_busqueda" class="block mb-2 text-sm font-medium text-gray-900 border-red-500">Criterio de búsqueda</label>
                <AutoComplete id="custom-autocomplete" />
            </div>
            <div class="flex-grow">
                <label for="periodo_de" class="block mb-2 text-sm font-medium text-gray-900">Periodo de:</label>
                <InputDate id="periodo_de" dateFormat="yyyy MM dd" />
            </div>
            <div class="flex-grow">
                <label for="periodo_al" class="block mb-2 text-sm font-medium text-gray-900">Periodo al:</label>
                <InputDate id="periodo_al" dateFormat="yyyy MM dd" />
            </div>
            <div class="flex items-end">
                <button type="button" class="inline-flex justify-center mr-2 mb-1 py-2 px-4 border border-gray-300 shadow-sm text-sm rounded-md text-white bg-Conexa_Grey100">Reiniciar</button>
                <button type="button" class="inline-flex justify-center mb-1 py-2 px-4 border border-gray-300 shadow-sm text-sm font-medium rounded-md text-white bg-Conexa_Blue100">Buscar</button>
            </div>
        </div>
    </section>

    <section name="tabla">
        <div class="m-4 my-8">
            <ul class="flex flex-wrap text-sm font-medium text-center text-gray-500 border-b border-gray-200 hide-on-small">
                <li class="me-2 cursor-pointer hidden xl:block">
                    <a class="inline-block p-4 rounded-t-lg bg-gray-100 active">Seguimiento</a>
                </li>
                <li class="me-2 cursor-pointer hidden xl:block">
                    <a class="inline-block p-4 rounded-t-lg">Información médica</a>
                </li>
                <li class="me-2 cursor-pointer hidden xl:block">
                    <a class="inline-block p-4 rounded-t-lg">Alta paciente</a>
                </li>
                <li class="me-2 cursor-pointer hidden xl:block">
                    <a class="inline-block p-4 rounded-t-lg">Casos rechazo</a>
                </li>
                <li class="me-2 cursor-pointer hidden xl:block">
                    <a class="inline-block p-4 rounded-t-lg">Consulta general</a>
                </li>
                <li class="me-2 ml-auto">
                    <a class="inline-block p-4 rounded-t-lg">Total de trámites en Seguimiento: <span class="font-bold">0</span></a>
                </li>
            </ul>
            <div class="table-container" style="overflow-x: auto;">
                <table class="w-full text-left text-gray-500">
                    <thead class="text-xs text-white bg-slate-400 focus:ring-4 focus:outline-none text-left">
                        <tr>
                            <th scope="col" class="px-2 py-2">Semáforo</th>
                            <th scope="col" class="px-2 py-2">Folio Conexa Plus</th>
                            <th scope="col" class="px-2 py-2">Folio hospital/Episodio</th>
                            <th scope="col" class="px-2 py-2">Folio aseguradora</th>
                            <th scope="col" class="px-2 py-2">Hospital</th>
                            <th scope="col" class="px-2 py-2">Aseguradora</th>
                            <th scope="col" class="px-2 py-2">Nombre asegurado</th>
                            <th scope="col" class="px-2 py-2">Fecha/Hora ingreso</th>
                            <th scope="col" class="px-2 py-2">Diagnóstico presuntivo</th>
                            <th scope="col" class="px-2 py-2">Tipo de ingreso</th>
                            <th scope="col" class="px-2 py-2">Dictaminador asignado</th>
                            <th scope="col" class="px-2 py-2">Estatus de trámite</th>
                        </tr>
                    </thead>
                    <tbody class="text-sm">
                        <tr class="bg-white border-b">
                            <td class="px-2 py-1 text-center">
                                <span>⬤</span>
                            </td>
                            <td class="px-2 py-1 font-medium text-gray-900 whitespace-nowrap">
                                <a class="underline decoration-solid">Folio</a>
                            </td>
                            <td class="px-2 py-4 whitespace-nowrap text-center">Folio</td>
                            <td class="px-2 py-4 whitespace-nowrap text-center">Folio</td>
                            <td class="px-2 py-4 whitespace-nowrap text-center">Hospital</td>
                            <td class="px-2 py-4 whitespace-nowrap text-center">Aseguradora</td>
                            <td class="px-2 py-4 whitespace-nowrap text-center">Nombre asegurado</td>
                            <td class="px-2 py-4 whitespace-nowrap text-center">Fecha/Hora ingreso</td>
                            <td class="px-2 py-4 whitespace-nowrap text-center">Diagnóstico presuntivo</td>
                            <td class="px-2 py-4 whitespace-nowrap text-center">Tipo de ingreso</td>
                            <td class="px-2 py-4 whitespace-nowrap text-center">Dictaminador asignado</td>
                            <td class="px-2 py-4 whitespace-nowrap text-center">Estatus de trámite</td>
                        </tr>
                    </tbody>
                </table>
                <div class="m-4">
                    <div class="relative mb-10 rounded border-blue-400 bg-blue-100 px-4 py-3 text-lg text-Conexa_Blue140" role="alert">
                        <strong class="font-bold text-base">Sin información</strong>
                        <p class="text-sm">Actualmente no hay datos disponibles para mostrar.</p>
                    </div>
                </div>
            </div>
        </div>

        <div class="flex justify-center text-center my-8 gap-4">
            <Link href="/" type="button" class="inline-flex justify-center mb-2 py-1 px-4 border border-gray-300 shadow-sm text-sm font-medium rounded-md text-white bg-Conexa_Grey100">Atrás</Link>
        </div>
    </section>
</template>