---
title: /Q – možnosti (operace nízké úrovně)
ms.date: 1/23/2018
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: a6dcbd256fa3510955884d3adba4855b23cdbfab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514250"
---
# <a name="q-options-low-level-operations"></a>/Q – možnosti (operace nízké úrovně)

Můžete použít **/Q** – možnosti kompilátoru k provedení následujících operací nízké úrovně kompilátoru:

- [/ Qfast_transcendentals (vynucení rychlých transcendentních objektů)](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md): vytvoří rychlé transcendentals.

- [/ QIfist (potlačit _ftol)](../../build/reference/qifist-suppress-ftol.md): potlačí `_ftol` při převodu z typu s plovoucí desetinnou čárkou na celočíselný typ je povinné (jenom x86).

- [/ Qimprecise_fwaits (odebrání příkazů fwaits z bloků Try)](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): Odebere `fwait` příkazy uvnitř `try` bloky.

- [/ Qpar (Automatická paralelizace)](../../build/reference/qpar-auto-parallelizer.md): Povolí automatickou paralelizaci smyček, které jsou označeny [#pragma loop()](../../preprocessor/loop.md) směrnice.

- [/ Qpar-report (úroveň sestav automatický Paralelizér)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md): Povolí protokolování úrovní pro automatickou paralelizaci.

- [/ Qsafe_fp_loads](../../build/reference/qsafe-fp-loads.md): registr s plovoucí desetinnou čárkou načte a zaregistruje pro přesuny mezi pamětí a MMX potlačuje optimalizace.

- [/ Qspectre](../../build/reference/qspectre.md): vygeneruje instrukce ke zmírnění určité chyby zabezpečení Spectre.

- [/ Qvec-report (úroveň sestav automatickou vektorizací)](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md): Povolí protokolování úrovní pro automatickou vektorizaci.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
