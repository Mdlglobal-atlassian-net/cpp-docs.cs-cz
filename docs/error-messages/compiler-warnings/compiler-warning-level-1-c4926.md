---
title: "Kompilátoru (úroveň 1) upozornění C4926 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4926
dev_langs: C++
helpviewer_keywords: C4926
ms.assetid: 5717fce0-146f-4ef2-bde0-e9a01c0922d1
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e5ae52162562fcd2ea16e693981b7b959a290e76
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4926"></a>C4926 kompilátoru upozornění (úroveň 1)
"identifikátor": symbol je již definován: atributy ignorovat  
  
 Byl nalezen deklaraci předat dál, ale s atributy konstrukce se stejným názvem již existuje. Atributy dopředného deklaraci se ignorují.  
  
 Následující ukázka generuje C4926:  
  
```  
// C4926.cpp  
// compile with: /W1  
[module(name="MyLib")];  
  
[coclass]  
struct a {  
};  
  
[coclass]  
struct a;   // C4926  
  
int main() {  
}  
```