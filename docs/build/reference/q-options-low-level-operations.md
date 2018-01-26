---
title: "-Q možnosti (operace nízké úrovně) | Microsoft Docs"
ms.custom: 
ms.date: 1/23/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /q
dev_langs: C++
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7636b042669c7f7b04d2bc662bcaa2fbe4bdc82a
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2018
---
# <a name="q-options-low-level-operations"></a>/Q – možnosti (operace nízké úrovně)

Můžete použít **/Q** – možnosti kompilátoru provádět následující operace nízké úrovně kompilátoru:

- [/ Qfast_transcendentals (vynutit rychlé Transcendentní objekty)](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md): generuje rychlé Transcendentní objekty.

- [/ QIfist (potlačit _ftol)](../../build/reference/qifist-suppress-ftol.md): potlačí `_ftol` po požadované (pouze x86) převod z typu s plovoucí desetinnou čárkou na typ integer.

- [/ Qimprecise_fwaits (odebrání příkazů fwaits z bloků Try)](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): Odebere `fwait` příkazy uvnitř `try` bloky.

- [/ Qpar (automatickou vektorizací)](../../build/reference/qpar-auto-parallelizer.md): umožňuje Automatická paralelizace cykly, které jsou označené [#pragma loop()](../../preprocessor/loop.md) – direktiva.

- [/ Qpar-report (úroveň sestav automatickou vektorizací)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md): umožňuje vytváření sestav úrovní Automatická paralelizace.

- [/ Qsafe_fp_loads](../../build/reference/qsafe-fp-loads.md): Potlačí optimalizace pro registraci s plovoucí desetinnou čárkou načte a pro přesun mezi paměti a MMX zaregistruje.

- [/ Qspectre](../../build/reference/qspectre.md): generuje pokyny ke zmírnění určité spektrum ohrožení zabezpečení.

- [/ Qvec-report (úroveň sestav automatickou vektorizací)](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md): umožňuje vytváření sestav úrovně pro automatické vectorization.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)  
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)  
