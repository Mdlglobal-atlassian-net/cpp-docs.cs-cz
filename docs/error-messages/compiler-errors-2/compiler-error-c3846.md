---
title: "C3846 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3846
dev_langs: C++
helpviewer_keywords: C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ede4decb1a6dde5a85008c6e15f5f764224627e3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3846"></a>C3846 chyby kompilátoru
'symbol': nelze importovat symbol 'assembly2': jako 'symbol' již byla naimportována ze sestavení 'assembly1'  
  
 Symbol nelze importovat z odkazovaného sestavení, protože byly dříve importovány z odkazované sestavení.  
  
## <a name="example"></a>Příklad
Následující ukázka generuje C3846:  
  
```  
// C3846a.cpp  
// compile with: /LD /clr  
public ref struct G  
{  
};  
```  
  
 A pak zkompilovat toto:  
  
```  
// C3846b.cpp  
// compile with: /clr  
#using "c3846a.dll"  
#using "c3846a.obj"   // C3846  
  
int main()  
{  
}  
```  
