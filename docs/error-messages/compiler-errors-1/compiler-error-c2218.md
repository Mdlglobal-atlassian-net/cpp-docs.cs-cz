---
title: Chyba kompilátoru C2218 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2218
dev_langs:
- C++
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52c449381c6e8a7391706ed6097bc38576bc69fe
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041282"
---
# <a name="compiler-error-c2218"></a>Chyba kompilátoru C2218

'__vectorcall' nelze použít s "/ arch: IA32.

`__vectorcall` Konvence volání je podporována pouze v nativním kódu x86 a x64 procesorů, které obsahují Streaming SIMD Extensions 2 (SSE2) a vyšší. Další informace najdete v tématu [__vectorcall](../../cpp/vectorcall.md).

Chcete-li vyřešit tuto chybu, změňte možnosti kompilátoru na cíl SSE2, AVX a AVX2 instrukční sadu. Další informace najdete v tématu [/arch (x86)](../../build/reference/arch-x86.md).