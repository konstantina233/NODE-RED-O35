# Ροές Αυτοματισμού Node-RED (Smart Home Flows)

Αυτό το αρχείο περιέχει τις πλήρεις ροές (flows) σε μορφή JSON για το σύστημα αυτοματισμού έξυπνου σπιτιού στο Node-RED. Περιλαμβάνει την επεξεργασία δεδομένων από αρχεία CSV και τον έλεγχο συσκευών με βάση τις τιμές των αισθητήρων.
### Οδηγίες Εισαγωγής Κώδικα

Για να εισαγάγετε αυτόν τον κώδικα στο Node-RED:

0. Πραγματοποιήστε λήψη και εγκατάσταση του περιβάλλοντος Node-RED, ακολουθώντας τις οδηγίες από την επίσημη ιστοσελίδα. Εάν το έχετε ήδη εγκαταστήσει, βεβαιωθείτε ότι η υπηρεσία εκτελείται κανονικά.Τις οδηγίες μπορείτε να τις βρείτε στο link: https://nodered.org/docs/getting-started/
1. **Αντιγράψτε** τον JSON κώδικα.
2. Στο workspace του Node-RED, ανοίξτε το κεντρικό μενού (εικονίδιο **☰**) στην επάνω δεξιά γωνία, ακριβώς δίπλα από το κουμπί **Deploy**.
3. Επιλέξτε **Import**.
4. Κάντε επικόλληση (Paste) τον κώδικα στο πεδίο και πατήστε το κουμπί **Import** στο κάτω μέρος του αναδυόμενου παραθύρου.
5. Πατήστε **Deploy** .
6. Στο Flow με όνομα εισαγωγή δεδομένων, πατήστε το **timestamp** .
```json

[
    {
        "id": "caa0099ca9e73e15",
        "type": "tab",
        "label": "εισαγωγη δεδομένων",
        "disabled": false,
        "info": "",
        "env": []
    },
    {
        "id": "792382d0cd50fc91",
        "type": "file in",
        "z": "caa0099ca9e73e15",
        "name": "",
        "filename": "C:\\Users\\eugep\\Desktop\\Data3.csv",
        "filenameType": "str",
        "format": "utf8",
        "chunk": false,
        "sendError": false,
        "encoding": "ISO-8859-7",
        "allProps": false,
        "x": 360,
        "y": 260,
        "wires": [
            [
                "9bc33aa1a746efe3"
            ]
        ]
    },
    {
        "id": "9bc33aa1a746efe3",
        "type": "csv",
        "z": "caa0099ca9e73e15",
        "name": "",
        "spec": "rfc",
        "sep": ";",
        "hdrin": true,
        "hdrout": "none",
        "multi": "one",
        "ret": "\\r\\n",
        "temp": "",
        "skip": "0",
        "strings": true,
        "include_empty_strings": "",
        "include_null_values": "",
        "x": 610,
        "y": 260,
        "wires": [
            [
                "cb3c14853dc5031a"
            ]
        ]
    },
    {
        "id": "519ba151cffbfc43",
        "type": "inject",
        "z": "caa0099ca9e73e15",
        "name": "",
        "props": [
            {
                "p": "payload"
            },
            {
                "p": "topic",
                "vt": "str"
            }
        ],
        "repeat": "",
        "crontab": "",
        "once": false,
        "onceDelay": 0.1,
        "topic": "",
        "payload": "",
        "payloadType": "date",
        "x": 100,
        "y": 260,
        "wires": [
            [
                "792382d0cd50fc91"
            ]
        ]
    },
    {
        "id": "cb3c14853dc5031a",
        "type": "delay",
        "z": "caa0099ca9e73e15",
        "name": "",
        "pauseType": "rate",
        "timeout": "5",
        "timeoutUnits": "seconds",
        "rate": "1",
        "nbRateUnits": "2",
        "rateUnits": "second",
        "randomFirst": "1",
        "randomLast": "5",
        "randomUnits": "seconds",
        "drop": false,
        "allowrate": false,
        "outputs": 1,
        "x": 800,
        "y": 260,
        "wires": [
            [
                "3dd6ad031f22e3f1",
                "057dfd0e3d3b4154"
            ]
        ]
    },
    {
        "id": "3dd6ad031f22e3f1",
        "type": "switch",
        "z": "caa0099ca9e73e15",
        "name": "",
        "property": "payload.sensor",
        "propertyType": "jsonata",
        "rules": [
            {
                "t": "eq",
                "v": "υγρασία",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "θερμοκρασία",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "mq2",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "κίνηση",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "γκαραζόπορτα",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "φωτεινότητα",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "πόρτα ψυγείου",
                "vt": "str"
            }
        ],
        "checkall": "true",
        "repair": false,
        "outputs": 7,
        "x": 990,
        "y": 260,
        "wires": [
            [
                "0d380ac4662b5680"
            ],
            [
                "f9148fa0c2f8d373"
            ],
            [
                "cf2bb4e0a912e8fd"
            ],
            [
                "df8a16fe3a128eb6"
            ],
            [
                "94f8aba5a07e2b9b"
            ],
            [
                "ce69737438182db9"
            ],
            [
                "1bcddda4d2cb38f0"
            ]
        ]
    },
    {
        "id": "0d380ac4662b5680",
        "type": "link out",
        "z": "caa0099ca9e73e15",
        "name": "link out 6",
        "mode": "link",
        "links": [
            "3c0444f0fd09ad0a"
        ],
        "x": 1125,
        "y": 20,
        "wires": []
    },
    {
        "id": "f9148fa0c2f8d373",
        "type": "link out",
        "z": "caa0099ca9e73e15",
        "name": "link out 7",
        "mode": "link",
        "links": [
            "96f81cf77dbf2e13"
        ],
        "x": 1135,
        "y": 80,
        "wires": []
    },
    {
        "id": "cf2bb4e0a912e8fd",
        "type": "link out",
        "z": "caa0099ca9e73e15",
        "name": "link out 8",
        "mode": "link",
        "links": [
            "538ca9d73d69e032"
        ],
        "x": 1175,
        "y": 140,
        "wires": []
    },
    {
        "id": "df8a16fe3a128eb6",
        "type": "link out",
        "z": "caa0099ca9e73e15",
        "name": "link out 9",
        "mode": "link",
        "links": [
            "140cd892096018c1"
        ],
        "x": 1175,
        "y": 200,
        "wires": []
    },
    {
        "id": "94f8aba5a07e2b9b",
        "type": "link out",
        "z": "caa0099ca9e73e15",
        "name": "link out 10",
        "mode": "link",
        "links": [
            "2d28c6c6086aabcd"
        ],
        "x": 1175,
        "y": 260,
        "wires": []
    },
    {
        "id": "ce69737438182db9",
        "type": "link out",
        "z": "caa0099ca9e73e15",
        "name": "link out 11",
        "mode": "link",
        "links": [
            "d25128de86177337"
        ],
        "x": 1155,
        "y": 320,
        "wires": []
    },
    {
        "id": "1bcddda4d2cb38f0",
        "type": "link out",
        "z": "caa0099ca9e73e15",
        "name": "link out 12",
        "mode": "link",
        "links": [
            "28ef3a1816c002e1"
        ],
        "x": 1165,
        "y": 380,
        "wires": []
    },
    {
        "id": "057dfd0e3d3b4154",
        "type": "change",
        "z": "caa0099ca9e73e15",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "payload.Περίοδος_Ώρα",
                "tot": "jsonata"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 760,
        "y": 480,
        "wires": [
            [
                "41dd57e6a95d09d5"
            ]
        ]
    },
    {
        "id": "41dd57e6a95d09d5",
        "type": "change",
        "z": "caa0099ca9e73e15",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "timestamp",
                "pt": "global",
                "to": "payload",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 1000,
        "y": 500,
        "wires": [
            []
        ]
    },
    {
        "id": "b8151c571b3ac7c7",
        "type": "tab",
        "label": "αισθητηρας φωτεινοτητας",
        "disabled": false,
        "info": "",
        "env": []
    },
    {
        "id": "2c8494a2645cb74e",
        "type": "change",
        "z": "b8151c571b3ac7c7",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "$log10(payload + 1)",
                "tot": "jsonata"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 440,
        "y": 240,
        "wires": [
            []
        ]
    },
    {
        "id": "660bf76a25693e23",
        "type": "range",
        "z": "b8151c571b3ac7c7",
        "minin": "0",
        "maxin": "100000",
        "minout": "10",
        "maxout": "100",
        "action": "clamp",
        "round": true,
        "property": "payload",
        "name": "",
        "x": 580,
        "y": 80,
        "wires": [
            [
                "770ea81625024d21"
            ]
        ]
    },
    {
        "id": "b89ea0ca05cc9fdc",
        "type": "debug",
        "z": "b8151c571b3ac7c7",
        "name": "debug 4",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 960,
        "y": 80,
        "wires": []
    },
    {
        "id": "26ee173d4260549c",
        "type": "change",
        "z": "b8151c571b3ac7c7",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "payload.value",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 300,
        "y": 80,
        "wires": [
            [
                "660bf76a25693e23"
            ]
        ]
    },
    {
        "id": "770ea81625024d21",
        "type": "template",
        "z": "b8151c571b3ac7c7",
        "name": "",
        "field": "payload",
        "fieldType": "msg",
        "format": "handlebars",
        "syntax": "mustache",
        "template": "Time:{{{global.timestamp}}},Φωτεινότητα οθόνης: {{payload}} %",
        "output": "str",
        "x": 780,
        "y": 80,
        "wires": [
            [
                "b89ea0ca05cc9fdc"
            ]
        ]
    },
    {
        "id": "d25128de86177337",
        "type": "link in",
        "z": "b8151c571b3ac7c7",
        "name": "link in 11",
        "links": [
            "ce69737438182db9"
        ],
        "x": 145,
        "y": 80,
        "wires": [
            [
                "26ee173d4260549c"
            ]
        ]
    },
    {
        "id": "d838b4da5bd7b4ee",
        "type": "tab",
        "label": "πορτα ψυγειου",
        "disabled": false,
        "info": "",
        "env": []
    },
    {
        "id": "f7e4a181c38014bb",
        "type": "trigger",
        "z": "d838b4da5bd7b4ee",
        "name": "",
        "op1": "",
        "op2": "Κλείσε την πόρτα του ψυγείου.",
        "op1type": "nul",
        "op2type": "str",
        "duration": "11",
        "extend": false,
        "overrideDelay": false,
        "units": "s",
        "reset": "0",
        "bytopic": "all",
        "topic": "topic",
        "outputs": 1,
        "x": 590,
        "y": 320,
        "wires": [
            [
                "9d361afe200cb84f",
                "8c4fb0053e7ecab4"
            ]
        ]
    },
    {
        "id": "a2665792c2f9bb5b",
        "type": "change",
        "z": "d838b4da5bd7b4ee",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "Η πόρτα του ψυγείου έκλεισε!",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 460,
        "y": 480,
        "wires": [
            [
                "e947008011049fcb",
                "ee7b3a5b17599e79"
            ]
        ]
    },
    {
        "id": "9d361afe200cb84f",
        "type": "ui_audio",
        "z": "d838b4da5bd7b4ee",
        "name": "",
        "group": "a9fa5578717d132e",
        "voice": "Microsoft Mark - English (United States)",
        "always": true,
        "x": 840,
        "y": 360,
        "wires": []
    },
    {
        "id": "e947008011049fcb",
        "type": "ui_audio",
        "z": "d838b4da5bd7b4ee",
        "name": "",
        "group": "a9fa5578717d132e",
        "voice": "Microsoft Mark - English (United States)",
        "always": true,
        "x": 760,
        "y": 520,
        "wires": []
    },
    {
        "id": "12fdd6bb23323466",
        "type": "ui_toast",
        "z": "d838b4da5bd7b4ee",
        "position": "top right",
        "displayTime": "3",
        "highlight": "",
        "sendall": true,
        "outputs": 0,
        "ok": "OK",
        "cancel": "",
        "raw": false,
        "className": "",
        "topic": "",
        "name": "",
        "x": 950,
        "y": 720,
        "wires": []
    },
    {
        "id": "03f390dedb789d17",
        "type": "switch",
        "z": "d838b4da5bd7b4ee",
        "name": "",
        "property": "payload",
        "propertyType": "msg",
        "rules": [
            {
                "t": "eq",
                "v": "1",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "0",
                "vt": "str"
            }
        ],
        "checkall": "true",
        "repair": false,
        "outputs": 2,
        "x": 290,
        "y": 340,
        "wires": [
            [
                "3efab4a79ab1c2cc",
                "f7e4a181c38014bb"
            ],
            [
                "a2665792c2f9bb5b",
                "f7e4a181c38014bb"
            ]
        ]
    },
    {
        "id": "51bf08761767e607",
        "type": "change",
        "z": "d838b4da5bd7b4ee",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "payload.value",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 140,
        "y": 340,
        "wires": [
            [
                "03f390dedb789d17"
            ]
        ]
    },
    {
        "id": "3efab4a79ab1c2cc",
        "type": "change",
        "z": "d838b4da5bd7b4ee",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "Η πόρτα του ψυγείου ανοιξε!",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 660,
        "y": 220,
        "wires": [
            [
                "da5b5d5f8d2cbc44"
            ]
        ]
    },
    {
        "id": "ee7b3a5b17599e79",
        "type": "change",
        "z": "d838b4da5bd7b4ee",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "Η πόρτα του ψυγειου έκλεισε!",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 760,
        "y": 440,
        "wires": [
            [
                "3878f9b7400f3423"
            ]
        ]
    },
    {
        "id": "8c4fb0053e7ecab4",
        "type": "debug",
        "z": "d838b4da5bd7b4ee",
        "name": "debug 2",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "false",
        "statusVal": "",
        "statusType": "auto",
        "x": 1080,
        "y": 220,
        "wires": []
    },
    {
        "id": "8ed4cdf7024b0490",
        "type": "debug",
        "z": "d838b4da5bd7b4ee",
        "name": "debug 5",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 1080,
        "y": 440,
        "wires": []
    },
    {
        "id": "28ef3a1816c002e1",
        "type": "link in",
        "z": "d838b4da5bd7b4ee",
        "name": "link in 12",
        "links": [
            "1bcddda4d2cb38f0"
        ],
        "x": 205,
        "y": 160,
        "wires": [
            [
                "51bf08761767e607"
            ]
        ]
    },
    {
        "id": "da5b5d5f8d2cbc44",
        "type": "template",
        "z": "d838b4da5bd7b4ee",
        "name": "",
        "field": "payload",
        "fieldType": "msg",
        "format": "handlebars",
        "syntax": "mustache",
        "template": "Time:{{{global.timestamp}}}  {{payload}}",
        "output": "str",
        "x": 900,
        "y": 180,
        "wires": [
            [
                "8c4fb0053e7ecab4"
            ]
        ]
    },
    {
        "id": "3878f9b7400f3423",
        "type": "template",
        "z": "d838b4da5bd7b4ee",
        "name": "",
        "field": "payload",
        "fieldType": "msg",
        "format": "handlebars",
        "syntax": "mustache",
        "template": "Time:{{{global.timestamp}}}  {{payload}}",
        "output": "str",
        "x": 920,
        "y": 440,
        "wires": [
            [
                "8ed4cdf7024b0490"
            ]
        ]
    },
    {
        "id": "dd0c96f039fa0a45",
        "type": "tab",
        "label": "γκαραζοπορτα",
        "disabled": false,
        "info": "",
        "env": []
    },
    {
        "id": "1a077c5862cc52b8",
        "type": "switch",
        "z": "dd0c96f039fa0a45",
        "name": "Έλεγχοσ κίνησης",
        "property": "payload",
        "propertyType": "msg",
        "rules": [
            {
                "t": "eq",
                "v": "1",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "0",
                "vt": "str"
            }
        ],
        "checkall": "true",
        "repair": false,
        "outputs": 2,
        "x": 450,
        "y": 160,
        "wires": [
            [
                "6e31468a4527a60a"
            ],
            [
                "f254c73e15197063"
            ]
        ]
    },
    {
        "id": "2fdd4d200f036c9d",
        "type": "debug",
        "z": "dd0c96f039fa0a45",
        "name": "Γκαζαρόπορτα",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 1020,
        "y": 180,
        "wires": []
    },
    {
        "id": "6e31468a4527a60a",
        "type": "template",
        "z": "dd0c96f039fa0a45",
        "name": "",
        "field": "payload",
        "fieldType": "msg",
        "format": "handlebars",
        "syntax": "mustache",
        "template": "Time:{{{global.timestamp}}} Η γκαραζόπορτα άνοιξε!",
        "output": "str",
        "x": 700,
        "y": 80,
        "wires": [
            [
                "2fdd4d200f036c9d"
            ]
        ]
    },
    {
        "id": "f254c73e15197063",
        "type": "template",
        "z": "dd0c96f039fa0a45",
        "name": "",
        "field": "payload",
        "fieldType": "msg",
        "format": "handlebars",
        "syntax": "mustache",
        "template": "Time:{{{global.timestamp}}} Η γκαραζόπορτα έκλεισε!",
        "output": "str",
        "x": 720,
        "y": 240,
        "wires": [
            [
                "2fdd4d200f036c9d"
            ]
        ]
    },
    {
        "id": "2d28c6c6086aabcd",
        "type": "link in",
        "z": "dd0c96f039fa0a45",
        "name": "link in 10",
        "links": [
            "94f8aba5a07e2b9b"
        ],
        "x": 65,
        "y": 160,
        "wires": [
            [
                "417613ef65f062c2"
            ]
        ]
    },
    {
        "id": "417613ef65f062c2",
        "type": "change",
        "z": "dd0c96f039fa0a45",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "payload.value",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 180,
        "y": 160,
        "wires": [
            [
                "1a077c5862cc52b8"
            ]
        ]
    },
    {
        "id": "e0ca0aec1e745e97",
        "type": "tab",
        "label": "αισθητηρας καπνου",
        "disabled": false,
        "info": "",
        "env": []
    },
    {
        "id": "147da0322137df67",
        "type": "switch",
        "z": "e0ca0aec1e745e97",
        "name": "value>350?",
        "property": "payload",
        "propertyType": "msg",
        "rules": [
            {
                "t": "gt",
                "v": "350",
                "vt": "num"
            },
            {
                "t": "lte",
                "v": "350",
                "vt": "num"
            }
        ],
        "checkall": "true",
        "repair": false,
        "outputs": 2,
        "x": 670,
        "y": 80,
        "wires": [
            [
                "cfd2c7e462b71c13"
            ],
            [
                "0fa3acba363efe12"
            ]
        ]
    },
    {
        "id": "903fc43ad310b912",
        "type": "change",
        "z": "e0ca0aec1e745e97",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "payload.value",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 460,
        "y": 80,
        "wires": [
            [
                "147da0322137df67"
            ]
        ]
    },
    {
        "id": "fcec449da84666a2",
        "type": "debug",
        "z": "e0ca0aec1e745e97",
        "name": "debug 3",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 1020,
        "y": 120,
        "wires": []
    },
    {
        "id": "cfd2c7e462b71c13",
        "type": "template",
        "z": "e0ca0aec1e745e97",
        "name": "",
        "field": "payload",
        "fieldType": "msg",
        "format": "handlebars",
        "syntax": "mustache",
        "template": "Time:{{{global.timestamp}}} ΠΡΟΣΟΧΗ: Ανιχνεύθηκε καπνός! Η τιμή είναι: {{payload}}",
        "output": "str",
        "x": 880,
        "y": 80,
        "wires": [
            [
                "fcec449da84666a2"
            ]
        ]
    },
    {
        "id": "0fa3acba363efe12",
        "type": "template",
        "z": "e0ca0aec1e745e97",
        "name": "",
        "field": "payload",
        "fieldType": "msg",
        "format": "handlebars",
        "syntax": "mustache",
        "template": "Time:{{{global.timestamp}}}, smoke value: {{payload}}, status:normal",
        "output": "str",
        "x": 840,
        "y": 140,
        "wires": [
            [
                "a44fcbdb5f65cda6"
            ]
        ]
    },
    {
        "id": "a44fcbdb5f65cda6",
        "type": "debug",
        "z": "e0ca0aec1e745e97",
        "name": "debug 1",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 940,
        "y": 200,
        "wires": []
    },
    {
        "id": "538ca9d73d69e032",
        "type": "link in",
        "z": "e0ca0aec1e745e97",
        "name": "link in 8",
        "links": [
            "cf2bb4e0a912e8fd"
        ],
        "x": 275,
        "y": 80,
        "wires": [
            [
                "903fc43ad310b912"
            ]
        ]
    },
    {
        "id": "c40db8e0ce2017dc",
        "type": "tab",
        "label": "αφυγραντηρας",
        "disabled": false,
        "info": "",
        "env": []
    },
    {
        "id": "327f58524a2ace0a",
        "type": "change",
        "z": "c40db8e0ce2017dc",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "payload.value",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 560,
        "y": 560,
        "wires": [
            [
                "31e776a8d5e25837"
            ]
        ]
    },
    {
        "id": "b25d4e75d5962a70",
        "type": "switch",
        "z": "c40db8e0ce2017dc",
        "name": "testing",
        "property": "payload",
        "propertyType": "msg",
        "rules": [
            {
                "t": "btwn",
                "v": "45",
                "vt": "num",
                "v2": "55",
                "v2t": "num"
            },
            {
                "t": "gt",
                "v": "55",
                "vt": "num"
            }
        ],
        "checkall": "true",
        "repair": false,
        "outputs": 2,
        "x": 1010,
        "y": 560,
        "wires": [
            [
                "4a5ffc8b60d5d3b1"
            ],
            [
                "2e74648de9ec679a"
            ]
        ]
    },
    {
        "id": "4a5ffc8b60d5d3b1",
        "type": "link out",
        "z": "c40db8e0ce2017dc",
        "name": "link out 3",
        "mode": "link",
        "links": [
            "317e1060cf452bc6"
        ],
        "x": 1285,
        "y": 460,
        "wires": []
    },
    {
        "id": "2e74648de9ec679a",
        "type": "link out",
        "z": "c40db8e0ce2017dc",
        "name": "link out 4",
        "mode": "link",
        "links": [
            "6511ce06dd0cb94a"
        ],
        "x": 1295,
        "y": 620,
        "wires": []
    },
    {
        "id": "317e1060cf452bc6",
        "type": "link in",
        "z": "c40db8e0ce2017dc",
        "name": "link in 3",
        "links": [
            "4a5ffc8b60d5d3b1"
        ],
        "x": 355,
        "y": 840,
        "wires": [
            [
                "792f0dedcc23c50d"
            ]
        ]
    },
    {
        "id": "6511ce06dd0cb94a",
        "type": "link in",
        "z": "c40db8e0ce2017dc",
        "name": "link in 4",
        "links": [
            "2e74648de9ec679a"
        ],
        "x": 365,
        "y": 940,
        "wires": [
            [
                "0a62c64dbc9db7d1"
            ]
        ]
    },
    {
        "id": "3e01c7ed166d2eed",
        "type": "debug",
        "z": "c40db8e0ce2017dc",
        "name": "OFF",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 1290,
        "y": 840,
        "wires": []
    },
    {
        "id": "7b1ebd228568d198",
        "type": "debug",
        "z": "c40db8e0ce2017dc",
        "name": "ON",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 1030,
        "y": 940,
        "wires": []
    },
    {
        "id": "31e776a8d5e25837",
        "type": "rbe",
        "z": "c40db8e0ce2017dc",
        "name": "",
        "func": "deadband",
        "gap": "3",
        "start": "",
        "inout": "out",
        "septopics": false,
        "property": "payload",
        "topi": "topic",
        "x": 800,
        "y": 560,
        "wires": [
            [
                "b25d4e75d5962a70"
            ]
        ]
    },
    {
        "id": "3c0444f0fd09ad0a",
        "type": "link in",
        "z": "c40db8e0ce2017dc",
        "name": "link in 6",
        "links": [
            "0d380ac4662b5680"
        ],
        "x": 375,
        "y": 560,
        "wires": [
            [
                "327f58524a2ace0a"
            ]
        ]
    },
    {
        "id": "792f0dedcc23c50d",
        "type": "template",
        "z": "c40db8e0ce2017dc",
        "name": "",
        "field": "payload",
        "fieldType": "msg",
        "format": "handlebars",
        "syntax": "mustache",
        "template": "Time:{{{global.timestamp}}},Humidity value: {{payload}}%, Αφυγραντήρας:OFF",
        "output": "str",
        "x": 980,
        "y": 840,
        "wires": [
            [
                "3e01c7ed166d2eed"
            ]
        ]
    },
    {
        "id": "0a62c64dbc9db7d1",
        "type": "template",
        "z": "c40db8e0ce2017dc",
        "name": "",
        "field": "payload",
        "fieldType": "msg",
        "format": "handlebars",
        "syntax": "mustache",
        "template": "Time:{{{global.timestamp}}},Humidity value: {{payload}}%, Αφυγραντήρας:ON\n",
        "output": "str",
        "x": 780,
        "y": 940,
        "wires": [
            [
                "7b1ebd228568d198"
            ]
        ]
    },
    {
        "id": "8da9c22f90d38586",
        "type": "tab",
        "label": "Smart AC (Διορθωμένο CSV)",
        "disabled": false,
        "info": "Διαβάζει το CSV γραμμή-γραμμή και προσομοιώνει τον αισθητήρα."
    },
    {
        "id": "33d7d78e393bac94",
        "type": "inject",
        "z": "8da9c22f90d38586",
        "name": "Sensor Simulation",
        "props": [
            {
                "p": "payload"
            }
        ],
        "repeat": "",
        "crontab": "",
        "once": true,
        "onceDelay": 0.1,
        "topic": "",
        "payload": "",
        "payloadType": "date",
        "x": 270,
        "y": 440,
        "wires": [
            [
                "b838f18cb0254f09"
            ]
        ]
    },
    {
        "id": "b838f18cb0254f09",
        "type": "file in",
        "z": "8da9c22f90d38586",
        "name": "",
        "filename": "C:\\data\\TemperatureSensor.csv",
        "filenameType": "str",
        "format": "utf8",
        "chunk": false,
        "sendError": false,
        "encoding": "utf8",
        "allProps": false,
        "x": 510,
        "y": 440,
        "wires": [
            [
                "934aa035ea510d56"
            ]
        ]
    },
    {
        "id": "934aa035ea510d56",
        "type": "csv",
        "z": "8da9c22f90d38586",
        "name": "",
        "spec": "rfc",
        "sep": ",",
        "hdrin": "",
        "hdrout": "all",
        "multi": "one",
        "ret": "\\r\\n",
        "temp": "temperature",
        "skip": "0",
        "strings": false,
        "include_empty_strings": "",
        "include_null_values": "",
        "x": 730,
        "y": 540,
        "wires": [
            []
        ]
    },
    {
        "id": "3f31473ec7153bb6",
        "type": "change",
        "z": "8da9c22f90d38586",
        "name": "Keep Number Only",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "payload.temperature",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 810,
        "y": 320,
        "wires": [
            []
        ]
    },
    {
        "id": "2875342bd9e8596a",
        "type": "rbe",
        "z": "8da9c22f90d38586",
        "name": "Only if the value changes",
        "func": "rbe",
        "gap": "",
        "start": "",
        "inout": "out",
        "septopics": true,
        "property": "payload",
        "topi": "topic",
        "x": 810,
        "y": 140,
        "wires": [
            [
                "e1698a375d77982c"
            ]
        ]
    },
    {
        "id": "e1698a375d77982c",
        "type": "switch",
        "z": "8da9c22f90d38586",
        "name": "Limits",
        "property": "payload",
        "propertyType": "msg",
        "rules": [
            {
                "t": "gte",
                "v": "25",
                "vt": "num"
            },
            {
                "t": "lte",
                "v": "24",
                "vt": "num"
            },
            {
                "t": "btwn",
                "v": "24",
                "vt": "num",
                "v2": "25",
                "v2t": "num"
            }
        ],
        "checkall": "false",
        "repair": false,
        "outputs": 3,
        "x": 1150,
        "y": 140,
        "wires": [
            [
                "143f3a84630b69bb"
            ],
            [
                "0ed6925ee9ad96ae"
            ],
            [
                "83156f9863031f17"
            ]
        ]
    },
    {
        "id": "1644cd05d4b1f480",
        "type": "rbe",
        "z": "8da9c22f90d38586",
        "name": "Block Duplicates",
        "func": "rbe",
        "gap": "",
        "start": "",
        "inout": "out",
        "septopics": true,
        "property": "payloa",
        "topi": "topic",
        "x": 1440,
        "y": 520,
        "wires": [
            []
        ]
    },
    {
        "id": "6667c9f49446476b",
        "type": "debug",
        "z": "8da9c22f90d38586",
        "name": "Final Action",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 1930,
        "y": 80,
        "wires": []
    },
    {
        "id": "96f81cf77dbf2e13",
        "type": "link in",
        "z": "8da9c22f90d38586",
        "name": "link in 7",
        "links": [
            "f9148fa0c2f8d373"
        ],
        "x": 335,
        "y": 160,
        "wires": [
            [
                "a0077aad2ec6ca6e"
            ]
        ]
    },
    {
        "id": "a0077aad2ec6ca6e",
        "type": "change",
        "z": "8da9c22f90d38586",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "payload.value",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 520,
        "y": 140,
        "wires": [
            [
                "2875342bd9e8596a"
            ]
        ]
    },
    {
        "id": "143f3a84630b69bb",
        "type": "template",
        "z": "8da9c22f90d38586",
        "name": "",
        "field": "payload",
        "fieldType": "msg",
        "format": "handlebars",
        "syntax": "mustache",
        "template": "Time:{{{global.timestamp}}},temperature value:{{payload}}, status:ON",
        "output": "str",
        "x": 1520,
        "y": 80,
        "wires": [
            [
                "6667c9f49446476b"
            ]
        ]
    },
    {
        "id": "0ed6925ee9ad96ae",
        "type": "template",
        "z": "8da9c22f90d38586",
        "name": "",
        "field": "payload",
        "fieldType": "msg",
        "format": "handlebars",
        "syntax": "mustache",
        "template": "Time:{{{global.timestamp}}},temperature value:{{payload}}, status:OFF",
        "output": "str",
        "x": 1520,
        "y": 220,
        "wires": [
            [
                "cf4711cac5439a71"
            ]
        ]
    },
    {
        "id": "cf4711cac5439a71",
        "type": "debug",
        "z": "8da9c22f90d38586",
        "name": "debug 7",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 1940,
        "y": 220,
        "wires": []
    },
    {
        "id": "83156f9863031f17",
        "type": "template",
        "z": "8da9c22f90d38586",
        "name": "",
        "field": "payload",
        "fieldType": "msg",
        "format": "handlebars",
        "syntax": "mustache",
        "template": "Time:{{{global.timestamp}}},temperature value:{{payload}}, status:ON",
        "output": "str",
        "x": 1520,
        "y": 320,
        "wires": [
            [
                "7c721c344b8a6848"
            ]
        ]
    },
    {
        "id": "7c721c344b8a6848",
        "type": "debug",
        "z": "8da9c22f90d38586",
        "name": "debug 9",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 1940,
        "y": 340,
        "wires": []
    },
    {
        "id": "c5b301b17b75a51b",
        "type": "tab",
        "label": "αισθητηρας κινησης",
        "disabled": false,
        "info": "",
        "env": []
    },
    {
        "id": "b89eb7df89635bee",
        "type": "trigger",
        "z": "c5b301b17b75a51b",
        "name": "",
        "op1": "",
        "op2": "",
        "op1type": "pay",
        "op2type": "nul",
        "duration": "1",
        "extend": false,
        "overrideDelay": false,
        "units": "s",
        "reset": "",
        "bytopic": "all",
        "topic": "topic",
        "outputs": 1,
        "x": 380,
        "y": 100,
        "wires": [
            [
                "7fc8c7bba7fba29e"
            ]
        ]
    },
    {
        "id": "d5d339866df9fe7a",
        "type": "template",
        "z": "c5b301b17b75a51b",
        "name": "",
        "field": "payload",
        "fieldType": "msg",
        "format": "handlebars",
        "syntax": "mustache",
        "template": "Time:{{{global.timestamp}}}  {{payload}}",
        "output": "str",
        "x": 860,
        "y": 300,
        "wires": [
            [
                "7e0cd05c78074892"
            ]
        ]
    },
    {
        "id": "ad2371945a01709b",
        "type": "debug",
        "z": "c5b301b17b75a51b",
        "name": "dashboard",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 1070,
        "y": 80,
        "wires": []
    },
    {
        "id": "7fc8c7bba7fba29e",
        "type": "switch",
        "z": "c5b301b17b75a51b",
        "name": "",
        "property": "payload",
        "propertyType": "msg",
        "rules": [
            {
                "t": "eq",
                "v": "1",
                "vt": "num"
            },
            {
                "t": "eq",
                "v": "0",
                "vt": "num"
            }
        ],
        "checkall": "false",
        "repair": false,
        "outputs": 2,
        "x": 490,
        "y": 160,
        "wires": [
            [
                "81c67afdd5a21e9d"
            ],
            [
                "4d3e8f2a56e6d382"
            ]
        ]
    },
    {
        "id": "a3d67dd35599aa86",
        "type": "template",
        "z": "c5b301b17b75a51b",
        "name": "",
        "field": "payload",
        "fieldType": "msg",
        "format": "handlebars",
        "syntax": "mustache",
        "template": "Time:{{{global.timestamp}}}  {{payload}}",
        "output": "str",
        "x": 900,
        "y": 80,
        "wires": [
            [
                "ad2371945a01709b"
            ]
        ]
    },
    {
        "id": "8d1440ef34423595",
        "type": "ui_audio",
        "z": "c5b301b17b75a51b",
        "name": "",
        "group": "be0f1c7392c46098",
        "voice": "Microsoft Zira - English (United States)",
        "always": true,
        "x": 940,
        "y": 180,
        "wires": []
    },
    {
        "id": "140cd892096018c1",
        "type": "link in",
        "z": "c5b301b17b75a51b",
        "name": "link in 9",
        "links": [
            "df8a16fe3a128eb6"
        ],
        "x": 155,
        "y": 280,
        "wires": [
            [
                "606e25c6fe80daeb"
            ]
        ]
    },
    {
        "id": "606e25c6fe80daeb",
        "type": "change",
        "z": "c5b301b17b75a51b",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "payload.value",
                "tot": "msg"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 220,
        "y": 200,
        "wires": [
            [
                "b89eb7df89635bee"
            ]
        ]
    },
    {
        "id": "81c67afdd5a21e9d",
        "type": "change",
        "z": "c5b301b17b75a51b",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "Η πόρτα εισόδου άνοιξε!",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 680,
        "y": 80,
        "wires": [
            [
                "8d1440ef34423595",
                "a3d67dd35599aa86"
            ]
        ]
    },
    {
        "id": "4d3e8f2a56e6d382",
        "type": "change",
        "z": "c5b301b17b75a51b",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "Ειδοποίηση συστήματος. Η πόρτα εισόδου έκλεισε!",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 620,
        "y": 300,
        "wires": [
            [
                "8d1440ef34423595",
                "d5d339866df9fe7a"
            ]
        ]
    },
    {
        "id": "7e0cd05c78074892",
        "type": "debug",
        "z": "c5b301b17b75a51b",
        "name": "debug 6",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "false",
        "statusVal": "",
        "statusType": "auto",
        "x": 1040,
        "y": 300,
        "wires": []
    },
    {
        "id": "a9fa5578717d132e",
        "type": "ui_group",
        "name": "Υγρασία",
        "tab": "6eb2a24e3d52c08a",
        "order": 1,
        "disp": true,
        "width": 6,
        "collapse": false,
        "className": ""
    },
    {
        "id": "be0f1c7392c46098",
        "type": "ui_group",
        "name": "Default",
        "tab": "c2d23f14e959d673",
        "order": 1,
        "disp": true,
        "width": 6,
        "collapse": false,
        "className": ""
    },
    {
        "id": "6eb2a24e3d52c08a",
        "type": "ui_tab",
        "name": "Σπίτι",
        "icon": "dashboard",
        "disabled": false,
        "hidden": false
    },
    {
        "id": "c2d23f14e959d673",
        "type": "ui_tab",
        "name": "Home",
        "icon": "dashboard",
        "disabled": false,
        "hidden": false
    },
    {
        "id": "9fa4395eed02b470",
        "type": "global-config",
        "env": [],
        "modules": {
            "node-red-dashboard": "3.6.6"
        }
    }
]
