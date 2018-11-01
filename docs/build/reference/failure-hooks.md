---
title: Selhání háků
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, failure hooks
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
ms.openlocfilehash: 2bda1d34c85b1e88c7d278816e30e76537a7523b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463607"
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