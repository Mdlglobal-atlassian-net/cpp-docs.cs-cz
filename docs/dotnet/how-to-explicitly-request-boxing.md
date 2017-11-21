---
title: "Postupy: explicitní žádost o zabalení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: boxing, explicitly requesting
ms.assetid: 1359e6e5-162d-4f5d-9b6a-1690d93df3ee
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c3221075341c188639de6007052d06d2609ab836
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-explicitly-request-boxing"></a>Postupy: Explicitní žádost o zabalení
Můžete explicitní žádost o zabalení přiřazením proměnné proměnné typu `Object`.  
  
## <a name="example"></a>Příklad  
  
```  
// vcmcppv2_explicit_boxing3.cpp  
// compile with: /clr  
using namespace System;  
  
void f(int i) {  
   Console::WriteLine("f(int i)");  
}  
  
void f(Object ^o) {  
   Console::WriteLine("f(Object^ o)");  
}  
  
int main() {  
   int i = 5;  
   Object ^ O = i;   // forces i to be boxed  
   f(i);  
   f(O);  
   f( (Object^)i );  // boxes i  
}  
```  
  
```Output  
f(int i)  
f(Object^ o)  
f(Object^ o)  
```  
  
## <a name="see-also"></a>Viz také  
 [Zabalení](../windows/boxing-cpp-component-extensions.md)