---
title: strerror, _strerror, _wcserror, __wcserror
ms.date: 11/04/2016
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
ms.openlocfilehash: 0b4d70687bc2f428162d035c80d6bc8525a8fb9e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958137"
---
# <a name="strerror-_strerror-_wcserror-__wcserror"></a>strerror, _strerror, _wcserror, __wcserror

Získá řetězec systémové chybové zprávy (**strerror –** , **_wcserror**) nebo zformátuje řetězec chybové zprávy zadaný uživatelem ( **_strerror**, **__wcserror**). K dispozici jsou bezpečnější verze těchto funkcí; viz [strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md).

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
Zpráva zadaná uživatelem

## <a name="return-value"></a>Návratová hodnota

Všechny tyto funkce vrací ukazatel na řetězec chybové zprávy. Následná volání mohou přepsat řetězec.

## <a name="remarks"></a>Poznámky

Funkce **strerror –** mapuje *errnum* na řetězec chybové zprávy a vrátí ukazatel na řetězec. Zpráva ani **strerror –** ani **_strerror** zprávu nevytiskne: V takovém případě musíte zavolat výstupní funkci, jako je například [fprintf –](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

Pokud je *strErrMsg* předán jako **null**, **_strerror** vrátí ukazatel na řetězec, který obsahuje chybovou zprávu systému pro poslední volání knihovny, které vytvořilo chybu. Řetězec chybové zprávy je ukončen znakem nového řádku (' \n '). Pokud *strErrMsg* není rovno hodnotě **null**, pak **_strerror** vrátí ukazatel na řetězec, který obsahuje (v pořadí) zprávu o řetězci, dvojtečku, mezeru, chybovou zprávu systému pro poslední volání knihovny, která vytvoří chybu, a nový řádek. optické. Vaše řetězcová zpráva může být delší než 94 znaků.

Skutečné číslo chyby pro **_strerror** je uloženo v proměnné [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Chcete-li vytvořit přesné výsledky, zavolejte **_strerror** ihned poté, co rutina knihovny vrátí chybu. V opačném případě mohou další volání **strerror –** nebo **_strerror** přepsat hodnotu **errno** .

**_wcserror** a **__wcserror** jsou verze s velkým znakem **strerror –** a **_strerror**, v uvedeném pořadí.

**_strerror**, **_wcserror**a **__wcserror** nejsou součástí definice ANSI; jsou to rozšíření Microsoftu a doporučujeme, abyste je nepoužívali tam, kde chcete přenosný kód. V případě kompatibility ANSI použijte místo toho **strerror –** .

Pro získání chybových řetězců doporučujeme **strerror –** nebo **_wcserror** namísto zastaralých maker [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) a [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) a nepoužívané interní funkce **__sys_errlist** a **__sys_nerr**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strerror**|\<String. h >|
|**_strerror**|\<String. h >|
|**_wcserror**, **__wcserror**|\<String. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [pError](perror-wperror.md).

## <a name="see-also"></a>Viz také:

[Manipulace s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
