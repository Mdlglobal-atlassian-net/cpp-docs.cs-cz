---
title: Chyba v běhu R6017 C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6017
dev_langs:
- C++
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f726f1e01acc20899085f8f1b84f74265843bbd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302721"
---
# <a name="c-runtime-error-r6017"></a>R6017 Chyba za běhu C
Chyba neočekávané uzamčení s více vlákny  
  
> [!NOTE]
>  Pokud narazíte na tato chybová zpráva při spuštění aplikace, aplikace se vypnout, protože má internímu problému. Existuje několik možných příčin této chyby, avšak často je způsobena značit potíže v kódu aplikace.  
>   
>  Zkuste chybu odstranit pomocí tohoto postupu:  
>   
>  -   Použití **aplikace a funkce** nebo **programy a funkce** stránky v **ovládací panely** opravit nebo znovu nainstalovat program.  
> -   Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.  
> -   Kontrola aktualizovaná verze aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.  
  
 **Informace pro programátory v jazyce**  
  
 Proces přijata neočekávaná chyba při pokusu o přístup k uzamčení C runtime s více vlákny systémový prostředek. Této chybě obvykle dochází, pokud proces nechtěně mění data haldy modulu runtime. Nicméně ji můžete také jednat k vnitřní chybě v modulu runtime knihoven nebo kód operačního systému.  
  
 Chcete-li tento problém vyřešit, zkontrolujte chyby poškození haldy v kódu. Další informace a příklady naleznete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Dále zkontrolujte, že používáte nejnovější redistributables pro nasazení aplikace. Informace najdete v tématu [nasazení v jazyce Visual C++](../../ide/deployment-in-visual-cpp.md).