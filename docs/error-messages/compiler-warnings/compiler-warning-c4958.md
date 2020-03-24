---
title: Upozornění kompilátoru C4958
ms.date: 11/04/2016
f1_keywords:
- C4958
helpviewer_keywords:
- C4958
ms.assetid: e79b9e9c-d572-4a3a-a3b6-60962b70864a
ms.openlocfilehash: 63371d91367902c1eab539cb370e55440fcbf917
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164882"
---
# <a name="compiler-warning-c4958"></a>Upozornění kompilátoru C4958

> '*Operation*': aritmetický ukazatel nelze ověřit

## <a name="remarks"></a>Poznámky

Použití aritmetického ukazatele vytvoří neověřitelný obrázek.

Další informace najdete v tématu [čistý a ověřitelný kódC++(/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Možnost **/clr: Safe** je v aplikaci visual Studio 2015 zastaralá a nepodporovaná ve visual studiu 2017.

Toto upozornění je vystaveno jako chyba a může být zakázáno pomocí direktivy pragma [Warning](../../preprocessor/warning.md) nebo [/WD](../../build/reference/compiler-option-warning-level.md) kompilátoru.

## <a name="example"></a>Příklad

Následující ukázka generuje C4958:

```cpp
// C4958.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4958 )
using namespace System;

int main( ) {
   Int32 arr[] = new Int32[10];
   Int32* p = &arr[0];
   p++;   // C4958
}
```

Kompilátor implementuje operace pole s aritmetickým ukazatelem. Proto nativní pole nelze ověřit; místo toho použijte pole CLR. Další informace naleznete v tématu [Array](../../extensions/arrays-cpp-component-extensions.md).

Následující ukázka generuje C4958:

```cpp
// C4958b.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4958 )

int main() {
   int array[5];
   array[4] = 0;   // C4958
}
```
