## Lösungsstrategie

Wenn eine RFID-Karte selbst beschreiben könnte, von welchem eMSP sie herausgegeben wurde, so wäre das Problem des UID-Austausches gelöst. Genau dies bietet die zweite Datenspur der NXP EV2-J.

Da Karten länger als einige Monate im Feld brauchen, wäre es aber von Nachteil, wenn man konkrete Endpunkte auf die Karte schreiben würde: dieser kann sich schließlich ändern. Um dieser Anforderung gerecht zu werden werden die [in RFC 8615 definierten](https://tools.ietf.org/html/rfc8615) Well-Known Uniform Resource Identifiers (URIs) verwendet, um den konkreten Endpunkt bekanntzumachen.

Die Spezifikation besteht also aus zwei Kernelementen:

1) Der Spezifikation der Datenspur, welche den Hostname des eMSP beinhalten muss.
2) Die Spezifikation der Well-Known URI, welche den Endpunkt des eMSPs bekannt geben muss.

