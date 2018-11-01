---
title: void (C++)
ms.date: 11/04/2016
f1_keywords:
- void_cpp
helpviewer_keywords:
- void keyword [C++]
- functions [C++], void
- pointers, void
ms.assetid: d203edba-38e6-4056-8b89-011437351057
ms.openlocfilehash: cb4be000c3c41862d5b4df766d21ae1cddeb6838
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594109"
---
# <a name="void-c"></a>void (C++)

Při použití jako návratový typ funkce **void** – klíčové slovo určuje, že funkce nevrací hodnotu. Při použití pro seznam parametrů funkce určuje void, že funkce nepřebírá žádné parametry. Při použití v deklaraci ukazatele určuje void, že je ukazatel „univerzální“.

Pokud je ukazatel typu `void *`, může odkazovat na libovolnou proměnnou, která není deklarována s **const** nebo **volatile** – klíčové slovo. Ukazatel void nelze přímo odkázat, pokud není přetypován na jiný typ. Ukazatel void lze převést na libovolný typ datového ukazatele.

Ukazatel void může v jazyce C++ odkazovat na funkci, ale nikoli na člen třídy.

Nelze deklarovat proměnnou typu void.

## <a name="example"></a>Příklad

```cpp
// void.cpp
void vobject;   // C2182
void *pv;   // okay
int *pint; int i;
int main() {
   pv = &i;
   // Cast optional in C required in C++
   pint = (int *)pv;
}
```

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Základní typy](../cpp/fundamental-types-cpp.md)