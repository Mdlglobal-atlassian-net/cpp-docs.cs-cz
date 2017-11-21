---
title: "Kompilátoru (úroveň 1) upozornění C4378 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4378
dev_langs: C++
helpviewer_keywords: C4378
ms.assetid: d08e11ef-891a-4752-9a5e-360e7394acf7
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c3ed33157c73c48b4d00b85e37f36a110ab3f721
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4378"></a>C4378 kompilátoru upozornění (úroveň 1)
Musíte získat ukazatelů na funkce Spustit inicializátory; Vezměte v úvahu System::ModuleHandle::ResolveMethodHandle  
  
 V části **/CLR**, inicializátoru symboly obsahují funkce tokeny, není funkce ukazatele.  Je nutné převést tokeny ukazatelů pomocí <xref:System.ModuleHandle.ResolveMethodHandle%2A>.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4378.  
  
```  
// C4378.cpp  
// compile with: /W1 /clr /c  
typedef void (__cdecl *PF)(void);  
int cxpf = 0;   // number of destructors to call  
PF pfx[200];   // ptrs to those dtors, watch for overflow  
  
int myexit (PF pf) {  
   pfx[cxpf++] = pf;  
   return 0;  
}  
  
struct A {  
   A() {}  
   ~A() {}  
};  
  
A aaaa;   
  
#pragma data_seg(".mine$a")  
PF InitSegStart = (PF)1;  
#pragma data_seg(".mine$z")  
PF InitSegEnd = (PF)1;  
#pragma data_seg()  
  
void InitializeObjects () {  
   PF *x = &InitSegStart;  
   for (++x ; x < &InitSegEnd ; ++x)  
      if (*x)  
         (*x)();  
}  
  
#pragma init_seg(".mine$m",myexit)   // C4378  
A bbbb;   // crash  
  
int main () {  
   InitializeObjects();  
}  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vyřešit C4378.  
  
```  
// C4378_b.cpp  
// compile with: /clr  
#pragma warning(disable:4378)  
using namespace System;  
typedef void (__cdecl *PF)(void);  
typedef void (__clrcall * CLRPF)(void);  
  
int cxpf = 0;  // number of destructors we need to call  
PF pfx[200];   // ptrs to those dtors. Watch out for overflow!  
  
ref class TypeClassHolder {  
public:  
   static TypeClassHolder ^typeClass = gcnew TypeClassHolder();  
};  
  
CLRPF FuncTokenToFuncPtr(PF tknFunc) {  
   ModuleHandle type =   
      Type::GetTypeFromHandle(Type::GetTypeHandle(TypeClassHolder::typeClass))->Module->ModuleHandle;  
   return (CLRPF)type.ResolveMethodHandle((int)(size_t)(tknFunc)).GetFunctionPointer().ToPointer();  
}  
  
int myexit (PF pf) {  
   pfx[cxpf++] = pf;  
   return 0;  
}  
  
struct A {  
   A() {}  
   ~A() {}  
};  
  
A aaaa;   
  
#pragma data_seg(".mine$a")  
PF InitSegStart = (PF)1;  
#pragma data_seg(".mine$z")  
PF InitSegEnd = (PF)1;  
#pragma data_seg()  
  
void InitializeObjects () {  
   PF *x = &InitSegStart;  
   for (++x ; x < &InitSegEnd ; ++x)  
      if(*x) {  
         CLRPF realppfunc;  
         realppfunc = FuncTokenToFuncPtr(*x);  
         (realppfunc)();  
      }  
}  
  
#pragma init_seg(".mine$m",myexit)  
A bbbb; // constructor call succeeds  
  
int main () {  
   InitializeObjects();  
}  
```