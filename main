[
    {
        "id": "7ac9fc08.853604",
        "type": "tab",
        "label": "Temperature Nodes"
    },
    {
        "id": "c61f4ca4.39e0b",
        "type": "mqtt in",
        "z": "7ac9fc08.853604",
        "name": "MQTT: emonhub/rx/#",
        "topic": "emonhub/rx/#",
        "qos": "2",
        "broker": "dcdae49e.232518",
        "x": 140,
        "y": 60,
        "wires": [
            [
                "f69dd54d.096228"
            ]
        ]
    },
    {
        "id": "923cb68f.6dc348",
        "type": "switch",
        "z": "7ac9fc08.853604",
        "name": "Separate Nodes",
        "property": "topic",
        "propertyType": "msg",
        "rules": [
            {
                "t": "eq",
                "v": "emonhub/rx/21/values",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "emonhub/rx/22/values",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "emonhub/rx/23/values",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "emonhub/rx/24/values",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "emonhub/rx/17/values",
                "vt": "str"
            }
        ],
        "checkall": "true",
        "outputs": 5,
        "x": 120,
        "y": 300,
        "wires": [
            [
                "f8d114e9.072ee8"
            ],
            [
                "b4aa3a62.4b55c8"
            ],
            [
                "a47c3ee4.5b83c"
            ],
            [
                "6dddc91e.922238"
            ],
            [
                "4342c77.f927a38"
            ]
        ]
    },
    {
        "id": "f69dd54d.096228",
        "type": "csv",
        "z": "7ac9fc08.853604",
        "name": "Decode MQTT payload --> JavaScript Object",
        "sep": ",",
        "hdrin": "",
        "hdrout": "",
        "multi": "one",
        "ret": "\\n",
        "temp": "temperature,sensorRetries,batteryVoltage",
        "x": 220,
        "y": 120,
        "wires": [
            [
                "7fe2ba66.801d44"
            ]
        ]
    },
    {
        "id": "7fe2ba66.801d44",
        "type": "function",
        "z": "7ac9fc08.853604",
        "name": "Set common node properties",
        "func": "msg.twitterRecipient = '@FriendlyKiwi'\nmsg.temperature = msg.payload.temperature / 100;\nmsg.batteryVoltage = msg.payload.batteryVoltage / 1000;\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 176.25,
        "y": 180.00000286102295,
        "wires": [
            [
                "923cb68f.6dc348"
            ]
        ]
    },
    {
        "id": "74d89ee3.8b276",
        "type": "function",
        "z": "7ac9fc08.853604",
        "name": "Compose Message",
        "func": "if(msg.temperature < msg.lowTemperatureThreshold)\n    {\n        node.log(msg.lowTemperatureMessage);\n        msg.payload = msg.lowTemperatureMessage;\n        return msg;\n    }\nelse if(msg.temperature > msg.highTemperatureThreshold)\n    {\n        node.log(msg.highTemperatureMessage);\n        msg.payload = msg.highTemperatureMessage;\n        return msg;\n    }\n    \nif(msg.batteryVoltage < msg.lowBatteryVoltage)\n    {\n       node.log(msg.lowBatteryMessage);\n        msg.payload = msg.lowBatteryMessage;\n        return msg; \n    }",
        "outputs": 1,
        "noerr": 0,
        "x": 964,
        "y": 303,
        "wires": [
            [
                "4d22710.9fa5b9",
                "4eec21c7.e6c51"
            ]
        ]
    },
    {
        "id": "f8d114e9.072ee8",
        "type": "function",
        "z": "7ac9fc08.853604",
        "name": "Node 21: Living Area : Unique Properties",
        "func": "msg.lowTemperatureThreshold = 5;\nmsg.highTemperatureThreshold = 32;\nmsg.lowBatteryVoltage = 2.40;\nmsg.lowTemperatureMessage = 'Temperature low in Living Area: ' + msg.temperature + ' °C\\n\\n';\nmsg.highTemperatureMessage = 'Temperature high in Living Area: ' + msg.temperature + ' °C\\n\\n';\nmsg.lowBatteryMessage = 'Battery voltage low in Living Area node: ' + msg.batteryVoltage + 'Volts'; \nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 414,
        "y": 243,
        "wires": [
            [
                "3d57d8d8.c2a828",
                "74f77ef1.3c65d",
                "7bdc8a26.e014b4"
            ]
        ]
    },
    {
        "id": "6dddc91e.922238",
        "type": "function",
        "z": "7ac9fc08.853604",
        "name": "Node 24: Master Bedroom : Unique Properties",
        "func": "msg.lowTemperatureThreshold = 18;\nmsg.highTemperatureThreshold = 32;\nmsg.lowBatteryVoltage = 2.40;\nmsg.lowTemperatureMessage = 'Temperature low in the Master Bedroom: ' + msg.temperature + ' °C\\n\\n';\nmsg.highTemperatureMessage = 'Temperature high in the Master Bedroom: ' + msg.temperature + ' °C\\n\\n';\nmsg.lowBatteryMessage = 'Battery voltage low in the Master Bedroom: ' + msg.batteryVoltage + 'Volts'; \nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 434,
        "y": 363,
        "wires": [
            [
                "e8aa247.f1755d8",
                "9db12edd.f8d6f"
            ]
        ]
    },
    {
        "id": "a47c3ee4.5b83c",
        "type": "function",
        "z": "7ac9fc08.853604",
        "name": "Node 23: James' Bedroom : Unique Properties",
        "func": "msg.lowTemperatureThreshold = 18;\nmsg.highTemperatureThreshold = 32;\nmsg.lowBatteryVoltage = 2.40;\nmsg.lowTemperatureMessage = 'The temperature is ' + msg.temperature + ' °C' + ' in James\\' bedroom.  You may want to check for open windows or turn the heating on in zone 2.';\nmsg.highTemperatureMessage = 'Temperature high in James\\' bedroom: ' + msg.temperature + ' °C\\n\\n';\nmsg.lowBatteryMessage = 'Battery voltage low in James\\' bedroom: ' + msg.batteryVoltage + 'Volts'; \nreturn msg;\n\n// *** Old Messages ***\n// msg.lowTemperatureMessage = 'Temperature low in James\\' bedroom: ' + msg.temperature + ' °C\\n\\n';",
        "outputs": 1,
        "noerr": 0,
        "x": 434,
        "y": 324,
        "wires": [
            [
                "3e49872e.c1b678",
                "62d30d51.3545d4"
            ]
        ]
    },
    {
        "id": "b4aa3a62.4b55c8",
        "type": "function",
        "z": "7ac9fc08.853604",
        "name": "Node 22: Daniel's Bedroom : Unique Properties",
        "func": "msg.lowTemperatureThreshold = 18;\nmsg.highTemperatureThreshold = 32;\nmsg.lowBatteryVoltage = 2.40;\nmsg.lowTemperatureMessage = 'The temperature is ' + msg.temperature + ' °C' + ' in Daniel\\'s bedroom. You may want to check for open windows or turn the heating on in zone 2.';\nmsg.highTemperatureMessage = 'Temperature high in Daniel\\'s bedroom: ' + msg.temperature + ' °C\\n\\n';\nmsg.lowBatteryMessage = 'Battery voltage low in Daniel\\'s bedroom: ' + msg.batteryVoltage + 'Volts'; \nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 434,
        "y": 282,
        "wires": [
            [
                "aa5ef536.55a108",
                "459f4b93.2c7954"
            ]
        ]
    },
    {
        "id": "3d57d8d8.c2a828",
        "type": "delay",
        "z": "7ac9fc08.853604",
        "name": "",
        "pauseType": "rate",
        "timeout": "5",
        "timeoutUnits": "seconds",
        "rate": "4",
        "nbRateUnits": "1",
        "rateUnits": "hour",
        "randomFirst": "1",
        "randomLast": "5",
        "randomUnits": "seconds",
        "drop": true,
        "x": 744,
        "y": 243,
        "wires": [
            [
                "74d89ee3.8b276"
            ]
        ]
    },
    {
        "id": "aa5ef536.55a108",
        "type": "delay",
        "z": "7ac9fc08.853604",
        "name": "",
        "pauseType": "rate",
        "timeout": "5",
        "timeoutUnits": "seconds",
        "rate": "4",
        "nbRateUnits": "1",
        "rateUnits": "hour",
        "randomFirst": "1",
        "randomLast": "5",
        "randomUnits": "seconds",
        "drop": true,
        "x": 744,
        "y": 283,
        "wires": [
            [
                "74d89ee3.8b276"
            ]
        ]
    },
    {
        "id": "3e49872e.c1b678",
        "type": "delay",
        "z": "7ac9fc08.853604",
        "name": "",
        "pauseType": "rate",
        "timeout": "5",
        "timeoutUnits": "seconds",
        "rate": "4",
        "nbRateUnits": "1",
        "rateUnits": "hour",
        "randomFirst": "1",
        "randomLast": "5",
        "randomUnits": "seconds",
        "drop": true,
        "x": 744,
        "y": 323,
        "wires": [
            [
                "74d89ee3.8b276"
            ]
        ]
    },
    {
        "id": "e8aa247.f1755d8",
        "type": "delay",
        "z": "7ac9fc08.853604",
        "name": "",
        "pauseType": "rate",
        "timeout": "5",
        "timeoutUnits": "seconds",
        "rate": "4",
        "nbRateUnits": "1",
        "rateUnits": "hour",
        "randomFirst": "1",
        "randomLast": "5",
        "randomUnits": "seconds",
        "drop": true,
        "x": 744,
        "y": 363,
        "wires": [
            [
                "74d89ee3.8b276"
            ]
        ]
    },
    {
        "id": "74f77ef1.3c65d",
        "type": "function",
        "z": "7ac9fc08.853604",
        "name": "Extract Temperature to msg.payload",
        "func": "msg.payload = msg.temperature;\nmsg.topic = \"Living Area\";\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 830,
        "y": 100,
        "wires": [
            [
                "b02bd8bf.799968",
                "a0b8583d.f7d2f8"
            ]
        ]
    },
    {
        "id": "b02bd8bf.799968",
        "type": "ui_gauge",
        "z": "7ac9fc08.853604",
        "name": "Living Area Gauge",
        "group": "2fa6b1ba.3b8ede",
        "order": 0,
        "width": 0,
        "height": 0,
        "gtype": "gage",
        "title": "Temperature",
        "label": "Degrees C",
        "format": "{{value}}",
        "min": 0,
        "max": "30",
        "colors": [
            "#000080",
            "#ff8000",
            "#ca3838"
        ],
        "seg1": "",
        "seg2": "",
        "x": 1110,
        "y": 80,
        "wires": []
    },
    {
        "id": "a0b8583d.f7d2f8",
        "type": "ui_chart",
        "z": "7ac9fc08.853604",
        "name": "Living Area Last 24 Hours",
        "group": "2fa6b1ba.3b8ede",
        "order": 0,
        "width": 0,
        "height": 0,
        "label": "Last 24 Hours",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm",
        "interpolate": "linear",
        "nodata": "Gathering Data...",
        "ymin": "5",
        "ymax": "25",
        "removeOlder": "24",
        "removeOlderPoints": "",
        "removeOlderUnit": "3600",
        "cutout": 0,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "x": 1130,
        "y": 120,
        "wires": [
            [],
            []
        ]
    },
    {
        "id": "459f4b93.2c7954",
        "type": "function",
        "z": "7ac9fc08.853604",
        "name": "Extract Temperature to msg.payload",
        "func": "msg.payload = msg.temperature;\nmsg.topic = \"Daniel's Bedroom\";\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 830,
        "y": 180,
        "wires": [
            [
                "749b7da1.89d9d4",
                "4c6f0530.27593c",
                "45a8d579.34e63c"
            ]
        ]
    },
    {
        "id": "749b7da1.89d9d4",
        "type": "ui_gauge",
        "z": "7ac9fc08.853604",
        "name": "Daniel's Bedroom Gauge",
        "group": "34209030.bf4",
        "order": 0,
        "width": 0,
        "height": 0,
        "gtype": "gage",
        "title": "Temperature",
        "label": "Degrees C",
        "format": "{{value}}",
        "min": 0,
        "max": "30",
        "colors": [
            "#000080",
            "#ff8000",
            "#ca3838"
        ],
        "seg1": "",
        "seg2": "",
        "x": 1130,
        "y": 160,
        "wires": []
    },
    {
        "id": "4c6f0530.27593c",
        "type": "ui_chart",
        "z": "7ac9fc08.853604",
        "name": "Daniel's Bedroom Last 24 Hours",
        "group": "34209030.bf4",
        "order": 0,
        "width": 0,
        "height": 0,
        "label": "Last 24 Hours",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm",
        "interpolate": "linear",
        "nodata": "Gathering Data...",
        "ymin": "5",
        "ymax": "25",
        "removeOlder": "24",
        "removeOlderPoints": "",
        "removeOlderUnit": "3600",
        "cutout": 0,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "x": 1150,
        "y": 200,
        "wires": [
            [],
            []
        ]
    },
    {
        "id": "4342c77.f927a38",
        "type": "function",
        "z": "7ac9fc08.853604",
        "name": "Node 17: Outside : Extract Temperature to msg.payload",
        "func": "msg.payload = msg.temperature;\nmsg.topic = \"Outside\";\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 303.7500305175781,
        "y": 655.0000095367432,
        "wires": [
            [
                "9934a743.bf5718",
                "556ae396.738d9c",
                "2976550d.5d80ba",
                "29e670b4.897a",
                "2229ea25.9a2526"
            ]
        ]
    },
    {
        "id": "9934a743.bf5718",
        "type": "ui_gauge",
        "z": "7ac9fc08.853604",
        "name": "Outside Gauge",
        "group": "5a75a0d4.3977e",
        "order": 0,
        "width": 0,
        "height": 0,
        "gtype": "gage",
        "title": "Temperature",
        "label": "Degrees C",
        "format": "{{value}}",
        "min": "0",
        "max": "30",
        "colors": [
            "#000080",
            "#ff8000",
            "#ca3838"
        ],
        "seg1": "",
        "seg2": "",
        "x": 639.7500305175781,
        "y": 632.0000095367432,
        "wires": []
    },
    {
        "id": "556ae396.738d9c",
        "type": "ui_chart",
        "z": "7ac9fc08.853604",
        "name": "Outside Last 24 Hours",
        "group": "5a75a0d4.3977e",
        "order": 0,
        "width": 0,
        "height": 0,
        "label": "Last 24 Hours",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "Gathering Data...",
        "ymin": "5",
        "ymax": "25",
        "removeOlder": "24",
        "removeOlderPoints": "",
        "removeOlderUnit": "3600",
        "cutout": 0,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "x": 659.7500305175781,
        "y": 672.0000095367432,
        "wires": [
            [],
            []
        ]
    },
    {
        "id": "62d30d51.3545d4",
        "type": "function",
        "z": "7ac9fc08.853604",
        "name": "Extract Temperature to msg.payload",
        "func": "msg.payload = msg.temperature;\nmsg.topic = \"James' Bedroom\";\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 450,
        "y": 440,
        "wires": [
            [
                "608d9301.4ba4fc",
                "e4c9f3b5.9c35"
            ]
        ]
    },
    {
        "id": "608d9301.4ba4fc",
        "type": "ui_gauge",
        "z": "7ac9fc08.853604",
        "name": "James' Bedroom Gauge",
        "group": "60f7a7a2.1c9358",
        "order": 0,
        "width": 0,
        "height": 0,
        "gtype": "gage",
        "title": "Temperature",
        "label": "Degrees C",
        "format": "{{value}}",
        "min": 0,
        "max": "30",
        "colors": [
            "#000080",
            "#ff8000",
            "#ca3838"
        ],
        "seg1": "",
        "seg2": "",
        "x": 750,
        "y": 420,
        "wires": []
    },
    {
        "id": "e4c9f3b5.9c35",
        "type": "ui_chart",
        "z": "7ac9fc08.853604",
        "name": "James' Bedrom Last 24 Hours",
        "group": "60f7a7a2.1c9358",
        "order": 0,
        "width": 0,
        "height": 0,
        "label": "Last 24 Hours",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "Gathering Data...",
        "ymin": "5",
        "ymax": "25",
        "removeOlder": "24",
        "removeOlderPoints": "",
        "removeOlderUnit": "3600",
        "cutout": 0,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "x": 770,
        "y": 460,
        "wires": [
            [],
            []
        ]
    },
    {
        "id": "9db12edd.f8d6f",
        "type": "function",
        "z": "7ac9fc08.853604",
        "name": "Extract Temperature to msg.payload",
        "func": "msg.payload = msg.temperature;\nmsg.topic = \"Master Bedroom\";\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 450,
        "y": 520,
        "wires": [
            [
                "d3cbb4cb.506738",
                "1cb2816f.acf89f",
                "b1c22280.5e4d2"
            ]
        ]
    },
    {
        "id": "d3cbb4cb.506738",
        "type": "ui_gauge",
        "z": "7ac9fc08.853604",
        "name": "Master Bedroom Gauge",
        "group": "26400317.e0b9ec",
        "order": 0,
        "width": 0,
        "height": 0,
        "gtype": "gage",
        "title": "Temperature",
        "label": "Decrees C",
        "format": "{{value}}",
        "min": 0,
        "max": "30",
        "colors": [
            "#000080",
            "#ff8000",
            "#ca3838"
        ],
        "seg1": "",
        "seg2": "",
        "x": 750,
        "y": 500,
        "wires": []
    },
    {
        "id": "1cb2816f.acf89f",
        "type": "ui_chart",
        "z": "7ac9fc08.853604",
        "name": "Master Bedrom Last 24 Hours",
        "group": "26400317.e0b9ec",
        "order": 0,
        "width": 0,
        "height": 0,
        "label": "Last 24 Hours",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "Gathering Data...",
        "ymin": "5",
        "ymax": "25",
        "removeOlder": "24",
        "removeOlderPoints": "",
        "removeOlderUnit": "3600",
        "cutout": 0,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "x": 770,
        "y": 540,
        "wires": [
            [],
            []
        ]
    },
    {
        "id": "2976550d.5d80ba",
        "type": "ui_chart",
        "z": "7ac9fc08.853604",
        "name": "Outside Last 7 Days",
        "group": "5a75a0d4.3977e",
        "order": 0,
        "width": 0,
        "height": 0,
        "label": "Last 7 Days",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "Gathering Data...",
        "ymin": "5",
        "ymax": "25",
        "removeOlder": "7",
        "removeOlderPoints": "",
        "removeOlderUnit": "86400",
        "cutout": 0,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "x": 659.7500305175781,
        "y": 712.0000095367432,
        "wires": [
            [],
            []
        ]
    },
    {
        "id": "4d22710.9fa5b9",
        "type": "function",
        "z": "7ac9fc08.853604",
        "name": "Compose Tweet",
        "func": "ComposeTweet(msg.payload);\n\nfunction ComposeTweet(message)\n{\n    var payload;\n    var UUID;\n        \n    node.log('Composing payload for tweet node...');\n        \n    // UUID = 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function(c) {\n    //         var r = Math.random()*16|0, v = c == 'x' ? r : (r&0x3|0x8);\n    //         return v.toString(16);\n    //         });\n        \n    // payload = 'D @FriendlyKiwi ' + message + 'Message ID : ' + UUID;\n    payload = 'D '+ msg.twitterRecipient + ' ' + message;\n        \n    node.log('Returning payload: ' + payload);\n        \n    return payload;\n}\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 1190.388916015625,
        "y": 303.22222900390625,
        "wires": [
            [
                "f944fc81.6ddb2"
            ]
        ]
    },
    {
        "id": "8cd077e.8976088",
        "type": "mqtt out",
        "z": "7ac9fc08.853604",
        "name": "Publish MQTT messages destined for AWS Polly Service",
        "topic": "polly/voice_message",
        "qos": "",
        "retain": "",
        "broker": "dcdae49e.232518",
        "x": 1403.750015258789,
        "y": 398.7500057220459,
        "wires": []
    },
    {
        "id": "f944fc81.6ddb2",
        "type": "twitter out",
        "z": "7ac9fc08.853604",
        "twitter": "",
        "name": "Tweet Alert Message",
        "x": 1440.5,
        "y": 305,
        "wires": []
    },
    {
        "id": "feb5f6bb.e71748",
        "type": "inject",
        "z": "7ac9fc08.853604",
        "name": "Test Message",
        "topic": "",
        "payload": "Test Message",
        "payloadType": "str",
        "repeat": "",
        "crontab": "",
        "once": false,
        "x": 1015.7500152587891,
        "y": 398.0000057220459,
        "wires": [
            [
                "8cd077e.8976088"
            ]
        ]
    },
    {
        "id": "51f34968.d7b058",
        "type": "function",
        "z": "7ac9fc08.853604",
        "name": "Compose Outside Temperature Announcement",
        "func": "// Initialise lastTemperature to 0 if it doesn't already exist\n\nvar lastTemperature = context.get('lastTemperature') || 0;\nvar currentTemperature = msg.temperature;\n// var delta = lastTemperature - currentTemperature;\nvar delta = currentTemperature - lastTemperature;\n\nif (delta > 0.25) {\n    observation = \"It's getting warmer.\";\n} else if (delta < -0.25) {\n    observation = \"It's getting colder.\";\n} else {\n    observation = \"\";\n}\n\ncontext.set('lastTemperature', msg.temperature);\nmsg.payload = \"The outside temperature is \" + msg.temperature + \" degrees:  \" + observation;\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 646.8750305175781,
        "y": 808.7500228881836,
        "wires": [
            [
                "5d35e8dc.700188",
                "4eec21c7.e6c51"
            ]
        ]
    },
    {
        "id": "5d35e8dc.700188",
        "type": "debug",
        "z": "7ac9fc08.853604",
        "name": "msg.payload",
        "active": false,
        "console": "false",
        "complete": "payload",
        "x": 991.2500152587891,
        "y": 808.7500133514404,
        "wires": []
    },
    {
        "id": "29e670b4.897a",
        "type": "function",
        "z": "7ac9fc08.853604",
        "name": "Rate Limiter",
        "func": "// minimum interval between messages (ms)\nvar interval = (1000*60*18);\ncontext.lastTime = context.lastTime || 0;\n\nvar now = Date.now();\n\nif (now-context.lastTime > interval) {\n  context.lastTime = now;\n  return msg;\n} else {\n  return null;\n}",
        "outputs": 1,
        "noerr": 0,
        "x": 322.5000305175781,
        "y": 810.0000200271606,
        "wires": [
            [
                "51f34968.d7b058"
            ]
        ]
    },
    {
        "id": "4eec21c7.e6c51",
        "type": "delay",
        "z": "7ac9fc08.853604",
        "name": "",
        "pauseType": "rate",
        "timeout": "30",
        "timeoutUnits": "seconds",
        "rate": "1",
        "nbRateUnits": "30",
        "rateUnits": "second",
        "randomFirst": "1",
        "randomLast": "5",
        "randomUnits": "seconds",
        "drop": false,
        "x": 1280.625015258789,
        "y": 468.7500057220459,
        "wires": [
            [
                "8cd077e.8976088"
            ]
        ]
    },
    {
        "id": "5178f1de.81da6",
        "type": "ui_text_input",
        "z": "7ac9fc08.853604",
        "name": "Test Message",
        "label": "Send Test Message to Polly",
        "group": "498acce9.46a5a4",
        "order": 0,
        "width": 0,
        "height": 0,
        "passthru": false,
        "mode": "text",
        "delay": "0",
        "topic": "Test Message",
        "x": 1026.875015258789,
        "y": 458.7500066757202,
        "wires": [
            [
                "4eec21c7.e6c51"
            ]
        ]
    },
    {
        "id": "7bdc8a26.e014b4",
        "type": "function",
        "z": "7ac9fc08.853604",
        "name": "Rate Limiter",
        "func": "// minimum interval between messages (ms)\nvar interval = (1000*60*30);\ncontext.lastTime = context.lastTime || 0;\n\nvar now = Date.now();\n\nif (now-context.lastTime > interval) {\n  context.lastTime = now;\n  return msg;\n} else {\n  return null;\n}",
        "outputs": 1,
        "noerr": 0,
        "x": 744,
        "y": 28,
        "wires": [
            [
                "b79b8434.596ba8"
            ]
        ]
    },
    {
        "id": "b79b8434.596ba8",
        "type": "function",
        "z": "7ac9fc08.853604",
        "name": "Compose Living Room Temperature Announcement",
        "func": "msg.payload = \"The living room temperature is \" + msg.temperature + \" degrees.\";\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 1050,
        "y": 28,
        "wires": [
            [
                "4eec21c7.e6c51"
            ]
        ]
    },
    {
        "id": "b1c22280.5e4d2",
        "type": "mqtt out",
        "z": "7ac9fc08.853604",
        "name": "MQTT: house/temperature/master_bedroom",
        "topic": "house/temperature/master_bedroom",
        "qos": "",
        "retain": "",
        "broker": "dcdae49e.232518",
        "x": 810,
        "y": 580,
        "wires": []
    },
    {
        "id": "45a8d579.34e63c",
        "type": "mqtt out",
        "z": "7ac9fc08.853604",
        "name": "MQTT: house/temperatures/daniels_bedroom",
        "topic": "house/temperature/daniels_bedroom",
        "qos": "",
        "retain": "",
        "broker": "dcdae49e.232518",
        "x": 1190,
        "y": 240,
        "wires": []
    },
    {
        "id": "2229ea25.9a2526",
        "type": "mqtt out",
        "z": "7ac9fc08.853604",
        "name": "MQTT: house/temperature/outside",
        "topic": "house/temperature/outside",
        "qos": "",
        "retain": "",
        "broker": "dcdae49e.232518",
        "x": 700,
        "y": 760,
        "wires": []
    },
    {
        "id": "dcdae49e.232518",
        "type": "mqtt-broker",
        "z": "7ac9fc08.853604",
        "broker": "192.168.178.20",
        "port": "1883",
        "clientid": "",
        "usetls": false,
        "verifyservercert": true,
        "compatmode": true,
        "keepalive": "60",
        "cleansession": true,
        "birthTopic": "",
        "birthQos": "0",
        "birthRetain": "false",
        "birthPayload": "",
        "willTopic": "",
        "willQos": "0",
        "willRetain": "false",
        "willPayload": ""
    },
    {
        "id": "2fa6b1ba.3b8ede",
        "type": "ui_group",
        "z": "7ac9fc08.853604",
        "name": "Living Area",
        "tab": "64836d7a.c4c164",
        "order": 4,
        "disp": true,
        "width": "6"
    },
    {
        "id": "34209030.bf4",
        "type": "ui_group",
        "z": "7ac9fc08.853604",
        "name": "Daniel's Bedroom",
        "tab": "64836d7a.c4c164",
        "order": 2,
        "disp": true,
        "width": "6"
    },
    {
        "id": "5a75a0d4.3977e",
        "type": "ui_group",
        "z": "",
        "name": "Outside",
        "tab": "64836d7a.c4c164",
        "order": 5,
        "disp": true,
        "width": "6"
    },
    {
        "id": "60f7a7a2.1c9358",
        "type": "ui_group",
        "z": "",
        "name": "James' Bedroom",
        "tab": "64836d7a.c4c164",
        "order": 3,
        "disp": true,
        "width": "6"
    },
    {
        "id": "26400317.e0b9ec",
        "type": "ui_group",
        "z": "",
        "name": "Master Bedroom",
        "tab": "64836d7a.c4c164",
        "order": 1,
        "disp": true,
        "width": "6"
    },
    {
        "id": "498acce9.46a5a4",
        "type": "ui_group",
        "z": "",
        "name": "Polly Test Message",
        "tab": "6d6c64b8.01a9cc",
        "order": 1,
        "disp": true,
        "width": "6"
    },
    {
        "id": "64836d7a.c4c164",
        "type": "ui_tab",
        "z": "7ac9fc08.853604",
        "name": "Home Tab",
        "icon": "dashboard",
        "order": 1
    },
    {
        "id": "6d6c64b8.01a9cc",
        "type": "ui_tab",
        "z": "",
        "name": "Polly Messaging",
        "icon": "dashboard",
        "order": 2
    }
]
