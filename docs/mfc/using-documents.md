---
title: "Použití dokumentů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b6e584804ce2d1828002b2fdb09bb4bc1a7ed773
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="using-documents"></a>Použití dokumentů
Spolupráci, dokumenty a zobrazení:  
  
-   Obsahovat, spravovat a zobrazit vaše konkrétní aplikace [data](../mfc/managing-data-with-document-data-variables.md).  
  
-   Poskytnutí rozhraní skládající se z [datových proměnných dokumentu](../mfc/managing-data-with-document-data-variables.md) pro manipulaci s daty.  
  
-   Účastnit [zápisu a čtení souborů](../mfc/serializing-data-to-and-from-files.md).  
  
-   Účastnit [tisk](../mfc/role-of-the-view-in-printing.md).  
  
-   [Zpracování](../mfc/handling-commands-in-the-document.md) většina příkazů a zpráv vaší aplikace.  
  
 Dokument je zvláště účastnící se správa dat. Ukládání dat, obvykle v dokumentu třída členské proměnné. Pro přístup k datům pro zobrazení a aktualizaci zobrazení používá tyto proměnné. Mechanismu serializace výchozí dokumentu spravuje čtení a zápis dat do a z soubory. Dokumenty může také zpracovat příkazy (ale ne Windows zprávy jiné než **wm_command –**).  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Odvození dokumentové třídy z objektu CDocument](../mfc/deriving-a-document-class-from-cdocument.md)  
  
-   [Správa dat s použitím datových proměnných dokumentu](../mfc/managing-data-with-document-data-variables.md)  
  
-   [Serializace dat do a ze souborů](../mfc/serializing-data-to-and-from-files.md)  
  
-   [Obcházení mechanismu serializace](../mfc/bypassing-the-serialization-mechanism.md)  
  
-   [Zpracování příkazů v dokumentu](../mfc/handling-commands-in-the-document.md)  
  
-   [OnNewDocument – členská funkce](../mfc/reference/cdocument-class.md#onnewdocument)  
  
-   [DeleteContents – členská funkce](../mfc/reference/cdocument-class.md#deletecontents)  
  
## <a name="see-also"></a>Viz také  
 [Document/View – architektura](../mfc/document-view-architecture.md)
