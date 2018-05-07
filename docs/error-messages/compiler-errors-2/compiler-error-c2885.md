---
title: C2885 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2885
dev_langs:
- C++
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f37ea0f9fadb74b44eea5ad110f7f12b884f0e41
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2885"></a>C2885 chyby kompilátoru
'class::identifier': není platný pomocí deklaraci v rozsahu – třída  
  
 Můžete použít [pomocí](../../cpp/using-declaration.md) deklarace nesprávně.  
  
## <a name="example"></a>Příklad  
 Tato chyba může vygenerovaného jako výsledek kompilátoru shoda práci, kterou bylo provedeno pro Visual C++ 2005: je již neplatný tak, aby měl `using` deklarace typu vnořené; musí explicitně kvalifikaci každý odkaz provedete vnořené typy, chápat název typu místo, nebo vytvořit definici typu.  
  
 Následující ukázka generuje C2885.  
  
```  
// C2885.cpp  
namespace MyNamespace {  
   class X1 {};  
}  
  
struct MyStruct {  
   struct X1 {  
      int i;  
   };  
};  
  
int main () {  
   using MyStruct::X1;   // C2885  
  
   // OK  
   using MyNamespace::X1;  
   X1 myX1;  
  
   MyStruct::X1 X12;  
  
   typedef MyStruct::X1 abc;  
   abc X13;  
   X13.i = 9;  
}  
```  
  
## <a name="example"></a>Příklad  
 Pokud použijete `using` – klíčové slovo s člena třídy C++ vyžaduje definování tohoto člena uvnitř jiné třídy (třídy odvozené).  
  
 Následující ukázka generuje C2885.  
  
```  
// C2885_b.cpp  
// compile with: /c  
class A {  
public:  
   int i;  
};  
  
void z() {  
   using A::i;   // C2885 not in a class  
}  
  
class B : public A {  
public:  
   using A::i;  
};  
```