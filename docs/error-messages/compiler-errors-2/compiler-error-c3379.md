---
title: "C3379 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3379
dev_langs:
- C++
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9fd5a8acf918a0f6b485cf9ba94ad759d58f7b2e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3379"></a>C3379 chyby kompilátoru
'class': vnořené třídy nemůže mít specifikátor přístupu sestavení jako součást jeho deklaraci  
  
 Při použití spravovaného typu, například třídě nebo struktuře, [veřejné](../../cpp/public-cpp.md) a [privátní](../../cpp/private-cpp.md) klíčová slova označuje, zda se třída zveřejní prostřednictvím metadata sestavení. `public`nebo `private` nelze použít pro vnořené třídy, které zdědí přístup sestavení nadřazených třídy.  
  
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
