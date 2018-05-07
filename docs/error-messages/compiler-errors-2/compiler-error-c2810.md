---
title: C2810 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2810
dev_langs:
- C++
helpviewer_keywords:
- C2810
ms.assetid: f63e8f24-d7f6-42ac-904f-72ff49592ba6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a07beb36269e45388f43d4eb5cfafbd909ac6dd3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2810"></a>C2810 chyby kompilátoru
"rozhraní": rozhraní může dědit vlastnosti pouze z jiné rozhraní  
  
 [Rozhraní](../../cpp/interface.md) mohou dědit pouze z jiné rozhraní a nemusí dědí třídě nebo struktuře.  
  
 Následující ukázka generuje C2810:  
  
```  
// C2810.cpp  
#include <unknwn.h>  
class CBase1 {  
public:  
  HRESULT mf1();  
  int  m_i;  
};  
  
[object, uuid="40719E20-EF37-11D1-978D-0000F805D73B"]  
__interface IDerived : public CBase1 {  // C2810  
// try the following line instead  
// __interface IDerived {  
   HRESULT mf2(void *a);  
};  
  
struct CBase2 {  
   HRESULT mf1(int a, char *b);  
   HRESULT mf2();  
};  
```