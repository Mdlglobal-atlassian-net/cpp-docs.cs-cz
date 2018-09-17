---
title: Selhání háků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, failure hooks
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4c69759034dbb7233970bd89616a062a369cc13
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721276"
---
# <a name="failure-hooks"></a>Selhání háků

Selhání připojení je povoleno stejným způsobem jako [oznámení hook](../../build/reference/notification-hooks.md). Zavěšení rutinní musí vrátit vhodnou hodnotu tak, aby zpracování může pokračovat (HINSTANCE nebo FARPROC) nebo 0, která znamená, že by měl být vyvolána výjimka.

Proměnné ukazatele, který odkazuje na uživatelem definované funkce je:

```
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}
ExternC
PfnDliHook   __pfnDliFailureHook2;
```

**DelayLoadInfo** struktura obsahuje všechny relevantní data potřebná pro přesné vytváření sestav v chybě, včetně hodnot z `GetLastError`.

Pokud je oznámení **dliFailLoadLib**, funkce háku může vrátit:

- 0, pokud nemůže zpracovat selhání.

- HMODULE, pokud selhání hook opraven problém a načtení samotné knihovny.

Pokud je oznámení **dliFailGetProc**, funkce háku může vrátit:

- 0, pokud nemůže zpracovat selhání.

- Adresa platnou proc (adresa funkce import), pokud selhání připojení bylo úspěšné při získávání adres samotné.

## <a name="see-also"></a>Viz také

[Zpracování chyb a oznámení](../../build/reference/error-handling-and-notification.md)