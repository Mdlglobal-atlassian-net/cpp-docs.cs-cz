---
title: C4746 upozornění kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d00c75b2b7cdf2fdafb4e109496a701fb561cb9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4746"></a>C4746 upozornění kompilátoru
volatile přístup '\<výraz >' podléhá/volatile: [iso&#124;ms] nastavení; zvažte použití vnitřní funkce __iso_volatile_load nebo úložiště.  
  
 C4746 jsou vydávány vždy, když volatile proměnné se k nim přistupuje přímo. Je určena k pomoci vývojářům určit umístění kódu, které jsou postižené konkrétním volatile modelu aktuálně zadaný (což se dá řídit pomocí [/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) – možnost kompilátoru). Konkrétně může být užitečné při hledání překážek paměti generované kompilátorem hardware při použití /volatile:ms.  
  
 Vnitřní funkce __iso_volatile_load/úložiště lze explicitně přístup k nestálým paměti bez ovlivnění volatile modelu. Pomocí těchto vnitřní funkce C4746 nespustí.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.