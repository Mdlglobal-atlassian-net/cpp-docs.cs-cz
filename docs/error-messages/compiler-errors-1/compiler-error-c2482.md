---
title: Chyba kompilátoru C2482
ms.date: 09/15/2017
f1_keywords:
- C2482
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
ms.openlocfilehash: 5afa81369b2cf329baae02bc1309587015946409
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205150"
---
# <a name="compiler-error-c2482"></a>Chyba kompilátoru C2482

>'*Identifier*': Dynamická inicializace dat vlákna není ve spravovaném/WinRT kódu povolena

## <a name="remarks"></a>Poznámky

V spravovaném nebo WinRTovém kódu proměnné deklarované pomocí atributu modifikátoru třídy úložiště [__declspec (thread)](../../cpp/thread.md) nebo specifikátoru třídy úložiště [thread_local](../../cpp/storage-classes-cpp.md#thread_local) nelze inicializovat pomocí výrazu, který vyžaduje vyhodnocení za běhu. Pro inicializaci `__declspec(thread)` nebo `thread_local` dat v těchto běhových prostředích je vyžadován statický výraz.

## <a name="example"></a>Příklad

Následující ukázka generuje C2482 ve spravovaném ( **/CLR**) a v WinRT ( **/ZW**) kódu:

```cpp
// C2482.cpp
// For managed example, compile with: cl /EHsc /c /clr C2482.cpp
// For WinRT example, compile with: cl /EHsc /c /ZW C2482.cpp
#define Thread __declspec( thread )
Thread int tls_i1 = tls_i1;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i2 = sizeof( tls_i2 );   // Okay in C and C++
```

Chcete-li tento problém vyřešit, inicializujte místní úložiště vlákna pomocí konstanty, **constexpr**nebo statického výrazu. Proveďte samostatnou inicializaci specifickou pro vlákno.
