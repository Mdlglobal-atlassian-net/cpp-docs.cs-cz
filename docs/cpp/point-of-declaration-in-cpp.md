---
title: Bod deklarace v C++
ms.date: 11/04/2016
helpviewer_keywords:
- point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
ms.openlocfilehash: d6cb4c3813d88c8b29fbcb2e0827805f406e6c81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560651"
---
# <a name="point-of-declaration-in-c"></a>Bod deklarace v C++

Název se považuje za deklarovat ihned po jeho deklarátor, ale před jeho vlastním inicializátoru (volitelné). (Další informace o deklarátorech naleznete v tématu [deklarace a definice](declarations-and-definitions-cpp.md).)

Podívejte se například:

```cpp
// point_of_declaration1.cpp
// compile with: /W1
double dVar = 7.0;
int main()
{
   double dVar = dVar;   // C4700
}
```

Bod deklarace byly *po* inicializace a potom místní `dVar` by inicializovány na hodnotu globální proměnné 7.0 `dVar`. Nicméně, protože se nejedná o případ, `dVar` je inicializován na nedefinovanou hodnotu.

## <a name="see-also"></a>Viz také:

[Rozsah](../cpp/scope-visual-cpp.md)