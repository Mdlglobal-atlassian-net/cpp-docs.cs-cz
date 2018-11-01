---
title: /TLS
ms.date: 11/04/2016
f1_keywords:
- /TLS
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
ms.openlocfilehash: c125a6439e6cda2159a8bde2317528e667eaf310
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532632"
---
# <a name="tls"></a>/TLS

Zobrazí strukturu IMAGE_TLS_DIRECTORY ze spustitelného souboru.

## <a name="remarks"></a>Poznámky

/ TLS zobrazí položky struktury TLS i adresu funkce zpětného volání protokolu TLS.

Pokud program nepoužívá místní úložiště vláken, jeho image nebude obsahovat strukturu TLS.  Zobrazit [vlákno](../../cpp/thread.md) Další informace.

IMAGE_TLS_DIRECTORY je definována v souboru winnt.h.

## <a name="see-also"></a>Viz také

[DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)