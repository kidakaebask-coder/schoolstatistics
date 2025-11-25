
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Thailand School Statistics Infographic</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
    body { 
      font-family: 'Segoe UI', Arial, sans-serif; 
      background: #f6f8fc; 
      margin: 0; 
      padding: 0;
    }
    .container {
      max-width: 900px;
      margin: 40px auto;
      background: #fff;
      border-radius: 12px;
      box-shadow: 0 8px 24px rgba(0,0,0,0.08);
      padding: 2rem;
    }
    h1 {
      text-align: center;
      color: #013c7b;
    }
    .stats-overview {
      display: flex;
      justify-content: space-around;
      margin-bottom: 32px;
      flex-wrap: wrap;
      gap: 20px;
    }
    .stat-box {
      flex: 1 1 200px;
      background: #e3eefa;
      border-radius: 10px;
      margin: 0 10px;
      text-align: center;
      padding: 1rem;
      box-shadow: 0 2px 8px rgba(0,0,32,0.06);
    }
    .stat-type {
      margin-bottom: 0.5em;
      font-size: 1.25em;
      font-weight: 600;
    }
    .stat-number {
      font-size: 2.5em;
      color: #0173e6;
      font-weight: bold;
    }
    #piechart {
      width: 100%;
      min-height: 350px;
      margin: auto;
      display: block;
    }
    @media (max-width: 700px) {
      .stats-overview { flex-direction: column; gap: 12px; }
    }
    footer {
      margin-top: 40px;
      text-align: center;
      color: #888;
      font-size: 0.95em;
    }
  </style>
  <!-- Google Charts Loader (Pie Chart) -->
  <script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>
  <script>
    // Example numbers (replace these with latest stats for Thailand)
    const publicSchools = 30000;
    const privateSchools = 3500;
    const internationalSchools = 180;

    google.charts.load('current', {'packages':['corechart']});
    google.charts.setOnLoadCallback(drawChart);

    function drawChart() {
      var data = google.visualization.arrayToDataTable([
        ['School Type', 'Number'],
        ['Public', publicSchools],
        ['Private', privateSchools],
        ['International', internationalSchools]
      ]);

      var options = {
        title: 'Thailand School Type Distribution',
        colors: ['#0173e6', '#17c8a7', '#f39c28'],
        pieSliceText: 'percentage',
        legend: { position: 'bottom' },
        fontName: 'Segoe UI',
        pieHole: 0.4,
        chartArea: {width:"90%",height:"75%"}
      };

      var chart = new google.visualization.PieChart(document.getElementById('piechart'));
      chart.draw(data, options);
    }
  </script>
</head>
<body>
  <div class="container">
    <h1>Schools Statistics in Thailand</h1>
    <div class="stats-overview">
      <div class="stat-box">
        <div class="stat-type">Public Schools</div>
        <div class="stat-number" id="public-num"></div>
      </div>
      <div class="stat-box">
        <div class="stat-type">Private Schools</div>
        <div class="stat-number" id="private-num"></div>
      </div>
      <div class="stat-box">
        <div class="stat-type">International Schools</div>
        <div class="stat-number" id="intl-num"></div>
      </div>
    </div>
    <div id="piechart"></div>
    <footer>
      Data is for infographic demonstration only. Please update figures for accuracy.
    </footer>
  </div>
  <script>
    document.getElementById('public-num').textContent = publicSchools.toLocaleString();
    document.getElementById('private-num').textContent = privateSchools.toLocaleString();
    document.getElementById('intl-num').textContent = internationalSchools.toLocaleString();
  </script>
</body>
</html>
