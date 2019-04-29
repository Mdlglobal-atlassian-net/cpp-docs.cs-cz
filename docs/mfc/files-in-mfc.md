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
ms.openlocfilehash: cf53c498e61bdf0a233d7638649b30e498e27cc5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392853"
---
# <a name="files-in-mfc"></a>Soubory v prostředí MFC

Třídy v třídy knihovny MFC (Microsoft Foundation), [cfile –](../mfc/reference/cfile-class.md) zpracovává normální souborových vstupně-výstupních operací. Tato řada článků vysvětluje, jak otevřít a zavřít soubory a číst a zapisovat data k těmto souborům. Také popisuje stav operace se soubory. Popis toho, jak používat funkce serializace založenou na objektech knihovny MFC jako alternativní způsob čtení a zápis dat v souborech, najdete v článku [serializace](../mfc/serialization-in-mfc.md).

> [!NOTE]
>  Při použití knihovny MFC `CDocument` objektů, rozhraní velkou část práce serializace udělá za vás. Zejména rozhraní vytváří a používá `CFile` objektu. Budete muset psát kód v přepsání metody `Serialize` členské funkce třídy `CDocument`.

`CFile` Třída poskytuje rozhraní pro operace s binárními soubory pro obecné účely. `CStdioFile` a `CMemFile` třídy odvozené z `CFile` a `CSharedFile` třída odvozená z `CMemFile` zadat více specializované souborové služby.

Další informace o alternativách do práce se soubory knihovny MFC naleznete v tématu [zpracování souborů](../c-runtime-library/file-handling.md) v *Run-Time Library Reference*.

Informace o odvozených `CFile` třídy, najdete v článku [graf hierarchie MFC](../mfc/hierarchy-chart.md).

## <a name="what-do-you-want-to-do"></a>Co chcete udělat

*Cfile – použití*

- [Otevřete soubor s cfile –](../mfc/opening-files.md)

- [Čtení a zápis do souboru s cfile –](../mfc/reading-and-writing-files.md)

- [Zavřete soubor s cfile –](../mfc/closing-files.md)

- [Stav přístupu k souboru s cfile –](../mfc/accessing-file-status.md)

*Použití knihovny MFC serializace (trvalost objektu)*

- [Vytvořit serializovatelné třídy](../mfc/serialization-making-a-serializable-class.md)

- [Serializace objektu prostřednictvím objektu CArchive](../mfc/serialization-serializing-an-object.md)

- [Vytvoření objektu CArchive](../mfc/two-ways-to-create-a-carchive-object.md)

- [Použít CArchive <\< a >> operátory](../mfc/using-the-carchive-output-and-input-operators.md)

- [Store a načítání objektů CObject a objekty odvozené třídy CObject prostřednictvím archivu](../mfc/storing-and-loading-cobjects-via-an-archive.md)

## <a name="see-also"></a>Viz také:

[Koncepty](../mfc/mfc-concepts.md)<br/>
[Obecná témata MFC](../mfc/general-mfc-topics.md)<br/>
[CArchive – třída](../mfc/reference/carchive-class.md)<br/>
[CObject – třída](../mfc/reference/cobject-class.md)
