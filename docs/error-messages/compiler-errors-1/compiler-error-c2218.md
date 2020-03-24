---
title: Chyba kompilátoru C2218
ms.date: 11/04/2016
f1_keywords:
- C2218
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
ms.openlocfilehash: db14c37992fc1e2dd409c653d622d3419fcae4f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206645"
---
# <a name="compiler-error-c2218"></a>Chyba kompilátoru C2218

' __vectorcall ' nelze použít s '/arch: IA32 '

Konvence volání `__vectorcall` je podporována pouze v nativním kódu u procesorů x86 a x64, které zahrnují Streaming SIMD Extensions 2 (SSE2) a vyšší. Další informace najdete v tématu [__vectorcall](../../cpp/vectorcall.md).

Chcete-li tuto chybu opravit, změňte možnosti kompilátoru na cílové sady instrukcí SSE2, AVX nebo AVX2. Další informace najdete v tématu [/arch (x86)](../../build/reference/arch-x86.md).
