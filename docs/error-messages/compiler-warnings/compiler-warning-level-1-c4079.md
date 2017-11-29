---
title: "Kompilátoru (úroveň 1) upozornění C4079 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4079
dev_langs: C++
helpviewer_keywords: C4079
ms.assetid: 549759f0-e168-47e9-8c9a-de93ac843689
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 548d8f801c39580b0f0ea4a0b945eb86b54f29d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4079"></a>C4079 kompilátoru upozornění (úroveň 1)
Neočekávaný token "token"  
  
 V seznamu argument – Direktiva pragma dojde k tokenu neočekávané oddělovače. Zbývající část – Direktiva pragma byl ignorován.  
  
 Následující ukázka generuje C4079:  
  
```  
// C4079.cpp  
// compile with: /W1  
#pragma warning(disable : 4081)  
#pragma pack(c,16)   // C4079  
  
int main() {  
}  
```