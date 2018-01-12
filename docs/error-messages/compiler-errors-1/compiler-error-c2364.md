---
title: "C2364 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2364
dev_langs: C++
helpviewer_keywords: C2364
ms.assetid: 4f550571-94b5-42ca-84cb-663fecbead44
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 10cfebe227cb1f774b9d1df19b4a7684497b1272
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2364"></a>C2364 chyby kompilátoru
'type': Neplatný typ pro vlastní atribut  
  
 Pojmenované argumenty pro vlastní atributy jsou omezeny na zkompilovat čas konstanty. Například celočíselných typů (int, char atd.), System::Type ^ a System::Object ^.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2364.  
  
```  
// c2364.cpp  
// compile with: /clr /c  
using namespace System;  
  
[attribute(AttributeTargets::All)]  
public ref struct ABC {  
public:  
   // Delete the following line to resolve.  
   ABC( Enum^ ) {}   // C2364  
   ABC( int ) {}   // OK  
};  
```