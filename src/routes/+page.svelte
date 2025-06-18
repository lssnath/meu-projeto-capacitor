<script>
    let value = '';
    let result = '';
    let fromUnit = 'm';
    let toUnit = 'km';
    let category = 'distance';
  
    const units = {
      distance: ['m', 'km', 'mi', 'ft', 'yd'],
      weight: ['kg', 'g', 'lb', 'oz'],
      temperature: ['C', 'F', 'K'],
      volume: ['L', 'mL', 'gal', 'oz', 'cup'],
      area: ['m2', 'km2', 'ft2', 'yd2', 'acre'],
    };
  
    const convert = () => {
      if (value === '') {
        result = '';
        return;
      }
  
      if (category === 'distance') {
        result = convertDistance(parseFloat(value), fromUnit, toUnit);
      } else if (category === 'weight') {
        result = convertWeight(parseFloat(value), fromUnit, toUnit);
      } else if (category === 'temperature') {
        result = convertTemperature(parseFloat(value), fromUnit, toUnit);
      } else if (category === 'volume') {
        result = convertVolume(parseFloat(value), fromUnit, toUnit);
      } else if (category === 'area') {
        result = convertArea(parseFloat(value), fromUnit, toUnit);
      }
    };
  
    const convertDistance = (value, from, to) => {
      const conversions = {
        m: { km: 0.001, mi: 0.000621371, ft: 3.28084, yd: 1.09361 },
        km: { m: 1000, mi: 0.621371, ft: 3280.84, yd: 1093.61 },
        mi: { m: 1609.34, km: 1.60934, ft: 5280, yd: 1760 },
        ft: { m: 0.3048, km: 0.0003048, mi: 0.000189394, yd: 0.333333 },
        yd: { m: 0.9144, km: 0.0009144, mi: 0.000568182, ft: 3 },
      };
      
      return value * conversions[from][to];
    };
  
    const convertWeight = (value, from, to) => {
      const conversions = {
        kg: { g: 1000, lb: 2.20462, oz: 35.274 },
        g: { kg: 0.001, lb: 0.00220462, oz: 0.035274 },
        lb: { kg: 0.453592, g: 453.592, oz: 16 },
        oz: { kg: 0.0283495, g: 28.3495, lb: 0.0625 },
      };
      
      return value * conversions[from][to];
    };
  
    const convertTemperature = (value, from, to) => {
      if (from === to) return value;
  
      if (from === 'C') {
        if (to === 'F') return (value * 9/5) + 32;
        if (to === 'K') return value + 273.15;
      }
      if (from === 'F') {
        if (to === 'C') return (value - 32) * 5/9;
        if (to === 'K') return (value - 32) * 5/9 + 273.15;
      }
      if (from === 'K') {
        if (to === 'C') return value - 273.15;
        if (to === 'F') return (value - 273.15) * 9/5 + 32;
      }
    };
  
    const convertVolume = (value, from, to) => {
      const conversions = {
        L: { mL: 1000, gal: 0.264172, oz: 33.814, cup: 4.22675 },
        mL: { L: 0.001, gal: 0.000264172, oz: 0.033814, cup: 0.00422675 },
        gal: { L: 3.78541, mL: 3785.41, oz: 128, cup: 16 },
        oz: { L: 0.0295735, mL: 29.5735, gal: 0.0078125, cup: 0.125 },
        cup: { L: 0.236588, mL: 236.588, gal: 0.0625, oz: 8 },
      };
      
      return value * conversions[from][to];
    };
  
    const convertArea = (value, from, to) => {
      const conversions = {
        m2: { km2: 1e-6, ft2: 10.7639, yd2: 1.19599, acre: 0.000247105 },
        km2: { m2: 1e6, ft2: 10763910.4, yd2: 1195990, acre: 247.105 },
        ft2: { m2: 0.092903, km2: 9.2903e-8, yd2: 0.111111, acre: 2.2957e-5 },
        yd2: { m2: 0.836127, km2: 8.36127e-7, ft2: 9, acre: 0.000206612 },
        acre: { m2: 4046.86, km2: 0.00404686, ft2: 43560, yd2: 4840 },
      };
      
      return value * conversions[from][to];
    };
  </script>
  
  <main>
    <div class="container">
      <h1>Conversor de Unidades</h1>
      <div class="header-image">
        <img src="https://via.placeholder.com/800x300/007BFF/ffffff?text=Conversor+de+Unidades" alt="Imagem de Cabeçalho" />
      </div>
  
      <div class="form-group">
        <label for="value">Valor:</label>
        <input type="number" id="value" bind:value={value} on:input={convert} placeholder="Digite um valor" />
      </div>
  
      <div class="form-group">
        <label for="category">Categoria:</label>
        <select id="category" bind:value={category} on:change={convert}>
          <option value="distance">Distância</option>
          <option value="weight">Peso</option>
          <option value="temperature">Temperatura</option>
          <option value="volume">Volume</option>
          <option value="area">Área</option>
        </select>
      </div>
  
      <div class="form-group">
        <label for="fromUnit">De:</label>
        <select id="fromUnit" bind:value={fromUnit} on:change={convert}>
          {#each units[category] as unit}
            <option value={unit}>{unit}</option>
          {/each}
        </select>
      </div>
  
      <div class="form-group">
        <label for="toUnit">Para:</label>
        <select id="toUnit" bind:value={toUnit} on:change={convert}>
          {#each units[category] as unit}
            <option value={unit}>{unit}</option>
          {/each}
        </select>
      </div>
  
      <div class="result">
        <p>Resultado: <strong>{result}</strong></p>
      </div>
  
      <div class="footer-image">
        <img src="https://via.placeholder.com/800x100/28a745/ffffff?text=Conversor+de+Unidades" alt="Rodapé" />
      </div>
    </div>
  </main>
  
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
  
    body {
      font-family: 'Arial', sans-serif;
      background-color: #f0f0f0;
      color: #333;
      line-height: 1.6;
    }
  
    main {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      padding: 20px;
    }
  
    .container {
      background-color: #fff;
      border-radius: 10px;
      padding: 40px;
      width: 100%;
      max-width: 450px;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    }
  
    h1 {
      text-align: center;
      font-size: 28px;
      margin-bottom: 20px;
      color: #007BFF;
      font-weight: bold;
    }
  
    .form-group {
      margin-bottom: 20px;
    }
  
    label {
      display: block;
      font-size: 14px;
      margin-bottom: 5px;
      font-weight: bold;
      color: #555;
    }
  
    input, select {
      width: 100%;
      padding: 12px;
      border-radius: 8px;
      border: 1px solid #ccc;
      font-size: 16px;
      color: #333;
    }
  
    input:focus, select:focus {
      border-color: #007BFF;
      outline: none;
    }
  
    .result {
      text-align: center;
      font-size: 18px;
      margin-top: 20px;
      color: #28a745;
    }
  
    .result strong {
      font-size: 22px;
      color: #007BFF;
    }
  
    .header-image, .footer-image {
      margin: 20px 0;
      text-align: center;
    }
  
    .header-image img, .footer-image img {
      max-width: 100%;
      border-radius: 8px;
    }
  
    input, select {
      transition: border-color 0.3s;
    }
  </style>


  
  