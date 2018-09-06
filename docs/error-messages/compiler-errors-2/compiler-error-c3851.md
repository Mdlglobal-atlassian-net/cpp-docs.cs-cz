---
title: Chyba kompilátoru C3851 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3851
dev_langs:
- C++
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f495a61fd3c157862fe65d82c1ffe5f047d798dd
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43895172"
---
# <a name="compiler-error-c3851"></a>Chyba kompilátoru C3851

> "*char*': universal-character-name nemůže označovat znak v základní znakové sadě

## <a name="remarks"></a>Poznámky

V kódu zkompilovaném jako C++ nemůžete použít univerzální název znaku představující znak v základní zdrojové znakové sady mimo řetězcový nebo znakový literál. Další informace najdete v tématu [znakových sad](../../cpp/character-sets.md). V kódu zkompilovaném jako C, nemůžete použít univerzální název znaku pro znaky v rozsahu 0x20 – 0x7f, včetně, s výjimkou 0x24 ('$'), 0x40 ("\@"), nebo 0x60 ("\`").

## <a name="example"></a>Příklad

Následující ukázky generovat C3851 a ukazují, jak ho opravit:

```cpp
// C3851.cpp
int main()  
{
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set
   int test2_A = 0;        // OK
}
```