---
title: Zřetězené struktury Unwind Info | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 176835bf-f118-45d9-9128-9db4b7571864
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6da09387595188026d855fb99a49b588e6f21aa3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715023"
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