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
ms.openlocfilehash: e6d0f6da9c3295aa6a8fad4bf5dfd8e725424739
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032475"
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