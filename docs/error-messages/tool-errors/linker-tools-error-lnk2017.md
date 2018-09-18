---
title: Chyba Linkerů LNK2017 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2017
dev_langs:
- C++
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80af2bb6475fc37b7feba5b29bfe9c1292740286
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022447"
---
# <a name="linker-tools-error-lnk2017"></a>Chyba linkerů LNK2017

'symbol' přemístění "segmentu" bez: No neplatná.

Pokoušíte se vytvořit bitovou kopii 64-bit s adresami 32-bit. Chcete-li to provést, musíte mít:

- Použijte adresu zatížení.

- Omezte na obrázku 3 GB.

- Zadejte [: No](../../build/reference/largeaddressaware-handle-large-addresses.md).