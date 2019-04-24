---
title: __super
ms.date: 11/04/2016
f1_keywords:
- __super_cpp
helpviewer_keywords:
- __super keyword [C++]
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
ms.openlocfilehash: a69d177bb83ce404a18d50c8f966be5d81f5fa72
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330528"
---
# <a name="super"></a>__super

**Microsoft Specific**

Umožňuje explicitně uvést, že je pro funkci, u které je prováděno přetížení, volána implementace základní funkce.

## <a name="syntax"></a>Syntaxe

```
__super::member_function();
```

## <a name="remarks"></a>Poznámky

Všechny dostupné metody základní třídy jsou ve fázi řešení přetížení zváženy a funkce, jež poskytne nejlepší výsledek, je ta, která je volána.

**__super** může být použit pouze v těle členské funkce.

**__super** nelze použít pomocí deklarace. Zobrazit [using – deklarace](../cpp/using-declaration.md) Další informace.

Se zavedením [atributy](../windows/attributes/attributes-alphabetical-reference.md) , které vkládají kód, může kód obsahovat jednu nebo více základních tříd, jejichž názvy nemusí být známy, ale které obsahují metody, které chcete volat.

## <a name="example"></a>Příklad

```cpp
// deriv_super.cpp
// compile with: /c
struct B1 {
   void mf(int) {}
};

struct B2 {
   void mf(short) {}

   void mf(char) {}
};

struct D : B1, B2 {
   void mf(short) {
      __super::mf(1);   // Calls B1::mf(int)
      __super::mf('s');   // Calls B2::mf(char)
   }
};
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)