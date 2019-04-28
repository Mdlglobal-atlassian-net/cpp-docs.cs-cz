---
title: quick_exit1
ms.date: 11/04/2016
apiname:
- quick_exit
apilocation:
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
apitype: DLLExport
f1_keywords:
- quick_exit
- process/quick_exit
- stdlib/quick_exit
helpviewer_keywords:
- quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
ms.openlocfilehash: 50f1ee72cce04c2bebc8f7396a2b6fad98301dd7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358031"
---
# <a name="quickexit"></a>quick_exit

Způsobí, že ukončení normální programu dojde k.

## <a name="syntax"></a>Syntaxe

```C
__declspec(noreturn) void quick_exit(
    int status
);
```

### <a name="parameters"></a>Parametry

*status*<br/>
Stavový kód se vraťte do hostitelského prostředí.

## <a name="return-value"></a>Návratová hodnota

**Quick_exit** funkce nemůže vracet volajícímu.

## <a name="remarks"></a>Poznámky

**Quick_exit** funkce způsobí ukončení normální programu. Volá žádné funkce registrovaných **atexit**, **_onexit** nebo registrovaných obslužné rutiny signálu **signál** funkce. Chování není definováno, pokud **quick_exit** je volána více než jednou, nebo pokud **ukončit** funkce se také nazývá.

**Quick_exit** volání v poslední dovnitř, první (ven LIFO) objednávky, funkce registrované pomocí funkcí **at_quick_exit**, s výjimkou pro tyto funkce již voláno, když byl zaregistrován funkce.  Chování není definováno, pokud [longjmp](longjmp.md) přišla během volání registrované funkci, která by jej měla ukončit volání funkce.

Po zavolání funkce registrované **quick_exit** vyvolá **_Exit** pomocí *stav* hodnoty k vrácení ovládacího prvku do hostitelského prostředí.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**quick_exit**|\<Process.h > nebo \<stdlib.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec – funkce](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
