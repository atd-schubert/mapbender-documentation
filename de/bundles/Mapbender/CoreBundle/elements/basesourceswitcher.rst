.. _basesourceswitcher:

BaseSourceSwitcher (Wechseln der Hintergrundkarten)
*********************************************************************

Mit diesem Element kann zwischen vordefinierten Hintergrundkarten gewechselt werden. 

.. image:: ../../../../../figures/basesourceswitcher.png
     :scale: 80

Konfiguration
=============

Die Konfiguration geschieht in zwei Schritten:

* Erzeugen eines Elements zum Wechseln der Hintergrundkarten mit Titel, Tooltip und Target
* Hinzufügen einer oder mehrerer Quellen


.. image:: ../../../../../figures/basesourceswitcher_configuration.png
     :scale: 80
     

YAML-Definition:

.. code-block:: yaml

    title:                                              # Titel
    tooltip:                                            # Text des Tooltips
    target: map                                         # ID des Kartenelements
    sourcesets:                                         # Liste der Sourcesets.
        - { title: sourcesetname, sources: [sourceId]}	# sourceset: title, sources list of sources
        

Class, Widget & Style
============================

* Class: Mapbender\\CoreBundle\\Element\\BaseSourceSwitcher
* Widget: mapbender.element.basesourceswitcher.js


HTTP Callbacks
==============

Keine.

JavaScript API
==============

Keine.

JavaScript Signals
==================

Keine.