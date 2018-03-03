---
title: "-Fi (předběžné zpracování názvu výstupního souboru) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /Fi
dev_langs:
- C++
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9bc3076a529984358aed16902f509ceb01423f9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fi-preprocess-output-file-name"></a>/Fi (předběžné zpracování názvu výstupního souboru)
Určuje název výstupního souboru, ke kterému [/P (předběžné zpracování souboru)](../../build/reference/p-preprocess-to-a-file.md) – možnost kompilátoru zapíše předběžně zpracované výstup.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Fipathname  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`pathname`|Název a cestu výstupního souboru vyprodukované **/P** – možnost kompilátoru.|  
  
## <a name="remarks"></a>Poznámky  
 Použití **/Fi** – možnost kompilátoru v kombinaci s **/P** – možnost kompilátoru.  
  
 Pokud zadáte pouze cestu pro `pathname` parametr, základní název zdrojového souboru se používá jako základní název předběžně zpracované výstupního souboru. `pathname` Parametr nevyžaduje konkrétní příponu názvu. Pokud nezadáte příponu názvu souboru se ale používá rozšíření ".i".  
  
## <a name="example"></a>Příklad  
 Následující příkazový řádek upraví PROGRAM.cpp, zachová komentáře, přidá [#line](../../preprocessor/hash-line-directive-c-cpp.md) direktivy a zapíše výsledek do souboru MYPROCESS.i.  
  
```  
CL /P /FiMYPROCESS.I PROGRAM.CPP  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [/P (předběžné zpracování souboru)](../../build/reference/p-preprocess-to-a-file.md)   
 [Určení názvu cesty](../../build/reference/specifying-the-pathname.md)