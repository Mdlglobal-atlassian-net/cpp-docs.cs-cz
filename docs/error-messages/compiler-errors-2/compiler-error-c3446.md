---
title: "C3446 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 07/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3446
dev_langs: C++
helpviewer_keywords: C3445
ms.assetid: 33064548-24e4-46f1-beb1-476e3c3b3fbf
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1147c83a0cdd1519b56f862312b721d0db54540b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3446"></a>C3446 chyby kompilátoru  
  
>'*třída*': inicializátoru výchozí člen není povolen pro člena – hodnotová třída  
  
V sadě Visual Studio 2015 a starší kompilátor povolené (ale ignoruje) inicializátoru výchozího člena pro člena třídy hodnotu. Výchozí inicializace – hodnotová třída vždy nula inicializuje členy; výchozí konstruktor není povoleno. Visual Studio 2017 vyvolávají výchozí člen inicializátory Chyba kompilátoru, jak je uvedeno v následujícím příkladu:

## <a name="example"></a>Příklad  
 Následující ukázka generuje C3446 Visual Studio 2017 a novější:  
  
```cpp  
// C3446.cpp  
value struct V
{
       int i = 0; // error C3446: 'V::i': a default member initializer  
                  // is not allowed for a member of a value class
       int j {0}; // C3446           
};
```  
  
Chcete-li chybu opravit, odeberte inicializátoru:  
  
```cpp  
// C3446b.cpp  
value struct V
{
       int i;  
       int j;
};
```  
  
