---
title: "Chyba linkerů Lnk1237 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1237
dev_langs:
- C++
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ee9ec0e197d51f76ff57ef06f5584c55df0a4746
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1237"></a>Chyba linkerů LNK1237
během generování kódu kompilátoru zavedená odkaz na symbol definované v modulu 'module' kompilovat s /GL symbol  
  
 Během generování kódu, by neměl kompilátor zavést znaky, které jsou později přeložit na definice zkompilovat **/GL**. `symbol`je třeba otazník, která byla zavedená a později byl přeložen na definici kompilovat s **/GL**.  
  
 Další informace najdete v tématu [/GL (optimalizace celého programu)](../../build/reference/gl-whole-program-optimization.md).  
  
 LNK1237 vyřešíte nejde kompilovat symbol s **/GL** nebo použijte [/INCLUDE (vynutit odkazy na symboly)](../../build/reference/include-force-symbol-references.md) vynutit odkaz na symbol.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje LNK1237. Pokud chcete tuto chybu vyřešit, nezadávejte inicializovat pole v LNK1237_a.cpp a přidat **/ include: funkce __chkstk** k příkazu odkaz.  
  
```  
// LNK1237_a.cpp  
int main() {  
   char c[5000] = {0};  
}  
```  
  
```  
// LNK1237_b.cpp  
// compile with: /GS- /GL /c LNK1237_a.cpp  
// processor: x86  
// post-build command: (lib LNK1237_b.obj /LTCG & link LNK1237_a.obj LNK1237_b.lib /nodefaultlib /entry:main /LTCG)  
extern "C" void _chkstk(size_t s) {}  
```