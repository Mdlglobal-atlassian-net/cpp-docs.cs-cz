---
title: Gramatika preprocesoru | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3c64c5a1855d80d5abc60d959bd68b33a380583b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="preprocessor-grammar"></a>Gramatika preprocesoru
**#define***identifikátor* *token řetězec*opt    
  
 *#***definovat***identifikátor*[**(** *identifikátor*opt**,** *...*  **,** *identifikátor*opt **)**] *token řetězec*opt    
  
 **definované (***identifikátor* **)**   
  
 **definované***identifikátor*   
  
 `#include`**"***cesta specifikace***"**  
  
 `#include` **\<**  *specifikace cesta***>**  
  
 **#line***číslice pořadí***"** *filename* **"**opt      
  
 *#***undef***identifikátor*   
  
 **#error***token řetězec*   
  
 **#pragma***token řetězec*   
  
 *Podmíněné* :  
 *Pokud část elif částí*vyjádřit výslovný*část else*opt*endif řádku*  
  
 *Pokud součást* :  
 *Pokud linetext*  
  
 *Pokud line* :  
 **#if***konstantní výraz*   
  
 **#ifdef***identifikátor*   
  
 **#ifndef***identifikátor*   
  
 *elif – částí* :  
 *elif – řádek textu*  
  
 *elif – částí elif – řádek textu*  
  
 *elif-line* :  
 **#elif***konstantní výraz*   
  
 *část else* :  
 *else linetext*  
  
 *else řádku* :  
 `#else`  
  
 *endif-line* :  
 `#endif`  
  
 *pořadí číslice* :  
 *číslice*  
  
 *pořadí číslice číslice*  
  
 *číslice* : jeden z  
 **0 1 2 3 4 5 6 7 8 9**  
  
 *token řetězec* :  
 Řetězec tokenů  
  
 *token* :  
 *– klíčové slovo*  
  
 *identifikátor*  
  
 *Konstanta*  
  
 *operátor*  
  
 `punctuator`  
  
 *Název souboru* :  
 Název souboru právní operačního systému  
  
 *Cesta specifikace* :  
 Cesta k souboru právní  
  
 *text* :  
 Žádné pořadí textu  
  
> [!NOTE]
>  Jsou následující terminálově nezávislých rozšířit [lexikální pravidla](../cpp/lexical-conventions.md) části *referenční příručka jazyka C++*: `constant`, `constant` - *výraz* , *identifikátor*, *– klíčové slovo*, `operator`, a `punctuator`.  
  
## <a name="see-also"></a>Viz také  
 [Gramatický souhrn (C/C++)](../preprocessor/grammar-summary-c-cpp.md)