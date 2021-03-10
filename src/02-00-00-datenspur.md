# Die Datenspur auf der RFID-Karte

Die Datenspur muss eine ASN.1 Struktur enthalten, um neben dem Hostname des eMSP auch weitere proprietäre Daten aufzunehmen. Wie bei der von NXP aufgebrachten Datenspur wird das BER-TLV Encoding eingesetzt.

Als umrahmenden Tag wird das Tag `70` verwendet, als Tag für den UTF8-Hostname `0C`. In einer TVL-Struktur sieht dies wie folgt aus:

```
70 LL 0C LL XXXXXXXXXX
```

`LL` sind hierbei die Länge des Tag-Inhaltes, `XXXXXXXXXX` die Daten des Tags `OC`. Der Hostname `okfn.de` wird so zu:

```
70 09 0C 07 6f6b666e2e6465
```

Möchte man weitere Daten in die Spur einfügen, so ist dies gemäß der TLV-Struktur mit einem eigenen Tag möglich. Die Tags `00` bis `3F` sind reserviert für offizielle Erweiterungen, mit den Tags `40` bis `4F` lassen sich proprietäre Erweiterungen umsetzen. Ein zusätzlicher Tag `4D` müsste wie folgt integriert werden:

```
70 LL 0C LL XXXXXXXXXX 4D LL YYYYYYYY  
```

Also zum Beispiel:

``` 
70 10 0C 07 6f6b666e2e6465 4D 04 62696b65
```

Das zweite Byte, also das Längen-Byte von `70`, wird entsprechend mit angepasst, da die `70` über die komplette Datenspur geht.
