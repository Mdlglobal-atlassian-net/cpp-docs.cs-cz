---
title: Chyba kompilátoru C2842
ms.date: 11/04/2016
f1_keywords:
- C2842
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
ms.openlocfilehash: 2ec39768a88da049c6a31ca2a9de226e25479c99
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571467"
---
# <a name="compiler-error-c2842"></a>Chyba kompilátoru C2842

'class': spravovaný typ WinRT nesmí definovat vlastní 'operator new' nebo 'operátor delete.

Můžete definovat vlastní ** operátor new nebo **operátor delete** Správa přidělování paměti na nativní haldě. Ale referenční třídy nelze definovat tyto operátory, protože jsou přiděleny pouze na spravované haldě.

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
