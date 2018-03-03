---
title: noinline | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- noinline_cpp
dev_langs:
- C++
helpviewer_keywords:
- noinline __declspec keyword
- __declspec keyword [C++], noinline
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6d959235cbcad3e33140c2711633a55c1bba2096
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="noinline"></a>noinline
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 **__declspec(noinline)** instruuje kompilátor, aby nikdy vložené konkrétní členské funkce (funkce v třídě).  
  
 Nevkládání funkce může být výhodné, je-li malé a není-li důležité pro výkon kódu. To znamená, je-li funkce malá a nebude volána často, například funkce, která zpracovává chybovou podmínku.  
  
 Mějte na paměti, že pokud je funkce označena jako `noinline`, volání funkce bude menší, a samo tedy bude kandidátem pro vkládání kompilátoru.  
  
```  
class X {  
   __declspec(noinline) int mbrfunc() {  
      return 0;   
   }   // will not inline  
};  
```  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [vložené, __inline, \__forceinline](inline-functions-cpp.md)

