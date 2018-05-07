---
title: Chyba v běhu R6018 C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6018
dev_langs:
- C++
helpviewer_keywords:
- R6018
ms.assetid: f6dd40d1-a119-4d8b-b39e-97350ea23349
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4946e3a8341963ee1a1ca2c3ad65d64cfbad8080
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="c-runtime-error-r6018"></a>R6018 Chyba za běhu C
Chyba neočekávané haldy  
  
> [!NOTE]
>  Pokud narazíte na tato chybová zpráva při spuštění aplikace, aplikace se vypnout, protože má internímu problému. Existuje několik možných příčin této chyby, avšak často je způsobena značit potíže v kódu aplikace.  
>   
>  Zkuste chybu odstranit pomocí tohoto postupu:  
>   
>  -   Použití **aplikace a funkce** nebo **programy a funkce** stránky v **ovládací panely** opravit nebo znovu nainstalovat program.  
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.  
> -   Kontrola aktualizovaná verze aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.  
  
 **Informace pro programátory v jazyce**  
  
 Program došlo k neočekávané chybě při provádění operace správy paměti.  
  
 Této chybě obvykle dochází, pokud program nechtěně mění data haldy běhu. Ale ho může také být způsobeno k vnitřní chybě v modulu runtime nebo kód operačního systému.  
  
 Chcete-li tento problém vyřešit, zkontrolujte chyby poškození haldy v kódu. Další informace a příklady naleznete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Dále zkontrolujte, že používáte nejnovější redistributables pro nasazení aplikace. Informace najdete v tématu [nasazení v jazyce Visual C++](../../ide/deployment-in-visual-cpp.md).