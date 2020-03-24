---
title: Upozornění kompilátoru (úroveň 1) C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: 6d110aa70a470382e274546e95599804fa3bc7d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199872"
---
# <a name="compiler-warning-level-1-c4190"></a>Upozornění kompilátoru (úroveň 1) C4190

' identifier1 ' obsahuje zadané propojení jazyka C, ale vrací typ UDT ' identifier2 ', který je nekompatibilní s C.

Funkce nebo ukazatel na funkci má parametr UDT (uživatelsky definovaný typ, což je třída, struktura, výčet nebo sjednocení) jako návratový typ a `extern` propojení "C". Tato akce je platná v případě, že:

- Všechna volání této funkce se vyskytují v C++.

- Definice funkce je v C++.

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
