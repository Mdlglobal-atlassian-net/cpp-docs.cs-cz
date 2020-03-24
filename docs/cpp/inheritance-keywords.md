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
ms.openlocfilehash: 781673582cb2c3086677b05abc6a7eb73eeabdb4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178178"
---
# <a name="inheritance-keywords"></a>Klíčová slova dědičnosti

**Specifické pro společnost Microsoft**

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

V kódu výše je `p` deklarován jako ukazatel na celočíselný člen třídy S. Nicméně `class S` ještě není v tomto kódu definován; byl deklarován pouze. Když kompilátor na takový ukazatel narazí, musí vytvořit obecné rozlišení ukazatele. Velikost rozlišení je závislá na zadaném modelu dědičnosti. Pro určení modelu dědičnosti existují čtyři způsoby:

- V integrovaném vývojovém prostředí (IDE) v rámci **reprezentace ukazatele na člena**

- Na příkazovém řádku pomocí přepínače [/VMG](../build/reference/vmb-vmg-representation-method.md)

- Použití direktivy pragma [pointers_to_members](../preprocessor/pointers-to-members.md)

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
>  Stejná dopředná deklarace reprezentace ukazatele na člen třídy by se měla nacházet v každé jednotce překladu, která deklaruje ukazatele na členy této třídy, a deklarace by se měla objevit před deklarací ukazatelů na členy.

Z důvodu kompatibility s předchozími verzemi jsou **_single_inheritance**, **_multiple_inheritance**a **_virtual_inheritance** synonyma pro **__single_inheritance**, **__multiple_inheritance**a **__virtual_inheritance** , pokud je zadána možnost kompilátoru [/za \(Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)
