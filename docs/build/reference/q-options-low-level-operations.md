---
title: Q – možnosti (operace nízké úrovně) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 1/23/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /q
dev_langs:
- C++
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 15854333a9f26f87d20f7819327e68050ab37bf6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717773"
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
