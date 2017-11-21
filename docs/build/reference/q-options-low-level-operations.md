---
title: "-Q možnosti (operace nízké úrovně) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
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
ms.assetid: 9fa738b9-630a-4bde-bc87-bdfa30552be4
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0fb7ef41e40b2ce6f4b3555de5b2369cc2d7a460
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="q-options-low-level-operations"></a>/Q – možnosti (operace nízké úrovně)
Můžete použít **/Q** – možnosti kompilátoru provádět následující operace nízké úrovně kompilátoru:  
  
-   [/ Qfast_transcendentals (vynutit rychlé Transcendentní objekty)](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md): generuje rychlé Transcendentní objekty.  
  
-   [/ QIfist (potlačit _ftol)](../../build/reference/qifist-suppress-ftol.md): potlačí `_ftol` po požadované (pouze x86) převod z typu s plovoucí desetinnou čárkou na typ integer.  
  
-   [/ Qimprecise_fwaits (odebrání příkazů fwaits z bloků Try)](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): Odebere `fwait` příkazy uvnitř `try` bloky.  
  
-   [/ Qpar (automatickou vektorizací)](../../build/reference/qpar-auto-parallelizer.md): umožňuje Automatická paralelizace cykly, které jsou označené [#pragma loop()](../../preprocessor/loop.md) – direktiva.  
  
-   [/ Qpar-report (úroveň sestav automatickou vektorizací)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md): umožňuje vytváření sestav úrovní Automatická paralelizace.  
  
-   [/ Qsafe_fp_loads](../../build/reference/qsafe-fp-loads.md): Potlačí optimalizace pro registraci s plovoucí desetinnou čárkou načte a pro přesun mezi paměti a MMX zaregistruje.  
  
-   [/ Qvec-report (úroveň sestav automatickou vektorizací)](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md): umožňuje vytváření sestav úrovně pro automatické vectorization.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)