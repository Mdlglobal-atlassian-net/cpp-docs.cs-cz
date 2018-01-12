---
title: "C2787 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2787
dev_langs: C++
helpviewer_keywords: C2787
ms.assetid: 34cb57e6-cafe-4ce7-bcc6-53d194629bd0
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e53b6936a28ede1470683fd46fe9a8c29451ff00
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2787"></a>C2787 chyby kompilátoru
"identifikátor": žádný identifikátor GUID je přidružen k tomuto objektu  
  
 [__Uuidof –](../../cpp/uuidof-operator.md) operátor má uživatelsky definovaný typ. s identifikátorem GUID připojen nebo objekt takového typu uživatelem definované. K této chybě dojde, když argument je typu uživatelem definované s žádný identifikátor GUID.  
  
 Následující ukázka generuje C2787:  
  
```  
// C2787.cpp  
#include <windows.h>  
struct F {};  
  
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) F2;  
  
int main() {  
   __uuidof(F);   // C2787  
   __uuidof(F2);   // OK  
}  
```