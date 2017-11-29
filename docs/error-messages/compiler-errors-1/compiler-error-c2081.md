---
title: "C2081 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2081
dev_langs: C++
helpviewer_keywords: C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 20f9f98ca03b9ed71d360b1b7c8bb64494a58416
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2081"></a>C2081 chyby kompilátoru
"identifikátor": název v seznamu Neplatná formální parametr  
  
 Identifikátor způsobila chybu syntaxe.  
  
 Tuto chybu mohl způsobit pomocí starém stylu pro formální parametr seznamu. V seznamu formální parametr musíte zadat typ formální parametrů.  
  
 Následující ukázka generuje C2081:  
  
```  
// C2081.c  
void func( int i, j ) {}  // C2081, no type specified for j  
```  
  
 Možná řešení:  
  
```  
// C2081b.c  
// compile with: /c  
void func( int i, int j ) {}  
```