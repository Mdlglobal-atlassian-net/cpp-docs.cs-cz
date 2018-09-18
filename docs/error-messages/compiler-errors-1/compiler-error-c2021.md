---
title: Chyba kompilátoru C2021 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2021
dev_langs:
- C++
helpviewer_keywords:
- C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31169c59ba9731d8eda52f22644294b8bb680bf2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101984"
---
# <a name="compiler-error-c2021"></a>Chyba kompilátoru C2021

očekávala se hodnota exponent, ne znak

Znak použitý jako exponent konstanty s plovoucí desetinnou čárkou není platné číslo. Nezapomeňte použít exponent, který je v dosahu.

## <a name="example"></a>Příklad

Následující ukázka generuje C2021:

```
// C2021.cpp
float test1=1.175494351E;   // C2021
```

## <a name="example"></a>Příklad

Možná řešení:

```
// C2021b.cpp
// compile with: /c
float test2=1.175494351E8;
```