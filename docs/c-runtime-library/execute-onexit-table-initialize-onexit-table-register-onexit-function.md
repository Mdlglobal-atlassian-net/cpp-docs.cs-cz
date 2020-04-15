---
title: _execute_onexit_table, _initialize_onexit_table, _register_onexit_function
ms.date: 4/2/2020
api_name:
- _execute_onexit_table
- _initialize_onexit_table
- _register_onexit_function
- _o__execute_onexit_table
- _o__initialize_onexit_table
- _o__register_onexit_function
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _execute_onexit_table
- process/_execute_onexit_table
- _initialize_onexit_table
- process/_initialize_onexit_table
- _register_onexit_function
- process/_register_onexit_function
helpviewer_keywords:
- _execute_onexit_table function
- _initialize_onexit_table function
- _register_onexit_function function
ms.assetid: ad9e4149-d4ad-4fdf-aaaf-cf786fcb4473
ms.openlocfilehash: a1e35d9e86a43e48849373a1cf1aa07febcd0e33
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351646"
---
# <a name="_execute_onexit_table-_initialize_onexit_table-_register_onexit_function"></a>_execute_onexit_table, _initialize_onexit_table, _register_onexit_function

Spravuje rutiny, které mají být volány v době ukončení.

## <a name="syntax"></a>Syntaxe

```
int _initialize_onexit_table(
    _onexit_table_t* table
    );

int _register_onexit_function(
    _onexit_table_t* table,
    _onexit_t        function
    );

int _execute_onexit_table(
    _onexit_table_t* table
    );
```

#### <a name="parameters"></a>Parametry

*Tabulka*<br/>
[dovnitř, ven] Ukazatel na tabulku funkcí onexit.

*Funkce*<br/>
[v] Ukazatel na funkci, kterou chcete přidat do tabulky funkcí onexit.

## <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, vrátí hodnotu 0. V opačném případě vrátí zápornou hodnotu.

## <a name="remarks"></a>Poznámky

Tyto funkce jsou podrobnosti implementace infrastruktury slouží k podpoře běhu C a by neměly být volány přímo z vašeho kódu. Runtime C používá *tabulku funkcí onexit* k reprezentaci `atexit`posloupnosti funkcí registrovaných voláním , `at_quick_exit`, a `_onexit`. Struktura dat tabulky funkce onexit je neprůhledný detail implementace periodtime C; pořadí a význam jeho datových členů se může změnit. Neměly by být kontrolovány externím kódem.

Funkce `_initialize_onexit_table` inicializuje tabulku funkce onexit na počáteční hodnotu.  Tato funkce musí být volána před onexit `_register_onexit_function` `_execute_onexit_table`funkce tabulka je předán a to buď nebo .

Funkce `_register_onexit_function` připojí funkci na konec tabulky funkce onexit.

Funkce `_execute_onexit_table` provede všechny funkce v tabulce funkce onexit, vymaže tabulku a potom vrátí. Po volání `_execute_onexit_table`na , tabulka je v neplatném stavu; musí být znovu inicializována voláním, aby byla `_initialize_onexit_table` znovu použita.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`_initialize_onexit_table function`, `_register_onexit_function`, `_execute_onexit_table`|C, C++: \<process.h>|

Funkce `_initialize_onexit_table` `_register_onexit_function`, `_execute_onexit_table` a jsou specifické pro společnost Microsoft. Informace o kompatibilitě naleznete v [tématu Kompatibilita](../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[atexit](../c-runtime-library/reference/atexit.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)
