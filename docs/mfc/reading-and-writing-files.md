---
title: "Čtení a zápis souborů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6ea8f37c09c852acb0309ee7361589b6006a44d2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="reading-and-writing-files"></a>Čtení ze souborů a zápis do nich
Pokud jste použili funkcí zpracování souboru běhové knihovny jazyka C, se zobrazí známé MFC operace čtení a zápisu. Tento článek popisuje přímo z čtení a zápis přímo na `CFile` objektu. Vám může také do vyrovnávací paměti vstupně-výstupní soubor s [CArchive](../mfc/reference/carchive-class.md) třídy.  
  
#### <a name="to-read-from-and-write-to-the-file"></a>Číst a zapisovat do souboru  
  
1.  Použití **čtení** a **zápisu** členské funkce Číst a zapisovat data v souboru.  
  
     -nebo-  
  
2.  `Seek` – Členská funkce je také k dispozici pro přesun na konkrétní posun v souboru.  
  
 **Čtení** trvá ukazatel vyrovnávací paměť a počet bajtů ke čtení a vrátí skutečný počet bajtů, které byly čtení. Pokud požadovaný počet bajtů nelze načíst, protože koncové souboru (EOF) je dosaženo, je vrácen skutečný počet přečtených bajtů. Pokud dojde k chybě čtení, je vyvolána výjimka. **Zápis** je podobná **čtení**, ale počet zapsaných bajtů nevrátí. Pokud dojde k chybě zápisu, včetně není zápis všech bajtů zadána, je vyvolána výjimka. Pokud máte platný `CFile` objektu, můžou číst z něj nebo do něj zapisovat, jak je znázorněno v následujícím příkladu:  
  
 [!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]  
  
> [!NOTE]
>  By měl obvykle provádět vstupně výstupní operace v rámci **zkuste**/**catch** bloku zpracování výjimek. Další informace najdete v tématu [zpracování výjimek (MFC)](../mfc/exception-handling-in-mfc.md).  
  
## <a name="see-also"></a>Viz také  
 [Soubory](../mfc/files-in-mfc.md)

