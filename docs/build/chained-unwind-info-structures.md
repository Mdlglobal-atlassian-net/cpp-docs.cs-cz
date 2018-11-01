---
title: Zřetězené struktury unwind info
ms.date: 11/04/2016
ms.assetid: 176835bf-f118-45d9-9128-9db4b7571864
ms.openlocfilehash: 19d0beb8c3438183fa594d7ec3cab4929b3a491a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502138"
---
# <a name="chained-unwind-info-structures"></a>Zřetězené struktury unwind info

Pokud je nastavený příznak UNW_FLAG_CHAININFO, je sekundární struktury unwind info a sdílenou – obslužná rutina/zřetězené – informace o výjimce adresu pole obsahuje informace o primární unwind. Následující kód načte primární unwind informace za předpokladu, že `unwindInfo` je nastaven příznak, který má UNW_FLAG_CHAININFO strukturu.

```
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

Zřetězené informace jsou užitečné ve dvou situacích. Nejdřív může sloužit pro segmenty nesouvislé kódu. Pomocí zřetězené informace můžete zmenšit velikost požadované unwind informací, protože není nutné duplikovat unwind kódů z primárního unwind info.

Zřetězené informace můžete použít také k seskupení uložení volatile registrů. Kompilátor může způsobit prodlevu při ukládání některé závislé registry, dokud není mimo položky prologu funkce. Můžete zaznamenat to tak, že primární unwind informace pro část funkce před seskupené kódu a následným nastavováním zřetězené informace o s nenulovou hodnotu size prologu, kde kódy unwind v zřetězené informace, které odrážejí uložení stálé registrů. V takovém případě jsou kódy unwind všechny výskyty UWOP_SAVE_NONVOL. Seskupení, který ukládá stálé registry s využitím PUSH nebo upravuje RSP registru pomocí dalších pevné zásobníku přidělení se nepodporuje.

UNWIND_INFO položku, která má nastaven UNW_FLAG_CHAININFO může obsahovat RUNTIME_FUNCTION položku, jejíž položku UNWIND_INFO má také UNW_FLAG_CHAININFO nastavit (více shrink-wrapping). Nakonec zřetězených unwind informací, že ukazatele dorazí na UNWIND_INFO položku, která má UNW_FLAG_CHAININFO vymazána; Toto je primární UNWIND_INFO položka, která odkazuje na vstupní bod skutečný procedury.

## <a name="see-also"></a>Viz také

[Unwind data pro zpracování výjimek, podpora ladění](../build/unwind-data-for-exception-handling-debugger-support.md)