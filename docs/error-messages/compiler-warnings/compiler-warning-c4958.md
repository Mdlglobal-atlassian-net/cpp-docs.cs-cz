---
title: Upozornění kompilátoru C4958
ms.date: 11/04/2016
f1_keywords:
- C4958
helpviewer_keywords:
- C4958
ms.assetid: e79b9e9c-d572-4a3a-a3b6-60962b70864a
ms.openlocfilehash: 96b73975f391493340dd01d85ad30a8c888b44c0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779346"
---
# <a name="compiler-warning-c4958"></a>Upozornění kompilátoru C4958

> "*operace*': není možné ověřit aritmetiku ukazatele

## <a name="remarks"></a>Poznámky

Použití aritmetické operace ukazatele vytvoří bitovou kopii nelze ověřit.

Další informace najdete v tématu [prázdná a ověřitelný kód (C++vyhodnocovací)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

**/CLR: safe** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

Toto upozornění je vyvoláno jako chyba a pomocí se dají zakázat [upozornění](../../preprocessor/warning.md) – Direktiva pragma nebo [/wd](../../build/reference/compiler-option-warning-level.md) – možnost kompilátoru.

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

Kompilátor implementuje operace pole s aritmetiku ukazatele. Proto nativní pole nejsou ověřitelný; Místo toho použijte pole CLR. Další informace najdete v tématu [pole](../../extensions/arrays-cpp-component-extensions.md).

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