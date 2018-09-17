---
title: -TLS | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /TLS
dev_langs:
- C++
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78f485a783dbe8b5fe9a49ed3100754115bf50b8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714649"
---
# <a name="tls"></a>/TLS

Zobrazí strukturu IMAGE_TLS_DIRECTORY ze spustitelného souboru.

## <a name="remarks"></a>Poznámky

/ TLS zobrazí položky struktury TLS i adresu funkce zpětného volání protokolu TLS.

Pokud program nepoužívá místní úložiště vláken, jeho image nebude obsahovat strukturu TLS.  Zobrazit [vlákno](../../cpp/thread.md) Další informace.

IMAGE_TLS_DIRECTORY je definována v souboru winnt.h.

## <a name="see-also"></a>Viz také

[DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)