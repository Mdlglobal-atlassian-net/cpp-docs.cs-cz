---
title: Zahrnutí názvů souboru v závorkách | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 6a4e5411-c35e-48b8-90ef-b37ac324ed94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37b4d0e6ccf0c0c01671082d2596528632fba6cb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100861"
---
# <a name="including-bracketed-filenames"></a>Zahrnutí názvů souboru v závorkách

**ANSI 3.8.2** metoda nalezení zahrnutelných zdrojových souborů

Pro specifikace souborů uzavřených do ostrých závorek preprocesor neprohledává adresáře nadřazených souborů. "Nadřazený" soubor je soubor, který má [#include](../preprocessor/hash-include-directive-c-cpp.md) direktivu. Místo toho se začíná vyhledáním souboru v adresářích určených příkazovým řádkem kompilátoru za možností /I. Pokud možnost /I není k dispozici nebo se nezdaří, preprocesor použije proměnnou prostředí INCLUDE k nalezení všech souborů include v lomených závorkách. Proměnná prostředí INCLUDE může obsahovat několik cest oddělených středníky (**;**). Pokud se více než jeden adresář zobrazí jako součást možnosti /I nebo v rámci proměnná prostředí INCLUDE, preprocesor je hledá v pořadí, v jakém jsou uvedeny.

## <a name="see-also"></a>Viz také

[Direktivy předběžného zpracování](../c-language/preprocessing-directives.md)