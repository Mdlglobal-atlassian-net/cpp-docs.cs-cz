---
title: Kompilátoru (úroveň 1) upozornění C4042 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4042
dev_langs:
- C++
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bcc4123c18eb9765841a5f6b54446cd064407700
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278382"
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