---
title: /Q – možnosti (operace nízké úrovně)
ms.date: 1/23/2018
f1_keywords:
- /q
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.openlocfilehash: 5bbb63b4f437f8aefd5c84c1c1c4bd20bdb965cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319392"
---
# <a name="q-options-low-level-operations"></a>/Q – možnosti (operace nízké úrovně)

Můžete použít **/Q** – možnosti kompilátoru k provedení následujících operací nízké úrovně kompilátoru:

- [/ Qfast_transcendentals (vynucení rychlých transcendentních objektů)](qfast-transcendentals-force-fast-transcendentals.md): Vytvoří rychlé transcendentals.

- [/ QIfist (potlačit _ftol)](qifist-suppress-ftol.md): Potlačí `_ftol` při převodu z typu s plovoucí desetinnou čárkou na celočíselný typ je povinné (jenom x86).

- [/ Qimprecise_fwaits (odebrání příkazů fwaits z bloků Try)](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): Odebere `fwait` příkazy uvnitř `try` bloky.

- [/ Qpar (Automatická paralelizace)](qpar-auto-parallelizer.md): Povolí automatickou paralelizaci smyček, které jsou označeny [#pragma loop()](../../preprocessor/loop.md) směrnice.

- [/ Qpar-report (úroveň sestav automatický Paralelizér)](qpar-report-auto-parallelizer-reporting-level.md): Povolí protokolování úrovní pro automatickou paralelizaci.

- [/ Qsafe_fp_loads](qsafe-fp-loads.md): Potlačuje optimalizace pro registr s plovoucí desetinnou čárkou zatížením a pro přesuny mezi pamětí a MMX registrů.

- [/ Qspectre](qspectre.md): Vygeneruje instrukce ke zmírnění určité chyby zabezpečení Spectre.

- [/ Qvec-report (úroveň sestav automatickou vektorizací)](qvec-report-auto-vectorizer-reporting-level.md): Povolí protokolování úrovní pro automatickou vektorizaci.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
