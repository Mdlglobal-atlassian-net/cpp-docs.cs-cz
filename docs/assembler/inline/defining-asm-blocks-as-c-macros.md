---
title: Definování bloků __asm jako maker v jazyce C
ms.date: 08/30/2018
helpviewer_keywords:
- macros, __asm blocks
- Visual C, macros
- __asm keyword [C++], as C macros
ms.assetid: 677ba11c-21c8-4609-bba7-cd47312243b0
ms.openlocfilehash: c48298cf802600995dbbf68885896b6feccb807d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554723"
---
# <a name="defining-asm-blocks-as-c-macros"></a>Definování bloků __asm jako maker v jazyce C

**Specifické pro Microsoft**

Nabízí pohodlný způsob, jak vložit sestavení kódu do zdrojového kódu maker v jazyce C, ale vyžadují zvláštní pozornost vzhledem k tomu makro rozšíří na jednoho logického řádku. Chcete-li vytvořit bezproblémovou makra, postupovat podle těchto pravidel:

- Uzavřete `__asm` blokovat ve složených závorkách.

- Vložit `__asm` – klíčové slovo před každou instrukci sestavení.

- Použití starého typu komentáře v jazyce C ( `/* comment */`) místo sestavení – vizuální styl komentáře ( `; comment`) nebo Jednořádkové komentáře v jazyce C ( `// comment`).

Pro ilustraci, následující příklad definuje jednoduchý makra:

```cpp
#define PORTIO __asm      \
/* Port output */         \
{                         \
   __asm mov al, 2        \
   __asm mov dx, 0xD007   \
   __asm out dx, al       \
}
```

Na první pohled, poslední tři `__asm` klíčových slov se zdá, že nadbytečný. Nejsou potřeba, ale vzhledem k tomu, že se makro rozbalí do jednoho řádku:

```cpp
__asm /* Port output */ { __asm mov al, 2  __asm mov dx, 0xD007 __asm out dx, al }
```

Třetí a čtvrtý `__asm` klíčová slova jsou nutné jako oddělovače příkazu. Jediným příkazem oddělovače rozpoznán v `__asm` bloky jsou znak nového řádku a `__asm` – klíčové slovo. Protože bloku definovány jako makra je jeden logický řádek, třeba oddělit každou instrukci s `__asm`.

Složené závorky jsou také nezbytné. Vynecháte-li je, kompilátor může být matoucí příkazy jazyka C nebo C++ na stejném řádku napravo od volání makra. Bez pravé složené závorce, kompilátor nemůže určit, kde zastaví sestavení kódu a jeho příkazy jazyka C nebo C++ se zobrazí `__asm` bloku jako pokyny k sestavení.

Sestavení – vizuální styl poznámky, které začínají středník (**;**) dál konci řádku. To způsobí, že problémy v makrech vzhledem k tomu, že kompilátor ignoruje všechno, co za komentář, až na konec logického řádku. Totéž platí o Jednořádkové komentáře jazyka C nebo C++ ( `// comment`). Chcete-li zabránit chybám, použijte komentáře v jazyce C starého typu ( `/* comment */`) v `__asm` bloky, které jsou definovány jako makra.

`__asm` Bloku zapisují jako maker jazyka C, můžete převzít argumenty. Na rozdíl od běžných C makru, ale `__asm` – makro nemůže vracet hodnotu. Proto tato makra nelze použít ve výrazech jazyka C nebo C++.

Dejte pozor, abyste bez vyvolání makra tohoto typu. Například volání makru jazyk sestavení ve funkci deklarována s `__fastcall` vytváření názvů může vést k neočekávaným výsledkům. (Viz [použití a zachování registrů ve vloženém sestavení](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md).)

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>