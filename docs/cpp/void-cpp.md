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
ms.openlocfilehash: 2de019f908942a58b232877fcd9eebc4689d8e22
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187476"
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

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Předdefinované typy](../cpp/fundamental-types-cpp.md)
