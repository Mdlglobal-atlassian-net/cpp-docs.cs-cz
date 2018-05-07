---
title: Chyba linkerů Lnk2028 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2028
dev_langs:
- C++
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7347e8edda7ad8b317d4e6e02dfc9345ac76f269
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk2028"></a>Chyba linkerů LNK2028
"exported_function" (decorated_name) odkazovat ve funkci "function_containing_function_call" (decorated_name)  
  
 Při pokusu o import nativní funkce do čistého bitové kopie, nezapomeňte, že implicitní konvence volání liší mezi nativní a čistý kompilace.  
  
## <a name="example"></a>Příklad  
 Tato ukázka kódu generuje součást s funkce exportované, nativní, jejichž konvence volání je implicitně [__cdecl](../../cpp/cdecl.md).  
  
```  
// LNK2028.cpp  
// compile with: /LD  
__declspec(dllexport) int func() {  
   return 3;  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří čistý klienta, který zpracovává nativní funkce. Ale konvence volání pod **/CLR: pure** je [__clrcall](../../cpp/clrcall.md). Následující ukázka generuje LNK2028.  
  
```  
// LNK2028_b.cpp  
// compile with: /clr:pure lnk2028.lib  
// LNK2028 expected  
int func();  
  
int main() {  
   return func();  
}  
```