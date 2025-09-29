<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Soil Health & Plant Data</title>
<style>
  body {
    font-family: Arial, sans-serif;
    margin: 30px;
    background-color: #f2f5f2;
  }
  h1 {
    color: #2f4f2f;
  }
  label {
    font-weight: bold;
  }
  select, input[type="text"], button {
    padding: 8px;
    margin-top: 6px;
    margin-bottom: 12px;
    width: 100%;
    max-width: 300px;
  }
  #results {
    margin-top: 20px;
    padding: 15px;
    background-color: #e6f2e6;
    border-radius: 6px;
    max-width: 500px;
  }
</style>
</head>
<body>

<h1>Soil Health & Plant Data Checker</h1>

<label for="soilType">Select Soil Type:</label>
<select id="soilType">
  <option value="">--Choose Soil Type--</option>
  <option value="sandy">Sandy</option>
  <option value="clay">Clay</option>
  <option value="loamy">Loamy</option>
  <option value="peaty">Peaty</option>
  <option value="chalky">Chalky</option>
  <option value="silty">Silty</option>
</select>

<button onclick="checkSoilData()">Get Soil Data</button>

<div id="results"></div>

<script>
  const soilData = {
    sandy: {
      moisture: "Low (10-20%)",
      health: "Low nutrient retention, requires organic matter",
      plants: ["Carrots", "Radishes", "Potatoes", "Melons"]
    },
    clay: {
      moisture: "High (40-60%)",
      health: "Poor drainage, high nutrient content",
      plants: ["Cabbage", "Broccoli", "Cauliflower", "Beans"]
    },
    loamy: {
      moisture: "Moderate (20-40%)",
      health: "Ideal for most plants, well balanced",
      plants: ["Tomatoes", "Corn", "Lettuce", "Strawberries"]
    },
    peaty: {
      moisture: "High (50-70%)",
      health: "Acidic, rich in organic material",
      plants: ["Blueberries", "Cranberries", "Rhododendrons"]
    },
    chalky: {
      moisture: "Variable but drains quickly",
      health: "Alkaline, may cause iron deficiency",
      plants: ["Beets", "Spinach", "Cabbage"]
    },
    silty: {
      moisture: "Moderate (30-50%)",
      health: "Fertile and holds moisture well",
      plants: ["Rice", "Cotton", "Vegetables"]
    }
  };

  function checkSoilData() {
    const soilType = document.getElementById('soilType').value;
    const resultsDiv = document.getElementById('results');

    if (!soilType) {
      resultsDiv.innerHTML = '<p style="color:red;">Please select a soil type.</p>';
      return;
    }

    const data = soilData[soilType];
    resultsDiv.innerHTML = `
      <h3>Soil Type: ${soilType.charAt(0).toUpperCase() + soilType.slice(1)}</h3>
      <p><strong>Moisture Percentage:</strong> ${data.moisture}</p>
      <p><strong>Soil Health:</strong> ${data.health}</p>
      <p><strong>Plants that grow well:</strong> ${data.plants.join(', ')}</p>
    `;
  }
</script>

</body>
</html>
