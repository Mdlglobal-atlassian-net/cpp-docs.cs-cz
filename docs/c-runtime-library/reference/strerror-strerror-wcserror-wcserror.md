---
title: strerror, _strerror, _wcserror, __wcserror
description: Popisuje funkce knihovny CRT (Microsoft C Runtime Library) strerror –, _strerror, _wcserror a __wcserror.
ms.date: 01/07/2020
api_name:
- strerror
- _strerror
- _wcserror
- __wcserror
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
ms.openlocfilehash: 8c9c6850d6620407897b2a3a1dbf32e61f6719c0
ms.sourcegitcommit: 7bd3567fc6a0e7124aab51cad63bbdb44a99a848
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75755037"
---
# <a name="strerror-_strerror-_wcserror-__wcserror"></a>strerror, _strerror, _wcserror, __wcserror

Získá řetězec systémové chybové zprávy (**strerror –** , **_wcserror**) nebo zformátuje řetězec chybové zprávy zadaný uživatelem ( **_strerror**, **__wcserror**). K dispozici jsou bezpečnější verze těchto funkcí; viz [strerror_s, _strerror_s, _wcserror_s \__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md).

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
Zpráva zadaná uživatelem

## <a name="return-value"></a>Návratová hodnota

Všechny tyto funkce vrací ukazatel na řetězec chybové zprávy ve vyrovnávací paměti místního vlákna, které vlastní modul runtime. Pozdější volání ve stejném vlákně mohou tento řetězec přepsat.

## <a name="remarks"></a>Poznámky

Funkce **strerror –** mapuje *errnum* na řetězec chybové zprávy a vrátí ukazatel na řetězec. Funkce **strerror –** a **_strerror** ve skutečnosti zprávy netiskou. Chcete-li tisknout, zavolejte výstupní funkci, jako je například [fprintf –](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile", 2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

Pokud je *strErrMsg* předán jako **null**, **_strerror** vrátí ukazatel na řetězec. Obsahuje chybovou zprávu systému pro poslední volání knihovny, které vytvořilo chybu. Řetězec chybové zprávy je ukončen znakem nového řádku (' \n '). Pokud *strErrMsg* není **null**, řetězec obsahuje, v pořadí: váš *strErrMsg* řetězec, dvojtečka, mezera, systémová chybová zpráva a znak nového řádku. Vaše řetězcová zpráva může být delší než 94 znaků, a to buď v úzkých ( **_strerror**), nebo ve velkých ( **__wcserror**) znacích.

Skutečné číslo chyby pro **_strerror** je uloženo v proměnné [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Chcete-li vytvořit přesné výsledky, zavolejte **_strerror** ihned poté, co rutina knihovny vrátí chybu. V opačném případě může pozdější volání rutin knihovny přepsat hodnotu **errno** .

**_wcserror** a **__wcserror** jsou verze **strerror –** a **_strerror**, v uvedeném pořadí.

**_strerror**, **_wcserror**a **__Wcserror** jsou specifické pro společnost Microsoft, nikoli součástí standardní knihovny jazyka C. Nedoporučujeme je používat tam, kde chcete použít přenosný kód. V případě kompatibility Standard C použijte místo toho **strerror –** .

Chcete-li získat chybové řetězce, doporučujeme namísto zastaralých maker [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) a [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) použít **strerror –** nebo **_wcserror** a nepoužívané interní funkce **__sys_errlist** a **__sys_nerr**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strerror**|\<String. h >|
|**_strerror**|\<String. h >|
|**_wcserror** **__wcserror**|\<String. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [pError](perror-wperror.md).

## <a name="see-also"></a>Viz také:

\ [manipulace s řetězci](../../c-runtime-library/string-manipulation-crt.md)
[clearerr](clearerr.md)\
\ pro [trajekty](ferror.md)
[perror, _wperror](perror-wperror.md)
