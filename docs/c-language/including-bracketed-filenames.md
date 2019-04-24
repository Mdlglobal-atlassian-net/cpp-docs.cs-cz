---
title: Zahrnutí názvů souboru v závorkách
ms.date: 11/04/2016
ms.assetid: 6a4e5411-c35e-48b8-90ef-b37ac324ed94
ms.openlocfilehash: 87de00814f58ed86ee33abdcf96dd210f418c5ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233096"
---
# <a name="including-bracketed-filenames"></a>Zahrnutí názvů souboru v závorkách

**ANSI 3.8.2** metoda nalezení zahrnutelných zdrojových souborů

Pro specifikace souborů uzavřených do ostrých závorek preprocesor neprohledává adresáře nadřazených souborů. "Nadřazený" soubor je soubor, který má [#include](../preprocessor/hash-include-directive-c-cpp.md) direktivu. Místo toho se začíná vyhledáním souboru v adresářích určených příkazovým řádkem kompilátoru za možností /I. Pokud možnost /I není k dispozici nebo se nezdaří, preprocesor použije proměnnou prostředí INCLUDE k nalezení všech souborů include v lomených závorkách. Proměnná prostředí INCLUDE může obsahovat několik cest oddělených středníky (**;**). Pokud se více než jeden adresář zobrazí jako součást možnosti /I nebo v rámci proměnná prostředí INCLUDE, preprocesor je hledá v pořadí, v jakém jsou uvedeny.

## <a name="see-also"></a>Viz také:

[Direktivy předběžného zpracování](../c-language/preprocessing-directives.md)
