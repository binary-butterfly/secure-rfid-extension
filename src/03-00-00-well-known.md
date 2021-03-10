# Well-Known Veröffentlichung der Autorisierungs-Endpunkte

Um auf Basis der ausgelesenen zweiten Datenspur das genutzte eMSP-Backend zu bekommen, wird [gemäß RFC 8615](https://tools.ietf.org/html/rfc8615) der Endpunkt als JSON veröffentlicht.

Da sich durch Unternehmens-Zusammenführungen oder Änderungen von Markennamen der eigentliche Autorisierungs-Endpunkt ändern kann, kann es durchaus vorkommen, dass der Autorisierungs-Server einen anderen Hostname hat als der auf der RFID-Karte angegebene Well-Known Hostname. Es ist sehr empfehlenswert, als Well-Known-Hostname einen sehr langlebigen Hostname zu wählen: ein Endkunde bekommt diesen nie zu Gesicht, ein Verlust der zum Hostname gehörigen Domain würde aber den Verlust der Roamingfähigkeit aller im Feld befindlicher Karten des eMSP bedeuten.

Für den Well-Known-Endpunkt ist der URL-Suffix-Ordner `rfid-roaming` vorgesehen, in welchem die `main.json` enthalten sein muss. Der vollständige Pfad lautet daher:

```
/.well-known/rfid-roaming/main.json
```

## Die main.json

In der `main.json` können ein oder mehrere Endpunkte nach der folgenden Struktur angegeben werden:

```
{
    "version": "1.0",
    "ttl": 86400,
    "protocols": {
        "ocpi": [
            {
                "name": "OCPI Server 01",
                "url": "https://1.ocpi.okfn.de/server/external,
                "stage": "production"
            },
            {
                "name": "OCPI Server 02",
                "url": "https://2.ocpi.okfn.de/server/external,
                "stage": "production"
            },
            {
                "name": "OCPI Staging Server",
                "url": "https://sandbox.ocpi.okfn.de/server/external,
                "stage": "sandbox"
            }
        ],
        "ochp": [
            {
                "name": "OCHP Server",
                "url: "https://ochp.okfn.de/server/external",
                "stage": "production"
            }
        ]
    }
}
```

In `version` wird die Version des hier beschriebenen Industrie-Standards angegeben. In `ttl` wird die Gültigkeit der Daten in Sekunden angegeben, nach dieser muss ein CPO die Werte erneut abrufen. In `protocols` werden die jeweiligen Endppunkte ausgegeben.

Innerhalb von `protocols` wird dabei zunächst die Art des Protokolls angegeben. Je Protokoll sind einer oder mehrere Endpunkte möglich, wobei der oberste Endpunkt die höchste Priorität hat. Es können jedoch weitere Endpunkte angegeben werden, um im Falle eines Server- oder Rechenzentrum-Ausfalls weitere Endpunkte abzufragen.

Im Feld `name` soll ein beschreibender Name stehen, in `url` der Entry-Endpunkt des Protokolls, bei OCPI ist dies zum Beispiel der in 1.1 definierte `version information endpoint`. Mit dem Feld `stage` können zusätzlich andere Stages ausgegeben werden, um automatisiert Sandbox-Tests durchführen zu können.

Ein JSON-Schema der Datei kann im Ordner `schema` eingesehen werden.
