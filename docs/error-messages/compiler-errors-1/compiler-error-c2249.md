---
title: "C2249 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2249
dev_langs: C++
helpviewer_keywords: C2249
ms.assetid: bdd6697c-e04b-49b9-8e40-d9eb6d74f2b6
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7ea314dbf34881a86faa862c6c6543bcee5f49e3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2249"></a>C2249 chyby kompilátoru
"člen": žádné a přístupnou cestu pro přístup člena deklarovaného v virtuální základní 'class'.  
  
 `member` Je zděděn z nonpublic `virtual` základní třídu nebo strukturu.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2249.  
  
```  
// C2249.cpp  
class A {  
private:  
   void privFunc( void ) {};  
public:  
   void pubFunc( void ) {};  
};  
  
class B : virtual public A {} b;  
  
int main() {  
   b.privFunc();    // C2249, private member of A  
   b.pubFunc();    // OK  
}  
```  
  
## <a name="example"></a>Příklad  
 C2249 může také dojít, pokud se pokusíte přiřadit datového proudu ze standardní knihovny C++ do jiného datového proudu.  Následující ukázka generuje C2249.  
  
```  
// C2249_2.cpp  
#include <iostream>  
using namespace std;  
int main() {  
   cout = cerr;   // C2249  
   #define cout cerr;   // OK  
}  
```