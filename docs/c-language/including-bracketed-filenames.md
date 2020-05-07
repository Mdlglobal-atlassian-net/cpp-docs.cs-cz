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

**3.8.2 ANSI** Metoda hledání zdrojových souborů zahrnutelných

Pro specifikace souborů uzavřených do ostrých závorek preprocesor neprohledává adresáře nadřazených souborů. "Nadřazený" soubor je soubor, který obsahuje direktivu [#include](../preprocessor/hash-include-directive-c-cpp.md) . Místo toho se začíná vyhledáním souboru v adresářích určených příkazovým řádkem kompilátoru za možností /I. Pokud možnost/I není přítomna nebo se nezdařila, preprocesor používá proměnnou prostředí INCLUDE k nalezení souborů zahrnutí do lomených závorek. Proměnná prostředí INCLUDE může obsahovat několik cest oddělených středníky (**;**). Pokud se více než jeden adresář zobrazuje jako součást parametru/I nebo v rámci proměnné prostředí INCLUDE, preprocesor je vyhledá v pořadí, ve kterém se zobrazí.

## <a name="see-also"></a>Viz také

[Direktivy předběžného zpracování](../c-language/preprocessing-directives.md)
