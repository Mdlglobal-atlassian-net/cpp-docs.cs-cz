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
ms.workload: cplusplus
ms.openlocfilehash: d970c2de5e34840ab2ed77f229c329db3c6f72fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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