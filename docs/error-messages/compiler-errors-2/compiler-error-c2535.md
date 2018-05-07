---
title: C2535 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2535
dev_langs:
- C++
helpviewer_keywords:
- C2535
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1dc791cd7782cc758aa51b0c61d87a79570c13c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2535"></a>C2535 chyby kompilátoru
'identifikátor': členská funkce je již definována nebo deklarována  
  
 Tato chyba může být způsobena použitím stejného seznamu formálních parametrů ve více než jedné definici nebo deklaraci přetížené funkce.  
  
 Pokud se kvůli uvolnění funkce C2535, najdete v části [destruktory a finalizační metody](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) Další informace.  
  
 Pokud kompilujete projekt knihovny ATL, další informace naleznete v článku Q241852 znalostní báze.  
  
 Následující ukázka generuje C2535:  
  
```  
// C2535.cpp  
// compile with: /c  
class C {  
public:  
   void func();   // forward declaration  
   void func() {}   // C2535  
};  
```