Bash Json Parser
================

A simple bash parser that uses python to query from values with dot-notation. Fairly simple library to use. The code is very simple, if you need additional functionality please feel free to add.

Sample Json
-----
```json
{
    "took": 1,
    "timed_out": false,
    "_shards": {
        "total": 1,
        "successful": 1,
        "failed": 0
    },
    "hits": {
        "total": 1,
        "max_score": 1.4142135,
        "hits": [
            {
                "_index": "command",
                "_type": "User",
                "_id": "AUnn9-3omsClW1gNsSXi",
                "_score": 1.4142135,
                "_source": {
                    "customerId": "blah",
                    "email": "ferronrsmith@gmail.com",
                    "password": "V7KtmQRNM3GXwMOf04I1asdsP-sdas2323B5Io",
                    "validated": true,
                    "areas": [
                        "Production"
                    ],
                    "access": [
                        "merchandising",
                        "queryRewrite",
                        "engineConfiguration",
                        "admin"
                    ]
                }
            }
        ]
    }
}
```


Accessing Values at depth one
--------

```bash
	./parser 'took' sample.json
	# will return '1'
```

Accessing Arrays
--------

```bash
	./parser 'hits.hits' sample.json
	# will return the hits array. not useful in bash \
    as it's a python dictionary as shown below :
```

```json
"hits": [
    {
        "_index": "command",
        "_type": "User",
        "_id": "AUnn9-3omsClW1gNsSXi",
        "_score": 1.4142135,
        "_source": {
            "customerId": "blah",
            "email": "ferronrsmith@gmail.com",
            "password": "V7KtmQRNM3GXwMOf04I1asdsP-sdas2323B5Io",
            "validated": true,
            "areas": [
                "Production"
            ],
            "access": [
                "merchandising",
                "queryRewrite",
                "engineConfiguration",
                "admin"
            ]
        }
    }
]
```


Accessing Arrays Elements inside an array
--------

```bash
	./parser 'hits.hits.0._source.email' sample.json
	# will return 'ferronrsmith@gmail.com'
```

Going in Limbo
--------

```bash
	./parser 'hits.hits.0._source.access.1' sample.json
	# will return 'queryRewrite'
```


...
----
I have tested it will fairly nested json and it still works! feel free to write your own examples and enhancements, thanks!