---
title: Kompilátoru (úroveň 4) upozornění C4268 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4268
dev_langs:
- C++
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bef62649af39df950c3966ef93dddb6c71ec2fd6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293361"
---
# <a name="compiler-warning-level-4-c4268"></a>C4268 kompilátoru upozornění (úroveň 4)
"identifikátor": 'const' statické nebo globálních dat inicializován s kompilátoru generované výchozí konstruktor doplní objekt s nulami  
  
 A **const** globální nebo statická instance netriviální třídy je inicializován s generované kompilátorem výchozí konstruktor.  
  
## <a name="example"></a>Příklad  
  
```  
// C4268.cpp  
// compile with: /c /LD /W4  
class X {  
public:  
   int m_data;  
};  
  
const X x1;   // C4268  
```  
  
 Protože je tato instance třídy **const**, hodnota `m_data` nelze změnit.