---
title: C2553 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2553
dev_langs:
- C++
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8cfb09f2701b418ab5570641a78c465ff72ed943
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33232531"
---
# <a name="compiler-error-c2553"></a>C2553 chyby kompilátoru
'base_function': přepisování virtuální funkce vrátí typ se liší od 'override_function.  
  
 Funkce v odvozené třídě pokusil přepsat virtuální funkce v základní třídě, ale funkce odvozené třídy neměl stejný návratový typ jako funkce základní třídy.  Podpis funkce přepsání musí odpovídat podpis funkce přepsání.  
  
 Následující ukázka generuje C2553:  
  
```  
// C2553.cpp  
// compile with: /clr /c  
ref struct C {  
   virtual void f();  
};  
  
ref struct D : C {  
   virtual int f() override ;   // C2553   
  
   // try the following line instead  
   // virtual void f() override;  
};  
```