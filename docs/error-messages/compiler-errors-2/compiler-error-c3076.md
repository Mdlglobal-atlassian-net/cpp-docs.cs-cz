---
title: C3076 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3076
dev_langs:
- C++
helpviewer_keywords:
- C3076
ms.assetid: 8a87b3e4-2c17-4b87-9622-ef0962d6a34e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 465dd45c4ddfc41e3ba7a059619028711d6f73e2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33247576"
---
# <a name="compiler-error-c3076"></a>C3076 chyby kompilátoru
'instance': instance typu odkaz, "typ", nelze vložit v nativním typu  
  
 Nativní typ nemůže obsahovat instance typu CLR.  
  
 Další informace najdete v tématu [C++ – sémantika zásobníku pro odkazové typy](../../dotnet/cpp-stack-semantics-for-reference-types.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3076.  
  
```  
// C3076.cpp  
// compile with: /clr /c  
ref struct U {};  
  
struct V {  
   U y;   // C3076  
};  
  
ref struct W {  
   U y;   // OK  
};  
```