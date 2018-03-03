---
title: "Chyba linkerů Lnk1301 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1301
dev_langs:
- C++
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cfcdb90b967ce5f0e9eda8dded9b93db5bdcc268
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1301"></a>Chyba linkerů LNK1301
Nalezeny, kompatibilní s /LTCG:parameter moduly LTCG clr  
  
 Modul kompilovat s/CLR a /GL byl předán linkeru společně s jedním z optimalizace na základě profilu (PGO) parametry/ltgc.  
  
 Optimalizace na základě profilu nejsou podporovány pro moduly/CLR.  
  
 Další informace naleznete v tématu:  
  
-   [/GL (celková optimalizace programu)](../../build/reference/gl-whole-program-optimization.md)  
  
-   [/ LTCG (vytváření kódu v době propojování)](../../build/reference/ltcg-link-time-code-generation.md)  
  
-   [/ CLR (kompilace common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md)  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Nejde kompilovat s volbou/CLR nebo nepropojovat s jedním z PGO parametry/ltgc.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje LNK1301:  
  
```  
// LNK1301.cpp  
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj  
// LNK1301 expected  
class MyClass {  
public:  
   int i;  
};  
```