---
title: pointers_to_members – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
helpviewer_keywords:
- class members, pointers to
- pragmas, pointers_to_members
- members, pointers to
- pointers_to_members pragma
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
ms.openlocfilehash: fb5b277252b6c1422a87c5f2a2e2b7230ec49632
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219071"
---
# <a name="pointers_to_members-pragma"></a>pointers_to_members – direktiva pragma

**C++Konkrétní**

Určuje, zda může být ukazatel na člena třídy deklarován před jeho přidruženou definicí třídy. Slouží k řízení velikosti ukazatele a kódu potřebného k interpretaci ukazatele.

## <a name="syntax"></a>Syntaxe

> **#pragma pointers_to_members (** *ukazatel-deklarace* [ **,** *většina-obecné-reprezentace* ])

## <a name="remarks"></a>Poznámky

Direktivu pragma **pointers_to_members** můžete umístit do zdrojového souboru jako alternativu k použití možností kompilátoru [/VMB nebo/VMG](../build/reference/vmb-vmg-representation-method.md) nebo [klíčových slov dědičnosti](../cpp/inheritance-keywords.md).

Argument *pointer-Declaration* určuje, zda jste deklarovali ukazatel na člen před nebo po přidružené definici funkce. Argument *pointer-Declaration* je jedním z následujících dvou symbolů:

| Argument | Komentáře |
|--------------|--------------|
| **full_generality** | Generuje bezpečný, někdy neoptimální kód. **Full_generality** použijete, pokud je jakýkoliv ukazatel na člen deklarovaný před definicí přidružené třídy. Tento argument vždy používá reprezentaci ukazatele určenou argumentem *nejvíc-General-reprezentaci* . Ekvivalentní možnosti /vmg. |
| **best_case** | Generuje bezpečný, optimální kód, který používá nejlepší reprezentaci pro všechny odkazy na členy. Vyžaduje definování třídy před deklarací ukazatele na člena této třídy. Výchozí hodnota je **best_case**. |

Argument *nejvíc-General-reprezentací* určuje nejmenší reprezentace ukazatele, kterou může kompilátor bezpečně použít pro odkazování na libovolný ukazatel na člen třídy v jednotce překladu. Argumentem může být jedna z těchto hodnot:

| Argument | Komentáře |
|--------------|--------------|
| **single_inheritance** | Nejobecnější reprezentace je jediná dědičnost, ukazatel na členskou funkci. Způsobí chybu, je-li model dědičnosti definice třídy, pro kterou je ukazatel na člen deklarován jako vícenásobný nebo virtuální. |
| **multiple_inheritance** | Nejobecnější reprezentace je vícenásobná dědičnost, ukazatel na členskou funkci. Způsobí chybu, je-li model dědičnosti definice třídy, pro kterou je ukazatel na člen deklarován jako virtuální. |
| **virtual_inheritance** | Nejobecnější reprezentace je virtuální dědičnost, ukazatel na členskou funkci. Nikdy nezpůsobí chybu. **virtual_inheritance** je výchozí argument při `#pragma pointers_to_members(full_generality)` použití. |

> [!CAUTION]
> Doporučujeme, abyste direktivu pragma **pointers_to_members** umístili pouze do souboru zdrojového kódu, který chcete ovlivnit, a až po jakékoli `#include` direktivy. Tímto postupem snížíte riziko, že tato direktiva pragma ovlivní další soubory a že bude náhodně zadáno více definic pro stejnou proměnnou, funkci nebo název třídy.

## <a name="example"></a>Příklad

```cpp
//   Specify single-inheritance only
#pragma pointers_to_members( full_generality, single_inheritance )
```

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
