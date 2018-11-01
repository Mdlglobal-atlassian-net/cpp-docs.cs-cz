---
title: Chyba linkerů LNK2017
ms.date: 11/04/2016
f1_keywords:
- LNK2017
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
ms.openlocfilehash: ce5332c2812740ef0b8c7d8e9c64a095d20a4e2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641455"
---
# <a name="linker-tools-error-lnk2017"></a>Chyba linkerů LNK2017

'symbol' přemístění "segmentu" bez: No neplatná.

Pokoušíte se vytvořit bitovou kopii 64-bit s adresami 32-bit. Chcete-li to provést, musíte mít:

- Použijte adresu zatížení.

- Omezte na obrázku 3 GB.

- Zadejte [: No](../../build/reference/largeaddressaware-handle-large-addresses.md).