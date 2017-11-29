---
title: "C2483 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 09/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2483
dev_langs: C++
helpviewer_keywords: C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 45b0f616f62287f82b35dfdfdc03c445ec529177
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2483"></a>C2483 chyby kompilátoru

>'*identifikátor*': objekt s konstruktoru nebo destruktor nelze deklarovat 'vláken.

Tato chybová zpráva je v sadě Visual Studio 2015 a novější verze zastaralé. V předchozích verzích proměnné deklarovány s `thread` atribut nemůže být inicializovaný s konstruktor nebo jiných výraz, který vyžaduje testování spuštění. Statický výraz se vyžaduje k chybě při inicializaci `thread` data.

## <a name="example"></a>Příklad

Následující ukázka generuje C2483 v sadě Visual Studio 2013 a starší verze.

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error  

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>Viz také

[přístup z více vláken](../../cpp/thread.md)