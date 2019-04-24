---
title: Chyba linkerů LNK2017
ms.date: 11/04/2016
f1_keywords:
- LNK2017
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
ms.openlocfilehash: ce5332c2812740ef0b8c7d8e9c64a095d20a4e2b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299052"
---
# <a name="linker-tools-error-lnk2017"></a>Chyba linkerů LNK2017

'symbol' přemístění "segmentu" bez: No neplatná.

Pokoušíte se vytvořit bitovou kopii 64-bit s adresami 32-bit. Chcete-li to provést, musíte mít:

- Použijte adresu zatížení.

- Omezte na obrázku 3 GB.

- Zadejte [: No](../../build/reference/largeaddressaware-handle-large-addresses.md).