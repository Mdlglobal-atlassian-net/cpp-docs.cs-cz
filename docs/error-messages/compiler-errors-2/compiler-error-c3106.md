---
title: "C3106 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3106
dev_langs: C++
helpviewer_keywords: C3106
ms.assetid: 39d97a32-0905-4702-87d3-7f8ce473fb93
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 451c7dc0acc1d76e574ac64b9d40c2fae7ceb4ba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3106"></a>C3106 chyby kompilátoru
'atribut': nepojmenované argumenty musí předcházet pojmenované argumenty  
  
 Nepojmenované argumenty musí být předán do atribut před pojmenované argumenty.  
  
 Další informace najdete v tématu [uživatelem definované atributy](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3106.  
  
```  
// C3106.cpp  
// compile with: /c  
[module(name="MyLib", dll)];   // C3106  
[module(dll, name="MyLib")];   // OK  
```