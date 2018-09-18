---
title: Bod deklarace v C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68ac24fcfe35701dd75d74800661aa5e41c005f8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072056"
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