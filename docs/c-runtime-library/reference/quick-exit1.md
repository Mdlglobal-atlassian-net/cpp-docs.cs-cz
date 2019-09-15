---
title: quick_exit1
ms.date: 11/04/2016
api_name:
- quick_exit
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- quick_exit
- process/quick_exit
- stdlib/quick_exit
helpviewer_keywords:
- quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
ms.openlocfilehash: 86246ed7a32dcd2f12b38aa4148570fc5fb3b7a6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949671"
---
# <a name="quick_exit"></a>quick_exit

Způsobí, že dojde k ukončení normálního programu.

## <a name="syntax"></a>Syntaxe

```C
__declspec(noreturn) void quick_exit(
    int status
);
```

### <a name="parameters"></a>Parametry

*status*<br/>
Stavový kód, který se má vrátit do hostitelského prostředí.

## <a name="return-value"></a>Návratová hodnota

Funkce **quick_exit** se nemůže vrátit volajícímu.

## <a name="remarks"></a>Poznámky

Funkce **quick_exit** způsobuje normální ukončení programu. Nevolá žádné funkce zaregistrované v **atexit**, **_onexit** nebo obslužných rutinách signálu zaregistrovaných funkcí **Signal** . Chování není definováno, pokud je **quick_exit** voláno více než jednou, nebo pokud je volána také funkce **Exit** .

Funkce **quick_exit** volá v pořadí posledních v, First-out (LIFO) funkce zaregistrované v **at_quick_exit**, s výjimkou těch, které již byly volány při registraci funkce.  Chování není definováno, pokud je provedeno volání [longjmp](longjmp.md) během volání registrované funkce, která by ukončila volání funkce.

Po volání registrovaných funkcí **quick_exit** vyvolá **_Exit** pomocí hodnoty *status* pro vrácení řízení hostitelskému prostředí.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**quick_exit**|\<Process. h > \<nebo Stdlib. h >|

Další informace o kompatibilitě najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
