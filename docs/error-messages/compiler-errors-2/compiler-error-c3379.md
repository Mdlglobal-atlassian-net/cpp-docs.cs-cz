---
title: C3379 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3379
dev_langs:
- C++
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ded7ebfba6ab9f9120ebfa48c1942209a74e704
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33258280"
---
# <a name="compiler-error-c3379"></a>C3379 chyby kompilátoru
'class': vnořené třídy nemůže mít specifikátor přístupu sestavení jako součást jeho deklaraci  
  
 Při použití spravovaného typu, například třídě nebo struktuře, [veřejné](../../cpp/public-cpp.md) a [privátní](../../cpp/private-cpp.md) klíčová slova označuje, zda se třída zveřejní prostřednictvím metadata sestavení. `public` nebo `private` nelze použít pro vnořené třídy, které zdědí přístup sestavení nadřazených třídy.  
  
 Při použití s [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), `ref` a `value` klíčová slova informuje, že je spravovaná třídu (viz [třídy a struktury](../../windows/classes-and-structs-cpp-component-extensions.md)).  
  
 Následující ukázka generuje C3379:  
  
```  
// C3379a.cpp  
// compile with: /clr  
using namespace System;  
  
public ref class A {  
public:  
   static int i = 9;  
  
   public ref class BA {   // C3379  
   // try the following line instead  
   // ref class BA {  
   public:  
      static int ii = 8;  
   };  
};  
  
int main() {  
  
   A^ myA = gcnew A;  
   Console::WriteLine(myA->i);  
  
   A::BA^ myBA = gcnew A::BA;  
   Console::WriteLine(myBA->ii);  
}  
```  
