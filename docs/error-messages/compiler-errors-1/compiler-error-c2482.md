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
ms.openlocfilehash: f2c4725dd357854db504272e5b8b9d88641b143d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2482"></a>C2482 chyby kompilátoru

>'*identifikátor*': dynamické inicializace dat 'přístup z více vláken, není povoleno

Tato chybová zpráva je v sadě Visual Studio 2015 a novější verze zastaralé. V předchozích verzích proměnné deklarovány s použitím `thread` atribut nemůže být inicializovaný s výraz, který vyžaduje testování spuštění. Statický výraz se vyžaduje k chybě při inicializaci `thread` data.

## <a name="example"></a>Příklad

Následující ukázka generuje C2482 v sadě Visual Studio 2013 a dříve:

```cpp
// C2482.cpp
// compile with: /c
#define Thread __declspec( thread )
Thread int tls_i = tls_i;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
```
