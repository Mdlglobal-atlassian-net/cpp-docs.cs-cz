---
title: "C3739 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3739
dev_langs: C++
helpviewer_keywords: C3739
ms.assetid: acffe894-08b8-4bf2-9249-9501e6e2bad3
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b3fa62f908f152e127669d1cd935fafdb75d413f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3739"></a>C3739 chyby kompilátoru
'class': syntaxe je podporován pouze, pokud parametr 'layout_dependent' event_receiver – hodnotu true  
  
 Pokusili jste se připojit celý rozhraní událostí, ale `layout_dependent` na [event_receiver –](../../windows/event-receiver.md) atribut není true; jednu událost musí připojit současně.  
  
 Následující ukázka generuje C3739:  
  
```  
// C3739.cpp  
struct A  
{  
   __event void e();  
};  
  
// event_receiver is implied  
// [ event_receiver(layout_dependent=false)]  
  
// use the following line instead  
// [event_receiver(com, layout_dependent=true), coclass ]  
struct B  
{  
   void f();  
   B(A* a)  
   {  
      __hook(A, a, &B::f);   // C3739  
      // use the following line instead to hook a single event  
      // __hook(&A::e, a, &B::f);  
   }  
};  
  
int main()  
{  
}  
```