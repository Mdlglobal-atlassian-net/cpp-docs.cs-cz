---
title: Chyba linkerů Lnk1301 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1301
dev_langs:
- C++
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b4e298ad3815c741ff6c901ac39bf7838ed135d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299702"
---
# <a name="linker-tools-error-lnk1301"></a>Chyba linkerů LNK1301
Nalezeny, kompatibilní s /LTCG:parameter moduly LTCG clr  
  
 Modul kompilovat s/CLR a /GL byl předán linkeru společně s jedním z optimalizace na základě profilu (PGO) parametry/ltgc.  
  
 Optimalizace na základě profilu nejsou podporovány pro moduly/CLR.  
  
 Další informace naleznete v tématu:  
  
-   [/GL (celková optimalizace programu)](../../build/reference/gl-whole-program-optimization.md)  
  
-   [/LTCG (generování kódu během propojování)](../../build/reference/ltcg-link-time-code-generation.md)  
  
-   [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
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