---
title: "Kompilátoru (úroveň 1) upozornění C4229 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4229
dev_langs: C++
helpviewer_keywords: C4229
ms.assetid: aadfc83b-1e5f-4229-bd0a-9c10a5d13182
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: eba360a71493ab63c9fa38ebae7856af335b9671
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4229"></a>C4229 kompilátoru upozornění (úroveň 1)
použít anachronism: Modifikátory na data jsou ignorovány.  
  
 Pomocí modifikátoru Microsoft, jako třeba `__cdecl` u datových deklarace je zastaralé praxi.  
  
## <a name="example"></a>Příklad  
  
```  
// C4229.cpp  
// compile with: /W1 /LD  
int __cdecl counter;   // C4229 cdecl ignored  
```