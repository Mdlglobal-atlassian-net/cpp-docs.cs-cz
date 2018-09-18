---
title: Upozornění (úroveň 1) C4190 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4190
dev_langs:
- C++
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d398331c159c6fc639160dbe54d6ab5f969d3dbd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063733"
---
# <a name="compiler-warning-level-1-c4190"></a>Kompilátor upozornění (úroveň 1) C4190

'identifier1' byl zadán C-linkage, ale vrací UDT "identifier2", který není kompatibilní s C

Funkce nebo ukazatel na funkci má jako návratový typ UDT (uživatelem definovaný typ, který je třída, struktura, výčtu nebo sjednocení) a `extern` propojení "C". Toto je právní pokud:

- Všechna volání této funkce dojde k z jazyka C++.

- Definice funkce je v jazyce C++.

## <a name="example"></a>Příklad

```cpp
// C4190.cpp
// compile with: /W1 /LD
struct X
{
   int i;
   X ();
   virtual ~X ();
};

extern "C" X func ();   // C4190
```