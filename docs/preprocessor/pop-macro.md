---
title: pop_macro | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.pop_macro
- pop_macro_CPP
dev_langs:
- C++
helpviewer_keywords:
- pop_macro pragma
- pragmas, pop_macro
ms.assetid: 3b5489d0-69ba-4c66-b572-2748af0f12bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf367a085b5e566a7783067aa7750eb5ecd343a3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072314"
---
# <a name="popmacro"></a>pop_macro
Nastaví hodnotu vlastnosti *macro_name* makra na hodnotu na vrcholu zásobníku tohoto makra.

## <a name="syntax"></a>Syntaxe

```
#pragma pop_macro("
macro_name
")
```

## <a name="remarks"></a>Poznámky

Nejprve musíte vydat [push_macro](../preprocessor/push-macro.md) pro *macro_name* předtím, než vám pomůžou **pop_macro**.

## <a name="example"></a>Příklad

```cpp
// pragma_directives_pop_macro.cpp
// compile with: /W1
#include <stdio.h>
#define X 1
#define Y 2

int main() {
   printf("%d",X);
   printf("\n%d",Y);
   #define Y 3   // C4005
   #pragma push_macro("Y")
   #pragma push_macro("X")
   printf("\n%d",X);
   #define X 2   // C4005
   printf("\n%d",X);
   #pragma pop_macro("X")
   printf("\n%d",X);
   #pragma pop_macro("Y")
   printf("\n%d",Y);
}
```

```Output
1
2
1
2
1
3
```

## <a name="see-also"></a>Viz také

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)