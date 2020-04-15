---
title: strerror_s, _strerror_s, _wcserror_s, __wcserror_s
ms.date: 4/2/2020
api_name:
- __wcserror_s
- _strerror_s
- _wcserror_s
- strerror_s
- _o__strerror_s
- _o__wcserror_s
- _o_strerror_s
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
ms.openlocfilehash: ef712ecb6236513d169b4a8836b1365b0aca0633
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337372"
---
# <a name="strerror_s-_strerror_s-_wcserror_s-__wcserror_s"></a>strerror_s, _strerror_s, _wcserror_s, __wcserror_s

Zobrazí se systémová chybová zpráva **(strerror_s**, **_wcserror_s**) nebo vytiskněte chybovou zprávu dodanou uživatelem (**_strerror_s**, **__wcserror_s**). Jedná se o verze [strerror, \__strerror, _wcserror, _wcserror](strerror-strerror-wcserror-wcserror.md) s vylepšeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Vyrovnávací paměti*<br/>
Vyrovnávací paměť pro uložení chybového řetězce.

*numberOfElements*<br/>
Velikost vyrovnávací paměti.

*errnum*<br/>
Číslo chyby.

*strErrMsg*<br/>
Zpráva dodaná uživatelem.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, kód chyby při selhání.

### <a name="error-condtions"></a>Chyba Condtions

|*Vyrovnávací paměti*|*numberOfElements*|*strErrMsg*|Obsah *vyrovnávací paměti*|
|--------------|------------------------|-----------------|--------------------------|
|**Null**|jakékoli|jakékoli|neuvedeno|
|jakékoli|0|jakékoli|nezměněno|

## <a name="remarks"></a>Poznámky

Funkce **strerror_s** *mapuje chybovost* na řetězec chybové zprávy a vrací řetězec ve *vyrovnávací paměti*. **_strerror_s** nebere číslo chyby; používá aktuální hodnotu **errno** k určení příslušné zprávy. Ani **strerror_s,** ani **_strerror_s** ve skutečnosti vytiskne zprávu: K tomu je třeba volat výstupní funkci, jako je [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
{
   _strerror_s(buffer, 80);
   fprintf( stderr, buffer );
}
```

Pokud *strErrMsg* je **NULL**, **vrátí _strerror_s** řetězec ve vyrovnávací *paměti* obsahující systémovou chybovou zprávu pro poslední volání knihovny, která způsobila chybu. Řetězec chybové zprávy je ukončen znakem nového řádku (\n"). Pokud *strErrMsg* není rovna **NULL**, **pak _strerror_s** vrátí řetězec ve vyrovnávací *paměti* obsahující (v pořadí) zprávu řetězce, dvojtečka, mezera, systémová chybová zpráva pro poslední volání knihovny produkující chybu a znak nového řádku. Zpráva o řetězci může být maximálně 94 znaků dlouhá.

Tyto funkce zkrátit chybovou zprávu, pokud jeho délka přesahuje *numberOfElements* -1. Výsledný řetězec ve *vyrovnávací paměti* je vždy ukončen a null.

Skutečné číslo chyby pro **_strerror_s** je uloženo v proměnné [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Systémové chybové zprávy jsou přístupné prostřednictvím proměnné [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), což je pole zpráv seřazených podle čísla chyby. **_strerror_s** přistupuje k příslušné chybové zprávě pomocí hodnoty **errno** jako indexu pro proměnnou **_sys_errlist**. Hodnota proměnné [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) je definována jako maximální počet prvků v **poli _sys_errlist.** Chcete-li vytvořit přesné výsledky, volání **_strerror_s** ihned po knihovně rutinní vrátí s chybou. V opačném případě mohou následná volání **strerror_s** nebo **_strerror_s** přepsat hodnotu **errno.**

**_wcserror_s** a **__wcserror_s** jsou širokoznakové verze **strerror_s** a **_strerror_s**.

Tyto funkce ověřují jejich parametry. Pokud je vyrovnávací paměť **null** nebo pokud je parametr size 0, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Validation](../../c-runtime-library/parameter-validation.md) . Pokud je spuštění povoleno pokračovat, funkce vrátí **EINVAL** a nastavit **errno** na **EINVAL**.

**_strerror_s**, **_wcserror_s**a **__wcserror_s** nejsou součástí definice ANSI, ale jsou k ní rozšíření společnosti Microsoft. Nepoužívejte je tam, kde je žádoucí přenositelnost; pro kompatibilitu s ANSI použijte místo toho **strerror_s.**

V jazyce C++ je použití těchto funkcí zjednodušeno přetížením šablony; přetížení lze odvodit délku vyrovnávací paměti automaticky, což eliminuje potřebu zadat argument velikosti. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze knihovny těchto funkcí nejprve vyplní vyrovnávací paměť 0xFE. Chcete-li toto chování zakázat, použijte [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror_s**|**strerror_s**|**strerror_s**|**_wcserror_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strerror_s**, **_strerror_s**|\<string.h>|
|**_wcserror_s** **__wcserror_s**|\<string.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Viz příklad pro [perror](perror-wperror.md).

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
