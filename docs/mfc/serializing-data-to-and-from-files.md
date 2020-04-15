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
ms.openlocfilehash: 043ba019c6b5ad79db2cedb6314c9e65f14b14b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376938"
---
# <a name="serializing-data-to-and-from-files"></a>Serializace dat při vstupu i výstupu ze souborů

Základní myšlenkou trvalosti je, že objekt by měl být schopen zapsat svůj aktuální stav, označený hodnotami jeho členských proměnných, do trvalého úložiště. Později objekt může být znovu vytvořen čtením nebo "reserializace", stav objektu z trvalého úložiště. Klíčovým bodem je, že samotný objekt je zodpovědný za čtení a psaní vlastního stavu. Proto pro třídu být trvalé, musí implementovat základní serializace operace.

Rozhraní Framework poskytuje výchozí implementaci pro ukládání dokumentů na diskové soubory v reakci na příkazy Uložit a Uložit jako v nabídce Soubor a pro načítání dokumentů ze souborů na disku v reakci na příkaz Otevřít. S velmi málo práce, můžete implementovat dokumentu schopnost psát a číst jeho data do a ze souboru. Hlavní věc, kterou musíte udělat, je přepsat [Serializovat](../mfc/reference/cobject-class.md#serialize) členské funkce ve třídě dokumentu.

Průvodce aplikací knihovny MFC umístí `CDocument` kosterní přepsání členské funkce `Serialize` do třídy dokumentu, kterou pro vás vytvoří. Po implementaci členských proměnných aplikace můžete přepsat `Serialize` kódem, který odesílá data do "objektu archivu" připojeného k souboru. [CArchive](../mfc/reference/carchive-class.md) Objekt je podobný **cin** a **cout** vstupní a výstupní objekty z knihovny C++ iostream. Však `CArchive` zapisuje a čte binární formát, není formátovaný text.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Serializace](../mfc/serialization-in-mfc.md)

- [Role dokumentu v serializaci](#_core_the_document.92.s_role_in_serialization)

- [Role dat v serializaci](#_core_the_data.92.s_role_in_serialization)

- [Vynechání mechanismu serializace](../mfc/bypassing-the-serialization-mechanism.md)

## <a name="the-documents-role-in-serialization"></a><a name="_core_the_document.92.s_role_in_serialization"></a>Role dokumentu v serializaci

Rozhraní framework automaticky reaguje na příkazy otevřít, uložit a uložit jako v `Serialize` nabídce Soubor voláním členské funkce dokumentu, pokud je implementována. Příkaz ID_FILE_OPEN například volá funkci obslužné rutiny v objektu aplikace. Během tohoto procesu uživatel uvidí a odpoví na dialogové okno Otevřít soubor a rozhraní získá název souboru, který uživatel zvolí. Rozhraní framework `CArchive` vytvoří objekt nastavený pro načítání dat do `Serialize`dokumentu a předá archiv . Rozhraní framework již otevřelsoubor. Kód v `Serialize` členské funkci dokumentu čte data v archivu a podle potřeby rekonstruuje datové objekty. Další informace o serializaci naleznete v článku [Serializace](../mfc/serialization-in-mfc.md).

## <a name="the-datas-role-in-serialization"></a><a name="_core_the_data.92.s_role_in_serialization"></a>Role dat v serializaci

Obecně by měla být data typu třídy schopna serializovat sama. To znamená, že když předáte objekt do archivu, objekt by měl vědět, jak se zapsat do archivu a jak číst sám z archivu. Knihovna MFC poskytuje podporu pro vytváření tříd serializovatelný tímto způsobem. Pokud navrhujete třídu pro definování datového typu a máte v úmyslu serializovat data tohoto typu, návrh pro serializaci.

## <a name="see-also"></a>Viz také

[Použití dokumentů](../mfc/using-documents.md)
