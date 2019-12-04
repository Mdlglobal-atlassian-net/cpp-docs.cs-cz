---
title: Závažná chyba C1197
ms.date: 11/04/2016
f1_keywords:
- C1197
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
ms.openlocfilehash: 7f698262c73f0b311a92a8940107b552430919bb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747238"
---
# <a name="fatal-error-c1197"></a>Závažná chyba C1197

nejde odkazovat na mscorlib. dll_1, protože program už odkazoval na mscorlib. dll_2.

Kompilátor se shoduje s verzí modulu CLR (Common Language Runtime).  Byl však proveden pokus o odkaz na verzi souboru společného jazykového modulu runtime z předchozí verze.

Chcete-li vyřešit tuto chybu, pouze referenční soubory z verze modulu CLR (Common Language Runtime), které byly dodávány s verzí vizuálu C++ , se kterou kompilujete.

## <a name="example"></a>Příklad

Následující ukázka generuje C1197:

```cpp
// C1197.cpp
// compile with: /clr /c
// processor: x86
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197
// try the following line instead
// #using "mscorlib.dll"
```
