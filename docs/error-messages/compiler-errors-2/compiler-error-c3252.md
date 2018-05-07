---
title: C3252 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3252
dev_langs:
- C++
helpviewer_keywords:
- C3252
ms.assetid: aa9ad096-e9ac-41c7-8ad9-b966751c7c75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4bc7ca0ccf3c973363e4427c89ccf497c20d1791
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3252"></a>C3252 chyby kompilátoru
"metody": usnadnění virtuální metoda ve spravovaných nebo typ WinRT nelze zmenšit.  
  
 Třídu, která implementuje virtuální metodu ze základní třídy nebo libovolnou metodu z rozhraní nelze omezit přístup k této metody.  
  
 Všimněte si, že jsou všechny metody v rozhraní veřejné.  
  
 Následující ukázka generuje C3252 a ukazuje, jak to opravit:  
  
```  
// C3252.cpp  
// compile with: /clr /c  
ref class A {  
public:  
   virtual void f1() {}  
};  
  
ref class B : public A {  
// To fix, uncomment the following line:   
// public:      
   virtual void f1() override sealed {}   // C3252, make this method public  
};  
```