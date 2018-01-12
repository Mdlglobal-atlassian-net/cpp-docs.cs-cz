---
title: "C2217 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2217
dev_langs: C++
helpviewer_keywords: C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6af2bbd43d6e522bbe6ede2a874b7e8ebbf27c10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2217"></a>C2217 chyby kompilátoru
"atribut1" vyžaduje "atribut2"  
  
 První atribut funkce vyžaduje, aby druhý atribut.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Přerušení (`__interrupt`) funkce deklarována jako `near`. Přerušení funkce musí být `far`.  
  
2.  Přerušení funkce deklarovat s `__stdcall`, nebo `__fastcall`. Přerušení funkce musíte použít C konvence volání.  
  
## <a name="example"></a>Příklad  
 C2217 může také nastat, pokud se pokusíte vytvořit vazbu delegáta funkce CLR, která přebírá proměnný počet argumentů. Pokud funkci má také e param pole přetížení, použijte místo toho. Následující ukázka generuje C2217.  
  
```  
// C2217.cpp  
// compile with: /clr  
using namespace System;  
delegate void MyDel(String^, Object^, Object^, ...);   // C2217  
delegate void MyDel2(String ^, array<Object ^> ^);   // OK  
  
int main() {  
   MyDel2^ wl = gcnew MyDel2(Console::WriteLine);  
   array<Object ^ > ^ x = gcnew array<Object ^>(2);  
   x[0] = safe_cast<Object^>(0);  
   x[1] = safe_cast<Object^>(1);  
  
   // wl("{0}, {1}", 0, 1);  
   wl("{0}, {1}", x);  
}  
```