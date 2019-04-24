---
title: /TLS
ms.date: 11/04/2016
f1_keywords:
- /TLS
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
ms.openlocfilehash: 751c212398f3d309b1d31d204291fe3a0503cf06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317260"
---
# <a name="tls"></a>/TLS

Zobrazí strukturu IMAGE_TLS_DIRECTORY ze spustitelného souboru.

## <a name="remarks"></a>Poznámky

/ TLS zobrazí položky struktury TLS i adresu funkce zpětného volání protokolu TLS.

Pokud program nepoužívá místní úložiště vláken, jeho image nebude obsahovat strukturu TLS.  Zobrazit [vlákno](../../cpp/thread.md) Další informace.

IMAGE_TLS_DIRECTORY je definována v souboru winnt.h.

## <a name="see-also"></a>Viz také:

[DUMPBIN – možnosti](dumpbin-options.md)
