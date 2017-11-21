---
title: "C2723 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2723
dev_langs: C++
helpviewer_keywords: C2723
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3816640569a503c8a56c4cf37f1bf23360b30a12
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2723"></a>C2723 chyby kompilátoru
'function': 'specifikátor' specifikátor neplatný v definici funkce  
  
 Specifikátor nelze vložit definici funkce mimo deklaraci třídy. `virtual` Specifikátor lze zadat pouze u deklaraci členské funkce v rámci deklaraci třídy.  
  
 Následující ukázka generuje C2723 a ukazuje, jak to opravit:  
  
```  
// C2723.cpp  
struct X {  
   virtual void f();  
   virtual void g();  
};  
  
virtual void X::f() {}   // C2723  
  
// try the following line instead  
void X::g() {}  
```