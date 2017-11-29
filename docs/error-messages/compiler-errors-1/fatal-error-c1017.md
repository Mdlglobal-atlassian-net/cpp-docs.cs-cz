---
title: "Závažná chyba C1017 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1017
dev_langs: C++
helpviewer_keywords: C1017
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 478a0a17ef8e0f0e6cb6589798d901837e7aff75
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1017"></a>Závažná chyba C1017
Neplatný celočíselný konstantní výraz.  
  
 Výraz v `#if` – direktiva složka neexistuje nebo neprovedl vyhodnocení na konstantu.  
  
 Konstanty definovat pomocí `#define` musí mít hodnoty, která se vyhodnotí jako celočíselná konstanta, pokud jsou použity v `#if`, `#elif`, nebo `#else` – direktiva.  
  
 Následující ukázka generuje C1017:  
  
```  
// C1017.cpp  
#define CONSTANT_NAME "YES"  
#if CONSTANT_NAME   // C1017  
#endif  
```  
  
 Možná řešení:  
  
```  
// C1017b.cpp  
// compile with: /c  
#define CONSTANT_NAME 1  
#if CONSTANT_NAME  
#endif  
```  
  
 Protože `CONSTANT_NAME` vyhodnocena jako řetězec a není celé číslo, `#if` – direktiva generuje závažná chyba C1017.  
  
 V ostatních případech preprocesor vyhodnotí nedefinované konstanta nula. To může způsobit neočekávané výsledky, jak znázorňuje následující ukázka. `YES`není definován, tak se vyhodnotí na hodnotu nula. Výraz `#if` `CONSTANT_NAME` vyhodnocena jako false a kód, který se má použít na `YES` preprocesor odstraní. `NO`Proto je nedefinovaný (nula), také `#elif` `CONSTANT_NAME==NO` vyhodnotí jako true (`0 == 0`), způsobuje preprocesor kód v `#elif` část příkazu – přesně opak zamýšlené chování.  
  
```  
// C1017c.cpp  
// compile with: /c  
#define CONSTANT_NAME YES  
#if CONSTANT_NAME  
   // Code to use on YES...  
#elif CONSTANT_NAME==NO  
   // Code to use on NO...  
#endif  
```  
  
 Pokud chcete zobrazit, přesně jak kompilátor zpracovává direktivy preprocesoru, použijte [/P](../../build/reference/p-preprocess-to-a-file.md), [/E](../../build/reference/e-preprocess-to-stdout.md), nebo [/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md).