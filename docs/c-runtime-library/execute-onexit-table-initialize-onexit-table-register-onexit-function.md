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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 051961f049109b4fa6a2881e442e621036cb279c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913826"
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

*stolní*<br/>
[in, out] Ukazatel na tabulku funkcí při ukončení.

*slouží*<br/>
pro Ukazatel na funkci, která se má přidat do tabulky funkcí k ukončení.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí hodnotu 0. V opačném případě vrátí zápornou hodnotu.

## <a name="remarks"></a>Poznámky

Tyto funkce jsou podrobnosti implementace infrastruktury používané k podpoře modulu runtime jazyka C a neměly by být volány přímo z vašeho kódu. Modul runtime jazyka C používá *tabulku funkcí* pro zastupuje sekvenci funkcí zaregistrovaných voláním do `atexit`, `at_quick_exit`a `_onexit`. Struktura dat tabulky funkce při ukončení je neprůhledná podrobnosti implementace modulu runtime jazyka C. pořadí a význam jeho datových členů se může změnit. Neměly by být kontrolovány externím kódem.

`_initialize_onexit_table` Funkce inicializuje počáteční hodnotu tabulky funkce Exit.  Tato funkce musí být volána před předáním tabulky funkce Exit do `_register_onexit_function` nebo. `_execute_onexit_table`

`_register_onexit_function` Funkce připojí funkci na konec tabulky funkcí při ukončení.

`_execute_onexit_table` Funkce spustí všechny funkce v tabulce funkce při ukončení, vymaže tabulku a potom vrátí. Po volání `_execute_onexit_table`je tabulka v neplatném stavu; je nutné jej znovu inicializovat voláním, `_initialize_onexit_table` než se znovu použije.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`_initialize_onexit_table function`, `_register_onexit_function`, `_execute_onexit_table`|C, C++: \<Process. h>|

Funkce `_initialize_onexit_table`, `_register_onexit_function`a `_execute_onexit_table` jsou specifické pro společnost Microsoft. Informace o kompatibilitě najdete v tématu [Kompatibilita](../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[atexit](../c-runtime-library/reference/atexit.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)
