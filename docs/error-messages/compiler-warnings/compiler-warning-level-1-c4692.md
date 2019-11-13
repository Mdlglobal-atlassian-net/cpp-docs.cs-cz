---
title: Upozornění kompilátoru (úroveň 1) C4692
ms.date: 11/04/2016
f1_keywords:
- C4692
helpviewer_keywords:
- C4692
ms.assetid: f6fb3acc-8228-491a-9c30-ce302d8a9c75
ms.openlocfilehash: e7ec657956c72f1e321227d54b796164292f0c0e
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052497"
---
# <a name="compiler-warning-level-1-c4692"></a>Upozornění kompilátoru (úroveň 1) C4692

'function': podpis nesoukromého členu obsahuje sestavení privátního nativního typu 'native_type'

Typ, který je viditelný mimo sestavení, obsahuje členskou funkci, jejíž signatura obsahuje nativní typ, který není viditelný vně sestavení. Proto by nemělo být volána členská funkce, je-li její nadřazený typ vytvořena mimo sestavení.

Další informace najdete v tématu [viditelnost typů](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility).

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4692.

```cpp
// C4692.cpp
// compile with: /W1 /c /clr
#pragma warning(default:4692)
class Private_Native_Class {};
public class Public_Native_Class {};
public ref class Public_Ref_Class {
public:
   void Test(Private_Native_Class *) {}   // C4692
   void Test2(Public_Native_Class *) {}   // OK
};
```