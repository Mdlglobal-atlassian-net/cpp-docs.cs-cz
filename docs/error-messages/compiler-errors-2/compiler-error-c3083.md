---
title: "Kompilátoru C3083 chyba | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3083
dev_langs: C++
helpviewer_keywords: C3083
ms.assetid: 05ff791d-52bb-41eb-9511-3ef89d7f4710
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8aa8296d117105b91a66bc134a1510519c17deff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3083"></a>C3083 chyby kompilátoru
'function': symbol nalevo od '::' musí být typu  
  
 Funkce byla zavolána nesprávně.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3083.  
  
```  
// C3083.cpp  
// compile with: /c  
struct N {  
   ~N();  
};  
  
struct N1 {  
   ~N1();  
};  
  
N::N::~N() {}   // C3083  
N1::~N1() {}   // OK  
```