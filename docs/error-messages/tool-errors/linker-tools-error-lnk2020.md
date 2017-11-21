---
title: "Chyba linkerů Lnk2020 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2020
dev_langs: C++
helpviewer_keywords: LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d9a4bedb06ccad45a105c0e47fbc1f839891bea7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk2020"></a>Chyba linkerů LNK2020
nerozpoznané token (token)  
  
 Podobně jako u chybu nedefinované externí, s tím rozdílem, že je odkaz prostřednictvím metadat. V metadatech musí být definovány veškerá data a funkce.  
  
 Chcete-li vyřešit:  
  
-   Definování chybějící funkce nebo data, nebo  
  
-   Patří k objektu souboru nebo knihovny, ve kterém je již definován chybějící funkce nebo data.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje LNK2020.  
  
```  
// LNK2020.cpp  
// compile with: /clr /LD  
ref struct A {  
   A(int x);   // LNK2020  
   static int f();   // LNK2020  
};  
  
// OK  
ref struct B {  
   B(int x) {}  
   static int f() { return 0; }  
};  
```  
  
## <a name="example"></a>Příklad  
 LNK2020 bude také nastat, pokud jste vytvoření proměnné spravované šablony typu, ale není také vytvořit instanci typu.  
  
 Následující ukázka generuje LNK2020.  
  
```  
// LNK2020_b.cpp  
// compile with: /clr   
  
template <typename T>  
ref struct Base {  
   virtual void f1() {};  
};  
  
template <typename T>  
ref struct Base2 {  
   virtual void f1() {};  
};  
  
int main() {  
   Base<int>^ p;   // LNK2020  
   Base2<int>^ p2 = gcnew Base2<int>();   // OK  
};  
```