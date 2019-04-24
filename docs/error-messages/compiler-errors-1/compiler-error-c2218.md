---
title: Chyba kompilátoru C2218
ms.date: 11/04/2016
f1_keywords:
- C2218
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
ms.openlocfilehash: 5a9d897686fc915c9892fa2bcd51fa3ca3c8b05e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165668"
---
# <a name="compiler-error-c2218"></a>Chyba kompilátoru C2218

'__vectorcall' nelze použít s "/ arch: IA32.

`__vectorcall` Konvence volání je podporována pouze v nativním kódu x86 a x64 procesorů, které obsahují Streaming SIMD Extensions 2 (SSE2) a vyšší. Další informace najdete v tématu [__vectorcall](../../cpp/vectorcall.md).

Chcete-li vyřešit tuto chybu, změňte možnosti kompilátoru na cíl SSE2, AVX a AVX2 instrukční sadu. Další informace najdete v tématu [/arch (x86)](../../build/reference/arch-x86.md).