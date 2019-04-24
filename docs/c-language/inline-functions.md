---
title: Vložené funkce
ms.date: 10/16/2017
helpviewer_keywords:
- fast code
- inline functions, __inline keyword
- functions [C++], inline functions
ms.assetid: 00f4b2ff-8ad0-4165-9f4c-2ef157d03f31
ms.openlocfilehash: ebe0fd3d785903c149999bd4ec8de9eabeabdb05
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325543"
---
# <a name="inline-functions"></a>Vložené funkce

**Microsoft Specific**

Klíčové slovo `__inline` přikazuje kompilátoru nahradit kód uvnitř definice funkce pro každou instanci jejího volání. K nahrazení však dochází pouze dle rozhodnutí kompilátoru. Kompilátor například nevloží funkci, je-li její adresa použita nebo je-li pro vložení příliš velká.

Aby byla funkce považována za vhodnou k vložení, musí pro svou definici používat nový styl.

Chcete-li zadat vloženou funkci, použijte tento tvar:

> **__inline** *typ*<sub>optimalizované</sub> *definice funkce*

Použití vložených funkcí generuje rychlejší a někdy i menší kód, než jaký generuje ekvivalentní volání funkce, a to z následujících důvodů:

- Šetří čas potřebný k provedení volání funkcí.

- Malé vložené funkce o velikost přibližně tři a méně řádků vytvoří méně kódu než ekvivalentní volání funkce, protože kompilátor negeneruje kód pro zpracování argumentů a návratové hodnoty.

- Funkce generované jako vložené jsou předmětem optimalizací kódu, které nejsou běžným funkcím dostupné, protože kompilátor neprovádí meziprocedurální optimalizace.

Funkce používající klíčové slovo `__inline` by neměly být zaměněny s vloženým kódem assembleru. Zobrazit [vložený Assembler](../c-language/inline-assembler-c.md) Další informace.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[inline, __inline, \__forceinline](../cpp/inline-functions-cpp.md)
