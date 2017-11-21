---
title: "C2513 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2513
dev_langs: C++
helpviewer_keywords: C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7eb4e7c63821f449bf9677cb5fe03c448bbbc6ee
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2513"></a>C2513 chyby kompilátoru
'type': žádné proměnné deklarovány před '='  
  
 Specifikátor typu se zobrazí v deklaraci identifikátorem žádné proměnné.  
  
 Následující ukázka generuje C2513:  
  
```  
// C2513.cpp  
int main() {  
   int = 9;   // C2513  
   int i = 9;   // OK  
}  
```  
  
 Tato chyba může být také vygenerovaného jako výsledek kompilátoru shoda práci pro Visual Studio .NET 2003: Inicializace typedef, již není povoleno. Inicializace definice typu není povolena standardní a nyní vygeneruje Chyba kompilátoru.  
  
```  
// C2513b.cpp  
// compile with: /c  
typedef struct S {  
   int m_i;  
} S = { 1 };   // C2513  
// try the following line instead  
// } S;  
```  
  
 Alternativou by mohla být odstranit `typedef` k definování proměnné s agregační inicializátoru seznamu, ale to není doporučeno, protože vytvoří proměnné se stejným názvem jako typ a skrýt název typu.