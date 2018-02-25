---
title: _SCL_SECURE_NO_WARNINGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
dev_langs:
- C++
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 285e54a2eab4d116df81c3e10c597c6dbb6dd9cb
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS
Volání jedné z metod potenciálně nebezpečného ve standardní knihovně C++ bude mít za následek [upozornění kompilátoru (úroveň 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Chcete-li zakázat toto upozornění, definujte makro **_SCL_SECURE_NO_WARNINGS** ve vašem kódu:  
  
```  
#define _SCL_SECURE_NO_WARNINGS  
```  
  
## <a name="remarks"></a>Poznámky  
 Další způsoby, jak zakázat upozornění C4996 patří:  
  
-   Pomocí [/D (Definice preprocesoru)](../build/reference/d-preprocessor-definitions.md) – možnost kompilátoru:  
  
 ```  
    cl /D_SCL_SECURE_NO_WARNINGS [other compiler options] myfile.cpp  
```  
  
-   Pomocí [/w](../build/reference/compiler-option-warning-level.md) – možnost kompilátoru:  
  
 ```  
    cl /wd4996 [other compiler options] myfile.cpp  
```  
  
-   Pomocí [#pragma – upozornění](../preprocessor/warning.md) – direktiva:  
  
 ```  
 #pragma warning(disable:4996)  
```  
  
 Navíc můžete ručně změnit úroveň upozornění C4996 s **/w\<l >\< n>**  – možnost kompilátoru. Chcete-li například nastavit upozornění C4996 na úroveň 4:  
  
```  
cl /w44996 [other compiler options] myfile.cpp  
```  
  
 Další informace najdete v tématu [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, nebo jsme /wo, /Wv, wdn (úroveň upozornění)](../build/reference/compiler-option-warning-level.md).  
  
## <a name="see-also"></a>Viz také  
 [Bezpečné knihovny: standardní knihovna C++](../standard-library/safe-libraries-cpp-standard-library.md)

