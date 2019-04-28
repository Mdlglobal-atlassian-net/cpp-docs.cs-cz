---
title: Compiler Error C2441
ms.date: 11/04/2016
f1_keywords:
- C2441
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
ms.openlocfilehash: 7fcf333f62253eb676c0f0ada1c927ab962ae1ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338919"
---
# <a name="compiler-error-c2441"></a>Compiler Error C2441

> "*proměnnou*': symbol deklarovaný s: __declspec(process), musí být const v/CLR: pure režimu

## <a name="remarks"></a>Poznámky

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

Ve výchozím nastavení, jsou proměnné pro doménu aplikace v rámci **/CLR: pure**. Proměnné označené `__declspec(process)` pod **/CLR: pure** jsou náchylné na chyby, pokud se změnil v jeden aplikační domény a číst v jiném.

Proto kompilátor vynucuje proces proměnné `const` pod **/CLR: pure**, provedení je číst pouze ve všech doménách aplikace.

Další informace najdete v tématu [procesu](../../cpp/process.md) a [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C2441.

```cpp
// C2441.cpp
// compile with: /clr:pure /c
__declspec(process) int i;   // C2441
__declspec(process) const int j = 0;   // OK
```