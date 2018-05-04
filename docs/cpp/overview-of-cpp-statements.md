---
title: Přehled příkazů jazyka C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- statements [C++]
ms.assetid: e56996b2-b846-4b99-ac94-ac72fffc5ec7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2858807816178115dd34c05d6c88c3dd6fecdee3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="overview-of-c-statements"></a>Přehled příkazů jazyka C++
Příkazy jazyka C++ jsou spouštěny postupně, s výjimkou případů, kdy příkaz výrazu, příkaz výběru, příkaz iterace nebo příkaz jump konkrétně upravuje danou sekvenci.  
  
 Příkazy mohou být následujících typů:  
  
```  
  
labeled-statement  
expression-statement  
compound-statement  
selection-statement  
iteration-statement  
jump-statement  
declaration-statement  
try-throw-catch  
  
```  
  
 Ve většině případů je stejná jako ANSI c. syntaxe příkazu C++ Základní rozdíl mezi nimi je, že v jazyce C deklarace jsou povoleny pouze na začátku bloku; Přidá C++ *deklarace příkaz*, které efektivně odebere toto omezení. To umožňuje zavést proměnné v aplikaci na místě, kde lze vypočítat předzpracovanou inicializační hodnotu.  
  
 Deklarování proměnných uvnitř bloků také umožňuje vykonávat přesnou kontrolu rozsahu a životnosti těchto proměnných.  
  
 Témata příkazů popisují následující klíčová slova jazyka C++:  
  
|||||  
|-|-|-|-|  
|[break](../cpp/break-statement-cpp.md)|[else](../cpp/if-else-statement-cpp.md)|[__if_exists –](../cpp/if-exists-statement.md)|[__try](../cpp/structured-exception-handling-c-cpp.md)|  
|[Případ](../cpp/switch-statement-cpp.md)|[__except](../cpp/structured-exception-handling-c-cpp.md)|[__if_not_exists –](../cpp/if-not-exists-statement.md)|[Zkuste](../cpp/try-throw-and-catch-statements-cpp.md)|  
|[catch](../cpp/try-throw-and-catch-statements-cpp.md)|[for](../cpp/for-statement-cpp.md)|[__leave](../c-language/try-finally-statement-c.md)|[while](../cpp/while-statement-cpp.md)|  
|[continue](../cpp/continue-statement-cpp.md)|[goto](../cpp/goto-statement-cpp.md)|[return](../cpp/return-statement-cpp.md)||  
|[default](../cpp/switch-statement-cpp.md)|[__finally](../cpp/structured-exception-handling-c-cpp.md)|[switch](../cpp/switch-statement-cpp.md)||  
|[do](../cpp/do-while-statement-cpp.md)|[if](../cpp/if-else-statement-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)||  
  
## <a name="see-also"></a>Viz také  
 [Příkazy](../cpp/statements-cpp.md)