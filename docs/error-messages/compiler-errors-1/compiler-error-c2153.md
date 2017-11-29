---
title: "C2153 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2153
dev_langs: C++
helpviewer_keywords: C2153
ms.assetid: cfc50cb7-9a0f-4b5b-879a-d419c99f7be1
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a1370e665708db783cf030c226de9de32c6c6b3f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2153"></a>C2153 chyby kompilátoru
šestnáctkových konstanty musí mít alespoň jeden číslice v hexadecimálním formátu  
  
 Hexadecimální konstanty 0 x 0 X a \x nejsou platné. Alespoň jedna číslice v hexadecimálním formátu postupujte x nebo X.  
  
 Následující ukázka generuje C2153:  
  
```  
// C2153.cpp  
int main() {  
   int a= 0x;    // C2153  
   int b= 0xA;   // OK  
}  
```