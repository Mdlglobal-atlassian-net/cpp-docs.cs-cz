---
title: Chyba kompilátoru C3353 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3353
dev_langs:
- C++
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63316a5a74c3981ec0f68d949eba654f8d6bbfef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110195"
---
# <a name="compiler-error-c3353"></a>Chyba kompilátoru C3353

'delegování': delegáta lze vytvořit pouze z globální funkce nebo členské funkce spravované nebo typ WinRT

Delegáty, deklarovaný pomocí [delegovat](../../windows/delegate-cpp-component-extensions.md) – klíčové slovo, lze deklarovat pouze v globálním oboru.

Následující ukázka generuje C3353:

```
// C3353.cpp
// compile with: /clr
delegate int f;   // C3353
```