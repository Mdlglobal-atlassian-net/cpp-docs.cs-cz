---
title: "C3656 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3656
dev_langs: C++
helpviewer_keywords: C3656
ms.assetid: 88965d85-73b0-4b35-8020-0650c9c94cd8
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: eb7e725152192ebecdc00e81208e0864ae35ff6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3656"></a>C3656 chyby kompilátoru
'přepsání': přepsání specifikátor nelze opakovat.  
  
 Přepsání explicit – klíčové slovo lze zadat pouze jednou. Další informace najdete v tématu [explicitní přepsání](../../windows/explicit-overrides-cpp-component-extensions.md).  
  
 Následující ukázka generuje C3656:  
  
```  
// C3656.cpp  
// compile with: /clr /c  
public interface struct O {  
   int f();  
};  
  
public ref struct V : O {  
   int f() override override { return 0; }   // C3656  
   // try the following line instead  
   // int f() override { return 0; }  
};  
```