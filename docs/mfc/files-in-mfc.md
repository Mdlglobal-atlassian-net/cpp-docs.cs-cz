---
title: Soubory v prostředí MFC
ms.date: 11/04/2016
helpviewer_keywords:
- serialization [MFC], MFC files
- I/O [MFC], MFC classes
- files [MFC], MFC
- files [MFC], serialization
- binary access, binary file operations in MFC
- file I/O classes [MFC]
- I/O [MFC]
- persistence [MFC]
- MFC, file operations
- files [MFC], manipulating
- binary access [MFC]
ms.assetid: ae25e2c5-2859-4679-ab97-438824e93ce1
ms.openlocfilehash: 3a99c4143bbd27ba765b0289b80be8870a940f63
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365316"
---
# <a name="files-in-mfc"></a>Soubory v prostředí MFC

V knihovně třídy Microsoft Foundation (MFC) [zpracovává soubor CFile](../mfc/reference/cfile-class.md) třídy normální operace vstupně-videa souboru. Tato rodina článků vysvětluje, jak otevřít a zavřít soubory, stejně jako číst a zapisovat data do těchto souborů. Popisuje také operace stavu souboru. Popis použití funkcí serializace založené na objektech knihovny MFC jako alternativního způsobu čtení a zápisu dat do souborů naleznete v článku [Serializace](../mfc/serialization-in-mfc.md).

> [!NOTE]
> Při použití objektů `CDocument` knihovny MFC, rozhraní provádí hodně serializace práce za vás. Zejména rozhraní vytvoří a používá `CFile` objekt. Stačí napsat kód v přepsání `Serialize` členské funkce `CDocument`třídy .

Třída `CFile` poskytuje rozhraní pro obecné účely binární operace souborů. A `CStdioFile` `CMemFile` třídy odvozené `CFile` `CSharedFile` z a `CMemFile` třídy odvozené z poskytování více specializovaných souborových služeb.

Další informace o alternativách zpracování souborů knihovny MFC naleznete v [tématu Zpracování souborů](../c-runtime-library/file-handling.md) v *odkazu knihovny run-time*.

Informace o odvozených `CFile` třídách naleznete v [diagramu hierarchie knihovny MFC](../mfc/hierarchy-chart.md).

## <a name="what-do-you-want-to-do"></a>Co chcete dělat

*Použít soubor CFile*

- [Otevření souboru s CFile](../mfc/opening-files.md)

- [Čtení a zápis souboru pomocí souboru CFile](../mfc/reading-and-writing-files.md)

- [Zavření souboru pomocí souboru CFile](../mfc/closing-files.md)

- [Stav souboru aplikace Access pomocí souboru CFile](../mfc/accessing-file-status.md)

*Použití serializace knihovny MFC (trvalost objektu)*

- [Vytvoření serializovatelné třídy](../mfc/serialization-making-a-serializable-class.md)

- [Serializace objektu pomocí objektu CArchive](../mfc/serialization-serializing-an-object.md)

- [Vytvoření objektu CArchive](../mfc/two-ways-to-create-a-carchive-object.md)

- [Použití operátorů \< <a >> CArchive](../mfc/using-the-carchive-output-and-input-operators.md)

- [Ukládání a načítání objektů CObjects a objektů odvozených z objektů CObject prostřednictvím archivu](../mfc/storing-and-loading-cobjects-via-an-archive.md)

## <a name="see-also"></a>Viz také

[Koncepty](../mfc/mfc-concepts.md)<br/>
[Obecná témata MFC](../mfc/general-mfc-topics.md)<br/>
[Třída CArchiv](../mfc/reference/carchive-class.md)<br/>
[CObject – třída](../mfc/reference/cobject-class.md)
