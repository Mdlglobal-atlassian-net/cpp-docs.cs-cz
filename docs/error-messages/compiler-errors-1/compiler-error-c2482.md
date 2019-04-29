---
title: Chyba kompilátoru C2482
ms.date: 09/15/2017
f1_keywords:
- C2482
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
ms.openlocfilehash: 481920fa2d8c32bc872e7b8805188cc674e6fe28
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375051"
---
# <a name="compiler-error-c2482"></a>Chyba kompilátoru C2482

>"*identifikátor*': dynamická inicializace není povolena v kódu spravované/WinRT data"vlákno"

## <a name="remarks"></a>Poznámky

Ve spravované nebo WinRT code, proměnné deklarované s použitím [__declspec(thread)](../../cpp/thread.md) atribut Modifikátor třídy úložiště nebo [thread_local](../../cpp/storage-classes-cpp.md#thread_local) specifikátor třídy úložiště se nedá inicializovat pomocí výrazu který vyžaduje vyhodnocení za běhu. Statický výraz je potřeba inicializovat `__declspec(thread)` nebo `thread_local` data v těchto prostředích modulu runtime.

## <a name="example"></a>Příklad

Následující ukázka generuje C2482 v managed (**/CLR**) a WinRT (**/ZW**) kódu:

```cpp
// C2482.cpp
// For managed example, compile with: cl /EHsc /c /clr C2482.cpp
// For WinRT example, compile with: cl /EHsc /c /ZW C2482.cpp
#define Thread __declspec( thread )
Thread int tls_i1 = tls_i1;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i2 = sizeof( tls_i2 );   // Okay in C and C++
```

Chcete-li tento problém vyřešit, inicializace úložiště thread-local se pomocí konstantu, **constexpr**, nebo statický výraz. Samostatně můžete udělat všechny inicializace specifické pro vlákno.