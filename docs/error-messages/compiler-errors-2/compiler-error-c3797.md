---
title: C3797 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3797
dev_langs:
- C++
helpviewer_keywords:
- C3797
ms.assetid: ab27ff34-8c1d-4297-b004-9e39bd3a4f25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 231db7e59eab4e59b4b51d113db431fc484c5fb3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274141"
---
# <a name="compiler-error-c3797"></a>C3797 chyby kompilátoru
'přepsání': deklaraci události nemůže mít specifikátor override (musí být umístěny na metody přidat, odebrat nebo vyvolat události místo)  
  
 Nejde přepsat trivial událostí (událost bez explicitně definovaných přístupových metod) s jinou trivial událost. Přepsání událostí musí definovat své chování se přístupové funkce.  
  
 Další informace najdete v tématu [událostí](../../windows/event-cpp-component-extensions.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3797.  
  
```  
// C3797.cpp  
// compile with: /clr /c  
delegate void MyDel();  
  
ref class Class1 {  
public:  
   virtual event MyDel ^ E;  
};  
  
ref class Class2 : public Class1 {  
public:  
   virtual event MyDel ^ E override;   // C3797  
};  
  
// OK  
ref class Class3 : public Class1 {  
public:  
   virtual event MyDel ^ E {  
      void add(MyDel ^ d) override {}  
      void remove(MyDel ^ d) override {}  
   }  
};  
```