---
title: Použití dokumentů
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], C++ applications
- data [MFC], reading
- documents [MFC]
- files [MFC], writing to
- data [MFC], documents
- files [MFC]
- views [MFC], C++ applications
- document/view architecture [MFC], documents
- reading data [MFC], documents and views
- printing [MFC], documents
- writing to files [MFC]
ms.assetid: f390d6d8-d0e1-4497-9b6a-435f7ce0776c
ms.openlocfilehash: fb35d1731912b2e322bc61621f7900e0d98e1e72
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294678"
---
# <a name="using-documents"></a>Použití dokumentů

Pracují společně, dokumentů a zobrazení:

- Obsahují, spravovat a zobrazit vaše specifické pro aplikaci [data](../mfc/managing-data-with-document-data-variables.md).

- Zadejte sestávající z rozhraní [datových proměnných dokumentu](../mfc/managing-data-with-document-data-variables.md) pro manipulaci s daty.

- Účastnit [zápis a čtení souborů](../mfc/serializing-data-to-and-from-files.md).

- Účastnit [tisk](../mfc/role-of-the-view-in-printing.md).

- [Zpracování](../mfc/handling-commands-in-the-document.md) většinu příkazů a zpráv vaší aplikace.

Dokument je zejména při správě dat. Za normálních okolností Store vaše data v proměnné členů třídy dokumentu. Zobrazení používá tyto proměnné přístup k datům pro zobrazení a aktualizace. Dokumentu výchozí serializace mechanismus spravuje čtení a zápis dat do a ze souborů. Dokumenty může také zpracovávat příkazy (ale ne zpráv Windows jiné než wm_command –).

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Odvození dokumentové třídy z objektu CDocument](../mfc/deriving-a-document-class-from-cdocument.md)

- [Správa dat s použitím datových proměnných dokumentu](../mfc/managing-data-with-document-data-variables.md)

- [Serializace dat do a ze souborů](../mfc/serializing-data-to-and-from-files.md)

- [Obcházení mechanismu serializace](../mfc/bypassing-the-serialization-mechanism.md)

- [Zpracování příkazů v dokumentu](../mfc/handling-commands-in-the-document.md)

- [Členská funkce OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument)

- [Členská funkce DeleteContents](../mfc/reference/cdocument-class.md#deletecontents)

## <a name="see-also"></a>Viz také:

[Document/View – architektura](../mfc/document-view-architecture.md)
