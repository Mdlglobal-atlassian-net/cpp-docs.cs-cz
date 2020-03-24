---
title: Upozornění kompilátoru C4936
ms.date: 11/04/2016
f1_keywords:
- C4936
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
ms.openlocfilehash: c6d54cf8b6704eec2a9e6af890c5c80c67106995
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164999"
---
# <a name="compiler-warning-c4936"></a>Upozornění kompilátoru C4936

> Tento __declspec je podporován pouze při kompilaci s možností/CLR nebo/CLR: Pure.

## <a name="remarks"></a>Poznámky

Možnost **/clr: Pure** Compiler je v aplikaci visual Studio 2015 zastaralá a není podporovaná v rámci sady visual Studio 2017.

Byl použit modifikátor `__declspec`, ale tento modifikátor `__declspec` je platný pouze při kompilování s jednou z možností [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) .

Další informace naleznete v tématu [AppDomain](../../cpp/appdomain.md) a [Process](../../cpp/process.md).

C4936 se vždy vydá jako chyba.  C4936 můžete zakázat pomocí direktivy pragma [Warning](../../preprocessor/warning.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C4936:

```cpp
// C4936.cpp
// compile with: /c
// #pragma warning (disable : 4936)
__declspec(process) int i;   // C4936
__declspec(appdomain) int j;   // C4936
```
