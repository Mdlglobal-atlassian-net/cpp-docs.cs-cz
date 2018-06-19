---
title: C2482 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 09/15/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2482
dev_langs:
- C++
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3dd23069f389d0a02e10d26edb7ee4fd3c373cb
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34256003"
---
# <a name="compiler-error-c2482"></a>C2482 chyby kompilátoru

>'*identifikátor*': dynamické inicializaci není povoleno v kódu spravované nebo WinRT dat 'přístup z více vláken.

## <a name="remarks"></a>Poznámky

Ve spravované nebo WinRT code, proměnných deklarovaných pomocí [__declspec(thread)](../../cpp/thread.md) atribut Modifikátor třídy úložiště nebo [thread_local](../../cpp/storage-classes-cpp.md#thread_local) specifikátor třídy úložiště nemůže být inicializovaný s výrazem který vyžaduje testování za běhu. Statický výraz se vyžaduje k chybě při inicializaci `__declspec(thread)` nebo `thread_local` data v těchto prostředích modulu runtime.

## <a name="example"></a>Příklad

Následující ukázka generuje C2482 spravovat (**/CLR**) a v WinRT (**/ZW**) kódu:

```cpp
// C2482.cpp
// For managed example, compile with: cl /EHsc /c /clr C2482.cpp
// For WinRT example, compile with: cl /EHsc /c /ZW C2482.cpp
#define Thread __declspec( thread )
Thread int tls_i1 = tls_i1;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i2 = sizeof( tls_i2 );   // Okay in C and C++
```

Chcete-li tento problém vyřešit, inicializace úložiště thread-local pomocí konstantu, **constexpr**, nebo statické výraz. Proveďte všechny inicializace specifické pro vlákno samostatně.