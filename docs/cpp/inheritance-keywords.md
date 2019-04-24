---
title: Klíčová slova dědičnosti
ms.date: 11/04/2016
f1_keywords:
- __multiple_inheritance
- __single_inheritance_cpp
- __virtual_inheritance_cpp
- __virtual_inheritance
- __multiple_inheritance_cpp
- __single_inheritance
helpviewer_keywords:
- __single_inheritance keyword [C++]
- declaring derived classes [C++]
- keywords [C++], inheritance keywords
- __multiple_inheritance keyword [C++]
- __virtual_inheritance keyword [C++]
- inheritance, declaring derived classes
- derived classes [C++], declaring
- inheritance, keywords
ms.assetid: bb810f56-7720-4fea-b8b6-9499edd141df
ms.openlocfilehash: 656ee7ed38c24c9f3b8881f84d8e33ca81e3d936
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183489"
---
# <a name="inheritance-keywords"></a>Klíčová slova dědičnosti

**Microsoft Specific**

```
class [__single_inheritance] class-name;
class [__multiple_inheritance] class-name;
class [__virtual_inheritance] class-name;
```

kde:

*class-name*<br/>
Název deklarované třídy.

Jazyk C++ umožňuje deklarovat ukazatel na člen třídy před definicí třídy. Příklad:

```cpp
class S;
int S::*p;
```

Ve výše uvedeném kódu `p` je deklarováno jako ukazatel na celočíselný člen třídy S. Ale `class S` má ještě není definována v tomto kódu; to je pouze deklarována. Když kompilátor na takový ukazatel narazí, musí vytvořit obecné rozlišení ukazatele. Velikost rozlišení je závislá na zadaném modelu dědičnosti. Pro určení modelu dědičnosti existují čtyři způsoby:

- V integrovaném vývojovém prostředí v rámci **reprezentace ukazatele na člena**

- Pomocí příkazového řádku [/vmg](../build/reference/vmb-vmg-representation-method.md) přepnout

- Použití [pointers_to_members](../preprocessor/pointers-to-members.md) – Direktiva pragma

- Pomocí klíčových slov dědičnosti **__single_inheritance**, **__multiple_inheritance**, a **__virtual_inheritance**. Tento postup řídí model dědičnosti na základě každé třídy.

    > [!NOTE]
    >  Je-li vždy po definování třídy deklarován ukazatel na člen třídy, není třeba použít žádnou z těchto možností.

Deklarování ukazatele na člen třídy před definicí třídy ovlivňuje velikost a rychlost výsledného spustitelného souboru. Čím složitější dědičnost třída používá, tím větší je počet bajtů potřebných k zastoupení ukazatele na člen třídy a tím větší je kód potřebný k interpretaci ukazatele. Jednoduchá dědičnost je nejméně náročná a virtuální dědičnost je nejsložitější.

Je-li výše uvedený příklad změněn na:

```cpp
class __single_inheritance S;
int S::*p;
```

ukazatelé na členy třídy `class S` budou používat nejmenší možnou reprezentaci bez ohledu na možnosti příkazového řádku nebo direktivy pragma.

> [!NOTE]
>  Stejná dopředná deklarace reprezentace ukazatele na člen třídy by se měla nacházet v každé jednotce překladu, která deklaruje ukazatele na členy této třídy, a deklarace by se měla objevit před deklarací ukazatelů na členy.

Z důvodu kompatibility s předchozími verzemi **_single_inheritance**, **_multiple_inheritance**, a **_virtual_inheritance** jsou synonyma pro **__ single_inheritance**, **__multiple_inheritance**, a **__virtual_inheritance** Pokud – možnost kompilátoru [/Za \(zakázat jazyka rozšíření)](../build/reference/za-ze-disable-language-extensions.md) určena.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Klíčová slova](../cpp/keywords-cpp.md)