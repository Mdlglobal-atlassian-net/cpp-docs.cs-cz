---
title: Definování bloků __asm jako maker v jazyce C
ms.date: 08/30/2018
helpviewer_keywords:
- macros, __asm blocks
- Visual C, macros
- __asm keyword [C++], as C macros
ms.assetid: 677ba11c-21c8-4609-bba7-cd47312243b0
ms.openlocfilehash: 46f0a23fcfd949843e3548354f52970b10b6d63b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169484"
---
# <a name="defining-__asm-blocks-as-c-macros"></a>Definování bloků __asm jako maker v jazyce C

**Specifické pro společnost Microsoft**

Makra jazyka C nabízejí pohodlný způsob, jak vložit kód sestavení do zdrojového kódu, ale vyžadují další péči, protože makro se rozšíří na jednu logickou čáru. Chcete-li vytvořit makra bez problémů, postupujte podle těchto pravidel:

- Uzavřete blok `__asm` do složených závorek.

- Před každou instrukci sestavení vložte klíčové slovo `__asm`.

- Místo komentářů ve stylu sestavení (`; comment`) nebo jednořádkových komentářů jazyka C (`// comment`) použijte původní styl komentáře jazyka C (`/* comment */`).

Pro ilustraci následující příklad definuje jednoduché makro:

```cpp
#define PORTIO __asm      \
/* Port output */         \
{                         \
   __asm mov al, 2        \
   __asm mov dx, 0xD007   \
   __asm out dx, al       \
}
```

Na první pohled se poslední tři klíčová slova `__asm` zdají být nadbytečných. Jsou však potřeba, protože se makro rozšíří na jeden řádek:

```cpp
__asm /* Port output */ { __asm mov al, 2  __asm mov dx, 0xD007 __asm out dx, al }
```

Třetí a čtvrté `__asm` klíčová slova jsou potřeba jako oddělovače příkazů. Jedinými oddělovači příkazů rozpoznanými v `__asm` blocích jsou znak nového řádku a klíčové slovo `__asm`. Vzhledem k tomu, že blok definovaný jako makro je jedna logická čára, je nutné jednotlivé instrukce oddělit pomocí `__asm`.

Složené závorky jsou také podstatné. Pokud je vynecháte, kompilátor může být zaměněn pomocí jazyka C++ C nebo příkazy na stejném řádku napravo od vyvolání makra. Bez uzavírací složené závorky nemůže kompilátor sdělit, kde se zastaví kód sestavení, a vidí příkazy jazyka C C++ nebo za `__asm` blok jako pokyny pro sestavení.

Komentáře ve stylu sestavení začínající středníkem ( **;** ) pokračují na konci řádku. To způsobuje problémy v makrech, protože kompilátor ignoruje vše po komentáři, a to vše jako na konci logického řádku. Totéž platí pro jednořádkový řádek C nebo C++ komentáře (`// comment`). Chcete-li zabránit chybám, použijte staré komentáře jazyka C (`/* comment */`) v `__asm` blocích definovaných jako makra.

Blok `__asm` zapsaný jako makro jazyka C může přebírat argumenty. Na rozdíl od obyčejného makra jazyka C však makro `__asm` nemůže vracet hodnotu. Takže taková makra nemůžete použít ve výrazech jazyka C nebo C++ .

Dejte pozor, abyste nevolali makra tohoto typu v nerozlišeném znění. Například volání makra jazyka sestavení ve funkci deklarované s konvencí `__fastcall` může způsobit neočekávané výsledky. (Viz [použití a zachování registrů ve vloženém sestavení](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md).)

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Vkládaný assembler](../../assembler/inline/inline-assembler.md)<br/>
