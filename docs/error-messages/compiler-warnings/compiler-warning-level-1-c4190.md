---
title: Kompilátor upozornění (úroveň 1) C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: 05984594a57878aad8037861a15ac9284ff65192
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386496"
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