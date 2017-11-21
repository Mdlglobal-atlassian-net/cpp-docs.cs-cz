---
title: "Kompilátoru (úroveň 1) upozornění C4274 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4274
dev_langs: C++
helpviewer_keywords: C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0c6bb31350af030879f23d9c0a9ac105e7293480
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4274"></a>C4274 kompilátoru upozornění (úroveň 1)
\#Ident ignorován; naleznete v dokumentaci k #pragma komentář (exestr, 'řetězec')  
  
 `#ident` – Direktiva, která vloží řetězec definované uživatelem v objektu nebo spustitelný soubor, je zastaralý. V důsledku toho kompilátor ignoruje direktivu.  
  
> [!CAUTION]
>  C4274 upozornění informuje o tom, abyste použili [#pragma komentář (exestr, 'řetězec')](../../preprocessor/comment-c-cpp.md) – direktiva. Tuto žádost, ale je zastaralá a bude v budoucí verzi kompilátoru revidován. Pokud použijete `#pragma` direktivy, nástroj linkeru (LINK.exe) ignoruje záznam komentář vyprodukované direktiva a vydá upozornění [LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md). Místo `#ident` direktivy, doporučujeme použít řetězec prostředku verzi souboru v aplikaci.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Odeberte `#ident "` *řetězec* `"` – direktiva.  
  
## <a name="see-also"></a>Viz také  
 [komentáře (C/C++)](../../preprocessor/comment-c-cpp.md)   
 [Upozornění LNK4229 nástroje linkeru](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)   
 [Práce se zdrojovými soubory](../../windows/working-with-resource-files.md)