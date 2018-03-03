---
title: "Chyba linkerů Lnk2031 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2031
dev_langs:
- C++
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a519b4241c9ffabaeeb387cc8e4997125d57781
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2031"></a>Chyba linkerů LNK2031
Nelze vygenerovat p/invoke pro "function_declaration" decorated_name; chybí v metadatech konvence volání  
  
 Při pokusu o import nativní funkce do čistého bitové kopie, nezapomeňte, že implicitní konvence volání liší mezi nativní a čistý kompilace. Další informace o čisté bitové kopie najdete v tématu [prázdná a ověřitelný kód (C + +/ CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
## <a name="example"></a>Příklad  
 Tato ukázka kódu generuje součást s funkce exportované, nativní, jejichž konvence volání je implicitně [__cdecl](../../cpp/cdecl.md).  
  
```  
// LNK2031.cpp  
// compile with: /LD  
extern "C" {  
   __declspec(dllexport) int func() { return 3; }  
};  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří čistý klienta, který zpracovává nativní funkce. Ale konvence volání pod **/CLR: pure** je [__clrcall](../../cpp/clrcall.md). Následující ukázka generuje LNK2031.  
  
```  
// LNK2031_b.cpp  
// compile with: /clr:pure LNK2031.lib  
// LNK2031 expected  
extern "C" int func();  
  
int main() {  
   return func();  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak využívat nativní funkce z čisté bitové kopie. Poznámka: explicitní **__cdecl** volání specifikátor konvence.  
  
```  
// LNK2031_c.cpp  
// compile with: /clr:pure LNK2031.lib  
extern "C" int __cdecl func();  
  
int main() {  
   return func();  
}  
```