---
title: "Kompilátoru (úroveň 3) upozornění C4159 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4159
dev_langs: C++
helpviewer_keywords: C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1997fc9b210723c5747f67e3b042987043c5c161
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4159"></a>C4159 kompilátoru upozornění (úroveň 3)
\#Direktiva pragma pragma(pop,...): má odebrány dříve stisknutí identifikátor "identifikátor"  
  
 Obsahuje zdrojový kód **nabízené** následuje instrukce s identifikátorem pro pragma **pop** instrukce bez identifikátor. V důsledku toho ***identifikátor*** je odebrány a následné použití ***identifikátor*** může způsobit neočekávané chování.  
  
 Abyste se vyhnuli toto upozornění, zadejte identifikátor **pop** instrukcí. Příklad:  
  
```  
// C4159.cpp  
// compile with: /W3  
#pragma pack(push, f)  
#pragma pack(pop)   // C4159  
  
// using the identifier resolves the warning  
// #pragma pack(pop, f)  
  
int main()  
{  
}  
```