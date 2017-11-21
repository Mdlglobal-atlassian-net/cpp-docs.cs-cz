---
title: "C2533 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2533
dev_langs: C++
helpviewer_keywords: C2533
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c21849c7318ac4f169bf7104a478fa57ba7dd040
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2533"></a>C2533 chyby kompilátoru
"identifikátor": konstruktory nejsou povoleny návratový typ.  
  
 Konstruktor nemůže mít typ vrácené hodnoty (není i `void` návratový typ).  
  
 Chybí středník mezi koncem definice třídy a první implementace konstruktor je běžné zdroj této chyby. Kompilátor vidí třída jako definice návratový typ pro funkci konstruktoru a generuje C2533.  
  
 Následující ukázka generuje C2533 a ukazuje, jak to opravit:  
  
```  
// C2533.cpp  
// compile with: /c  
class X {  
public:  
   X();     
};  
  
int X::X() {}   // C2533 - constructor return type not allowed  
X::X() {}   // OK - fix by using no return type  
```