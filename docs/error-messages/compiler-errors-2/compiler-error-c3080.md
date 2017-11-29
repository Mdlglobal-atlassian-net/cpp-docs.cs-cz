---
title: "C3080 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3080
dev_langs: C++
helpviewer_keywords: C3080
ms.assetid: ff62a3f7-9b3b-44bd-b8d9-f3a8e5354560
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fe5dd1e5c3609ed88c0083fa5d5b6cc7f4207567
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3080"></a>C3080 chyby kompilátoru
'finalizer_function': finalizační metody nemůže mít – specifikátor třídy úložiště-  
  
 Další informace najdete v tématu [destruktory a finalizační metody v postupy: definování a používání tříd a struktur (C + +/ CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3080.  
  
```  
// C3080.cpp  
// compile with: /clr /c  
ref struct rs {  
protected:  
   static !rs(){}   // C3080  
   !rs(){}   // OK  
};  
```