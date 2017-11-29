---
title: "C3421 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3421
dev_langs: C++
helpviewer_keywords: C3421
ms.assetid: b52050c6-17a4-424a-8894-337b0cec7010
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c70d062f90410f6af170af45e8213c65777d3977
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3421"></a>C3421 chyby kompilátoru
'type': finalizační metodu nelze volat pro tuto třídu, jako je buď nedostupné nebo neexistuje  
  
 Finalizační metody je implicitně soukromé, takže ji nelze volat z mimo jeho nadřazených typů.  
  
 Další informace najdete v tématu [destruktory a finalizační metody v postupy: definování a používání tříd a struktur (C + +/ CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3421.  
  
```  
// C3421.cpp  
// compile with: /clr  
ref class A {};  
  
ref class B {   
   !B() {}  
  
public:  
   ~B() {}  
};  
  
int main() {  
   A a;  
   a.!A();   // C3421  
  
   B b;  
   b.!B();   // C3421  
}  
```