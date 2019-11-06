---
title: strerror_s, _strerror_s, _wcserror_s, __wcserror_s
ms.date: 11/04/2016
api_name:
- __wcserror_s
- _strerror_s
- _wcserror_s
- strerror_s
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
- wcserror_s
- __wcserror_s
- _tcserror_s
- _wcserror_s
- tcserror_s
- strerror_s
- _strerror_s
helpviewer_keywords:
- __wcserror_s function
- error messages, printing
- tcserror_s function
- printing error messages
- strerror_s function
- _wcserror_s function
- _tcserror_s function
- _strerror_s function
- wcserror_s function
- error messages, getting
ms.assetid: 9e5b15a0-efe1-4586-b7e3-e1d7c31a03d6
ms.openlocfilehash: 74caba0398fdb5cdd0f9c80270a42d2903200a5d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73625811"
---
# <a name="strerror_s-_strerror_s-_wcserror_s-__wcserror_s"></a>strerror_s, _strerror_s, _wcserror_s, __wcserror_s

Získání systémové chybové zprávy (**strerror_s**, **_wcserror_s**) nebo vytištění uživatelem zadané chybové zprávy ( **_strerror_s**, **__wcserror_s**). Jedná se o verze [strerror –, _strerror, _wcserror, \__wcserror](strerror-strerror-wcserror-wcserror.md) s vylepšeními zabezpečení, jak [je popsáno v části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t strerror_s(
   char *buffer,
   size_t numberOfElements,
   int errnum
);
errno_t _strerror_s(
   char *buffer,
   size_t numberOfElements,
   const char *strErrMsg
);
errno_t _wcserror_s(
   wchar_t *buffer,
   size_t numberOfElements,
   int errnum
);
errno_t __wcserror_s(
   wchar_t *buffer,
   size_t numberOfElements,
   const wchar_t *strErrMsg
);
template <size_t size>
errno_t strerror_s(
   char (&buffer)[size],
   int errnum
); // C++ only
template <size_t size>
errno_t _strerror_s(
   char (&buffer)[size],
   const char *strErrMsg
); // C++ only
template <size_t size>
errno_t _wcserror_s(
   wchar_t (&buffer)[size],
   int errnum
); // C++ only
template <size_t size>
errno_t __wcserror_s(
   wchar_t (&buffer)[size],
   const wchar_t *strErrMsg
); // C++ only
```

### <a name="parameters"></a>Parametry

*vyrovnávací paměti*<br/>
Vyrovnávací paměť pro uložení řetězce chyb.

*numberOfElements*<br/>
Velikost vyrovnávací paměti.

*errnum*<br/>
Číslo chyby.

*strErrMsg*<br/>
Zpráva zadaná uživatelem

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, chybový kód při selhání.

### <a name="error-condtions"></a>Chyba podmínky

|*vyrovnávací paměti*|*numberOfElements*|*strErrMsg*|Obsah *vyrovnávací paměti*|
|--------------|------------------------|-----------------|--------------------------|
|**PLATNOST**|Jakýmikoli|Jakýmikoli|není k dispozici|
|Jakýmikoli|0,8|Jakýmikoli|Neupraveno|

## <a name="remarks"></a>Poznámky

Funkce **strerror_s** mapuje *errnum* na řetězec chybové zprávy a vrátí řetězec v *bufferu*. **_strerror_s** nepřijímá číslo chyby. k určení příslušné zprávy používá aktuální hodnotu **errno** . **Strerror_s** ani **_strerror_s** zprávu skutečně nevytiskne: pro to je třeba volat výstupní funkci, jako je například [fprintf –](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
{
   _strerror_s(buffer, 80);
   fprintf( stderr, buffer );
}
```

Pokud má StrErrMsg **hodnotu null**, **_strerror_s** vrátí řetězec ve *vyrovnávací paměti* obsahující chybovou zprávu systému pro poslední volání knihovny, které vytvořilo chybu. Řetězec chybové zprávy je ukončen znakem nového řádku (' \n '). Pokud *strErrMsg* není rovno hodnotě **null**, pak **_strerror_s** vrátí řetězec ve *vyrovnávací paměti* obsahující (v pořadí) zprávu o řetězci, dvojtečku, mezeru, chybovou zprávu systému pro poslední volání knihovny, která vytvoří chybu, a nový řádek. optické. Vaše řetězcová zpráva může být delší než 94 znaků.

Tyto funkce oříznou chybovou zprávu, pokud její délka překročí *numberOfElements* -1. Výsledný řetězec ve *vyrovnávací paměti* je vždy zakončený hodnotou null.

Skutečné číslo chyby pro **_strerror_s** je uloženo v proměnné [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). K systémovým chybovým zprávám se dostanete prostřednictvím proměnné [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), což je pole zpráv seřazené podle čísla chyby. **_strerror_s** přistupuje k příslušné chybové zprávě pomocí hodnoty **errno** jako indexu proměnné **_sys_errlist**. Hodnota proměnné [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) je definována jako maximální počet prvků v poli **_sys_errlist** . Chcete-li vytvořit přesné výsledky, zavolejte **_strerror_s** ihned poté, co rutina knihovny vrátí chybu. V opačném případě mohou další volání **strerror_s** nebo **_strerror_s** přepsat hodnotu **errno** .

**_wcserror_s** a **__wcserror_s** jsou verze s velkým znakem **strerror_s** a **_strerror_s**, v uvedeném pořadí.

Tyto funkce ověřují své parametry. Pokud má vyrovnávací paměť **hodnotu null** nebo je-li parametr velikosti 0, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, funkce vrátí **EINVAL** a nastaví **errno** na **EINVAL**.

**_strerror_s**, **_wcserror_s**a **__wcserror_s** nejsou součástí definice ANSI, ale místo toho jsou rozšíření Microsoft. Nepoužívejte je tam, kde je žádoucí přenositelnost; v případě kompatibility ANSI použijte místo toho **strerror_s** .

V C++systému je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky a eliminují nutnost zadat argument Size. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Verze knihovny ladění těchto funkcí nejprve naplní vyrovnávací paměť pomocí 0xFE. Pokud chcete toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror_s**|**strerror_s**|**strerror_s**|**_wcserror_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strerror_s**, **_strerror_s**|\<string. h >|
|**_wcserror_s**, **__wcserror_s**|\<String. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [pError](perror-wperror.md).

## <a name="see-also"></a>Viz také:

[Manipulace s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
