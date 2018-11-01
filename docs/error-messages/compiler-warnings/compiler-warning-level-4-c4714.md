---
title: Kompilátor upozornění (úroveň 4) C4714
ms.date: 11/04/2016
f1_keywords:
- C4714
helpviewer_keywords:
- C4714
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
ms.openlocfilehash: ed94e5b716a697ec96d7fecac75433823c9a67e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553852"
---
# <a name="compiler-warning-level-4-c4714"></a>Kompilátor upozornění (úroveň 4) C4714

Funkce označená jako __forceinline není vložená funkce

Dané funkce byla vybrána pro vložené rozšíření, ale kompilátor neprovedli vkládání.

I když `__forceinline` je silnější označení kompilátoru než `__inline`, vkládání je stále prováděny uvážení kompilátoru, ale žádné heuristické metody se používají k určení výhody z vložené této funkce.

V některých případech kompilátor nevloží určitou funkci mechanických důvodů. Například kompilátor nevloží:

- Funkce, pokud by výsledkem kombinace SEH a C++ EH.

- Některé funkce, pomocí kopie vytvořený předán podle hodnoty, když - GX/EHs/EHa na objekty.

- Funkce, která vrátí objekt v nerozvinutelných podle hodnoty, když - GX/EHs/EHa na.

- Funkcí s vloženým sestavením při kompilaci bez - Og/Ox/O1/O2.

- Funkce se seznamem argumentů s proměnnou délkou.

- Funkce s **zkuste** – příkaz (zpracování výjimek jazyka C++).

Následující ukázka generuje C4714:

```
// C4714.cpp
// compile with: /Ob1 /GX /W4
__forceinline void func1()
{
   try
   {
   }
   catch (...)
   {
   }
}

void func2()
{
   func1();   // C4714
}

int main()
{
}
```