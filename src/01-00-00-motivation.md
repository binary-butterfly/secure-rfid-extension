# Besseres Roaming mit sicheren RFID-Karten

## Motivation

In der DKE-Arbeitsgruppe AK 353.0.8 wurde in Anhang 1 eine abstrakte sichere Ladekarte und die Umsetzung einer solchen Karte im Ladesäulen-Standard OCPP spezifiziert. Eine Implemetierung dieser Ladekarte ist die NXP EV2-J.

Grundsätzlich handelt es sich bei der sicheren Ladekarte um eine Ladekarte mit einem geschützten Private Key, mit welchem ECDSA-Signaturen von Zufallszahlen erstellt werden können. Zusätzlich befinden sich zwei Datenspuren auf der Karte, von der die erste eine Art Mini-Zertifikat des Kartenherstellers über wichtige Daten wie den Public Key und UID der Karte enthält.     

Die EV2-J besitzt aber noch eine zweite Datenspur, und die ist frei beschreibbar. Mit diesem Dokument soll ein Mechanismus aufgezeigt werden, wie mit dieser zweiten Datenspur Roaming in der E-Mobilität erheblich vereinfacht werden kann.
