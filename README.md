<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>TDS Monitor</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background-color: #f5f5f5;
      padding: 50px;
    }
    h1 {
      color: #333;
    }
    .value-box {
      font-size: 24px;
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <h1>Water Quality Monitor</h1>
  <div class="value-box">
    <strong>TDS Value: </strong><span id="tdsValue">-- ppm</span>
  </div>

  <script>
    // Optional: Simulate live TDS value updates from device
    function fetchTDS() {
      fetch('/tds') // Example endpoint, needs to be implemented on device
        .then(res => res.text())
        .then(data => {
          document.getElementById('tdsValue').textContent = data + " ppm";
        })
        .catch(() => {
          document.getElementById('tdsValue').textContent = "Error";
        });
    }

    // Auto-refresh every 15 seconds
    setInterval(fetchTDS, 15000);
    fetchTDS(); // Initial load
  </script>
</body>
</html>
