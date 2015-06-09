Versionshistorie
================

`English Version of this document. <../../en/book/versions.html>`_

Die Übersicht der Meilensteine finden Sie auf Github unter: https://github.com/mapbender/mapbender/milestones

Zukünftige Meilensteine: Details finden sich unter https://github.com/mapbender/mapbender/issues

 
Milestone 3.0.5.0
-----------------

Release Datum: xx-05-2015

Übersicht der Änderungen finden Sie unter:  https://github.com/mapbender/mapbender-starter/blob/develop/CHANGELOG.md

* **WMS neuladen:** WMS Quellen können nun neugeladen werden, wenn sich deren Strutkur geändert hat.

* **Digitalisierung:** Im Rahmen des Releases wurde das neue Element Digitizer eingeführt. Über dieses kann durch eine YAML-Definition eine Erfassungsmaske für Punkte, Linien oder Flächen aufgebaut werden. Dabei wird wie bisher PostgreSQL als Datenquelle unterstützt. Oracle und SpatiaLite sind experimentell verfügbar. Die Entwicklung wurde so durchgeführt, dass die Erfassung auch auf andere Datenquellen wie z.B. OGC WFS erweitert werden kann.

* **Druck mit Legende:** Im Druck ist es nun möglich, die Legende auf einer separaten Seite auszugeben. Die Ausgabe kann über eine Checkbox gesteuert werden.

* **Konfigurierbarer Layerbaum:** Der Layerbaum unterstützt nun mehr als ein layerset. Sie müssen das Kartenelement anpassen, um die Layersets festzulegen, die angezeigt werden sollen sowie den Layerbaum selbt. Die Dokumentation befindet sich unter `auf der Seite zum Layertree <../bundles/Mapbender/CoreBundle/elements/layertree.html>`_.

* **Verbesserte Infoausgabe:** Die Ausgabe der Infoabfrage wurde für die neue Version verbessert. So bleiben nun die Stile der Infoabfrage erhalten. Dienste, die keine Antwort liefern, werden nicht über einen Reiter angezeigt. Es erfolgen Meldungen, wenn keine Antwort geliefert wurde.

* **Mobiles Template:** In mehreren Projektlösungen haben wir uns bereits mit einer mobilen Lösung auf Basis von Mapbender3 auseinandergesetzt. Nun wird diese Lösung als Mapbender Mobile Template in der neuen Version 3.0.5.0 zur Verfügung gestellt.   Sie finden eine neue Demo-Anwendung in der mapbender.yml mit Namen Mapbender Mobile (mapbender_mobile). Diese können Sie als Vorlage für Ihre Lösung verwenden. In der `Release-Demo <http://demo.mapbender3.org/>`_ kann die Anwendung „Mapbender Mobile“ getestet werden.

* **SASS Compiler:** Änderungen an der Architektur bezüglich des SASS Compilers führen zu einer performanteren Oberfläche.

* **Vendor Specific Parameter:** Eine WMS Layer Instanz unterstützt nun die Angabe von Vendor Specific Parametern, die an einen WMS Request angehangen werden. Die Werte können fest vergeben werden oder auf die User- und Gruppeninformation des angemeldeten Benutzers zurückgreifen. Dokumentation ist unter dem Abschnitt `Vendor Specific Parameters <../book/quickstart.html#konfiguration-von-diensten>`_ verfügbar.

* **Formular-Builder:** In Zusammenhang mit der Digitalisierung können für die Erfassung von dazugehörigen Sachdaten sehr komplexe Formulare generiert werden. Hierbei wurde sich an den Möglichkeiten, die in Mapbender 2.x zur Verfügung stehen, orientiert.

* **Neue Schaltflächen:** Einige Schaltflächen basieren auf einer neuen Schriftart, die alten Schaltflächen sind noch mit dem Namen FontAwesome verfügbar.

* **URL Parameter:** Mapbender3 kann mit Startparametern aufgerufen werden. Eine Liste der Parameter findet sich in der Dokumentation zu den `URL Parametern <../bundles/Mapbender/CoreBundle/elements/map.html#kontrolle-uber-den-aufruf>`_.

* Symfony Update auf 2.3.29.


**Änderungen in der config.yml:**

* Änderung bei einer dbal connection:

  * **logging: false**: Die Option sorgt dafür, das *alle* SQL's nicht mehr geloggt werden. Mehr dazu hier: http://www.loremipsum.at/blog/doctrine-2-sql-profiler-in-debugleiste/

  * **profiling: false**: Profiling von SQL Anfragen. Diese Option kann in der Produktion ausgeschaltet werden.

    Wo möglich sollen die Optionen so umgestellt werden, dass die erst in Debug modus aktiv werden:

    .. code-block:: yaml

                    logging:               "%kernel.debug%"
                    profiling:             "%kernel.debug%" 


**Bekannte Probleme**

* Beim Kopieren einer Anwendung von Mapbender 3.0.4.x muss in der Map/Overview der jeweilige Layerset neu gesetzt werden.
                    

Milestone 3.0.4.1
-----------------

