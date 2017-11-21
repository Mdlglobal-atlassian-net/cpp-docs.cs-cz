---
title: "C2120 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2120
dev_langs: C++
helpviewer_keywords: C2120
ms.assetid: b0f3f66c-6cd2-4f48-9ea3-c270b53c2b8c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 845740c871d13b62dfa91313c136c5f0331deb9c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2120"></a>C2120 chyby kompilátoru
void neplatná ve všech typech  
  
 `void` Typ se používá v deklaraci s jiným typem.  
  
 Následující ukázka generuje C2120:  
  
```  
// C2120.cpp  
int main() {  
   void int i;   // C2120  
   int j;   // OK  
}  
```