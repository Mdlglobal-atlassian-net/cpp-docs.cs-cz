---
title: Konvence knihovny C++
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, conventions
- classes [C++]
- functions [C++], library naming conventions
- naming conventions [C++], C++ Standard Library
- conventions [C++], C++ Standard Library
- function names [C++]
- coding conventions, C++ Standard Library
- naming conventions [C++], C++ library
ms.assetid: bf41b79a-2d53-4f46-8d05-779358335146
ms.openlocfilehash: d92636a7ed63e09396ff68749560cde9d1f8639c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755704"
---
# <a name="c-library-conventions"></a>Konvence knihovny C++

Knihovna C++ se řídí stejnými konvencemi jako standardní knihovna jazyka C a ještě více popsaných věcí.

Implementace má určitou zeměpisnou šířku v tom, jak deklaruje typy a funkce v C++ knihovně:

- Názvy funkcí ve standardní knihovně jazyka C mohou mít propojení extern "C++" nebo extern "C". Místo deklarace vložené entity knihovny zahrňte odpovídající standardní hlavičku jazyka C.

- Název členské funkce ve třídě knihovny může mít další signatury funkcí v rámci těch, které jsou uvedeny v tomto dokumentu. Můžete zkontrolovat, že se zde popsané volání funkce chová podle očekávání, ale nemůžete spolehlivě převzít adresu členské funkce knihovny. (Typ nemusí být to, co očekáváte.)

- Třída knihovny může mít nedokumentované (nevirtuální) základní třídy. Třída dokumentovaný jako odvozená z jiné třídy může ve skutečnosti být odvozena z této třídy prostřednictvím jiných nedokumentované třídy.

- Typ definovaný jako synonymum pro nějaký typ Integer může být stejný jako jeden z několika různých celočíselných typů.

- Typ bitové masky lze implementovat buď jako typ integer, nebo jako výčet. V obou případech můžete provádět bitové operace (například `AND` a `OR`) na hodnoty stejného typu bitové masky. Prvky `A` a `B` typu maskování bitů jsou nenulové hodnoty, například `A` & `B` nula.

- Funkce knihovny, která nemá žádnou specifikaci výjimek, může vyvolat jakoukoli výjimku, pokud její definice jasně neomezuje takovou možnost.

Na druhé straně platí určitá omezení:

- Standardní knihovna C nepoužívá žádná maskující makra. Jsou rezervovány pouze konkrétní signatury funkcí, nikoli názvy samotných funkcí.

- Název funkce knihovny mimo třídu nebude mít další, nedokumentované signatury funkce. Můžete spolehlivě převzít její adresu.

- Základní třídy a členské funkce, které jsou popsány jako virtuální, jsou zajištěny jako virtuální, a ty, které jsou popsány jako nevirtuální, jsou zajištěny

- Dva typy definované C++ knihovnou jsou vždy rozdílné, pokud tento dokument explicitně nenavrhne jinak.

- Funkce poskytované knihovnou, včetně výchozích verzí nahraditelných funkcí, mohou vyvolat *nejvíce* těch výjimek, které jsou uvedeny v jakékoli specifikaci výjimky. Žádné destruktory poskytnuté knihovnou nevyvolávají výjimky. Funkce ve standardní knihovně jazyka C mohou šířit výjimku, jako když `qsort` volá funkci porovnání, která vyvolá výjimku, ale jinak nevyvolává výjimky.

## <a name="see-also"></a>Viz také:

Přehled standardní knihovny\ [ C++ ](../standard-library/cpp-standard-library-overview.md)
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
