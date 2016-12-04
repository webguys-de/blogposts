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

Intro: In diesem Beitrag geht es um den aktuellen Stand der Import/Export-Schnittstelle bei Magento 2. 

----

Das <strong>ImportExport</strong>-Modul unter Magento 2 ist im Wesentlichen eine Weiterentwicklung des bekannten Import/Export Moduls von Magento1. Der Aufbau der CSV wurde allerdings grundlegend geändert, das Prinzip ist aber gleich geblieben. Das Modul ermöglicht den Import sowie den Export von Produkt- und Kundendaten im CSV-Format.

## Magento Standard

Im Magento-Administrationsbereich findet sich die Importmöglichkeit unter System -> Import/Export -> Import. Dort enthält man einen Dialog , in welchem man eine CSV-Datei hochladen kann. Diese wird dann für den Import verwendet. Die Produktdaten müssen für den Import mit dem Import/Export-Modul in einer vorgegebenen Struktur vorliegen. Für erste Schritte empfiehlt es sich einige Produkte im Backend anzulegen, diese zu exportieren, die CSV zu ändern und danach wieder einen Import zu fahren. Glücklicherweise ist das Format zwischen Import/Export nahezu gleich, was bei Magento 1 leider nicht der Fall war.


## Magento "Community" Lösung

Wenn die Daten nicht per Hand importiert werden können, da die Daten beispielsweise in einem andren Format vorliegen, benötigt man eine programmtechnische Schnittstelle. Diese kann man natürlich selbst programmieren, indem man an die passenden Import/Export-Klassen andockt. Es empfiehlt sich allerdings ein Blick auf die aktuellen Community Projekte. Durch den Erfolg des Magento1 Moduls AVS_SimpleImportExport hat sich natürlich die Community die Mühe gemacht, das bekannte Modul auf Magento 2 zu portieren. Während dem Hackathon in [Paderborn](  https://www.integer-net.de/magento-2-hackathon-paderborn-2016/) wurde eine erste Version des Importers entwickelt. Dabei wurde auch beschlossen, das Modul zukünftig in dem Firegento Namespace mit aufzunehmen. Beim nächsten [ Hackathon](  https://www.integer-net.com/magento-hackathon-leipzig-2016/)  auf der Meet-Magento wurde der Importer dann um einige Features erweitert. Im wesentlichen besteht er nun aus 4 Modulen:
  
 1.  [FireGento_FastSimpleImport2](https://github.com/firegento/FireGento_FastSimpleImport2)
 
	Hierbei handelt es sich um das Basismodul. Es stellt eine Schnittstelle bereit, um den Import mithilfe von PHP-Arrays zu betreiben.
  
2.  [FireGento_FastSimpleImport2Demo](  https://github.com/firegento/FireGento_FastSimpleImport2_Demo)

	Das Demo-Modul zeigt anhand zahlreicher Beispiele wie man Imports fahren kann.

3.  [FireGento_ExtendedImport2]( https://github.com/firegento/FireGento_ExtendedImport2)

	Das "Erweiterungsmodul" erweitert die bestehende Importlösung um weitere Funktionen. Derzeit ist beispielsweise eine sehr beliebte Anforderung implementiert, durch die sämtliche Attributoptionen bei einem Import automatisch angelegt werden können. Weitere Funktionen sind in Planung. 

4. [FastSimpleExport2]( https://github.com/magento-hackathon/FastSimpleExport2)

	Das Export-Modul bietet die Möglichkeit Daten aus Magento in ein PHP-Array zu überführen.

## Dokumentation

Die  Dokumentation der einzelnen Module befindet sich gesammelt auf [readthedocs](http://firegento-fastsimpleimport2.readthedocs.io/en/latest/Installation.html).

Auf eine Beschreibung der einzelnen Feldernamen verzichte ich bewusst, da diese bereits ausreichend durch die vielen Codebeispiele im Demo-Modul beschrieben sind. Am besten fängt man [hier](https://github.com/firegento/FireGento_FastSimpleImport2_Demo/tree/master/Console/Command) an um die wichtigsten Importfunktionen einzusehen.

Wer ausgefallenere Imports fahren möchte, dem empfehle ich die Lektüre der Folien vom Vortrag von Benno Lippert. Dieser enthält sämtliche Felder sowie eine Beschreibung was dort zu finden ist. Diese befinden sich [hier](http://de.slideshare.net/bennolippert/magento-2-product-import-export).

## Ausblick

Durch die vielen bereits Erweiterungen, sind die grundlegenden Funktionen abgedeckt. Spannend bleibt es dagegen bei den zukünftigen Magento Versionen. Es könnte durchaus sein, das die eine oder andere Funktion bei den neueren Magento Versionen nicht mehr funktioniert. Des Weiteren wurden während der Entwicklung einige Core-Bugs gefunden, welche an Magento gemeldet wurden. Eine Übersicht der offenen Bugs findet sich [hier](https://github.com/magento/magento2/issues?utf8=%E2%9C%93&q=is%3Aissue%20is%3Aopen%20importexport). Es bleibt offen wann diese geschlossen werden.





----

Article-options:

----

Cover:

----

Main: 0

----

Wpid: 2490
