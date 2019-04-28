---
title: strerror, _strerror, _wcserror, __wcserror
ms.date: 11/04/2016
apiname:
- strerror
- _strerror
- _wcserror
- __wcserror
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
ms.openlocfilehash: 4038fcc29c18e5d73024cbe5688c674e00d1409e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353856"
---
# <a name="strerror-strerror-wcserror-wcserror"></a>strerror, _strerror, _wcserror, __wcserror

Získá řetězec chybové zprávy systému (**strerror**, **_wcserror –**) ani neformátuje řetězec uživatelem zadanou chybovou zprávu (**_strerror –**, **__wcserror –**). Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [strerror_s – _strerror_s –, _wcserror_s –, \__wcserror_s –](strerror-s-strerror-s-wcserror-s-wcserror-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *strerror(
   int errnum
);
char *_strerror(
   const char *strErrMsg
);
wchar_t * _wcserror(
   int errnum
);
wchar_t * __wcserror(
   const wchar_t *strErrMsg
);
```

### <a name="parameters"></a>Parametry

*errnum*<br/>
Číslo chyby.

*strErrMsg*<br/>
Zpráva zadaná uživatelem.

## <a name="return-value"></a>Návratová hodnota

Všechny tyto funkce vrátí ukazatel na řetězec chybové zprávy. Následná volání můžete přepsat řetězec.

## <a name="remarks"></a>Poznámky

**Strerror** funkce mapy *errnum* na řetězec chybové zprávy a vrací ukazatel na řetězec. Ani **strerror** ani **_strerror –** ve skutečnosti zprávu nevytiskne: K tomu budete muset zavolat výstupní funkci, jako například [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

Pokud *strErrMsg* je předán jako **NULL**, **_strerror –** vrací ukazatel na řetězec, který obsahuje chybovou zprávu systému pro poslední volání knihovny, které vytvořilo chybu. Řetězec chybové zprávy je ukončen znakem nového řádku ('\n'). Pokud *strErrMsg* není roven **NULL**, pak **_strerror –** vrací ukazatel na řetězec, který obsahuje (v pořadí) zprávu řetězce, dvojtečku, mezeru, systémová chyba zpráva pro poslední volání knihovny, který generuje chybu a znak nového řádku. Vaše Řetězcová zpráva může obsahovat nejvýše, 94 znaků.

Aktuální číslo chyby pro **_strerror –** je uložen v proměnné [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Chcete-li přesné výsledky zavolejte **_strerror –** ihned poté, co knihovní rutina vrátí chybu. Jinak následná volání **strerror** nebo **_strerror –** můžete přepsat **errno** hodnotu.

**_wcserror –** a **__wcserror –** jsou širokoznaké verze **strerror** a **_strerror –** v uvedeném pořadí.

**_strerror –**, **_wcserror –**, a **__wcserror –** nejsou součástí definice ANSI, jsou rozšíření společnosti Microsoft a doporučujeme vám, že je velmi riskantní používat je místo, kam chcete přenositelný kód. Z důvodu kompatibility ANSI, použijte **strerror** místo.

Chcete-li získat chybové řetězce, doporučujeme **strerror** nebo **_wcserror –** namísto zastaralé makra [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) a [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) a zastaralé funkce vnitřní **__sys_errlist** a **__sys_nerr**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strerror**|\<string.h>|
|**_strerror**|\<string.h>|
|**_wcserror**, **__wcserror**|\<string.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [perror](perror-wperror.md).

## <a name="see-also"></a>Viz také:

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
