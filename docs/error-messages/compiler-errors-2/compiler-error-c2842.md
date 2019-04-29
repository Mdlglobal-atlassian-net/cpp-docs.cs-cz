---
title: Chyba kompilátoru C2842
ms.date: 11/04/2016
f1_keywords:
- C2842
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
ms.openlocfilehash: 99b2c86d1e914c9425c2664d4e858bba6cb99486
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62382941"
---
# <a name="compiler-error-c2842"></a>Chyba kompilátoru C2842

> "*třídy*': spravovaný typ WinRT nesmí definovat vlastní 'operator new' nebo 'operátor delete.

## <a name="remarks"></a>Poznámky

Můžete definovat vlastní **operátor new** nebo **operátor delete** Správa přidělování paměti na nativní haldě. Ale referenční třídy nelze definovat tyto operátory, protože jsou přiděleny pouze na spravované haldě.

Další informace najdete v tématu [uživatelem definované operátory (C++vyhodnocovací)](../../dotnet/user-defined-operators-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C2842.

```cpp
// C2842.cpp
// compile with: /clr /c
ref class G {
   void* operator new( size_t nSize );   // C2842
};
```
