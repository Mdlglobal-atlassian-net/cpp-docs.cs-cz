---
title: "Kompilátoru (úroveň 3) upozornění C4390 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4390
dev_langs: C++
helpviewer_keywords: C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8d042a9d89ca30be5971f31360f7958e9fb96cf2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4390"></a>C4390 kompilátoru upozornění (úroveň 3)
';': prázdný řízené příkaz nalezen; je to záměr?  
  
 Středník byl nalezen po příkazu ovládací prvek, který obsahuje žádné pokyny.  
  
 Pokud se z důvodu makra C4390, měli byste použít [upozornění](../../preprocessor/warning.md) – Direktiva pragma zakázat C4390 v modul, který obsahuje makro.  
  
 Následující ukázka generuje C4390:  
  
```  
// C4390.cpp  
// compile with: /W3  
int main() {  
   int i = 0;  
   if (i);   // C4390  
      i++;  
}  
```