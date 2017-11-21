---
title: "C2010 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2010
dev_langs: C++
helpviewer_keywords: C2010
ms.assetid: 5795ed1d-e206-410b-b7b4-528d125c67b4
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0863e96dfc137cf262fe1aef977c83dc592b798c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2010"></a>C2010 chyby kompilátoru
'znak': v seznamu formální parametr – makro  
  
 Znak, který je nesprávně použitá v seznamu formální parametr definici makra. Odeberte znak, který má opravte případné chyby.  
  
 Následující ukázka generuje C2010:  
  
```  
// C2010.cpp  
// compile with: /c  
#define mymacro(a|) (2*a)   // C2010  
#define mymacro(a) (2*a)   // OK  
```