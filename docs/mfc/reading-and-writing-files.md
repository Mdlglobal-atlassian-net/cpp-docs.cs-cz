---
title: Čtení a zápis do souborů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d0fd41c085b9498d3f1ebb76378a83cce464142a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404069"
---
# <a name="reading-and-writing-files"></a>Čtení ze souborů a zápis do nich

Pokud jste použili funkcí zpracování souborů knihovny run-time jazyka C, se zobrazí známé MFC operace čtení a zápisu. Tento článek popisuje přímo z pro čtení a zápis přímo `CFile` objektu. Vám může také ukládány do vyrovnávací paměti vstup a výstup souborů se [CArchive](../mfc/reference/carchive-class.md) třídy.

#### <a name="to-read-from-and-write-to-the-file"></a>Číst z a zapisovat do souboru

1. Použití `Read` a `Write` členské funkce pro čtení a zápisu dat do souboru.

     -nebo-

1. `Seek` Členská funkce je také k dispozici pro přechod na konkrétním odsazení v souboru.

`Read` bere ukazatel do vyrovnávací paměti a počet bajtů ke čtení a vrátí skutečný počet bajtů, které byly přečteny. Pokud požadovaný počet bajtů nelze číst, protože endovém souborovém dosažení (EOF), se vrátí skutečný počet přečtených bajtů. Pokud dojde k jakékoli chybě čtení, je vyvolána výjimka. `Write` je podobný `Read`, ale počet zapsaných bajtů nevrátí. Pokud dojde k chybě zápisu, včetně nezapíše všechny bajty zadán, je vyvolána výjimka. Pokud máte platný `CFile` objektu, můžete z něj číst nebo do ní zapisovat, jak je znázorněno v následujícím příkladu:

[!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]

> [!NOTE]
>  By obvykle provádět vstupně výstupní operace v rámci **zkuste**/**catch** bloku zpracování výjimek. Další informace najdete v tématu [zpracování výjimek (MFC)](../mfc/exception-handling-in-mfc.md).

## <a name="see-also"></a>Viz také

[Soubory](../mfc/files-in-mfc.md)

