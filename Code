export const handler = async (event, context) => {

 

    let weatherData = await send()
    let data = weatherData.sensors[2].data[0] // TODO change to handle this more generally
    // Create an HTML string with the data
    const htmlContent = `<html>
      <head>
        <link rel="stylesheet" type="text/css" href="//fonts.googleapis.com/css?family=Vollkorn" />
        <title>Weather Data</title>
        <style>
            body {
                background-color: #FFFFFF; /*White */
                color: #144734; /* Piedmont Green */
                font-family: Vollkorn, sans-serif;
                margin: 0;
                display: table;
                width: 100%;
                height: 100vh;
                border: 20px solid #144734;
                border-radius: 25px;
                box-sizing: border-box;
            }
            .center-content{
                display: table-cell;
                text-align: center;
                vertical-align: middle;
                
            }
            h1 {
                font-size: 2.5em;
                color: #B5A268; /* Yohanian Gold */
                background-color: #144734; /* Piedmont Green */
                display: inline-block;
                padding: 10px;
                border-radius: 10px;
            }
            p {
                font-size: 1.5em;
                color: #144734; /* Piedmont Green */
                
            }
        </style>
      </head>
      <body>
        <div class= "center-content">
            <h1>Piedmont Weather Station Data</h1>
            <p>Temperature: ${data.temp}&deg F</p>
            <p>Humidity: ${data.hum}%</p>
            <p>Wind Speed: ${data.wind_speed_avg_last_10_min} m/s</p>
            <p>Wind Gusting: ${data.wind_speed_hi_last_2_min} m/s</p>
            <p>Rainfall (15 Min): ${data.rainfall_last_15_min_in} inches</p>
            <p>Rainfall (24 Hrs): ${data.rainfall_last_24_hr_in} inches</p>
            <!-- Add more data points here -->
        </div>
      </body>
    </html>`;

 

    return {
        statusCode: 200,
        body: htmlContent,
        headers: {'Content-Type': 'text/html'}
    }

 

};

 

async function send() {
    const key = 'c5hl3euhqgih7xk5yonp6uch8apbojmb';
    const station_id = '48e9f1e1-108e-449d-a8bb-18126f248576';
    const url = `https://api.weatherlink.com/v2/current/${station_id}?api-key=${key}`;

 

    const headers = {'X-Api-Secret': 'fqfj2rzo9ew4ngxacffkxyrarj06nppo'}
    const response = await fetch(url, {headers: headers})

 

    if (!response.ok) 
        throw new Error('HTTP error! status: ${response.status}');
    else
        return response.json()
}
