---
title: void (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- void_cpp
dev_langs:
- C++
helpviewer_keywords:
- void keyword [C++]
- functions [C++], void
- pointers, void
ms.assetid: d203edba-38e6-4056-8b89-011437351057
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1aab4a8c18424fdbd52ac24444dd35a1660a714b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114342"
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