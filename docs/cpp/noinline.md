---
title: noinline | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- noinline_cpp
dev_langs:
- C++
helpviewer_keywords:
- noinline __declspec keyword
- __declspec keyword [C++], noinline
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de433a1eccab3b58858aaf5fd3aa9ddb04d0cc1c
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406074"
---
# <a name="noinline"></a>noinline
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 **__declspec(noinline)** instruuje kompilátor, aby nikdy nevkládal členské funkce (funkce ve třídě).  
  
 Nevkládání funkce může být výhodné, je-li malé a není-li důležité pro výkon kódu. To znamená, je-li funkce malá a nebude volána často, například funkce, která zpracovává chybovou podmínku.  
  
 Mějte na paměti, která pokud je funkce označena **noinline**, volání funkce bude menší a proto samotné kandidátem pro vkládání kompilátoru.  
  
```cpp 
class X {  
   __declspec(noinline) int mbrfunc() {  
      return 0;   
   }   // will not inline  
};  
```  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [__declspec](../cpp/declspec.md)   
 [klíčová slova](../cpp/keywords-cpp.md)   
 [inline, __inline, \__forceinline](inline-functions-cpp.md)

