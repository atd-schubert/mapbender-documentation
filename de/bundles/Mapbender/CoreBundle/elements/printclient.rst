﻿PrintClient (Druck)
***********************

Mit dem Druck kann ein definierter Bereich der Karte ausgedruckt werden. Gewählt werden können Eigenschaften, die für den Ausdruck benötigt wird, wie eine Vorlage, das Format und der Maßstab.
Der Ausdruck kann auch gedreht werden.

Bitte beachten Sie, dass sich der Druck noch im Aufbau befindet.


.. image:: ../../../../../figures/print_client.png
     :scale: 80

Konfiguration
=============

.. image:: ../../../../../figures/print_client_configuration.png
     :scale: 80

Für das Element wird ein Button verwendet. Siehe unter :doc:`button` für die Konfiguration.


YAML-Definition:

.. code-block:: yaml

    target: map                            	# ID des Kartenelements
    autoOpen: false				# true, wenn das Druckfenster beim Start der Anwendung geöffnet werden soll, der Standardwert ist false.
    templates:
        - { template: a4portrait, label: A4 Portrait, format: a4}	# Vorlagen (template): Vorlagename, Vorlagedateiname ohne Dateierweiterung (Mapbender sucht die Datei a4portrait.odg und a4portrait.pdf), die Vorlagedateien befinden sich in app/Resources/MapbenderPrintBundle
        - { template: a4landscape, label: A4 Landscape, format: a4} 	# Vorlagebeschriftung im Druckdialog, Format (A4,A3,...) wird definiert
    scales: [5000, 10000, 25000]        		# Maßstäbe definieren, die in der Selectbox ausgewählt werden können. Wenn keine Maßstäbe angegeben werden, kann ein beliebiger Maßstab in einem Textfeld definiert werden.
    quality_levels:					# die Qualität in dpi definieren und die dazugehörige Beschriftung angegeben
        - { dpi: 72 , label: Draft (72dpi)}		# die erste Angabe ist der dpi Wert, die zweite Angabe ist die Beschriftung
        - { dpi: 288,  label: Document (288dpi)}	# es können weitere dpi-Werte angegeben werden
    rotatable: true                             	# true/false ob der Ausdruck gedreht werden kann, der Standardwert ist true
    legend: true                        # true/false, der Standardwert ist false
    file_prefix: mapbender3             # Definition des Dateinames für das PDF (wird zusammengesetzt zu file_prefix_date.pdf)
    optional_fields:                            # es können optional weitere Felder definiert werden (z.B. Titel-Feld)
        title:                                  # Name des optionalen Feldes, der Standardwert ist null (keine optionalen Felder sind definiert)
            label: Titel                        # Beschriftung des optionalen Feldes
            type: text                          # Typ des optionalen Feldes
            options:                            
                required: true                  # erforderlich: true or false
        comment1:
            label: Kommentar 1
            options: { required: false }
        comment2:
            label: Kommentar 2
            options: { required: false }
        bearbeiter:
            label: Bearbeiter
            options: { required: true }
    replace_pattern:                            # Für den Druck kann der Kartenaufruf verändert werden. 
            -                                   # Es können zusätzliche Parameter hinzugefügt werden (wie map_resolution für MapServer)
                default: { 288: '&map_resolution=288' }
            -
                pattern: 'stadtplan.xml'        # oder es können für den Druck optimierte Dienste angefordert werden.
                replacement: { 288: 'stadtplan_4.xml' }

Class, Widget & Style
======================

* Class: Mapbender\\CoreBundle\\Element\\PrintClient
* Widget: mapbender.element.printClient.js


File location
===============
**northarrow**
Das Bild des Nordpfeils ("North arrow") befindet sich unter images/. Sie können das Bild des Nordpfeils auch durch ein anderes Bild ersetzen.

**print templates**
Die Vorlagen befinden sich unter app/Resources/MapbenderPrintBundle/templates/. Sie können eigene Druckvorlagen erstellen.


Erstellen eines individuellen Vorlage
=======================================
Um eine individuelle Druckvorlage zu erstellen, kopieren Sie eine vorhandene Druckvorlage (ODG-Datei) und bearbeiten diese. Sie können auch eine neue Libre Office Draw-Datei erzeugen. Die Vorlage kann feste Objekte wie ein Logo, ein Copyright oder Druckinformationen beinhalten. Zusätzlich muss eine Ebene für die dynamischen Elemente wie die Karte, die Übersichtskarte, der Nordpfeil, der Maßstab, das Datum und optionale Felder erstellt werden. Die dynamische Ebene ist eine zusätzliche nicht druckbare Ebene in der Libre Office Draw-Datei. Fügen Sie die Ebene in Libre Office Draw folgendermaßen hinzu: **Menü: Einfügen -> Ebene... -> definieren Sie einen Namen für die Ebene und wählen Sie die Option nicht druckbar**.

.. image:: ../../../../../figures/print_template_odg.png
     :scale: 80

Definieren Sie Bereiche für die Karte, den Nordpfeil, den Maßstab, das Datum und mehr sowie für optionale Felder. 

Die folgenden Bereiche liegen standardmäßig vor:

* map (Karte)
* overview (Übersichtskarte)
* scale (Maßstabsangabe in der Form 1:1000)
* scalebar (Maßstabsleiste)
* date (Datum in der Form 10.10.2014)
* northarrow (Nordpfeil)

Sie könne optionale Felder über die Element-Konfiguration definieren (wie Titel, Kommentar, Bearbeiter). Diese müssen Sie dann auch in die Open Office Draw Datei einfügen. Die dynamisch erstellten Text müssen in der ODG-Datei auf dem nicht druckbaren Bereich abgelegt werden, so dass Sie nicht im Vorlage-PDF ausgegeben werden.

Exportieren Sie die Vorlage als PDF unter dem gleichen Namen wie die ODG-Datei. Verwenden Sie den Namen ohne Dateierweiterung in der Druck yml-Definition.

Das Druck-Skript liest die Informationen (Position, Größe, Schriftgröße, Ausrichtung) aus der ODG-Datei aus und verwendet ebenfalls das PDF-Dokument mit den festen Objekten. Aus beiden und den aktuellen Karten wird dann eine PDF-Druckdatei erstellt.

