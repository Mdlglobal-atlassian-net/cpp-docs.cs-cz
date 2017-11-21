---
title: "C4746 upozornění kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs: C++
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
caps.latest.revision: "2"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1b88f51aa9365c0795c8d3d944ba9f3a8db059d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-c4746"></a>C4746 upozornění kompilátoru
volatile přístup '\<výraz >' podléhá/volatile: [iso &#124; ms] nastavení; zvažte použití vnitřní funkce __iso_volatile_load nebo úložiště.  
  
 C4746 jsou vydávány vždy, když volatile proměnné se k nim přistupuje přímo. Je určena k pomoci vývojářům určit umístění kódu, které jsou postižené konkrétním volatile modelu aktuálně zadaný (což se dá řídit pomocí [/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) – možnost kompilátoru). Konkrétně může být užitečné při hledání překážek paměti generované kompilátorem hardware při použití /volatile:ms.  
  
 Vnitřní funkce __iso_volatile_load/úložiště lze explicitně přístup k nestálým paměti bez ovlivnění volatile modelu. Pomocí těchto vnitřní funkce C4746 nespustí.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.