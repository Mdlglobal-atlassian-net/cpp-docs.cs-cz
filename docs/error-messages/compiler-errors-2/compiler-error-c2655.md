---
title: "C2655 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2655
dev_langs: C++
helpviewer_keywords: C2655
ms.assetid: beaefa6e-51b3-4df9-9150-960f3fbf40e0
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2d3c9199979d83c91e4c4d12dec648482c4999b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2655"></a>C2655 chyby kompilátoru
"identifikátor": definice nebo opětovná deklarace neplatný v aktuálním oboru  
  
 Identifikátor lze deklarovat pouze v globálním oboru.  
  
 Následující ukázka generuje C2655:  
  
```  
// C2655.cpp  
class A {};  
class B {  
public:  
   static int i;  
};  
  
int B::i;  // OK  
  
int main() {  
   A B::i;  // C2655  
}  
```