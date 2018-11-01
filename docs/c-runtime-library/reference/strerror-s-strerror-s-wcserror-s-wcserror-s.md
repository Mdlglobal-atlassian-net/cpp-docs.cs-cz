---
title: strerror_s, _strerror_s, _wcserror_s, __wcserror_s
ms.date: 11/04/2016
apiname:
- __wcserror_s
- _strerror_s
- _wcserror_s
- strerror_s
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
ms.openlocfilehash: 00ff9d0df1a78d07eaa509201fb998b30396cc4c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429637"
---
# <a name="strerrors-strerrors-wcserrors-wcserrors"></a>strerror_s, _strerror_s, _wcserror_s, __wcserror_s

Získat chybovou zprávu systému (**strerror_s –**, **_wcserror_s –**) nebo vytisknout uživatelem zadanou chybovou zprávu (**_strerror_s –**, **__wcserror_s –** ). Jde o verzích [strerror _strerror –, _wcserror –, \__wcserror –](strerror-strerror-wcserror-wcserror.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Vyrovnávací paměť pro uložení řetězce chyb.

*numberOfElements*<br/>
Velikost vyrovnávací paměti.

*errnum*<br/>
Číslo chyby.

*strErrMsg*<br/>
Zpráva zadaná uživatelem.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, při selhání kód chyby.

### <a name="error-condtions"></a>Chybové podmínky

|*Vyrovnávací paměti*|*numberOfElements*|*strErrMsg*|Obsah *vyrovnávací paměti*|
|--------------|------------------------|-----------------|--------------------------|
|**HODNOTU NULL**|Všechny|Všechny|není k dispozici|
|Všechny|0|Všechny|Nezměněno|

## <a name="remarks"></a>Poznámky

**Strerror_s –** funkce mapy *errnum* na řetězec chybové zprávy, vrací řetězec do *vyrovnávací paměti*. **_strerror_s –** nepřijímá číslo chyby; používá aktuální hodnotu **errno** k určení příslušné zprávy. Ani **strerror_s –** ani **_strerror_s –** ve skutečnosti zprávu nevytiskne: K tomu je potřeba zavolat výstupní funkci, jako například [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
{
   _strerror_s(buffer, 80);
   fprintf( stderr, buffer );
}
```

Pokud *strErrMsg* je **NULL**, **_strerror_s –** vrátí řetězec v *vyrovnávací paměti* obsahující chybovou zprávu systému pro poslední volání knihovny které vytvořilo chybu. Řetězec chybové zprávy je ukončen znakem nového řádku ('\n'). Pokud *strErrMsg* není roven **NULL**, pak **_strerror_s –** vrátí řetězec v *vyrovnávací paměti* obsahující (v pořadí) zprávu řetězce, dvojtečku, mezeru, chybovou zprávu systému pro poslední volání knihovny chybu a znak nového řádku. Vaše Řetězcová zpráva může obsahovat nejvýše, 94 znaků.

Tyto funkce zkrátí chybovou zprávu, pokud její délka přesahuje *numberOfElements* -1. Výsledný řetězec v *vyrovnávací paměti* je vždy zakončený hodnotou null.

Aktuální číslo chyby pro **_strerror_s –** je uložen v proměnné [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Chybové zprávy systému jsou přístupné prostřednictvím proměnné [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), což je pole zpráv seřazené podle čísla chyby. **_strerror_s –** přistupuje k příslušné chybové zprávě pomocí **errno** hodnotu jako indexu proměnné **_sys_errlist**. Hodnota proměnné [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) je definována jako maximální počet prvků v **_sys_errlist** pole. Chcete-li přesné výsledky zavolejte **_strerror_s –** ihned poté, co knihovní rutina vrátí chybu. Jinak následná volání **strerror_s –** nebo **_strerror_s –** můžete přepsat **errno** hodnotu.

**_wcserror_s –** a **__wcserror_s –** jsou širokoznaké verze **strerror_s –** a **_strerror_s –** v uvedeném pořadí.

Tyto funkce ověřují své parametry. Pokud je vyrovnávací paměť **NULL** nebo pokud je parametr velikosti 0, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, vrátí funkce **EINVAL** a nastavte **errno** k **EINVAL**.

**_strerror_s –**, **_wcserror_s –**, a **__wcserror_s –** nejsou součástí definice ANSI, ale místo toho jsou jejími rozšířeními Microsoft. Nepoužívejte je kde je žádoucí přenositelnost; z důvodu kompatibility ANSI, použijte **strerror_s –** místo.

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky, takže odpadá nutnost určit velikost argumentu. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze těchto funkcí nejprve naplní vyrovnávací paměť hodnotou 0xFD. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror_s –**|**strerror_s**|**strerror_s**|**_wcserror_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strerror_s –**, **_strerror_s –**|\<String.h >|
|**_wcserror_s –**, **__wcserror_s –**|\<String.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [perror](perror-wperror.md).

## <a name="see-also"></a>Viz také:

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
