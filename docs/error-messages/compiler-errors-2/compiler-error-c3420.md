---
title: C3420 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3420
dev_langs:
- C++
helpviewer_keywords:
- C3420
ms.assetid: 99b53c77-f36b-4574-9199-b53111becccb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d7614d07cf98ae9fe857809bf9400d36a48ab0b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3420"></a>C3420 chyby kompilátoru
'finalizační metodu': finalizační metody nemůže být virtuální  
  
 Finalizační metody lze volat pouze jiný prakticky z jeho nadřazených typů. Proto je chyba virtuální finalizační metodu deklarovat.  
  
 Další informace najdete v tématu [destruktory a finalizační metody v postupy: definování a používání tříd a struktur (C + +/ CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3420.  
  
```  
// C3420.cpp  
// compile with: /clr /c  
ref class R {  
   virtual !R() {}   // C3420  
};  
```