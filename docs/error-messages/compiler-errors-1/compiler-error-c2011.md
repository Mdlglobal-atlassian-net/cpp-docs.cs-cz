---
title: "C2011 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2011
dev_langs: C++
helpviewer_keywords: C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0f32048e0de21e5af2d4d52a0c703813b1a1ff8b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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