Release Datum: 23-01-2015

Übersicht der Änderungen finden Sie unter:  https://github.com/mapbender/mapbender-starter/blob/develop/CHANGELOG.md

* parameter 'layerRemove' removed from layertree configuration
* option 'removelayer' added into layertree menu
* container accordion structure changed
* import / export from applications added (without acls)
* display layer metadata
* Frontend: Sidepane Accordeon Legend is displayed without horizontal Scrollbar
* Backend: WMS Instanz configuration - contextmenu for layers shows wrong ID (only instance ID)
* Frontend: Legend - displays WMS Information although the checkbox Show
* Frontend: Layertree - contextmenu zoomlayer does not use the layer extent
* Backend: Add Source with user/password - informations is added to field originUrl not to fields user and password
* app/console mapbender:generate:element fixed errors
* bug visiblelayers fixed
* WMS with authentication saves in table mb_wms_wmssource username and password
* no metadata for applications coming from mapbender.yml definition (no entry in context menu)
* copy an application via button on application fixed
* print template resize northarrow, overview added
* improved screenshot for application handling
* https://github.com/mapbender/mapbender/milestones/3.0.4.1
 

Milestone 3.0.4.0
-----------------

Release Datum: 12-09-2014
Übersicht der Änderungen finden Sie unter:  https://github.com/mapbender/mapbender-starter/blob/develop/CHANGELOG.md

* Wechsel zur MIT Lizenz
* Symfony Update 2.3 LTS
* OpenLayers 2.13 mit zusätzlichen Patches
* Dienste Aktivieren über Button oder Menü (BaseSourceSwitcher)
* HTML-Element
* CSS-Editor für Anwendungen
* Reiterstruktur in der Seitenleiste
* Laden von Vorschaubildern für Anwendungen
* Import/Export von Anwendungen und Diensten
* spanische Übersetzung
 

Milestone 3.0.3
----------------

Release Datum: 17-03-2014
Übersicht der Tickets finden Sie unter: https://github.com/mapbender/mapbender/issues?milestone=8

* Erweiterungen Such-Router für SQL-Suchen (Selectboxen, Distinct)
* WMC Editor und Loader
* WMSLoader Erweiterung WMS über Link hinzufügen
* i18n - Internationalisation (english / german)
* Sketch zum Zeichnen von Skizzen
* POI - Treffpunktfunktion
* Bildexport zur Ausgabe von png und jpg
* WMS Anzeige über Button wechseln
* Druckausgabe mit Übersichtskarte, Replace-Pattern, optionalen Feldern
* Zusammenstellung von mehreren Elementen in der Seitenleiste (Wechsel über Button)
* Layerbaum mit Kontextmenü zur Transparenzeinstellung und zum Zoom auf das Thema
* Übergabe von Parametern beim Öffnen der Anwendung (Position)
* ACL für Elemente
* Funktion zur Validierung von WMS GetCapabilities Dokumenten
 

Milestone 3.0.2
---------------

Release Datum: 27-11-2013
Übersicht der Tickets finden Sie unter: https://github.com/mapbender/mapbender/issues?milestone=6

* Such-Router für SQL-Suchen
* WMC Editor und Loader
* WMSLoader Erweiterung WMS über Link hinzufügen
 

Milestone 3.0.1
---------------

Release Datum: 06-09-2013

Übersicht der Tickets finden Sie unter: https://github.com/mapbender/mapbender/issues?milestone=5

* Kopieren einer Anwendung mit Diensten
* Popup - draggable
* PrintClient Erweiterung Druck EPSG 4326, neue Drucklayouts, Druck A4-A0
* Abfangen von fehlerhaften Anmeldungen zum Abwenden von brute force login Versuchen
* Bug fixes
 

Milestone 3.0.0.2
-----------------

Bugfix-Release Datum: 19-07-2013

Übersicht der Tickets finden Sie unter: https://github.com/mapbender/mapbender/issues?milestone=4

 

Milestone 3.0.0.1
-----------------

Bugfix-Release Datum: 07-06-2013

Übersicht der Tickets finden Sie unter: https://github.com/mapbender/mapbender/issues?milestone=3

 

Milestone 3.0.0.0
-----------------

Release Datum: 29-05-2013

Übersicht der Tickets finden Sie unter: https://github.com/mapbender/mapbender/issues?milestone=1

* Administrations Backend für Services, Applikationen, Benutzer/Gruppen und Zugriffsverwaltung
* Backend-/Frontend Design  
* Zugriffsverwaltung
* Benutzer-/Gruppen-Administration
* WMS Administration
* Kartenelement
* Layerbaum
* Legende
* Übersichtskarte
* Navigations-Werkzeugkasten
* Infoabfrage
* Koordinatenanzeige
* Copyright
* Linien/Flächen-Messung
* Maßstabsauswahl
* Maßstabsleiste
* Spatial Reference System-Auswahl
* GPS-Position
* Druck
* WMS zur Anwendung hinzufügen
* Dokumentation unter http://doc.mapbender3.org