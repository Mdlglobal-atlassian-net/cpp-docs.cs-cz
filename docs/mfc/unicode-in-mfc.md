---
title: "Kódování Unicode v prostředí MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- wide characters, Unicode
- Unicode [MFC], MFC
- wide characters, encoding
- strings [MFC], Unicode
- Unicode [MFC], enabling
ms.assetid: 1002004b-4113-4380-bf63-e1570934b793
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2c1a104ffc30a7463d640f63d26f7a80faad333b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="unicode-in-mfc"></a>Unicode v prostředí MFC
MFC podporuje kódování Unicode standard pro kódování široké znaky na platformách systému Windows NT, Windows 2000 a Windows XP. Aplikace kódování Unicode nelze spustit na platformách Windows 98.  
  
 Unicode verze knihovny MFC jsou následující:  
  
### <a name="static-link-libraries"></a>Statické knihovny  
  
|Vydaná verze|Ladit|Popis|  
|-------------|-----------|-----------------|  
|UAFXCW.lib, PDB|UAFXCWD.lib, PDB|Staticky propojené knihovny MFC kódování Unicode|  
  
### <a name="dynamic-link-libraries"></a>Knihovny DLL  
  
|Vydaná verze|Ladit|Popis|  
|-------------|-----------|-----------------|  
|MFC100U.lib, dbg, def, .dll, .map, PDB, soubor PRF|MFC100UD.lib, .def, .dll, .map, PDB|Importovat knihovny Unicode MFC (viz poznámky níže vysvětlení přípony souboru)|  
|MFCS100U.lib, PDB|MFCS100UD.lib, PDB|Knihovna, která obsahuje kód, který musí být v aplikaci nebo knihovny DLL staticky propojené importovat Unicode MFC|  
  
 **Typy souborů**  
  
-   Soubory knihoven importovat mít příponu (LIB).  
  
-   Soubory knihoven DLL mít příponu (DLL.dll).  
  
-   Soubory modulu definice (.def) jsou textové soubory, které obsahují příkazy pro definování s příponou .exe nebo .dll.  
  
-   Soubory mapy (.map) jsou textové soubory, které obsahují informace, které linkeru používá při propojování program.  
  
-   Soubory knihovny (LIB) se používají ve spojení s knihovny DLL verze knihovny MFC. Tyto soubory obsahují kód, který musí být v aplikaci nebo knihovny DLL staticky propojené.  
  
-   Soubory databáze (.pdb) program obsahovat informace o stavu ladění a projektu.  
  
-   Soubory ladění (DBG) obsahují informace (COFF FPO a CodeView), který používá ladicí program Visual C++.  
  
 Podrobné informace o vytváření názvů najdete v tématu [zásady vytváření názvů knihoven](../mfc/library-naming-conventions.md).  
  
 Informace o používání Unicode s MFC najdete v tématu [řetězce: Podpora vícebajtových znakovou sadu (MBCS) kódování Unicode a](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../mfc/mfc-concepts.md)   
 [Obecná témata MFC](../mfc/general-mfc-topics.md)

