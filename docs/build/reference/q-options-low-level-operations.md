---
title: /Q – možnosti (operace nízké úrovně)
ms.date: 01/08/2020
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: 722a63a43e5e08fe80b26f908c7ae92df2fdb29c
ms.sourcegitcommit: 0f4ee9056d65043fa5a715f0ad1031c0ed30e2b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2020
ms.locfileid: "77034516"
---
# <a name="q-options-low-level-operations"></a>/Q – možnosti (operace nízké úrovně)

K provedení následujících operací kompilátoru nižší úrovně můžete použít možnosti kompilátoru **/q** :

- [/Qfast_transcendentals (vynutit rychlou transcendentní objekty)](qfast-transcendentals-force-fast-transcendentals.md): generuje rychlé transcendentní objekty.

- [/QIfist (Potlačit _ftol)](qifist-suppress-ftol.md): potlačí `_ftol`, je-li vyžadován převod z typu s plovoucí desetinnou čárkou na typ Integer (pouze x86).

- [/Qimprecise_fwaits (odebrat příkazů fwaits uvnitř bloků try)](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): Odebere `fwait` příkazy uvnitř `try` bloků.

- [/QIntel-JCC-erratum](qintel-jcc-erratum.md): snižuje dopad na výkon, který způsobila aktualizace kontrola (JCC) vyžádal povolení mikrokódu.

- [/Qpar (auto-paralelizace)](qpar-auto-parallelizer.md): povolí automatické paralelismue smyček, které jsou označeny direktivou [#pragma Loop ()](../../preprocessor/loop.md) .

- [/Qpar-Report (úroveň vytváření sestav auto paralelizace)](qpar-report-auto-parallelizer-reporting-level.md): povoluje úrovně generování sestav pro automatické paralelismuy.

- [/Qsafe_fp_loads](qsafe-fp-loads.md): potlačí optimalizace pro načtení registru s plovoucí desetinnou čárkou a pro přesun mezi registry paměti a MMX.

- [/Qspectre](qspectre.md): vygeneruje pokyny pro zmírnění některých ohrožení zabezpečení Spectre.

- [/Qspectre-Load](qspectre-load.md): vygeneruje pokyny pro zmírnění ohrožení zabezpečení Spectre na základě zatížení.

- [/Qspectre-Load-CF](qspectre-load-cf.md): vygeneruje pokyny pro zmírnění ohrožení zabezpečení Spectre v závislosti na pokynech toku ovládacích prvků, které se načítají.

- [/Qvec-Report (úroveň vytváření sestav auto vektorizace)](qvec-report-auto-vectorizer-reporting-level.md): povoluje úrovně generování sestav pro automatické rozkládání.

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
