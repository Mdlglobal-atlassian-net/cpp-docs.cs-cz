---
title: Upozornění kompilátoru (úroveň 1) C4376
ms.date: 11/04/2016
f1_keywords:
- C4376
helpviewer_keywords:
- C4376
ms.assetid: 5f202c74-9489-48fe-b36f-19cd882b1589
ms.openlocfilehash: 8009d2e5d09ad173f6150ebe9a907be9f4947cd7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162853"
---
# <a name="compiler-warning-level-1-c4376"></a>Upozornění kompilátoru (úroveň 1) C4376

specifikátor přístupu old_specifier: už není podporovaný: místo toho prosím použijte klíčové slovo new_specifier:.

Další informace o určení dostupnosti typu a člena v metadatech naleznete v tématu [viditelnost typů](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) a [viditelnost členů](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility) v tématu [How to: Define and spotřebovávají ClassesC++and Structs (/CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4376.

```cpp
// C4376.cpp
// compile with: /clr /W1 /c
public ref class G {
public public:   // C4376
   void m2();
};

public ref class H {
public:   // OK
   void m2();
};
```
