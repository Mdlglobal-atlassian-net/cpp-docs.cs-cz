---
title: Serializace dat při vstupu i výstupu ze souborů
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], serialization
- documents [MFC], saving
- saving documents
- deserialization [MFC]
- serialization [MFC], role of document
- serialization [MFC], role of data
- data [MFC]
- data [MFC], serializing
- document data [MFC]
ms.assetid: b42a0c68-4bc4-4012-9938-5433a26d2c24
ms.openlocfilehash: 87e216f1959a7c169673822ffa7041ed511817d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473616"
---
# <a name="serializing-data-to-and-from-files"></a>Serializace dat při vstupu i výstupu ze souborů

Základní myšlenka trvalosti je, že objekt by měl být schopni napsat jejím aktuálním stavu indikován hodnoty jeho členů proměnných do trvalého úložiště. Později objekt lze znovu vytvořit čtením nebo "deserializaci" stav objektu z trvalého úložiště. Zásadním aspektem je, že objekt samotný zodpovídá za čtení a zápis svůj stav. Proto pro, aby byla trvalá třída musí implementovat operace základní serializace.

Poskytuje výchozí implementaci pro ukládání dokumentů do souborů disku v reakci na uložení rozhraní framework a uložit jako příkazy v nabídce Soubor a pro načítání dokumentů ze souborů na disku v reakci na příkaz Otevřít. S příliš mnoho zásahů můžete implementovat dokumentu možnost zapisovat a číst data do a ze souboru. Přepsání je hlavní věc, kterou musíte udělat [serializace](../mfc/reference/cobject-class.md#serialize) členské funkce ve třídě dokumentů.

Průvodce aplikací MFC umístí základní přepsání `CDocument` členskou funkci `Serialize` ve třídě dokumentů ho vytvoří za vás. Po dokončení implementace proměnné člena vaší aplikace můžete vyplnit vaše `Serialize` přepsat s kódem, který odesílá data do "archivu objektu" připojení k souboru. A [CArchive](../mfc/reference/carchive-class.md) objektu je podobný **cin** a **cout** vstupních/výstupních objektů z iostream – knihovna jazyka C++. Ale `CArchive` zápisy a čtení binární formát, ne formátovaný text.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Serializace](../mfc/serialization-in-mfc.md)

- [Role dokumentu v serializaci](#_core_the_document.92.s_role_in_serialization)

- [Role dat v serializaci](#_core_the_data.92.s_role_in_serialization)

- [Obcházení mechanismu serializace](../mfc/bypassing-the-serialization-mechanism.md)

##  <a name="_core_the_document.92.s_role_in_serialization"></a> Role dokumentu v serializaci

Rozhraní automaticky reaguje na nabídku soubor otevřít, uložte a uložte jako příkazy voláním dokumentu `Serialize` členskou funkci, pokud je implementovaná. Id_file_open – příkaz, například volání funkce obslužné rutiny v objektu aplikace. Během tohoto procesu uživatel uvidí a reaguje na dialogovém okně Otevřít soubor a rozhraní získá název souboru, který uživatel vybere. Vytvoří rozhraní `CArchive` nastavil objekt pro načítání dat do dokumentu a předává archivní úrovně do `Serialize`. Rozhraní je už otevřený soubor. Kód v dokumentu, a `Serialize` členská funkce čte data prostřednictvím archivu rekonstrukce datové objekty podle potřeby. Další informace o serializaci naleznete v článku [serializace](../mfc/serialization-in-mfc.md).

##  <a name="_core_the_data.92.s_role_in_serialization"></a> Role dat v serializaci

Obecně platí data typu třídy by možné serializovat sama sebe. To znamená při předání objektu do archivu objektu by měla vědět, jak zapsat samotné do archivu a samotné čtení z archivu. Knihovna MFC poskytuje podporu pro vytváření tříd serializovatelný tímto způsobem. Pokud při návrhu tříd k definování datový typ a máte v úmyslu serializovat tento typ dat, návrh pro serializaci.

## <a name="see-also"></a>Viz také

[Použití dokumentů](../mfc/using-documents.md)

