---
title: "C2842 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2842
dev_langs: C++
helpviewer_keywords: C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3998ff0b07ba78228ac51bccac047d8889ccf81b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
