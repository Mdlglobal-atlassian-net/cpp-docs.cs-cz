---
title: _execute_onexit_table _initialize_onexit_table, _register_onexit_function
ms.date: 11/04/2016
apiname:
- _execute_onexit_table
- _initialize_onexit_table
- _register_onexit_function
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 0090d5d1504f4320c122ae1e811e0af88cccdd2e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62343964"
---
# <a name="executeonexittable-initializeonexittable-registeronexitfunction"></a>_execute_onexit_table _initialize_onexit_table, _register_onexit_function

Spravuje rutiny má volat na čas ukončení.

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
[out v] Ukazatel na tabulce onexit – funkce

*– funkce*<br/>
[in] Ukazatel na funkci, kterou chcete přidat do tabulky onexit – funkce

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí hodnotu 0. V opačném případě vrátí zápornou hodnotu.

## <a name="remarks"></a>Poznámky

Tyto funkce jsou podrobnosti implementace infrastruktury slouží k podpoře modulu runtime jazyka C a neměla být volána přímo z uživatelského kódu. C runtime používá *onexit – funkce tabulky* představující pořadí registrovaných volání funkce `atexit`, `at_quick_exit`, a `_onexit`. Datová struktura onexit – funkce tabulky je podrobnosti neprůhledné implementace modulu C Runtime; může změnit pořadí a význam svých datových členů. Prověřovány by neměl být externím kódu.

`_initialize_onexit_table` Funkce inicializuje tabulce onexit – funkce na počáteční hodnotu.  Tato funkce musí být volána před tabulce onexit – funkce je předána buď `_register_onexit_function` nebo `_execute_onexit_table`.

`_register_onexit_function` Funkce připojí funkci na konec tabulky onexit – funkce.

`_execute_onexit_table` Funkce spustí všechny funkce v tabulce onexit – funkce, vymaže v tabulce a vrátí. Po volání `_execute_onexit_table`, v tabulce je ve stavu není platná; musí být znovu inicializovány voláním `_initialize_onexit_table` předtím, než je znovu použit.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`_initialize_onexit_table function`, `_register_onexit_function`, `_execute_onexit_table`|C, C++: \<process.h>|

`_initialize_onexit_table`, `_register_onexit_function`, A `_execute_onexit_table` funkce jsou specifické pro Microsoft. Informace o kompatibilitě naleznete v tématu [kompatibility](../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[atexit](../c-runtime-library/reference/atexit.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)
