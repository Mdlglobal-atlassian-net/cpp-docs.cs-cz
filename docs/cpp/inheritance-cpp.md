---
title: Dědičnost (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [C++]
- derived classes [C++], about derived classes
- classes [C++], derived
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
ms.openlocfilehash: 214900f8f36de0fa90ffcd6ca75f3a4e6e2c0777
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178251"
---
# <a name="inheritance--c"></a>Dědičnost (C++)

Tento oddíl vysvětluje, jak lze pomocí odvozených tříd vytvářet rozšiřitelné programy.

## <a name="overview"></a>Přehled

Nové třídy lze odvodit z existujících tříd pomocí mechanismu s názvem "dědičnost" (viz informace, které začínají v rámci [jedné dědičnosti](../cpp/single-inheritance.md)). Třídy, které jsou používány pro odvození, se nazývají „základní třídy“ určitých odvozených tříd. Odvozená třída je deklarována pomocí následující syntaxe:

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

Po značce (názvu) třídy zadejte dvojtečku následovanou seznamem základních specifikací.  Základní třídy s těmito názvy musí být deklarovány dříve.  Základní specifikace mohou obsahovat specifikátor přístupu, což je jedno z klíčových slov **Public**, **Protected** nebo **Private**.  Tyto specifikátory přístupu zadejte před název základní třídy a platí pouze pro tuto základní třídu.  Tyto specifikátory řídí oprávnění odvozené třídy k použití členů základní třídy.  Informace o přístupu ke členům základní třídy naleznete v tématu [Member-Access Control](../cpp/member-access-control-cpp.md) .  Pokud je specifikátor přístupu vynechán, přístup k této základně se považuje za **soukromý**.  Základní specifikace mohou obsahovat klíčové slovo **Virtual** k označení virtuální dědičnosti.  Toto klíčové slovo lze zadat před nebo za specifikátor přístupu, pokud existuje.  Pokud je použita virtuální dědičnost, základní třída se nazývá virtuální základní třída.

Lze zadat více základních tříd oddělených čárkami.  Pokud je určena jedna základní třída, je model dědičnosti [jedinou dědičností](../cpp/single-inheritance.md). Pokud je zadána více než jedna základní třída, model dědičnosti se nazývá [vícenásobná dědičnost](../cpp/multiple-base-classes.md).

Jsou k dispozici následující témata:

- [Jednoduchá dědičnost](../cpp/single-inheritance.md)

- [Více základních tříd](../cpp/multiple-base-classes.md)

- [Virtuální funkce](../cpp/virtual-functions.md)

- [Explicitní přepsání](../cpp/explicit-overrides-cpp.md)

- [Abstraktní třídy](../cpp/abstract-classes-cpp.md)

- [Souhrn pravidel oboru](../cpp/summary-of-scope-rules.md)

V této části jsou popsána klíčová slova [__super](../cpp/super.md) a [__interface](../cpp/interface.md) .

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)
