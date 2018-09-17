---
title: Je v konfliktu s x86 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8e47f0d3-afe0-42d9-9efa-de239ddd3a05
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f01e65adfb42a5fb3361e75ce34060f7dc1b9f9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709667"
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