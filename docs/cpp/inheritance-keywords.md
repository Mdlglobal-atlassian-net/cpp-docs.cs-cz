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
ms.openlocfilehash: f0aae655540b4d3f9130d9840d77e0abcf270cc2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374102"
---
# <a name="inheritance-keywords"></a>Klíčová slova dědičnosti

**Specifické pro Microsoft**

```
class [__single_inheritance] class-name;
class [__multiple_inheritance] class-name;
class [__virtual_inheritance] class-name;
```

kde:

*název třídy*<br/>
Název deklarované třídy.

Jazyk C++ umožňuje deklarovat ukazatel na člen třídy před definicí třídy. Příklad:

```cpp
class S;
int S::*p;
```

Ve výše uvedeném kódu `p` je deklarován jako ukazatel na celé číslo člena třídy S. V `class S` tomto kódu však ještě nebyla definována; byla pouze deklarována. Když kompilátor na takový ukazatel narazí, musí vytvořit obecné rozlišení ukazatele. Velikost rozlišení je závislá na zadaném modelu dědičnosti. Pro určení modelu dědičnosti existují čtyři způsoby:

- V rozhraní IDE pod **reprezentací ukazatele na člen**

- Na příkazovém řádku pomocí přepínače [/vmg](../build/reference/vmb-vmg-representation-method.md)

- Použití [pointers_to_members](../preprocessor/pointers-to-members.md) pragma

- Pomocí klíčových slov dědičnosti **__single_inheritance**, **__multiple_inheritance**a **__virtual_inheritance**. Tento postup řídí model dědičnosti na základě každé třídy.

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
> Stejná dopředná deklarace reprezentace ukazatele na člen třídy by se měla nacházet v každé jednotce překladu, která deklaruje ukazatele na členy této třídy, a deklarace by se měla objevit před deklarací ukazatelů na členy.

Pro kompatibilitu s předchozími verzemi jsou synonyma **_single_inheritance pro** **__single_inheritance** **_multiple_inheritance**, **__multiple_inheritance** **_virtual_inheritance** a **__virtual_inheritance,** pokud není zadána možnost kompilátoru [/Za \(zakázat jazykové rozšíření).](../build/reference/za-ze-disable-language-extensions.md)

**END Microsoft Specifické**

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)
