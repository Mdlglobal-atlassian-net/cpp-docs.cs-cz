---
title: "C2117 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2117
dev_langs: C++
helpviewer_keywords: C2117
ms.assetid: b947379d-5861-42fc-ac26-170318579cbd
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3e326e7a7dde296439d1a9c24c1d042af63dc6f9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2117"></a>C2117 chyby kompilátoru
"identifikátor": pole hranice přetečení  
  
 Pole má příliš mnoho inicializátory:  
  
-   Inicializátory elementů polí a neodpovídají velikost a množství.  
  
-   Žádné místo pro hodnotu null. ukončovací znak v řetězci.  
  
 Následující ukázka generuje C2117:  
  
```  
// C2117.cpp  
int main() {  
   char abc[4] = "abcd";   // C2117  
   char def[4] = "abd";   // OK  
}  
```