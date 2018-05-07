---
title: C2011 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2011
dev_langs:
- C++
helpviewer_keywords:
- C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 898a724f022a81f590ec1f8165de9752de6c1d0b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2011"></a>C2011 chyby kompilátoru
"identifikátor": "typ" Zadejte předefinování  
  
 Identifikátor již byl definován jako `type`. Zkontrolujte, zda předefinování identifikátoru.  
  
 Může také k C2011, pokud se importovat soubor záhlaví, nebo knihovna více než jednou do stejného souboru. Aby se zabránilo více zahrnutí z typů front definovaných v záhlaví souboru, použijte zahrnují chrání nebo `#pragma` [po](../../preprocessor/once.md) direktivy v záhlaví souboru.  
  
 Pokud potřebujete najít počáteční deklaraci Předefinovaná typu, můžete použít [/P](../../build/reference/p-preprocess-to-a-file.md) kompilátoru příznak ke generování předběžně zpracované výstup předaný kompilátoru. Text vyhledávací nástroje vám pomůže najít instancí identifikátor Předefinovaná ve výstupním souboru.  
  
 Následující ukázka generuje C2011 a ukazuje jeden ze způsobů a opravte ji:  
  
```  
// C2011.cpp  
// compile with: /c  
struct S;  
union S;   // C2011  
union S2;   // OK  
```