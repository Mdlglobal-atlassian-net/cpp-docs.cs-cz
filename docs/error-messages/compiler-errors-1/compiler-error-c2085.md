---
title: C2085 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2085
dev_langs:
- C++
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c0fe489dbdd0934926a056bbc7e5539f40ca1ba8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169839"
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