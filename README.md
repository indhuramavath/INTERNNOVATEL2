# INTERNNOVATEL2
#html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Basic Weather App</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="weather-app">
        <h1 class="location">Hyderabad, India</h1>
        <div class="weather-info">
            <div class="temperature">25°C</div>
            <div class="condition">Sunny</div>
            <div class="additional-info">
                <p>Humidity: 60%</p>
                <p>Wind Speed: 5 km/h</p>
            </div>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>
#css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Arial, sans-serif;
}

body {
    background-color: #f0f4f8;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

.weather-app {
    background: #fff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
    text-align: center;
    width: 300px;
}

.location {
    font-size: 24px;
    font-weight: bold;
    color: #333;
    margin-bottom: 15px;
}

.weather-info .temperature {
    font-size: 48px;
    color: #ff9800;
}

.weather-info .condition {
    font-size: 18px;
    color: #666;
    margin-top: 10px;
}

.additional-info p {
    font-size: 14px;
    color: #777;
    margin-top: 8px;
}


#java script
document.addEventListener('DOMContentLoaded', () => {
    const apiKey = 'your-api-key-here';
    const city = 'Hyderabad';
    
    fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`)
        .then(response => response.json())
        .then(data => {
            document.querySelector('.location').textContent = `${data.name}, ${data.sys.country}`;
            document.querySelector('.temperature').textContent = `${data.main.temp}°C`;
            document.querySelector('.condition').textContent = data.weather[0].main;
            document.querySelector('.additional-info').innerHTML = `
                <p>Humidity: ${data.main.humidity}%</p>
                <p>Wind Speed: ${data.wind.speed} km/h</p>
            `;
        })
        .catch(error => console.error('Error fetching data:', error));
});


