---
title: "Kompilátoru (úroveň 1) upozornění C4042 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4042
dev_langs: C++
helpviewer_keywords: C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3369b2786c552e408e8eedf8e6ed8bf73f272ff6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4042"></a>C4042 kompilátoru upozornění (úroveň 1)
"identifikátor": má chybný úložiště – třída  
  
 Zadané úložiště třídy nelze použít s identifikátorem v tomto kontextu. Kompilátor místo toho používá výchozí třídu úložiště:  
  
-   `extern`, pokud *identifikátor* je funkce.  
  
-   **Automatické**, pokud *identifikátor* je formální parametr nebo místní proměnné.  
  
-   Třídy žádné úložiště, pokud *identifikátor* je globální proměnné.  
  
 Toto upozornění může být způsobeno zadáním třídy úložiště než **zaregistrovat** v deklaraci parametrů.  
  
 Následující ukázka generuje C4042  
  
```  
// C4042.cpp  
// compile with: /W1 /LD  
int func2( __declspec( thread ) int tls_i )    // C4042  
// try the following line instead  
// int func2( int tls_i )  
{  
   return tls_i;  
}  
```