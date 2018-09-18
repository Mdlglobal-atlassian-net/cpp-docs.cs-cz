---
title: Chyba kompilátoru C3198 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3198
dev_langs:
- C++
helpviewer_keywords:
- C3198
ms.assetid: ec4ecf61-0067-4aa4-b443-a91013a1e59d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbb91d6f7b3ef6b8204a5f8bfb753db98ab6f93d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023381"
---
# <a name="compiler-error-c3198"></a>Chyba kompilátoru C3198

Neplatné použití direktiv pragma s plovoucí desetinnou čárkou: Direktiva pragma fenv_access funguje jedině v režimu přesné

[fenv_access](../../preprocessor/fenv-access.md) – Direktiva pragma byl použit v rámci [/FP](../../build/reference/fp-specify-floating-point-behavior.md) nastavení jiné než **/FP: precise**.

Následující ukázka generuje C3198:

```
// C3198.cpp
// compile with: /fp:fast
#pragma fenv_access(on)   // C3198
```