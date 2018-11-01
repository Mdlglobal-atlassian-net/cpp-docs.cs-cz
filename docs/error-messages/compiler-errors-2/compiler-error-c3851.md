---
title: Chyba kompilátoru C3851
ms.date: 09/05/2018
f1_keywords:
- C3851
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
ms.openlocfilehash: 52c4f3a393ffaf2b61a65c8e2e0dcc8efac08288
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502996"
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