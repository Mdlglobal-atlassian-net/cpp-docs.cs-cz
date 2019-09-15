---
title: _strdate, _wstrdate
ms.date: 11/04/2016
api_name:
- _strdate
- _wstrdate
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
- api-ms-win-crt-time-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tstrdate
- wstrdate
- _wstrdate
- _strdate
- strdate
helpviewer_keywords:
- strdate function
- dates, copying
- tstrdate function
- _wstrdate function
- wstrdate function
- _strdate function
- _tstrdate function
- copying dates
ms.assetid: de8e4097-58f8-42ba-9dcd-cb4d9a9f1696
ms.openlocfilehash: e1164db5857643bac649e96493a3d66cdee3b6e2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958227"
---
# <a name="_strdate-_wstrdate"></a>_strdate, _wstrdate

Zkopírujte aktuální systémové datum do vyrovnávací paměti. K dispozici jsou bezpečnější verze těchto funkcí; viz [_strdate_s, _wstrdate_s](strdate-s-wstrdate-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *_strdate(
   char *datestr
);
wchar_t *_wstrdate(
   wchar_t *datestr
);
template <size_t size>
char *_strdate(
   char (&datestr)[size]
); // C++ only
template <size_t size>
wchar_t *_wstrdate(
   wchar_t (&datestr)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*datestr*<br/>
Ukazatel na vyrovnávací paměť obsahující formátovaný řetězec data.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto funkcí vrací ukazatel na výsledný řetězec znaků *datestr*.

## <a name="remarks"></a>Poznámky

K dispozici jsou bezpečnější verze těchto funkcí; viz [_strdate_s, _wstrdate_s](strdate-s-wstrdate-s.md). Doporučuje se používat bezpečnější funkce tam, kde je to možné.

Funkce **_strdate** zkopíruje aktuální systémové datum do vyrovnávací paměti, na kterou ukazuje *datestr*, formátovanou **mm**/**DD**/**RR**, kde **mm** jsou dvě číslice představující měsíc, **DD** představují dvě číslice představující den a **YY** jsou poslední dvě číslice roku. Například řetězec **12/05/99** představuje 5. prosince 1999. Vyrovnávací paměť musí být alespoň 9 bajtů dlouhá.

Pokud je *datestr* ukazatel s **hodnotou null** , je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce hodnotu-1 a nastaví **errno** na **EINVAL**.

**_wstrdate** je **_strdate**verze s velkým znakem; argument a návratová hodnota **_wstrdate** jsou řetězce s velkým počtem znaků. Tyto funkce se chovají identicky jinak.

V C++nástroji mají tyto funkce přetížení šablony, které vyvolávají novější a zabezpečené protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate**|**_strdate**|**_strdate**|**_wstrdate**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strdate**|\<time.h>|
|**_wstrdate**|\<Time. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// strdate.c
// compile with: /W3
#include <time.h>
#include <stdio.h>
int main()
{
    char tmpbuf[9];

    // Set time zone from TZ environment variable. If TZ is not set,
    // the operating system is queried to obtain the default value
    // for the variable.
    //
    _tzset();

    printf( "OS date: %s\n", _strdate(tmpbuf) ); // C4996
    // Note: _strdate is deprecated; consider using _strdate_s instead
}
```

```Output
OS date: 04/25/03
```

## <a name="see-also"></a>Viz také:

[Správa času](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
