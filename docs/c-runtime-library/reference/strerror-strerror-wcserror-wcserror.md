---
title: strerror, _strerror, _wcserror, __wcserror
description: Popisuje funkce strerror funkce Knihovna runtime (Microsoft C Runtime), _strerror, _wcserror a __wcserror.
ms.date: 4/2/2020
api_name:
- strerror
- _strerror
- _wcserror
- __wcserror
- _o___wcserror
- _o__strerror
- _o__wcserror
- _o_strerror
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __sys_errlist
- wcserror
- _strerror
- __wcserror
- strerror
- __sys_nerr
- _tcserror
- _wcserror
- tcserror
helpviewer_keywords:
- strerror function
- _strerror function
- __sys_errlist
- wcserror function
- error messages, printing
- __sys_nerr
- tcserror function
- printing error messages
- _wcserror function
- _tcserror function
- __wcserror function
- error messages, getting
ms.assetid: 27b72255-f627-43c0-8836-bcda8b003e14
ms.openlocfilehash: 9eecb7376cf476f0128dc20c8884746a3b4d47d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337333"
---
# <a name="strerror-_strerror-_wcserror-__wcserror"></a>strerror, _strerror, _wcserror, __wcserror

Získá řetězec systémové chybové zprávy (**strerror**, **_wcserror**) nebo zformátuje řetězec chybové zprávy zadaný uživatelem (**_strerror**, **__wcserror**). K dispozici jsou bezpečnější verze těchto funkcí. viz [strerror_s, _strerror_s, \__wcserror_s, _wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md).

## <a name="syntax"></a>Syntaxe

```C
char * strerror(
   int errnum );

char * _strerror(
   const char *strErrMsg );

wchar_t * _wcserror(
   int errnum );

wchar_t * __wcserror(
   const wchar_t *strErrMsg );
```

### <a name="parameters"></a>Parametry

*errnum*\
Číslo chyby.

*strErrMsg*\
Zpráva dodaná uživatelem.

## <a name="return-value"></a>Návratová hodnota

Všechny tyto funkce vrátí ukazatel na řetězec chybové zprávy ve vyrovnávací paměti místního vlákna vlastněné runtime. Pozdější volání ve stejném vlákně můžete přepsat tento řetězec.

## <a name="remarks"></a>Poznámky

Funkce **strerror** *mapuje chybovost* na řetězec chybové zprávy a vrací ukazatel na řetězec. **Funkce strerror** a **_strerror** ve skutečnosti zprávu nevytisknou. Chcete-li tisknout, zavolejte výstupní funkci, [například fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile", 2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

Pokud *strErrMsg* je předán jako **NULL**, **_strerror** vrátí ukazatel na řetězec. Obsahuje systémovou chybovou zprávu pro poslední volání knihovny, která způsobila chybu. Řetězec chybové zprávy je ukončen znakem nového řádku (\n"). Když *strErrMsg* není **NULL**, řetězec obsahuje, v pořadí: *strErrMsg* řetězec, dvojtečka, mezera, chybová zpráva systému a znak nového řádku. Zpráva o řetězci může být maximálně 94 znaků dlouhá, buď úzkými (**_strerror)** nebo širokými **(__wcserror)** znaky.

Skutečné číslo chyby pro **_strerror** je uloženo v proměnné [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Chcete-li vytvořit přesné výsledky, volání **_strerror** ihned poté, co rutina knihovny vrátí chybu. V opačném případě může pozdější volání rutin knihovny přepsat hodnotu **errno.**

**_wcserror** a **__wcserror** jsou verze **strerror** s širokými znaky a **_strerror**.

**_strerror**, **_wcserror**a **__wcserror** jsou specifické pro společnost Microsoft, nikoli součástí knihovny Standard C. Nedoporučujeme je používat tam, kde chcete přenosný kód. Pro kompatibilitu se standardem C použijte místo toho **strerror.**

Chcete-li získat chybové řetězce, doporučujeme **strerror** nebo **_wcserror** namísto zastaralé makra [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) a [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) a zastaralé vnitřní funkce **__sys_errlist** a **__sys_nerr**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecných textů

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strerror**|\<string.h>|
|**_strerror**|\<string.h>|
|**_wcserror** **, __wcserror**|\<string.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad pro [perror](perror-wperror.md).

## <a name="see-also"></a>Viz také

[Manipulace s řetězci](../../c-runtime-library/string-manipulation-crt.md)\
[jasnější](clearerr.md)\
[ferror](ferror.md)\
[perror, _wperror](perror-wperror.md)
