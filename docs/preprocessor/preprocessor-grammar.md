---
title: Gramatika preprocesoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1871d1b8281f4dd74733133ede70ed80430246b3
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465568"
---
# <a name="preprocessor-grammar"></a>Gramatika preprocesoru
**#define***identifikátor* *řetězci tokenu*optimalizované    
  
*#* **definování***identifikátor*[**(** *identifikátor*optimalizované **,** *...*  **,** *identifikátor*optimalizované **)**] *řetězci tokenu*optimalizované    
  
**definovaný (***identifikátor* **)**   
  
**definované***identifikátor*   
  
`#include` **"***path-spec***"**  
  
`#include` **\<***Path-spec***>**  
  
**#line***sekvence číslic***"** *filename* **"** optimalizované      
  
*#* **undef***identifikátor*   
  
**#error***řetězci tokenu*   
  
**#pragma***řetězci tokenu*   
  
*Podmíněné* :  
*část IF části elif*optimalizované*část else*optimalizované*řádek endif*  
  
*část IF* :  
*if-linetext*  
  
*řádek IF* :  
**#if***konstantního výrazu.*  
  
**#ifdef***identifikátor*  
  
**#ifndef***identifikátor*  
  
*části elif* :  
*text řádku elif*  
  
*části elif text řádku elif*  
  
*řádek elif* :  
**#elif***konstantního výrazu.*  
  
*části else* :  
*else-linetext*  
  
*řádek else* :  
`#else`  
  
*řádek endif* :  
`#endif`  
  
*sekvence číslic* :  
*číslice*  
  
*sekvence číslic číslice*  
  
*číslice* : jeden z  
**0 1 2 3 4 5 6 7 8 9**  
  
*řetězcový token* :  
Řetězec tokenů  
  
*token* :  
*Klíčové slovo*  
  
*identifikátor*  
  
*Konstanty*  
  
*operator*  
  
`punctuator`  
  
*Název souboru* :  
Název souboru právní operačního systému  
  
*Path-spec* :  
Cesta k souboru právní  
  
*text* :  
Libovolná sekvence textu  
  
> [!NOTE]
> Následující neterminály jsou rozbaleny v [lexikální konvence](../cpp/lexical-conventions.md) část *referenční dokumentace jazyka C++*: `constant`, `constant` - *výraz* , *identifikátor*, *– klíčové slovo*, `operator`, a `punctuator`.  
  
## <a name="see-also"></a>Viz také  
 
[Gramatický souhrn (C/C++)](../preprocessor/grammar-summary-c-cpp.md)