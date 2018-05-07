---
title: C4485 upozornění kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4485
dev_langs:
- C++
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b84d2976e31d5cc3a9b6547d0c4b02a61327ce0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4485"></a>C4485 upozornění kompilátoru
'override_function': odpovídá metody třídy base ref 'base_class_function', ale není označen jako 'nové' nebo 'přepsání'; 'nové (a "virtuální") se předpokládá, že  
  
 Přistupující objekt přepsání, bez ohledu `virtual` – klíčové slovo, přistupujícího objektu funkce základní třídy, ale `override` nebo `new` specifikátor nebyla součástí přepsání podpis funkce. Přidat `new` nebo `override` specifikátor vyřešit toto upozornění.  
  
 V tématu [přepsat](../../windows/override-cpp-component-extensions.md) a [new (nový slot v tabulce vtable)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md) Další informace.  
  
 C4485 je vždy vydané jako chyba. Použití [upozornění](../../preprocessor/warning.md) – Direktiva pragma pro potlačení C4485.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4485  
  
```  
// C4485.cpp  
// compile with: /clr  
delegate void Del();  
  
ref struct A {  
   virtual event Del ^E;  
};  
  
ref struct B : A {  
   virtual event Del ^E;   // C4485  
};  
  
ref struct C : B {  
   virtual event Del ^E {  
      void raise() override {}  
      void add(Del ^) override {}  
      void remove(Del^) override {}  
   }  
};  
```