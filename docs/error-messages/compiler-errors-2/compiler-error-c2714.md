---
title: "C2714 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2714
dev_langs: C++
helpviewer_keywords: C2714
ms.assetid: 401a5a42-660c-4bad-9d63-1a2d092bc489
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1f0fc4847cc6f3ab50f840b1ed5a097cc405cff8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2714"></a>C2714 chyby kompilátoru
__alignof(void) není povolen.  
  
 Byla předána neplatná hodnota pro operátor.  
  
 V tématu [__alignof – operátor](../../cpp/alignof-operator.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2714.  
  
```  
// C2714.cpp  
int main() {  
   return __alignof(void);   // C2714  
   return __alignof(char);   // OK  
}  
```