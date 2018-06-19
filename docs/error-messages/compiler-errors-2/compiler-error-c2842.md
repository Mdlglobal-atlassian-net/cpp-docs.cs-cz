---
title: C2842 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2842
dev_langs:
- C++
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe0a95edfa484eb8606b914424e52483c4c1c52d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33245293"
---
# <a name="compiler-error-c2842"></a>C2842 chyby kompilátoru
'class': spravované WinRT typu nesmí definovat vlastní 'new – operátor' nebo 'operátor odstranit.  
  
 Můžete definovat vlastní ** new – operátor nebo **delete – operátor** ke správě přidělení paměti na nativní haldě. Referenční třídy však nelze definovat tyto operátory, protože jsou pouze přiděleny na spravovaná halda.  

  
 Další informace najdete v tématu [uživatelem definované operátory (C + +/ CLI)](../../dotnet/user-defined-operators-cpp-cli.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2842.  
  
```  
// C2842.cpp  
// compile with: /clr /c  
ref class G {  
   void* operator new( size_t nSize );   // C2842  
};  
```  
