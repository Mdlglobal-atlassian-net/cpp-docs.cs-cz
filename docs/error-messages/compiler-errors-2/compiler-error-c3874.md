---
title: "C3874 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3874
dev_langs: C++
helpviewer_keywords: C3874
ms.assetid: fd55fc05-69a7-4237-b3b7-dca1d5400b4f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cd30858e2118a7305583736c31b84ed56ab7095a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3874"></a>C3874 chyby kompilátoru
Návratový typ 'function' by měl být 'int"místo"typ"  
  
 Funkce nemá návratový typ, který byl očekáván kompilátorem.  
  
 Následující ukázka generuje C3874:  
  
```  
// C3874b.cpp  
double main()  
{   // C3874  
}  
```