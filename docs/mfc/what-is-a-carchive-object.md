---
title: Co je objekt CArchive | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CArchive
dev_langs: C++
helpviewer_keywords:
- archive objects [MFC]
- archives [MFC], for serialization
- buffers, serializable objects
- CArchive class [MFC], about CArchive class [MFC]
- buffering, serializable objects
ms.assetid: 843f1825-288d-4d89-a1fa-70e1f92d9b8b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cb9b0c3e24094deb0d4fd4ac20d673d9ffafca6d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="what-is-a-carchive-object"></a>Co je objekt CArchive
A `CArchive` objekt poskytuje mechanismus bezpečného typu vyrovnávací paměti pro zápisu nebo čtení serializovatelné objekty do nebo z `CFile` objektu. Obvykle `CFile` objekt představuje soubor na disku; však může být také soubor paměti (`CSharedFile` objektu), případně představující schránky.  
  
 A zadané `CArchive` objektu buď úložiště (zapíše, serializuje) data nebo zatížení (čtení, deserializuje) data, ale nikdy obojí. Dobu životnosti `CArchive` objektu je omezený na jednu předávání zápis objektů do souboru nebo čtení objektů ze souboru. Proto dvě postupně vytvořit `CArchive` objekty jsou potřeba k serializaci dat do souboru a jeho následné deserializaci zpět ze souboru.  
  
 Když archiv uloží objekty do souboru, archivu připojí `CRuntimeClass` názvem k objektům. Když jiné archivu načte objekty ze souboru do paměti, potom `CObject`-odvozené objekty jsou dynamicky znovu vytvořena na základě `CRuntimeClass` objektů. Daný objekt může odkazovat více než jednou zapsané do souboru pomocí ukládání archivu. Načítání archivu, ale bude rekonstrukci objekt pouze jednou. Podrobnosti o tom, jak se připojí archivu `CRuntimeClass` informace, které objekty a rekonstruuje objekty, s ohledem na účet možných více odkazů, jsou popsané v [technické poznámky 2](../mfc/tn002-persistent-object-data-format.md).  
  
 Jako data serializován do archivu, archivu shromažďuje data, dokud jeho vyrovnávací paměť je plná. Pak archivu zapíše jeho vyrovnávací paměti pro `CFile` objektu na kterou odkazuje `CArchive` objektu. Podobně se při čtení dat z archivu, přečte data ze souboru do vyrovnávací paměti a potom z vyrovnávací paměti pro deserializovaný objekt. Tato ukládání do vyrovnávací paměti snižuje počet časy, kdy na pevný disk je fyzicky pro čtení, tedy zvýšení výkonu vaší aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md)

