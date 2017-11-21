---
title: "C2075 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2075
dev_langs: C++
helpviewer_keywords: C2075
ms.assetid: 8b1865d2-540b-4117-b982-e7a58a0b6cf7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3f71631369c1f12910e323fcbdeec6dd4a6a4ce8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2075"></a>C2075 chyby kompilátoru
"identifikátor": inicializace pole musí složené závorky  
  
 Neexistují žádné složené závorky kolem inicializátoru zadané pole.  
  
 Následující ukázka generuje C2075:  
  
```  
// C2075.c  
int main() {  
   int i[] = 1, 2, 3 };   // C2075  
}  
```  
  
 Možná řešení:  
  
```  
// C2075b.c  
int main() {  
   int j[] = { 1, 2, 3 };  
}  
```