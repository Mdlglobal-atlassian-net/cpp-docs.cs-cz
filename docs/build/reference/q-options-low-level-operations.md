---
title: /Q – možnosti (operace nízké úrovně)
ms.date: 01/23/2018
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: 6348226aa38d1f2eefdf9e19e27c4c87bd2f0812
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927670"
---
# <a name="q-options-low-level-operations"></a>/Q – možnosti (operace nízké úrovně)

K provedení následujících operací kompilátoru nižší úrovně můžete použít možnosti kompilátoru **/q** :

- [/Qfast_transcendentals (vynutit rychlé transcendentní objekty)](qfast-transcendentals-force-fast-transcendentals.md): Generuje rychle transcendentní objekty.

- [/QIfist (Potlačit _ftol)](qifist-suppress-ftol.md): Potlačí `_ftol` , když je vyžadován převod z typu s plovoucí desetinnou čárkou na celočíselný typ (pouze x86).

- [/Qimprecise_fwaits (odebrat příkazů fwaits uvnitř bloků try)](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): Odebere `fwait` příkazy uvnitř `try` bloků.

- [/Qpar (auto-paralelizace)](qpar-auto-parallelizer.md): Povoluje automatické paralelismuing smyček, které jsou označeny direktivou [#pragma Loop ()](../../preprocessor/loop.md) .

- [/Qpar-Report (úroveň vytváření sestav auto-paralelizace)](qpar-report-auto-parallelizer-reporting-level.md): Povoluje úrovně generování sestav pro automatické paralelismus.

- [/Qsafe_fp_loads](qsafe-fp-loads.md): Potlačí optimalizace pro načtení registru s plovoucí desetinnou čárkou a pro přesun mezi registry paměti a MMX.

- [/Qspectre](qspectre.md): Vygeneruje pokyny pro zmírnění některých ohrožení zabezpečení Spectre.

- [/Qvec-Report (úroveň vytváření sestav auto-vektorizace)](qvec-report-auto-vectorizer-reporting-level.md): Povoluje generování úrovní pro automatické rozkládání.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
