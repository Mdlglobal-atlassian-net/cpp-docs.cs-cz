---
title: "C2459 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2459
dev_langs: C++
helpviewer_keywords: C2459
ms.assetid: 81e29f4c-5b60-40fb-9557-1cdc630d77e8
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 702b7f29cf0fe8be51f073e66efe701824ab0793
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2459"></a>C2459 chyby kompilátoru
"identifikátor": je definovaný; Nelze přidat jako člena anonymní  
  
 Třída, struktura nebo sjednocení je předefinovat v jeho vlastní oboru členem anonymní sjednocení.  
  
 Následující ukázka generuje C2459:  
  
```  
// C2459.cpp  
// compile with: /c  
class C {  
   union { int C; };   // C2459  
   union { int D; };  
};  
```