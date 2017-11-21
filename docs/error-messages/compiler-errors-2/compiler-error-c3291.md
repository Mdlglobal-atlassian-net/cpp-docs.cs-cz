---
title: "C3291 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3291
dev_langs: C++
helpviewer_keywords: C3291
ms.assetid: ed2e9f89-8dbc-4387-bc26-cc955e840858
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: da6145b3a3aecd5f550a58c009020fb24280349e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3291"></a>C3291 chyby kompilátoru
"default": nemůže být název trivial vlastnosti  
  
 Trivial vlastnost nemůže mít název `default`. V tématu [vlastnost](../../windows/property-cpp-component-extensions.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3291.  
  
```  
// C3291.cpp  
// compile with: /clr /c  
ref struct C {  
   property System::String ^ default;   // C3291  
   property System::String ^ Default;   // OK  
};  
```