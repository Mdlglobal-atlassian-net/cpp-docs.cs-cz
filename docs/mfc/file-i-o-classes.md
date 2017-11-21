---
title: "Třídy I-O souborů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.file
dev_langs: C++
helpviewer_keywords:
- disk file classes [MFC]
- stdio classes [MFC]
- OLE streams [MFC]
- I/O [MFC], MFC classes
- translated stream classes [MFC]
- file I/O classes [MFC]
- I/O [MFC], classes
- sockets classes [MFC]
- stream classes [MFC]
- memory file classes [MFC]
ms.assetid: 92821c3f-d9e1-47f6-98c9-3b632d86e811
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4d5321c2e4167c38123f57ff8e416e50bc8ac5a4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="file-io-classes"></a>Třídy I/O souborů
Tyto třídy poskytuje rozhraní pro tradiční disku soubory, soubory v paměti, aktivní datové proudy a rozhraní Windows sockets. Všechny třídy odvozené od `CFile` lze použít s `CArchive` objekt pro provedení serializace.  
  
 Použijte následující třídy, zejména `CArchive` a `CFile`v případě, že můžete psát vlastní zpracování vstupu a výstupu. Normálně není potřeba odvozena z těchto tříd. Pokud používáte rozhraní, výchozí implementace **otevřete** a **Uložit** příkazy **souboru** nabídky zpracuje vstupně-výstupní soubor (pomocí třídy `CArchive`), tak dlouho, dokud přepsat váš dokument `Serialize` funkce zadat podrobnosti o tom, jak dokument serializuje obsah. Další informace o souboru třídy a serializaci, najdete v článku [soubory v prostředí MFC](../mfc/files-in-mfc.md) a v článku [serializace](../mfc/serialization-in-mfc.md).  
  
 [Cfile –](../mfc/reference/cfile-class.md)  
 Poskytuje rozhraní, které je soubor na disku binární soubory.  
  
 [CStdioFile](../mfc/reference/cstdiofile-class.md)  
 Poskytuje `CFile` rozhraní k souborům disku datového proudu ve vyrovnávací paměti, obvykle v textovém režimu.  
  
 [CMemFile](../mfc/reference/cmemfile-class.md)  
 Poskytuje `CFile` rozhraní k souborům v paměti.  
  
 [CSharedFile](../mfc/reference/csharedfile-class.md)  
 Poskytuje `CFile` rozhraní sdílených souborů v paměti.  
  
 [COleStreamFile](../mfc/reference/colestreamfile-class.md)  
 Používá modelu COM `IStream` rozhraní zajistit `CFile` přístup k složené soubory.  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md)  
 Poskytuje `CFile` rozhraní Windows soketu.  
  
## <a name="related-classes"></a>Související třídy  
 [CArchive](../mfc/reference/carchive-class.md)  
 Spolupracuje s `CFile` objektu k implementaci trvalého úložiště pro objekty prostřednictvím serializace (viz [CObject::Serialize](../mfc/reference/cobject-class.md#serialize)).  
  
 [CArchiveException](../mfc/reference/carchiveexception-class.md)  
 Výjimku archivu.  
  
 [CFileException](../mfc/reference/cfileexception-class.md)  
 Výjimka zaměřené na konkrétní soubor.  
  
 [CFileDialog](../mfc/reference/cfiledialog-class.md)  
 Poskytuje standardní dialogové okno pro otevření nebo uložení souboru.  
  
 [CRecentFileList](../mfc/reference/crecentfilelist-class.md)  
 Udržuje naposledy použité seznamu souborů (naposledy použitých).  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)

