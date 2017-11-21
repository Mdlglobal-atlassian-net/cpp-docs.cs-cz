---
title: "C4485 upozornění kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4485
dev_langs: C++
helpviewer_keywords: C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 435e49a857e3c448ac7e5f7ef00bb9032320aa25
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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