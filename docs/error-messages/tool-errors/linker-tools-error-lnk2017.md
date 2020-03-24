---
title: Chyba linkerů LNK2017
ms.date: 11/04/2016
f1_keywords:
- LNK2017
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
ms.openlocfilehash: 02e80de5c34809a331003f3b0fb28d32e138a531
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194730"
---
# <a name="linker-tools-error-lnk2017"></a>Chyba linkerů LNK2017

přemístění ' symbol ' na ' segment ' je neplatné bez/LARGEADDRESSAWARE: NO

Pokoušíte se vytvořit 64 bitovou kopii s 32 adresami. K tomu je potřeba:

- Použijte pevnou adresu zatížení.

- Omezí obraz na 3 GB.

- Zadejte [/LARGEADDRESSAWARE: No](../../build/reference/largeaddressaware-handle-large-addresses.md).
