---
title: Atol, _atoll_l –, _wtoll –, _wtoll_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _wtoll
- _atoll_l
- _wtoll_l
- atoll
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tstoll_l
- _wtoll
- _atoll_l
- _ttoll
- _tstoll
- _wtoll_l
- atoll
dev_langs:
- C++
helpviewer_keywords:
- atoll function
- _wtoll_l function
- _wtoll function
- _atoll_l function
ms.assetid: 5e85fcac-b351-4882-bff2-6e7c469b7fa8
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8c6c3876b3b4f603bd4a0bcdfeceee17583de300
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="atoll-atolll-wtoll-wtolll"></a>atoll, _atoll_l, _wtoll, _wtoll_l

Převede řetězec na **dlouho** **dlouho** celé číslo.

## <a name="syntax"></a>Syntaxe

```C
long long atoll(
   const char *str
);
long long _wtoll(
   const wchar_t *str
);
long long _atoll_l(
   const char *str,
   _locale_t locale
);
long long _wtoll_l(
   const wchar_t *str,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*str –*<br/>
Řetězec, který má být převeden.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Jednotlivé funkce vrátí **dlouho** **dlouho** hodnotu, která je produkovaný interpretace vstupu znaky jako číslo. Návratovou hodnotu pro **atol** je 0, pokud vstupní nelze převést na hodnotu daného typu.

Pro přetečení s velké kladné celočíselné hodnoty **atol** vrátí **LLONG_MAX**, a pro přetečení s velké záporné celočíselné hodnoty, vrátí **LLONG_MIN**.

Ve všech případech out-of-range **errno** je nastaven na **erange –**. Pokud je parametr, který se předává v **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce **errno** k **einval –** a vrátí 0.

## <a name="remarks"></a>Poznámky

Tyto funkce převést na řetězec znaků **dlouho** **dlouho** celočíselnou hodnotu.

Vstupní řetězec je posloupnost znaků, které lze interpretovat jako hodnotu zadaného typu. Funkce zastaví čtení vstupní řetězec u prvního znaku, který nelze rozpoznat jako součást číslo. Tento znak může být znak hodnoty null ('\0' nebo L '\0'), která ukončuje řetězec.

*Str* argument **atol** má následující formát:

> [*prázdné*] [*přihlašovací*] [*číslic*]

A *prázdné* se skládá z místa nebo kartě znaků, které se mají ignorovat; *přihlašovací* je buď plus (+) nebo minus (-) a *číslic* jsou jeden nebo více číslic.

**_wtoll –** je stejný jako **atol** s tím rozdílem, že trvá řetězec široké znaků jako parametr.

Verze tyto funkce, které mají **_l** příponu jsou shodné s verzí, které nemají, s výjimkou toho, aby využívaly parametr národního prostředí, který se předává v místo aktuální národní prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tstoll**|**Atol**|**Atol**|**_wtoll**|
|**_tstoll_l**|**_atoll_l**|**_atoll_l**|**_wtoll_l**|
|**_ttoll**|**_atoll**|**_atoll**|**_wtoll**|

## <a name="requirements"></a>Požadavky

|Rutiny|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**Atol**, **_atoll_l –**|\<stdlib.h>|
|**_wtoll –**, **_wtoll_l –**|\<stdlib.h > nebo \<wchar.h >|

## <a name="example"></a>Příklad

Tento program ukazuje způsob použití **atol** funkce k převedení čísel uložené jako řetězce pro číselné hodnoty.

```C
// crt_atoll.c
// Build with: cl /W4 /Tc crt_atoll.c
// This program shows how to use the atoll
// functions to convert numbers stored as
// strings to numeric values.
#include <stdlib.h>
#include <stdio.h>
#include <errno.h>

int main(void)
{
    char *str = NULL;
    long long value = 0;

    // An example of the atoll function
    // with leading and trailing white spaces.
    str = "  -27182818284 ";
    value = atoll(str);
    printf("Function: atoll(\"%s\") = %lld\n", str, value);

    // Another example of the atoll function
    // with an arbitrary decimal point.
    str = "314127.64";
    value = atoll(str);
    printf("Function: atoll(\"%s\") = %lld\n", str, value);

    // Another example of the atoll function
    // with an overflow condition occurring.
    str = "3336402735171707160320";
    value = atoll(str);
    printf("Function: atoll(\"%s\") = %lld\n", str, value);
    if (errno == ERANGE)
    {
       printf("Overflow condition occurred.\n");
    }
}
```

```Output
Function: atoll("  -27182818284 ") = -27182818284
Function: atoll("314127.64") = 314127
Function: atoll("3336402735171707160320") = 9223372036854775807
Overflow condition occurred.

```

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
