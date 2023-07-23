# Data-visualization-javascript-script.js
script.js
document.addEventListener("DOMContentLoaded", function () {
    const dataForm = document.getElementById("dataForm");
    const dataInput = document.getElementById("dataInput");
    const pieChartCanvas = document.getElementById("pieChart");
    let chart = null;

    dataForm.addEventListener("submit", function (event) {
        event.preventDefault();

        const data = dataInput.value.split(",").map(Number);
        if (!data || !Array.isArray(data) || data.some(isNaN)) {
            alert("Invalid input. Please enter comma-separated numbers.");
            return;
        }

        if (chart) {
            chart.destroy();
        }

        chart = new Chart(pieChartCanvas, {
            type: "pie",
            data: {
                labels: data.map((value, index) => `Data ${index + 1}`),
                datasets: [{
                    data: data,
                    backgroundColor: [
                        "rgba(255, 99, 132, 0.6)",
                        "rgba(54, 162, 235, 0.6)",
                        "rgba(255, 206, 86, 0.6)",
                        "rgba(75, 192, 192, 0.6)",
                        "rgba(153, 102, 255, 0.6)",
                        "rgba(255, 159, 64, 0.6)",
                    ],
                    borderWidth: 1
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false
            }
        });
    });
});

