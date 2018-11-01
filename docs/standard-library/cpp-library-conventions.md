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
ms.openlocfilehash: f1790b75baea340d0b3ab1044290317055ac81d7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524778"
---
# <a name="c-library-conventions"></a>Konvence knihovny C++

Knihovny C++ dodržuje mnohem stejnými konvencemi jako standardní knihovny jazyka C a navíc několik dalších uvedených zde.

Implementace má určitá zeměpisná šířka v tom, jak deklaruje typy a funkce v knihovně C++:

- Názvy funkcí v knihovně Standard C mohou mít # extern "C++" nebo propojení extern "C". Zahrňte vhodné záhlaví Standard C, spíše než deklarovat vložené entity knihovny.

- Název členské funkce v knihovně tříd může být podpisy další funkce nad hodnotami uvedenými v tomto dokumentu. Můžete si být jisti, že volání funkce je zde popsáno, jak se bude chovat podle očekávání, ale nelze spolehlivě převzetí adresy členské funkce knihovny. (Typ nemusí být co očekáváte.)

- Knihovna tříd může mít nedokumentované (nevirtuální) základní třídy. Třída zdokumentované odvozena z jiné třídy mohou ve skutečnosti odvozená z této třídy pomocí jiných nedokumentované tříd.

- Typ definovaný jako synonymum pro nějaký typ celé číslo může být stejný jako jeden z několika rozdílnými celočíselnými typy.

- Typ bitové masky je možné implementovat jako typ integer nebo výčet. V obou případech se může provedení bitové operace (například `AND` a `OR`) u hodnot typu stejný typ bitové masky. Prvky `A` a `B` typ bitové masky jsou nenulové hodnoty tak, aby `A`  &  `B` je nula.

- Funkce knihovny, který nemá žádné specifikace výjimky může vyvolat výjimku libovolného, pokud její definice jasně omezuje tato možnost.

Na druhé straně platí určitá omezení:

- Standardní knihovny jazyka C používá žádná makra maskování. Jenom konkrétní funkce, které jsou vyhrazená podpisy, ne názvy funkcí sami.

- Název funkce knihovny mimo třídu nebudou mít další, nedokumentované, funkce podpisy. Můžete spolehlivě provést její adresu.

- Základní třídy a označuje jako virtuální členské funkce jsou assuredly virtuální při těch popsaných jako nevirtuální jsou assuredly nevirtuální.

- Dva typy definované knihovnou jazyka C++ se vždy liší, není-li tento dokument explicitně navrhuje jinak.

- Knihovna, včetně výchozí verze nahraditelné funkcí, funkce může vyvolat *maximálně* těchto výjimek uvedené ve specifikaci žádné výjimky. Žádné destruktory knihovna vyvolávat výjimky. Funkce standardní knihovny jazyka C může propagovat výjimku, jako když `qsort` volání funkce porovnání, které vyvolá výjimku, ale jsou v opačném případě nevyvolají výjimky.

## <a name="see-also"></a>Viz také:

[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
