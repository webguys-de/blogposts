Article-meta:

----

Title: Türchen 5: ImportExport-Schnittstelle unter Magento2

----

**Date: 2016-11-27

----

Description:

----

Tags: adventskalender

----

Author: Elias Kotlyar

----

Article-content:

----

Intro: In diesem Beitrag geht es um den aktuellen Stand der Import/Export-Schnittstelle bei Magento2. 

----

Das <strong>ImportExport</strong>-Modul unter Magento 2 ist im wesentlichen eine Weiterentwicklung des bekannten Import-Export Module von Magento1. Der Aufbau der CSV wurde allerdings grundlegend geändert, das Prinzip ist aber gleich geblieben. Das Modul ermöglicht den Import und Export von Produkt- und Kundendaten in/aus CSV-Dateien. 

## Magento Standard

Im Magento-Administrationsbereich findet sich die Importmöglichkeit unter System -> Import/Export -> Import.
Die Produktdaten müssen für den Import mit dem ImportExport-Modul in einer vorgegebenen Struktur vorliegen. 

## Magento "Community" Standard
  Durch den Erfolg des Magento1 Moduls AVS_SimpleImportExport hat sich natürlich die Community die Mühe gemacht, das Modul auf Magento2 zu portieren. Während dem Hackathon in [ Paderborn](  https://www.integer-net.de/magento-2-hackathon-paderborn-2016/) wurde eine erste Version des Importers entwickelt. Dabei wurde auch beschlossen, das Modul zukünftig in dem Firegento Namespace mitaufzunehmen. Beim nächsten [ Hackathon](  https://www.integer-net.com/magento-hackathon-leipzig-2016/)  auf der Meet-Magento wurde der Importer dann um einige Features erweitert. Im wesentlichen besteht er nun aus 4 Modulen:
  
 1.  [FireGento_FastSimpleImport2](https://github.com/firegento/FireGento_FastSimpleImport2)
 
	Das Basismodul. Stellt eine Schnittstelle bereit, um den Import mithilfe von PHP-Arrays zu betreiben.
  
2.  [FireGento_FastSimpleImport2Demo](  https://github.com/firegento/FireGento_FastSimpleImport2_Demo)

	Das Demo-Modul zeigt anhand zahlreicher Beispiele wie man Imports fahren kann.

3.  [FireGento_ExtendedImport2]( https://github.com/firegento/FireGento_ExtendedImport2)

	Das "Erweiterungsmodul" erweitert die bestehende Importlösung um weitere Funktionen. Derzeit ist beispielsweise die beliebte Anforderung implementiert: Durch die Erweiterung werden sämtliche Attributoptionen bei einem Import automatisch mitanlegt. Weitere Funktionen sind in Planung. 

4. [FastSimpleExport2]( https://github.com/magento-hackathon/FastSimpleExport2)

	Das Export-Modul bietet die Möglichkeit Daten aus Magento in ein PHP-Array zu überführen.

## Dokumentation

Die  Dokumentation der einzelnen Module befindet sich gesammelt auf [readthedocs](http://firegento-fastsimpleimport2.readthedocs.io/en/latest/Installation.html)

Auf eine Beschreibung der einzelnen Feldernamen verzichte ich bewusst, da diese bereits ausreichend durch die vielen Codebeispiele im Demo-Modul beschrieben sind. Am besten fängt man [hier](https://github.com/firegento/FireGento_FastSimpleImport2_Demo/tree/master/Console/Command) an um die wichtigsten Importfunktionen einzusehen.

Wer ausgefallenere Imports fahren möchte, dem empfehle ich die Lektüre der [Folien](http://de.slideshare.net/bennolippert/magento-2-product-import-export) vom Vortrag von Benno Lippert. Dieser enthält sämtliche Felder sowie eine Beschreibung was dort zu finden ist. 

## Ausblick

Durch die vielen bereits implementierten Funktionen, sind die grundlegenden Funktionen abgedeckt. Spannend bleibt es dagegen bei den zukünftigen Magento Versionen. Es könnte durchaus sein, das die eine oder andere Funktion bei den neueren Magento Versionen nicht mehr funktioniert. Desweiteren wurden während der Entwicklung einige Core-Bugs gefunden, welche an Magento gemeldet wurden. 





----

Article-options:

----

Cover:

----

Main: 0

----

Wpid: 2490
