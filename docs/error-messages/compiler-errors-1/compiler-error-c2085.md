---
title: "C2085 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2085
dev_langs: C++
helpviewer_keywords: C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 45805bbea2eca77ae81922088471e99de26be1e4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2085"></a>C2085 chyby kompilátoru
"identifikátor": není v seznamu formální parametr  
  
 Identifikátor byla deklarována v definici funkce ale není v seznamu formální parametr. (Jenom ANSI C)  
  
 Následující ukázka generuje C2085:  
  
```  
// C2085.c  
void func1( void )  
int main( void ) {}   // C2085  
```  
  
 Možná řešení:  
  
```  
// C2085b.c  
void func1( void );  
int main( void ) {}  
```  
  
 S chybějícími středník, `func1()` vypadá definici funkce není prototyp, takže `main` je definována v rámci `func1()`, generování C2085 chyba identifikátoru `main`.