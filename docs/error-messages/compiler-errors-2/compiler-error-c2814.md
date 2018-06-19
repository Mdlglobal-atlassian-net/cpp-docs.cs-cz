---
title: C2814 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2814
dev_langs:
- C++
helpviewer_keywords:
- C2814
ms.assetid: 7d165136-a08b-4497-a76d-60a21bb19404
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75215a0df53606c8807cc275e86616c1ae8c6b42
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33237148"
---
# <a name="compiler-error-c2814"></a>C2814 chyby kompilátoru
"člen": nativního typu nemůže být vnořena ve spravované nebo WinRT zadejte "typ"  
  
## <a name="example"></a>Příklad  
 Nativní typ nemůže být vnořena v typu CLR nebo WinRT. Následující ukázka generuje C2814 a ukazuje, jak ji odstranit.  
  
```  
// C2814.cpp  
// compile with: /clr /c  
ref class A {  
   class B {};   // C2814  
   ref class C {};   // OK  
};  
```  
