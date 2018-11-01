---
title: Konflikty s kompilátorem x86
ms.date: 11/04/2016
ms.assetid: 8e47f0d3-afe0-42d9-9efa-de239ddd3a05
ms.openlocfilehash: e56ebc5631ac5c96a9cdd2dfc2b8e81cdeed9769
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614263"
---
# <a name="conflicts-with-the-x86-compiler"></a>Konflikty s kompilátorem x86

Datové typy, které jsou větší než 4 bajty nejsou zarovnány automaticky v zásobníku při použití x86 kompilátoru kompilovat aplikace. Protože architektura x86 kompilátoru je 4 bajty. zarovnané zásobníku, nic větší než 4 bajty, například 64bitové celé číslo, nelze automaticky zarovnány na adresu 8 bajtů.

Práce s nezarovnaná data po má dva důsledky.

- Může trvat déle, získat přístup k umístění nezarovnaných trvá pro přístup k umístěním zarovnaný.

- Nezarovnané umístění nelze použít v propojené operace.

Pokud budete potřebovat více striktní zarovnání, použijte `__declspec(align(N)) on your variable declarations`. To způsobí, že kompilátor, aby dynamicky zarovnat stack pro splnění vašich požadavků. Dynamické úpravy do zásobníku za běhu však může způsobit pomalejší spuštění vaší aplikace.

## <a name="see-also"></a>Viz také

[Typy a úložiště](../build/types-and-storage.md)<br/>
[align](../cpp/align-cpp.md)