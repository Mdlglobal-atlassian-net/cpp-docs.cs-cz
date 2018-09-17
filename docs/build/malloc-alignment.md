---
title: malloc – zarovnání | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a8d1d1b4-5122-456f-9a64-a50e105e55a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa6e2748691eeb8a11834bcf8e6962252be7ab3f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712059"
---
# <a name="malloc-alignment"></a>malloc – zarovnání

[malloc](../c-runtime-library/reference/malloc.md) je zaručeno, že vrací paměť, která je vhodně zarovnaný pro uložení libovolného objektu, který má základní zarovnání a který může podle množství paměti, která je přidělena. A *základní zarovnání* je zarovnání menší než nebo rovno největšímu zarovnání, které je podporováno implementací bez specifikace zarovnání. (V jazyce Visual C++, je toto zarovnání, které je vyžadováno pro `double`, nebo 8 bajtů. V kódu, který cílí na 64bitové platformy je 16 bajtový.) Například přidělení čtyř bajtů by mělo být zarovnáno na hranici, která podporuje libovolný čtyřbajtový nebo menší objekt.

Visual C++ umožňuje typy, které mají *rozšířené zarovnání*, která se také označují jako *nadbytečně zarovnané* typy. Například typy SSE [__m128](../cpp/m128.md) a `__m256`a typy, které jsou deklarovány pomocí `__declspec(align( n ))` kde `n` je větší než 8, mají rozšířené zarovnání. Zarovnání paměti na hranici, která je vhodná pro objekt, který vyžaduje rozšířené zarovnání není zaručeno, že podle `malloc`. Chcete-li přidělit paměť pro nadbytečně zarovnané typy, použijte [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) a související funkce.

## <a name="see-also"></a>Viz také

[Použití zásobníku](../build/stack-usage.md)<br/>
[align](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)