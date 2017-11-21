---
title: "C2054 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2054
dev_langs: C++
helpviewer_keywords: C2054
ms.assetid: 37f7c612-0d7d-4728-9e67-ac4160555f48
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1ab12a8395f3587f0fbdca5ad821cd9ec2241d25
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2054"></a>C2054 chyby kompilátoru
Očekávaný ' (' podle "identifikátor"  
  
 Funkce identifikátor se používá v kontextu, který vyžaduje koncové uvozovky.  
  
 Tato chyba může být způsobeno vynechání na komplexní inicializace symbolem rovná se (=).  
  
 Následující ukázka generuje C2054:  
  
```  
// C2054.c  
int array1[] { 1, 2, 3 };   // C2054, missing =  
```  
  
 Možná řešení:  
  
```  
// C2054b.c  
int main() {  
   int array2[] = { 1, 2, 3 };  
}  
```