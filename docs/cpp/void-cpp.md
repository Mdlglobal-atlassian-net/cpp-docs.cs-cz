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
ms.openlocfilehash: 7d01d5b50cb347736bbd2a42fb76811bdfdb546c
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245206"
---
# <a name="void-c"></a>void (C++)

Při použití jako návratový typ funkce určuje klíčové slovo **void** , že funkce nevrací hodnotu. Při použití pro seznam parametrů funkce **void** určuje, že funkce nepřijímá žádné parametry. Při použití v deklaraci ukazatele Určuje **void** , že ukazatel je "Universal".

Pokud je typ ukazatele typu **void\*** , ukazatel může ukazovat na jakoukoliv proměnnou, která není deklarována s klíčovým slovem **const** nebo **volatile** . Ukazatel typu **void\*** nelze odkázat, pokud není přetypování na jiný typ. Ukazatel **void\*** lze převést na jakýkoli jiný typ ukazatele dat.

Ukazatel **void** může ukazovat na funkci, ale ne na člen třídy v C++.

Nelze deklarovat proměnnou typu **void**.

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