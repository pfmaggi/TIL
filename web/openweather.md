# Open Weather API 

With this request:

    http://api.openweathermap.org/data/2.5/weather?q=Lecco,it&appid=<API KEY>

We get the current weather:

    {
    	"coord": {
    		"lon": 9.39,
    		"lat": 45.85
    	},
    	"weather": [{
    		"id": 800,
    		"main": "Clear",
    		"description": "clear sky",
    		"icon": "01d"
    	}],
    	"base": "stations",
    	"main": {
    		"temp": 303.41,
    		"pressure": 1010.7,
    		"humidity": 53,
    		"temp_min": 301.48,
    		"temp_max": 305.37
    	},
    	"wind": {
    		"speed": 2.42,
    		"deg": 157.506
    	},
    	"rain": {
    		"3h": 0.08
    	},
    	"clouds": {
    		"all": 0
    	},
    	"dt": 1470313781,
    	"sys": {
    		"type": 3,
    		"id": 1450876174,
    		"message": 0.0214,
    		"country": "IT",
    		"sunrise": 1470283789,
    		"sunset": 1470336377
    	},
    	"id": 6541997,
    	"name": "Lecco",
    	"cod": 200
    }

To get the 5 days forecast:

    http://api.openweathermap.org/data/2.5/forecast?id=6541997&appid=<API KEY>

