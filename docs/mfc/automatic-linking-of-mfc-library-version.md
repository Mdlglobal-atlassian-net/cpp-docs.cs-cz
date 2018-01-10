---
title: "Automatické propojení knihovní verze rozhraní MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: defaultlib
dev_langs: C++
helpviewer_keywords:
- defaultlib in MFC
- automatic links [MFC]
- MFC libraries, linking to
- linking [MFC], automatic of MFC library version
- linking [MFC]
- linking [MFC], of MFC
- MFC libraries, versions
ms.assetid: 02af4a20-2034-4fce-b200-c2202c3c8311
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ddc156d8518318a686796a25e89ee84a9a67ee59
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="automatic-linking-of-mfc-library-version"></a>Automatické propojení knihovní verze rozhraní MFC
Ve verzích MFC před verze 3.0 (před Visual C++ verze 2.0) jste museli zadávat ručně správná verze knihovny MFC ve vstupním seznamu knihoven linkeru. MFC verze 3.0 a novějších již není potřeba ručně zadejte verzi knihovny MFC. Místo toho soubory hlaviček MFC automaticky určit správnou verzi knihovny MFC založené na hodnotách, které jsou definované s `#define`, jako například **_DEBUG –** nebo **_UNICODE**. Přidat soubory hlaviček MFC **/defaultlib** direktivy propojovací program pro odkaz na konkrétní verzi knihovny MFC.  
  
 Například následující fragment kódu z afx –. Soubor hlaviček H dá pokyn linkeru propojení v buď NAFXCWD. LIB nebo NAFXCW. LIB verze knihovny MFC, v závislosti na tom, jestli používáte ladicí verze knihovny MFC:  
  
```c++
#ifndef _UNICODE 
#ifdef _DEBUG
#pragma comment(lib, "nafxcwd.lib")
#else
#pragma comment(lib, "nafxcw.lib")
#endif
#else
#ifdef _DEBUG
#pragma comment(lib, "uafxcwd.lib")
#else
#pragma comment(lib, "uafxcw.lib")
#endif
#endif
```  
  
 Soubory hlaviček MFC také odkaz v všechny požadované knihoven, včetně knihovny MFC, knihovny Win32, knihoven OLE, knihoven OLE sestaven z ukázky, rozhraní ODBC knihovny a tak dále. Knihovny Win32 zahrnují Kernel32.Lib, User32.Lib a GDI32.Lib.  
  
## <a name="see-also"></a>Viz také  
 [MFC – knihovní verze](../mfc/mfc-library-versions.md)

