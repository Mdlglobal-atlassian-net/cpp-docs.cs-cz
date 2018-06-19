---
title: Chyba linkerů Lnk1237 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1237
dev_langs:
- C++
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ffc337d6b1548db4717dc4b87ff8aa25ef92e93
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298613"
---
# <a name="linker-tools-error-lnk1237"></a>Chyba linkerů LNK1237
během generování kódu kompilátoru zavedená odkaz na symbol definované v modulu 'module' kompilovat s /GL symbol  
  
 Během generování kódu, by neměl kompilátor zavést znaky, které jsou později přeložit na definice zkompilovat **/GL**. `symbol` je třeba otazník, která byla zavedená a později byl přeložen na definici kompilovat s **/GL**.  
  
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