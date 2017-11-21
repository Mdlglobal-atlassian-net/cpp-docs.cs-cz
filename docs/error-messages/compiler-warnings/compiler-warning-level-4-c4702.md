---
title: "Kompilátoru (úroveň 4) upozornění C4702 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4702
dev_langs: C++
helpviewer_keywords: C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ffb7dd376881b36bbf70b5e64f646aaf3f112552
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4702"></a>C4702 kompilátoru upozornění (úroveň 4)
Nedosažitelný kódu  
  
 Toto upozornění je výsledkem kompilátoru shoda práci, kterou bylo provedeno pro Visual Studio .NET 2003: nedosažitelný kód. Zjistí-li kompilátoru (back-end) nedostupný kódu, vygeneruje C4702, úroveň 4 upozornění.  
  
 Pro kód, který je platný v sadě Visual Studio .NET 2003 i sady Visual Studio .NET verzí aplikace Visual C++ odeberte kód nedostupný, nebo zajistit, že všechny zdrojový kód je dosažitelná některé toku spouštění.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4702.  
  
```  
// C4702.cpp  
// compile with: /W4  
#include <stdio.h>  
  
int main() {  
   return 1;  
   printf_s("I won't print.\n");   // C4702 unreachable  
}  
```  
  
## <a name="example"></a>Příklad  
 Při kompilaci s **/GX**, **/EHc**, **/EHsc**, nebo **/EHac** a pomocí funkce extern C, kód se může stát nedostupný protože extern C funkce se předpokládá, že není throw, proto není dosažitelný blok catch.  Pokud si myslíte, že toto upozornění je neplatný, protože funkce můžete vyvolat, kompilovat s **/EHa** nebo **/EHs**podle toho, že došlo k výjimce.  
  
 Další informace najdete v tématu [/EH (Model zpracování výjimek)](../../build/reference/eh-exception-handling-model.md) Další informace.  
  
 Následující ukázka generuje C4702.  
  
```  
// C4702b.cpp  
// compile with: /W4 /EHsc  
#include <iostream>  
  
using namespace std;  
extern "C" __declspec(dllexport) void Function2(){}  
  
int main() {  
   try {  
      Function2();  
   }  
   catch (...) {  
      cout << "Exp: Function2!" << endl;   // C4702  
   }  
}  
```