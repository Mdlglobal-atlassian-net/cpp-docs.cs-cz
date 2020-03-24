---
title: Chyba kompilátoru C3851
ms.date: 09/05/2018
f1_keywords:
- C3851
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
ms.openlocfilehash: 97d9ef1eeeffa0e5a63d2c8ae2428a3fad0ff238
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165577"
---
# <a name="compiler-error-c3851"></a>Chyba kompilátoru C3851

> *char*: Universal-Character-Name nemůže určovat znak v základní znakové sadě.

## <a name="remarks"></a>Poznámky

V kódu kompilovaném C++jako nemůžete použít univerzální název znaku, který představuje znak v základní zdrojové znakové sadě mimo řetězec nebo znakový literál. Další informace naleznete v tématu [znakové sady](../../cpp/character-sets.md). V kódu kompilovaném jako C nemůžete použít univerzální název znaku pro znaky v rozsahu 0x20-0x7F, včetně, s výjimkou 0x24 ($), 0x40 ('\@') nebo 0x60 ('\`').

## <a name="example"></a>Příklad

Následující ukázky generují C3851 a ukazují, jak je opravit:

```cpp
// C3851.cpp
int main()
{
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set
   int test2_A = 0;        // OK
}
```
