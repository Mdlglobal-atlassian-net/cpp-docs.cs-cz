---
title: "C2144 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2144
dev_langs: C++
helpviewer_keywords: C2144
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0f541465009dcc137b8853351d10ceb9d5db4d05
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2144"></a>C2144 chyby kompilátoru
Chyba syntaxe: 'type' musí předcházet (token)  
  
 Kompilátor očekává `token` a najít `type` místo.  
  
 Tato chyba může být způsobeno chybí pravé složené závorce, pravé závorky nebo středníkem.  
  
 C2144 může dojít také při pokusu vytvořit od CLR klíčové slovo, které obsahuje prázdný znak.  
  
 C2144 také může zobrazit, pokud se pokoušíte předávání typů. V tématu [předávání typu (C + +/ CLI)](../../windows/type-forwarding-cpp-cli.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2144.  
  
```  
// C2144.cpp  
// compile with: /clr /c  
#define REF ref  
REF struct MyStruct0;   // C2144  
  
// OK  
#define REF1 ref struct  
REF1 MyStruct1;  
```  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2144.  
  
```  
// C2144_2.cpp  
// compile with: /clr /c  
ref struct X {  
  
   property double MultiDimProp[,,] {   // C2144  
   // try the following line instead  
   // property double MultiDimProp[int , int, int] {  
      double get(int, int, int) { return 1; }  
      void set(int i, int j, int k, double l) {}  
   }  
  
   property double MultiDimProp2[] {   // C2144  
   // try the following line instead  
   // property double MultiDimProp2[int] {  
      double get(int) { return 1; }  
      void set(int i, double l) {}  
   }  
};  
```