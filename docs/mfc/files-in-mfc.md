---
title: "Soubory v prostředí MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d2cd6344f11a9c32ade0fc3241225a8763c18b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="files-in-mfc"></a>Soubory v prostředí MFC
Třídy v Microsoft Foundation Class Library (MFC), [cfile –](../mfc/reference/cfile-class.md) zpracovává normální souborových vstupně-výstupních operací. Tato řada článků vysvětluje, jak otevřít a zavřete soubory a také pro čtení a zápisu dat do těchto souborů. Popisuje také operací se soubory stavu. Popis toho, jak používat funkce na základě objektů serializace MFC jako alternativní způsob čtení a zápis dat v souborech, najdete v článku [serializace](../mfc/serialization-in-mfc.md).  
  
> [!NOTE]
>  Při použití MFC **CDocument** objekty, systém provádí většinu práce serializace pro vás. Konkrétně rozhraní framework vytvoří a použije `CFile` objektu. Budete muset psát kód ve vaší přepsání `Serialize` funkce člena třídy **CDocument**.  
  
 `CFile` Třída poskytuje rozhraní pro operace se pro obecné účely binární soubory. `CStdioFile` a `CMemFile` třídy odvozené od `CFile` a `CSharedFile` třída odvozená z `CMemFile` zadat více specializované souborové služby.  
  
 Další informace o alternativních zpracování souboru MFC najdete v tématu [zpracování souborů](../c-runtime-library/file-handling.md) v *referenční dokumentace běhové knihovny*.  
  
 Informace o odvozené `CFile` třídách naleznete v tématu [graf hierarchie MFC](../mfc/hierarchy-chart.md).  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat  
 *Cfile – použití*  
  
-   [Otevřete soubor s cfile –](../mfc/opening-files.md)  
  
-   [Čtení a zápis do souboru s cfile –](../mfc/reading-and-writing-files.md)  
  
-   [Zavřete soubor s cfile –](../mfc/closing-files.md)  
  
-   [Stav přístupu k souboru s cfile –](../mfc/accessing-file-status.md)  
  
 *Použití knihovny MFC serializace (objekt trvalost)*  
  
-   [Vytvoření serializovatelné třídy](../mfc/serialization-making-a-serializable-class.md)  
  
-   [Serializovat objekt prostřednictvím objektu CArchive](../mfc/serialization-serializing-an-object.md)  
  
-   [Vytvoření objektu CArchive](../mfc/two-ways-to-create-a-carchive-object.md)  
  
-   [Použít CArchive <\< a >> operátory](../mfc/using-the-carchive-output-and-input-operators.md)  
  
-   [Ukládání a načítání objektů CObject a objekt odvozené třídy CObject prostřednictvím archivu](../mfc/storing-and-loading-cobjects-via-an-archive.md)  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../mfc/mfc-concepts.md)   
 [Obecná témata MFC](../mfc/general-mfc-topics.md)   
 [CArchive – třída](../mfc/reference/carchive-class.md)   
 [CObject – třída](../mfc/reference/cobject-class.md)
