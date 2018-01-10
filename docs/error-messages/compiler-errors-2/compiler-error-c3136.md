---
title: "C3136 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3136
dev_langs: C++
helpviewer_keywords: C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e2b4daa5076a04825cea6a96709f40716f3eaeff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3136"></a>C3136 chyby kompilátoru
"rozhraní": rozhraní modelu COM může dědit vlastnosti pouze z jiné rozhraní modelu COM, není 'rozhraní' rozhraní modelu COM  
  
 Rozhraní, u kterého jste se použít [rozhraní atribut](../../windows/interface-attributes.md) dědí z rozhraní, které není rozhraní modelu COM. Rozhraní modelu COM nakonec dědí z `IUnknown`. Žádné rozhraní sebou atribut rozhraní je rozhraní modelu COM.  
  
 Následující příklad generuje C3136:  
  
```  
// C3136.cpp  
#include "unknwn.h"  
  
__interface A   // C3136  
// try the following line instead  
// _interface A : IUnknown  
{  
   int a();  
};  
  
[object]  
__interface B : A  
{  
   int aa();  
};  
```