---
title: "C3824 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3824
dev_langs: C++
helpviewer_keywords: C3824
ms.assetid: b6c6adf1-0a29-401c-a06e-616fd50d4c37
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e18e20cb1ffbe6d06060b3001c48f01b8b8b8cbf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3824"></a>C3824 chyby kompilátoru
"člen": Tento typ se nemůže vyskytovat v tomto kontextu (parametr funkce, návratový typ nebo je statický člen)  
  
 Přídavných ukazatelů nemůže být funkce parametry, návratové typy nebo deklarovaný `static`.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3824:  
  
```  
// C3824a.cpp  
// compile with: /clr /c  
void func() {  
   static pin_ptr<int> a; // C3824  
   pin_ptr<int> b; // OK  
}  
```  
