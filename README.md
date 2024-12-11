<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Traffic Light Simulator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 0;
            padding: 0;
            background-color:  pink;
            color: #333;
        }

        h1 {
            color: #333;
            padding: 20px;
            margin: 20px 0;
            font-size: 2em;
            display: inline-block;
        }

        .traffic-light {
            width: 100px;
            height: 300px;
            background-color: #333;
            margin: 50px auto;
            padding: 10px;
            border-radius: 20px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .light {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            background-color: #ccc;
            transition: background-color 0.5s ease;
        }

        .red-on {
            background-color: #e74c3c;
        }

        .yellow-on {
            background-color: #f39c12;
        }

        .green-on {
            background-color: #2ecc71;
        }

        button {
            padding: 12px 25px;
            font-size: 18px;
            cursor: pointer;
            margin-top: 30px;
            display: block;
            margin-left: auto;
            margin-right: auto;
            border-radius: 25px;
            border: none;
            background-color: #3498db;
            color: white;
            transition: background-color 0.3s, transform 0.2s ease;
        }

        button:hover {
            background-color: #2980b9;
            transform: scale(1.05);
        }

        button:active {
            background-color: #1d6f99;
        }

    </style>
</head>
<body>

    <h1>Traffic Light Simulator</h1>
    
    <div id="traffic-light" class="traffic-light">
        <div id="red" class="light"></div>
        <div id="yellow" class="light"></div>
        <div id="green" class="light"></div>
    </div>

    <button onclick="changeLight()">Change Light</button>
    <button onclick="startCycle()">Start Automatic Cycle</button>

    <script>
        let currentLight = 0;
        let cycleInterval;

        function changeLight() {
            resetLights();

            if (currentLight === 0) {
                document.getElementById('red').classList.add('red-on');
                currentLight = 1;
            } else if (currentLight === 1) {
                document.getElementById('yellow').classList.add('yellow-on');
                currentLight = 2;
            } else {
                document.getElementById('green').classList.add('green-on');
                currentLight = 0;
            }
        }

        function resetLights() {
            document.getElementById('red').classList.remove('red-on');
            document.getElementById('yellow').classList.remove('yellow-on');
            document.getElementById('green').classList.remove('green-on');
        }

        function startCycle() {
            if (cycleInterval) {
                clearInterval(cycleInterval);
            }
            cycleInterval = setInterval(changeLight, 2000);
        }
    </script>

</body>
</html>