We get as result... as of today :-)

    {
        "city": {
            "id": 6541997,
            "name": "Lecco",
            "coord": {
                "lon": 9.39048,
                "lat": 45.85334
            },
            "country": "IT",
            "population": 0,
            "sys": {
                "population": 0
            }
        },
        "cod": "200",
        "message": 0.0041,
        "cnt": 40,
        "list": [{
            "dt": 1470322800,
            "main": {
                "temp": 305.56,
                "temp_min": 302.027,
                "temp_max": 305.56,
                "pressure": 993.22,
                "sea_level": 1025.4,
                "grnd_level": 993.22,
                "humidity": 68,
                "temp_kf": 3.53
            },
            "weather": [{
                "id": 500,
                "main": "Rain",
                "description": "light rain",
                "icon": "10d"
            }],
            "clouds": {
                "all": 24
            },
            "wind": {
                "speed": 2.13,
                "deg": 80.5007
            },
            "rain": {
                "3h": 2.535
            },
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-04 15:00:00"
        }, {
            "dt": 1470333600,
            "main": {
                "temp": 304.23,
                "temp_min": 300.887,
                "temp_max": 304.23,
                "pressure": 992.3,
                "sea_level": 1024.68,
                "grnd_level": 992.3,
                "humidity": 63,
                "temp_kf": 3.35
            },
            "weather": [{
                "id": 802,
                "main": "Clouds",
                "description": "scattered clouds",
                "icon": "03d"
            }],
            "clouds": {
                "all": 44
            },
            "wind": {
                "speed": 0.82,
                "deg": 102.002
            },
            "rain": {},
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-04 18:00:00"
        }, {
            "dt": 1470344400,
            "main": {
                "temp": 295.6,
                "temp_min": 292.434,
                "temp_max": 295.6,
                "pressure": 992.41,
                "sea_level": 1025.19,
                "grnd_level": 992.41,
                "humidity": 96,
                "temp_kf": 3.16
            },
            "weather": [{
                "id": 501,
                "main": "Rain",
                "description": "moderate rain",
                "icon": "10n"
            }],
            "clouds": {
                "all": 32
            },
            "wind": {
                "speed": 2.76,
                "deg": 10.5009
            },
            "rain": {
                "3h": 5.73
            },
            "sys": {
                "pod": "n"
            },
            "dt_txt": "2016-08-04 21:00:00"
        }, {
            "dt": 1470355200,
            "main": {
                "temp": 294.13,
                "temp_min": 291.151,
                "temp_max": 294.13,
                "pressure": 992.34,
                "sea_level": 1025,
                "grnd_level": 992.34,
                "humidity": 96,
                "temp_kf": 2.98
            },
            "weather": [{
                "id": 501,
                "main": "Rain",
                "description": "moderate rain",
                "icon": "10n"
            }],
            "clouds": {
                "all": 44
            },
            "wind": {
                "speed": 2.86,
                "deg": 16.5038
            },
            "rain": {
                "3h": 7.14
            },
            "sys": {
                "pod": "n"
            },
            "dt_txt": "2016-08-05 00:00:00"
        }, {
            "dt": 1470366000,
            "main": {
                "temp": 294.06,
                "temp_min": 291.273,
                "temp_max": 294.06,
                "pressure": 991.17,
                "sea_level": 1023.89,
                "grnd_level": 991.17,
                "humidity": 96,
                "temp_kf": 2.79
            },
            "weather": [{
                "id": 501,
                "main": "Rain",
                "description": "moderate rain",
                "icon": "10n"
            }],
            "clouds": {
                "all": 92
            },
            "wind": {
                "speed": 2.22,
                "deg": 5.00085
            },
            "rain": {
                "3h": 3.41
            },
            "sys": {
                "pod": "n"
            },
            "dt_txt": "2016-08-05 03:00:00"
        }, {
            "dt": 1470376800,
            "main": {
                "temp": 294.56,
                "temp_min": 291.956,
                "temp_max": 294.56,
                "pressure": 990.56,
                "sea_level": 1023.35,
                "grnd_level": 990.56,
                "humidity": 96,
                "temp_kf": 2.6
            },
            "weather": [{
                "id": 500,
                "main": "Rain",
                "description": "light rain",
                "icon": "10d"
            }],
            "clouds": {
                "all": 88
            },
            "wind": {
                "speed": 3.81,
                "deg": 75.5033
            },
            "rain": {
                "3h": 2.92
            },
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-05 06:00:00"
        }, {
            "dt": 1470387600,
            "main": {
                "temp": 294,
                "temp_min": 291.583,
                "temp_max": 294,
                "pressure": 991.43,
                "sea_level": 1024.18,
                "grnd_level": 991.43,
                "humidity": 100,
                "temp_kf": 2.42
            },
            "weather": [{
                "id": 501,
                "main": "Rain",
                "description": "moderate rain",
                "icon": "10d"
            }],
            "clouds": {
                "all": 88
            },
            "wind": {
                "speed": 2.76,
                "deg": 60.5025
            },
            "rain": {
                "3h": 6.37
            },
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-05 09:00:00"
        }, {
            "dt": 1470398400,
            "main": {
                "temp": 292.22,
                "temp_min": 289.985,
                "temp_max": 292.22,
                "pressure": 992.2,
                "sea_level": 1025.25,
                "grnd_level": 992.2,
                "humidity": 100,
                "temp_kf": 2.23
            },
            "weather": [{
                "id": 502,
                "main": "Rain",
                "description": "heavy intensity rain",
                "icon": "10d"
            }],
            "clouds": {
                "all": 92
            },
            "wind": {
                "speed": 3.52,
                "deg": 0.504944
            },
            "rain": {
                "3h": 13.55
            },
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-05 12:00:00"
        }, {
            "dt": 1470409200,
            "main": {
                "temp": 291.92,
                "temp_min": 289.873,
                "temp_max": 291.92,
                "pressure": 992.55,
                "sea_level": 1025.64,
                "grnd_level": 992.55,
                "humidity": 99,
                "temp_kf": 2.05
            },
            "weather": [{
                "id": 502,
                "main": "Rain",
                "description": "heavy intensity rain",
                "icon": "10d"
            }],
            "clouds": {
                "all": 92
            },
            "wind": {
                "speed": 3.76,
                "deg": 341.5
            },
            "rain": {
                "3h": 12.67
            },
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-05 15:00:00"
        }, {
            "dt": 1470420000,
            "main": {
                "temp": 292.34,
                "temp_min": 290.482,
                "temp_max": 292.34,
                "pressure": 993.6,
                "sea_level": 1026.74,
                "grnd_level": 993.6,
                "humidity": 90,
                "temp_kf": 1.86
            },
            "weather": [{
                "id": 501,
                "main": "Rain",
                "description": "moderate rain",
                "icon": "10d"
            }],
            "clouds": {
                "all": 44
            },
            "wind": {
                "speed": 2.37,
                "deg": 319.001
            },
            "rain": {
                "3h": 4.65
            },
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-05 18:00:00"
        }, {
            "dt": 1470430800,
            "main": {
                "temp": 288.72,
                "temp_min": 287.051,
                "temp_max": 288.72,
                "pressure": 995.92,
                "sea_level": 1029.03,
                "grnd_level": 995.92,
                "humidity": 91,
                "temp_kf": 1.67
            },
            "weather": [{
                "id": 500,
                "main": "Rain",
                "description": "light rain",
                "icon": "10n"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 1,
                "deg": 357.001
            },
            "rain": {
                "3h": 0.21
            },
            "sys": {
                "pod": "n"
            },
            "dt_txt": "2016-08-05 21:00:00"
        }, {
            "dt": 1470441600,
            "main": {
                "temp": 286.28,
                "temp_min": 284.795,
                "temp_max": 286.28,
                "pressure": 997.32,
                "sea_level": 1030.49,
                "grnd_level": 997.32,
                "humidity": 88,
                "temp_kf": 1.49
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01n"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 1.05,
                "deg": 20.0021
            },
            "rain": {},
            "sys": {
                "pod": "n"
            },
            "dt_txt": "2016-08-06 00:00:00"
        }, {
            "dt": 1470452400,
            "main": {
                "temp": 285.07,
                "temp_min": 283.764,
                "temp_max": 285.07,
                "pressure": 998.09,
                "sea_level": 1031.4,
                "grnd_level": 998.09,
                "humidity": 83,
                "temp_kf": 1.3
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01n"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 2.32,
                "deg": 27.5017
            },
            "rain": {},
            "sys": {
                "pod": "n"
            },
            "dt_txt": "2016-08-06 03:00:00"
        }, {
            "dt": 1470463200,
            "main": {
                "temp": 287.97,
                "temp_min": 286.858,
                "temp_max": 287.97,
                "pressure": 1000.44,
                "sea_level": 1033.74,
                "grnd_level": 1000.44,
                "humidity": 83,
                "temp_kf": 1.12
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01d"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 3.45,
                "deg": 28.5019
            },
            "rain": {},
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-06 06:00:00"
        }, {
            "dt": 1470474000,
            "main": {
                "temp": 295.23,
                "temp_min": 294.305,
                "temp_max": 295.23,
                "pressure": 1002.02,
                "sea_level": 1034.91,
                "grnd_level": 1002.02,
                "humidity": 80,
                "temp_kf": 0.93
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01d"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 1.66,
                "deg": 324.502
            },
            "rain": {},
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-06 09:00:00"
        }, {
            "dt": 1470484800,
            "main": {
                "temp": 297.24,
                "temp_min": 296.497,
                "temp_max": 297.24,
                "pressure": 1001.99,
                "sea_level": 1034.66,
                "grnd_level": 1001.99,
                "humidity": 80,
                "temp_kf": 0.74
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01d"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 2.02,
                "deg": 256
            },
            "rain": {},
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-06 12:00:00"
        }, {
            "dt": 1470495600,
            "main": {
                "temp": 297.84,
                "temp_min": 297.286,
                "temp_max": 297.84,
                "pressure": 1001.08,
                "sea_level": 1033.61,
                "grnd_level": 1001.08,
                "humidity": 71,
                "temp_kf": 0.56
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01d"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 2.2,
                "deg": 271.007
            },
            "rain": {},
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-06 15:00:00"
        }, {
            "dt": 1470506400,
            "main": {
                "temp": 295.22,
                "temp_min": 294.849,
                "temp_max": 295.22,
                "pressure": 1000.99,
                "sea_level": 1033.78,
                "grnd_level": 1000.99,
                "humidity": 81,
                "temp_kf": 0.37
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01d"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 1.41,
                "deg": 245.502
            },
            "rain": {},
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-06 18:00:00"
        }, {
            "dt": 1470517200,
            "main": {
                "temp": 289.04,
                "temp_min": 288.856,
                "temp_max": 289.04,
                "pressure": 1002.6,
                "sea_level": 1035.62,
                "grnd_level": 1002.6,
                "humidity": 85,
                "temp_kf": 0.19
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01n"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 1.37,
                "deg": 291.004
            },
            "rain": {},
            "sys": {
                "pod": "n"
            },
            "dt_txt": "2016-08-06 21:00:00"
        }, {
            "dt": 1470528000,
            "main": {
                "temp": 287.59,
                "temp_min": 287.59,
                "temp_max": 287.59,
                "pressure": 1003.64,
                "sea_level": 1036.7,
                "grnd_level": 1003.64,
                "humidity": 79,
                "temp_kf": 0
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01n"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 2.47,
                "deg": 14.0016
            },
            "rain": {},
            "sys": {
                "pod": "n"
            },
            "dt_txt": "2016-08-07 00:00:00"
        }, {
            "dt": 1470538800,
            "main": {
                "temp": 287.331,
                "temp_min": 287.331,
                "temp_max": 287.331,
                "pressure": 1003.84,
                "sea_level": 1037.05,
                "grnd_level": 1003.84,
                "humidity": 71,
                "temp_kf": 0
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01n"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 3.32,
                "deg": 23.504
            },
            "rain": {},
            "sys": {
                "pod": "n"
            },
            "dt_txt": "2016-08-07 03:00:00"
        }, {
            "dt": 1470549600,
            "main": {
                "temp": 289.739,
                "temp_min": 289.739,
                "temp_max": 289.739,
                "pressure": 1004.99,
                "sea_level": 1038.22,
                "grnd_level": 1004.99,
                "humidity": 78,
                "temp_kf": 0
            },
            "weather": [{
                "id": 803,
                "main": "Clouds",
                "description": "broken clouds",
                "icon": "04d"
            }],
            "clouds": {
                "all": 56
            },
            "wind": {
                "speed": 2.52,
                "deg": 15.5008
            },
            "rain": {},
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-07 06:00:00"
        }, {
            "dt": 1470560400,
            "main": {
                "temp": 295.943,
                "temp_min": 295.943,
                "temp_max": 295.943,
                "pressure": 1006.1,
                "sea_level": 1038.94,
                "grnd_level": 1006.1,
                "humidity": 75,
                "temp_kf": 0
            },
            "weather": [{
                "id": 803,
                "main": "Clouds",
                "description": "broken clouds",
                "icon": "04d"
            }],
            "clouds": {
                "all": 56
            },
            "wind": {
                "speed": 1.56,
                "deg": 64.5018
            },
            "rain": {},
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-07 09:00:00"
        }, {
            "dt": 1470571200,
            "main": {
                "temp": 297.772,
                "temp_min": 297.772,
                "temp_max": 297.772,
                "pressure": 1005.67,
                "sea_level": 1038.41,
                "grnd_level": 1005.67,
                "humidity": 77,
                "temp_kf": 0
            },
            "weather": [{
                "id": 801,
                "main": "Clouds",
                "description": "few clouds",
                "icon": "02d"
            }],
            "clouds": {
                "all": 12
            },
            "wind": {
                "speed": 1.87,
                "deg": 185.511
            },
            "rain": {},
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-07 12:00:00"
        }, {
            "dt": 1470582000,
            "main": {
                "temp": 298.438,
                "temp_min": 298.438,
                "temp_max": 298.438,
                "pressure": 1004.83,
                "sea_level": 1037.4,
                "grnd_level": 1004.83,
                "humidity": 71,
                "temp_kf": 0
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01d"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 1.86,
                "deg": 215.503
            },
            "rain": {},
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-07 15:00:00"
        }, {
            "dt": 1470592800,
            "main": {
                "temp": 296.433,
                "temp_min": 296.433,
                "temp_max": 296.433,
                "pressure": 1004.74,
                "sea_level": 1037.45,
                "grnd_level": 1004.74,
                "humidity": 76,
                "temp_kf": 0
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01d"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 1.32,
                "deg": 207.5
            },
            "rain": {},
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-07 18:00:00"
        }, {
            "dt": 1470603600,
            "main": {
                "temp": 290.479,
                "temp_min": 290.479,
                "temp_max": 290.479,
                "pressure": 1006.17,
                "sea_level": 1039.23,
                "grnd_level": 1006.17,
                "humidity": 86,
                "temp_kf": 0
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01n"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 1.33,
                "deg": 301.502
            },
            "rain": {},
            "sys": {
                "pod": "n"
            },
            "dt_txt": "2016-08-07 21:00:00"
        }, {
            "dt": 1470614400,
            "main": {
                "temp": 289.369,
                "temp_min": 289.369,
                "temp_max": 289.369,
                "pressure": 1006.72,
                "sea_level": 1039.81,
                "grnd_level": 1006.72,
                "humidity": 86,
                "temp_kf": 0
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01n"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 2.51,
                "deg": 13.0006
            },
            "rain": {},
            "sys": {
                "pod": "n"
            },
            "dt_txt": "2016-08-08 00:00:00"
        }, {
            "dt": 1470625200,
            "main": {
                "temp": 289.388,
                "temp_min": 289.388,
                "temp_max": 289.388,
                "pressure": 1006.25,
                "sea_level": 1039.43,
                "grnd_level": 1006.25,
                "humidity": 82,
                "temp_kf": 0
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01n"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 3.31,
                "deg": 36.0052
            },
            "rain": {},
            "sys": {
                "pod": "n"
            },
            "dt_txt": "2016-08-08 03:00:00"
        }, {
            "dt": 1470636000,
            "main": {
                "temp": 292.479,
                "temp_min": 292.479,
                "temp_max": 292.479,
                "pressure": 1006.62,
                "sea_level": 1039.76,
                "grnd_level": 1006.62,
                "humidity": 75,
                "temp_kf": 0
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01d"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 2.72,
                "deg": 53.5038
            },
            "rain": {},
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-08 06:00:00"
        }, {
            "dt": 1470646800,
            "main": {
                "temp": 296.973,
                "temp_min": 296.973,
                "temp_max": 296.973,
                "pressure": 1007.08,
                "sea_level": 1039.87,
                "grnd_level": 1007.08,
                "humidity": 73,
                "temp_kf": 0
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01d"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 2.15,
                "deg": 144.504
            },
            "rain": {},
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-08 09:00:00"
        }, {
            "dt": 1470657600,
            "main": {
                "temp": 299,
                "temp_min": 299,
                "temp_max": 299,
                "pressure": 1005.8,
                "sea_level": 1038.47,
                "grnd_level": 1005.8,
                "humidity": 72,
                "temp_kf": 0
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01d"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 1.91,
                "deg": 202.001
            },
            "rain": {},
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-08 12:00:00"
        }, {
            "dt": 1470668400,
            "main": {
                "temp": 299.907,
                "temp_min": 299.907,
                "temp_max": 299.907,
                "pressure": 1004.18,
                "sea_level": 1036.68,
                "grnd_level": 1004.18,
                "humidity": 66,
                "temp_kf": 0
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01d"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 1.87,
                "deg": 216
            },
            "rain": {},
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-08 15:00:00"
        }, {
            "dt": 1470679200,
            "main": {
                "temp": 297.705,
                "temp_min": 297.705,
                "temp_max": 297.705,
                "pressure": 1003.33,
                "sea_level": 1035.95,
                "grnd_level": 1003.33,
                "humidity": 73,
                "temp_kf": 0
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01d"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 1.26,
                "deg": 200.002
            },
            "rain": {},
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-08 18:00:00"
        }, {
            "dt": 1470690000,
            "main": {
                "temp": 291.323,
                "temp_min": 291.323,
                "temp_max": 291.323,
                "pressure": 1004.25,
                "sea_level": 1037.15,
                "grnd_level": 1004.25,
                "humidity": 85,
                "temp_kf": 0
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01n"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 0.91,
                "deg": 244.501
            },
            "rain": {},
            "sys": {
                "pod": "n"
            },
            "dt_txt": "2016-08-08 21:00:00"
        }, {
            "dt": 1470700800,
            "main": {
                "temp": 289.484,
                "temp_min": 289.484,
                "temp_max": 289.484,
                "pressure": 1004.45,
                "sea_level": 1037.46,
                "grnd_level": 1004.45,
                "humidity": 85,
                "temp_kf": 0
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01n"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 1.62,
                "deg": 8.50397
            },
            "rain": {},
            "sys": {
                "pod": "n"
            },
            "dt_txt": "2016-08-09 00:00:00"
        }, {
            "dt": 1470711600,
            "main": {
                "temp": 288.766,
                "temp_min": 288.766,
                "temp_max": 288.766,
                "pressure": 1003.89,
                "sea_level": 1037.08,
                "grnd_level": 1003.89,
                "humidity": 83,
                "temp_kf": 0
            },
            "weather": [{
                "id": 500,
                "main": "Rain",
                "description": "light rain",
                "icon": "10n"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 2.02,
                "deg": 52.5244
            },
            "rain": {
                "3h": 0.0025
            },
            "sys": {
                "pod": "n"
            },
            "dt_txt": "2016-08-09 03:00:00"
        }, {
            "dt": 1470722400,
            "main": {
                "temp": 292.642,
                "temp_min": 292.642,
                "temp_max": 292.642,
                "pressure": 1004.42,
                "sea_level": 1037.38,
                "grnd_level": 1004.42,
                "humidity": 76,
                "temp_kf": 0
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01d"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 2.61,
                "deg": 60.0056
            },
            "rain": {},
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-09 06:00:00"
        }, {
            "dt": 1470733200,
            "main": {
                "temp": 298.453,
                "temp_min": 298.453,
                "temp_max": 298.453,
                "pressure": 1004.37,
                "sea_level": 1037,
                "grnd_level": 1004.37,
                "humidity": 70,
                "temp_kf": 0
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01d"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 1.77,
                "deg": 153.5
            },
            "rain": {},
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-09 09:00:00"
        }, {
            "dt": 1470744000,
            "main": {
                "temp": 300.624,
                "temp_min": 300.624,
                "temp_max": 300.624,
                "pressure": 1002.73,
                "sea_level": 1035.28,
                "grnd_level": 1002.73,
                "humidity": 65,
                "temp_kf": 0
            },
            "weather": [{
                "id": 800,
                "main": "Clear",
                "description": "clear sky",
                "icon": "01d"
            }],
            "clouds": {
                "all": 0
            },
            "wind": {
                "speed": 2.08,
                "deg": 225.5
            },
            "rain": {},
            "sys": {
                "pod": "d"
            },
            "dt_txt": "2016-08-09 12:00:00"
        }]
    }

[More information can be found on open weather documentation website](http://openweathermap.org/api)