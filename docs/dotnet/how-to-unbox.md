---
title: 'Postupy: rozbalení'
ms.date: 11/04/2016
helpviewer_keywords:
- unboxing
ms.assetid: 75794696-9275-47bf-9a7d-5abe6585ab91
ms.openlocfilehash: ae80497a24b090bc5866b3cfb22748b20adda223
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747940"
---
# <a name="how-to-unbox"></a>Postupy: rozbalení

Předvádí postup při rozbalení a třeba hodnotu změnit.

## <a name="example"></a>Příklad

```
// vcmcppv2_unboxing.cpp
// compile with: /clr
using namespace System;

int main() {
   int ^ i = gcnew int(13);
   int j;
   Console::WriteLine(*i);   // unboxing
   *i = 14;   // unboxing and assignment
   Console::WriteLine(*i);
   j = safe_cast<int>(i);   // unboxing and assignment
   Console::WriteLine(j);
}
```

```Output
13
14
14
```

## <a name="see-also"></a>Viz také:

[Zabalení](../windows/boxing-cpp-component-extensions.md)
