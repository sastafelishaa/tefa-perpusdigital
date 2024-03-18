<script setup lang="ts">
import Chart from 'chart.js/auto';

const labels = [
    'Januari',
    'Februari',
    'Maret',
    'April',
    'Mei',
    'Juni',
    'Juli',
    'Agustus',
    'September',
    'Oktober',
    'November',
    'Desember',
  ];

  const data = {
    labels: labels,
    datasets: [{
      label: 'Pengunjung',
      backgroundColor: 'rgb(56, 121, 181)',
      borderColor: 'rgb(56, 121, 181)',
      data: [10, 10, 5, 2, 20, 30, 45, 35, 20, 5, 7, 2],
    }]
  };

  const config = {
    type: 'bar',
    data: data,
    options: {}
  };

  onMounted(() => {
      const myChart = new Chart(
      document.getElementById('myChart'),
      config
    );
  });
  

</script>

<template>
  <div>
    <canvas id="myChart"></canvas>
  </div>
</template>

<style scoped>
canvas {
  width: 50%;
  height: 50%;
}
</style>

