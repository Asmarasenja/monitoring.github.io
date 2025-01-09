<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Monitoring Progress</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        .rotate-270 {
            transform: rotate(270deg);
        }

        @media print {
            body * {
                visibility: hidden;
            }

            .print-area, .print-area * {
                visibility: visible;
            }

            .print-area {
                position: absolute;
                left: 0;
                top: 0;
                width: 100%;
            }
        }
    </style>
</head>
<body class="bg-gray-100 p-6">
    <div class="text-center text-2xl font-bold text-gray-700 mb-6">Target Cabang <span class="text-purple-600">100%</span></div>
    <div class="text-center text-xl font-semibold text-gray-800 mb-4">KC CIRUAS NAGA HITAM</div>
    <div class="text-center text-lg font-semibold text-gray-700 mb-6">Monitoring Progress Kolektibilitas Mingguan</div>

    <!-- Tombol Print -->
    <div class="mb-4 text-right">
        <button onclick="printTable()" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
            Print
        </button>
    </div>

    <!-- Area yang Akan Dicetak -->
    <div class="print-area overflow-x-auto shadow-md rounded-lg">
        <table class="table-auto border-collapse border border-gray-300 w-full text-sm">
            <thead>
                <tr>
                    <th class="border border-gray-300 bg-gray-200 p-3" colspan="6">Minggu Lalu</th>
                    <th class="border border-gray-300 bg-gray-200 p-3" colspan="6">Minggu Ini</th>
                    <th class="border border-gray-300 bg-gray-200 p-3" colspan="8">Hasil</th>
                </tr>
                <tr>
                    <th class="border border-gray-300 bg-blue-500 text-white p-2">No</th>
                    <th class="border border-gray-300 bg-blue-500 text-white p-2">Petugas</th>
                    <th class="border border-gray-300 bg-blue-500 text-white p-2">Target Minggu Lalu</th>
                    <th class="border border-gray-300 bg-blue-500 text-white p-2">Senin</th>
                    <th class="border border-gray-300 bg-blue-500 text-white p-2">Selasa</th>
                    <th class="border border-gray-300 bg-blue-500 text-white p-2">Rabu</th>
                    <th class="border border-gray-300 bg-blue-500 text-white p-2">Kamis</th>
                    <th class="border border-gray-300 bg-blue-500 text-white p-2">Total</th>
                    <th class="border border-gray-300 bg-blue-500 text-white p-2">Target Minggu Ini</th>
                    <th class="border border-gray-300 bg-blue-500 text-white p-2">Senin</th>
                    <th class="border border-gray-300 bg-blue-500 text-white p-2">Selasa</th>
                    <th class="border border-gray-300 bg-blue-500 text-white p-2">Rabu</th>
                    <th class="border border-gray-300 bg-blue-500 text-white p-2">Kamis</th>
                    <th class="border border-gray-300 bg-blue-500 text-white p-2">Total</th>
                    <th class="border border-gray-300 bg-green-500 text-white p-2">Progress</th>
                    <th class="border border-gray-300 bg-green-500 text-white p-2">Senin</th>
                    <th class="border border-gray-300 bg-green-500 text-white p-2">Selasa</th>
                    <th class="border border-gray-300 bg-green-500 text-white p-2">Rabu</th>
                    <th class="border border-gray-300 bg-green-500 text-white p-2">Kamis</th>
                    <th class="border border-gray-300 bg-green-500 text-white p-2">Jumlah Collect</th>
                    <th class="border border-gray-300 bg-green-500 text-white p-2">Pencapaian</th>
                </tr>
            </thead>
            <tbody>
                <!-- Template untuk tiap petugas -->
                <tr class="hover:bg-gray-100" id="row-1">
                    <td class="border border-gray-300 p-2 text-center">1</td>
                    <td class="border border-gray-300 p-2 bg-orange-200 text-center">ARNOLD JOSUA NAHATAN</td>
                    <td class="border border-gray-300 p-2 text-center">11</td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" value="2" id="last-monday-1" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" value="3" id="last-tuesday-1" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" value="3" id="last-wednesday-1" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" value="3" id="last-thursday-1" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center" id="last-total-1">11</td>
                    <td class="border border-gray-300 p-2 text-center">12</td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" id="this-monday-1" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" id="this-tuesday-1" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" id="this-wednesday-1" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" id="this-thursday-1" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center" id="this-total-1">0</td>
                    <td class="border border-gray-300 p-2 text-center">80%</td>
                    <td class="border border-gray-300 p-2 text-center" id="result-monday-1">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="result-tuesday-1">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="result-wednesday-1">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="result-thursday-1">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="total-collect-1">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="achievement-1">0%</td>
                </tr>

                <!-- petugas -->
                <tr class="hover:bg-gray-100" id="row-2">
                    <td class="border border-gray-300 p-2 text-center">2</td>
                    <td class="border border-gray-300 p-2 bg-orange-200 text-center">SETIYADI</td>
                    <td class="border border-gray-300 p-2 text-center">13</td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" value="2" id="last-monday-2" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" value="3" id="last-tuesday-2" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" value="3" id="last-wednesday-2" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" value="3" id="last-thursday-2" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center" id="last-total-2">11</td>
                    <td class="border border-gray-300 p-2 text-center">12</td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" id="this-monday-2" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" id="this-tuesday-2" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" id="this-wednesday-2" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" id="this-thursday-2" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center" id="this-total-2">0</td>
                    <td class="border border-gray-300 p-2 text-center">80%</td>
                    <td class="border border-gray-300 p-2 text-center" id="result-monday-2">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="result-tuesday-2">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="result-wednesday-2">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="result-thursday-2">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="total-collect-2">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="achievement-2">0%</td>
                </tr>
                
                <tr class="hover:bg-gray-100" id="row-3">
                    <td class="border border-gray-300 p-2 text-center">3</td>
                    <td class="border border-gray-300 p-2 bg-orange-200 text-center">JUNENI</td>
                    <td class="border border-gray-300 p-2 text-center">13</td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" value="2" id="last-monday-3" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" value="3" id="last-tuesday-3" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" value="3" id="last-wednesday-3" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" value="3" id="last-thursday-3" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center" id="last-total-3">11</td>
                    <td class="border border-gray-300 p-2 text-center">12</td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" id="this-monday-3" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" id="this-tuesday-3" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" id="this-wednesday-3" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" id="this-thursday-3" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center" id="this-total-3">0</td>
                    <td class="border border-gray-300 p-2 text-center">80%</td>
                    <td class="border border-gray-300 p-2 text-center" id="result-monday-3">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="result-tuesday-3">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="result-wednesday-3">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="result-thursday-3">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="total-collect-3">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="achievement-3">0%</td>
                </tr>

                <tr class="hover:bg-gray-100" id="row-4">
                    <td class="border border-gray-300 p-2 text-center">4</td>
                    <td class="border border-gray-300 p-2 bg-orange-200 text-center">SUMINAH</td>
                    <td class="border border-gray-300 p-2 text-center">13</td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" value="2" id="last-monday-4" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" value="3" id="last-tuesday-4" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" value="3" id="last-wednesday-4" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" value="3" id="last-thursday-4" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center" id="last-total-4">11</td>
                    <td class="border border-gray-300 p-2 text-center">12</td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" id="this-monday-4" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" id="this-tuesday-4" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" id="this-wednesday-4" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" id="this-thursday-4" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center" id="this-total-4">0</td>
                    <td class="border border-gray-300 p-2 text-center">80%</td>
                    <td class="border border-gray-300 p-2 text-center" id="result-monday-4">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="result-tuesday-4">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="result-wednesday-4">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="result-thursday-4">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="total-collect-4">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="achievement-4">0%</td>
                </tr>

                <tr class="hover:bg-gray-100" id="row-5">
                    <td class="border border-gray-300 p-2 text-center">5</td>
                    <td class="border border-gray-300 p-2 bg-orange-200 text-center">SOLIYAH</td>
                    <td class="border border-gray-300 p-2 text-center">13</td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" value="2" id="last-monday-5" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" value="3" id="last-tuesday-5" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" value="3" id="last-wednesday-5" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" value="3" id="last-thursday-5" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center" id="last-total-5">11</td>
                    <td class="border border-gray-300 p-2 text-center">12</td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" id="this-monday-5" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" id="this-tuesday-5" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" id="this-wednesday-5" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center">
                        <input type="number" class="w-full p-1 border border-gray-300 rounded" id="this-thursday-5" oninput="calculateTotals()">
                    </td>
                    <td class="border border-gray-300 p-2 text-center" id="this-total-5">0</td>
                    <td class="border border-gray-300 p-2 text-center">80%</td>
                    <td class="border border-gray-300 p-2 text-center" id="result-monday-5">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="result-tuesday-5">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="result-wednesday-5">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="result-thursday-5">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="total-collect-5">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="achievement-5">0%</td>
                </tr>
                <!-- Tambahkan petugas lain di sini -->
            </tbody>
            <tfoot>
                <tr class="bg-gray-200 font-bold">
                    <td class="border border-gray-300 p-2 text-center" colspan="3">Total Keseluruhan</td>
                    <td class="border border-gray-300 p-2 text-center" id="total-last-monday">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="total-last-tuesday">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="total-last-wednesday">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="total-last-thursday">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="total-last-week">0</td>
                    <td class="border border-gray-300 p-2 text-center">-</td>
                    <td class="border border-gray-300 p-2 text-center" id="total-this-monday">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="total-this-tuesday">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="total-this-wednesday">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="total-this-thursday">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="total-this-week">0</td>
                    <td class="border border-gray-300 p-2 text-center">-</td>
                    <td class="border border-gray-300 p-2 text-center" id="total-result-monday">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="total-result-tuesday">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="total-result-wednesday">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="total-result-thursday">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="total-collect-all">0</td>
                    <td class="border border-gray-300 p-2 text-center" id="overall-achievement">0%</td>
                </tr>
            </tfoot>
        </table>
    </div>

    <script>
        function calculateTotals() {
    const rows = document.querySelectorAll('tbody tr');
    const totals = {
        lastMonday: 0,
        lastTuesday: 0,
        lastWednesday: 0,
        lastThursday: 0,
        thisMonday: 0,
        thisTuesday: 0,
        thisWednesday: 0,
        thisThursday: 0,
        resultMonday: 0,
        resultTuesday: 0,
        resultWednesday: 0,
        resultThursday: 0,
        collectAll: 0
    };

    rows.forEach((row, index) => {
        const lastMonday = Number(row.querySelector(`#last-monday-${index + 1}`)?.value || 0);
        const lastTuesday = Number(row.querySelector(`#last-tuesday-${index + 1}`)?.value || 0);
        const lastWednesday = Number(row.querySelector(`#last-wednesday-${index + 1}`)?.value || 0);
        const lastThursday = Number(row.querySelector(`#last-thursday-${index + 1}`)?.value || 0);
        const lastTotal = lastMonday + lastTuesday + lastWednesday + lastThursday;

        const thisMonday = Number(row.querySelector(`#this-monday-${index + 1}`)?.value || 0);
        const thisTuesday = Number(row.querySelector(`#this-tuesday-${index + 1}`)?.value || 0);
        const thisWednesday = Number(row.querySelector(`#this-wednesday-${index + 1}`)?.value || 0);
        const thisThursday = Number(row.querySelector(`#this-thursday-${index + 1}`)?.value || 0);
        const thisTotal = thisMonday + thisTuesday + thisWednesday + thisThursday;

        const resultMonday = thisMonday;
        const resultTuesday = thisTuesday;
        const resultWednesday = thisWednesday;
        const resultThursday = thisThursday;

        const collect = resultMonday + resultTuesday + resultWednesday + resultThursday;

        // Update individual results
        row.querySelector(`#result-monday-${index + 1}`).textContent = resultMonday;
        row.querySelector(`#result-tuesday-${index + 1}`).textContent = resultTuesday;
        row.querySelector(`#result-wednesday-${index + 1}`).textContent = resultWednesday;
        row.querySelector(`#result-thursday-${index + 1}`).textContent = resultThursday;
        row.querySelector(`#total-collect-${index + 1}`).textContent = collect;

        // Update total last and this totals
        row.querySelector(`#last-total-${index + 1}`).textContent = lastTotal;
        row.querySelector(`#this-total-${index + 1}`).textContent = thisTotal;

        // Calculate and update achievement for the row
        const achievement = lastTotal ? ((collect / lastTotal) * 100).toFixed(2) : 0;
        row.querySelector(`#achievement-${index + 1}`).textContent = `${achievement}%`;

        // Aggregate totals
        totals.lastMonday += lastMonday;
        totals.lastTuesday += lastTuesday;
        totals.lastWednesday += lastWednesday;
        totals.lastThursday += lastThursday;
        totals.thisMonday += thisMonday;
        totals.thisTuesday += thisTuesday;
        totals.thisWednesday += thisWednesday;
        totals.thisThursday += thisThursday;
        totals.resultMonday += resultMonday;
        totals.resultTuesday += resultTuesday;
        totals.resultWednesday += resultWednesday;
        totals.resultThursday += resultThursday;
        totals.collectAll += collect;
    });

    // Update footer totals for each day
    document.getElementById('total-last-monday').textContent = totals.lastMonday;
    document.getElementById('total-last-tuesday').textContent = totals.lastTuesday;
    document.getElementById('total-last-wednesday').textContent = totals.lastWednesday;
    document.getElementById('total-last-thursday').textContent = totals.lastThursday;
    document.getElementById('total-this-monday').textContent = totals.thisMonday;
    document.getElementById('total-this-tuesday').textContent = totals.thisTuesday;
    document.getElementById('total-this-wednesday').textContent = totals.thisWednesday;
    document.getElementById('total-this-thursday').textContent = totals.thisThursday;
    document.getElementById('total-result-monday').textContent = totals.resultMonday;
    document.getElementById('total-result-tuesday').textContent = totals.resultTuesday;
    document.getElementById('total-result-wednesday').textContent = totals.resultWednesday;
    document.getElementById('total-result-thursday').textContent = totals.resultThursday;

    // Calculate and update total last week and total this week
    const totalLastWeek = totals.lastMonday + totals.lastTuesday + totals.lastWednesday + totals.lastThursday;
    const totalThisWeek = totals.thisMonday + totals.thisTuesday + totals.thisWednesday + totals.thisThursday;

    document.getElementById('total-last-week').textContent = totalLastWeek;
    document.getElementById('total-this-week').textContent = totalThisWeek;

    // Update total collected across all days
    document.getElementById('total-collect-all').textContent = totals.collectAll;

    // Update overall achievement
    const achievement = totalLastWeek ? ((totals.collectAll / totalLastWeek) * 100).toFixed(2) : 0;
    document.getElementById('overall-achievement').textContent = `${achievement}%`;
    
}

    
        function printTable() {
            window.print();
        }
    </script>
    
    
    
</body>
</html>
