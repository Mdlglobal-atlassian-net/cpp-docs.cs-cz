---
title: Čtení ze souborů a zápis do nich
ms.date: 11/04/2016
helpviewer_keywords:
- CFile class [MFC], objects
- examples [MFC], reading files
- files [MFC], writing to
- examples [MFC], writing to files
- files [MFC], reading
- MFC, file operations
- CFile class [MFC], reading and writing CFile objects
- reading files
- writing to files [MFC]
ms.assetid: cac0c826-ba56-495f-99b3-ce6336f65763
ms.openlocfilehash: 6c4b2b21bbfa19fb73997f8475cfa9a4047dc0ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371801"
---
# <a name="reading-and-writing-files"></a>Čtení ze souborů a zápis do nich

Pokud jste použili funkce zpracování souborů knihovny C run-time, budou vám známé operace čtení a zápisu knihovny MFC. Tento článek popisuje čtení přímo z `CFile` a zápis přímo do objektu. Můžete také provést vstupně-tovem souboru ve vyrovnávací paměti s třídou [CArchive.](../mfc/reference/carchive-class.md)

#### <a name="to-read-from-and-write-to-the-file"></a>Čtení a zápis do souboru

1. Pomocí `Read` členských `Write` funkcí a ke čtení a zápisu dat do souboru.

     -nebo-

1. Členská `Seek` funkce je také k dispozici pro přesunutí na konkrétní posun v rámci souboru.

`Read`přebírá ukazatel na vyrovnávací paměť a počet bajtů ke čtení a vrátí skutečný počet bajtů, které byly přečteny. Pokud požadovaný počet bajtů nelze číst, protože je dosaženo konce souboru (EOF), je vrácen skutečný počet přečtených bajtů. Pokud dojde k chybě čtení, je vyvolána výjimka. `Write`je podobný `Read`, ale počet zapsaných bajtů není vrácena. Pokud dojde k chybě zápisu, včetně nezápisu všech zadaných bajtů, je vyvolána výjimka. Pokud máte platný `CFile` objekt, můžete z něj číst nebo do něj zapisovat, jak je znázorněno v následujícím příkladu:

[!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]

> [!NOTE]
> Za normálních okolností byste měli provádět operace vstupu a výstupu v rámci bloku zpracování výjimky **try**/**catch.** Další informace naleznete v [tématu Zpracování výjimek (MFC).](../mfc/exception-handling-in-mfc.md)

## <a name="see-also"></a>Viz také

[Soubory](../mfc/files-in-mfc.md)
