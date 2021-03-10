## Problemstellung

Roaming basiert zur Zeit auf den realen oder virtuellen UIDs. Um die UIDs einem Betreiber zuzuordnen, mussten im Backend des Ladesäulenbetreibers (CPO) lange UID-Listen gepflegt werden. Eine UID muss im CPO-Backend dem Kartenherausgeber eMSP zugeordnet werden, die Herkunft der Karte geht aus der UID nicht hervor.

Eine Möglichkeit dies zu tun ist der direkte Austausch von Listen. Dies geschieht über eine Vielzahl von Protokollen (z.B. OCPI, OCHP, ...) und Synchronisations-Strategien, was zu Lasten der Zuverlässigkeit geht.

Eine andere Möglichkeit sind zentrale Dienstleister, welche die UID-Zuordnungen verwalten. Dies erhöht jedoch die Komplexität des Gesamtsystems, da es neben CPO und eMSP noch eine dritte Rolle benötigt wird. Zudem sind nicht alle CPOs und eMSPs an einem solchen zentralen System angeschlossen.

Durch die Vielzahl verschiedener Protokolle und Arbeitsweisen ist dies extrem fehleranfällig, z.B. funktionierten Ladekarten manchmal gar nicht, und manchmal braucht es sehr lange, bis eine Sperrung durch fehlende Kontodeckung bei allen CPOs angekommen ist.

