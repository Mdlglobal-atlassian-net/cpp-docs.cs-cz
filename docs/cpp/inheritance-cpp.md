---
title: Dědičnost (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [C++]
- derived classes [C++], about derived classes
- classes [C++], derived
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
ms.openlocfilehash: 0180a2f7b41e3169bc9e25d8b598dbe2b84be088
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184577"
---
# <a name="inheritance--c"></a>Dědičnost (C++)

Tento oddíl vysvětluje, jak lze pomocí odvozených tříd vytvářet rozšiřitelné programy.

## <a name="overview"></a>Přehled

Nové třídy lze odvodit z existujících tříd pomocí mechanismu nazývá "dědičnost" (zobrazit informace počínaje [jednoduchá dědičnost](../cpp/single-inheritance.md)). Třídy, které jsou používány pro odvození, se nazývají „základní třídy“ určitých odvozených tříd. Odvozená třída je deklarována pomocí následující syntaxe:

```cpp
class Derived : [virtual] [access-specifier] Base
{
   // member list
};
class Derived : [virtual] [access-specifier] Base1,
   [virtual] [access-specifier] Base2, . . .
{
   // member list
};
```

Po značce (názvu) třídy zadejte dvojtečku následovanou seznamem základních specifikací.  Základní třídy s těmito názvy musí být deklarovány dříve.  Základní specifikace mohou obsahovat specifikátor přístupu, který je jedním z klíčových slov **veřejné**, **chráněné** nebo **privátní**.  Tyto specifikátory přístupu zadejte před název základní třídy a platí pouze pro tuto základní třídu.  Tyto specifikátory řídí oprávnění odvozené třídy k použití členů základní třídy.  Zobrazit [řízení přístupu členů](../cpp/member-access-control-cpp.md) informace o přístupu k členům základní třídy.  Pokud je specifikátor přístupu vynechán, bude považován za přístup k této základní třídě **privátní**.  Základní specifikace mohou obsahovat klíčové slovo **virtuální** označuje virtuální dědičnost.  Toto klíčové slovo lze zadat před nebo za specifikátor přístupu, pokud existuje.  Pokud je použita virtuální dědičnost, základní třída se nazývá virtuální základní třída.

Lze zadat více základních tříd oddělených čárkami.  Pokud je zadána jedna základní třída, je model dědičnosti [jednoduché dědičnosti](../cpp/single-inheritance.md). Pokud je zadán více než jedné základní třídy, se nazývá model dědičnosti [vícenásobná dědičnost](../cpp/multiple-base-classes.md).

Jsou zahrnuty v následujících tématech:

- [Jedna dědičnost](../cpp/single-inheritance.md)

- [Vícenásobné třídy base](../cpp/multiple-base-classes.md)

- [Virtuální funkce](../cpp/virtual-functions.md)

- [Explicitní přepsání](../cpp/explicit-overrides-cpp.md)

- [Abstraktní třídy](../cpp/abstract-classes-cpp.md)

- [Souhrn pravidel rozsahu](../cpp/summary-of-scope-rules.md)

[__Super](../cpp/super.md) a [__interface](../cpp/interface.md) klíčová slova jsou popsané v této části.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)