---
title: _strtime, _wstrtime
ms.date: 11/04/2016
api_name:
- _wstrtime
- _strtime
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
- _wstrtime
- _strtime
- wstrtime
- strtime
- _tstrtime
helpviewer_keywords:
- strtime function
- _strtime function
- _wstrtime function
- copying time to buffers
- wstrtime function
- tstrtime function
- _tstrtime function
- time, copying
ms.assetid: 9e538161-cf49-44ec-bca5-c0ab0b9e4ca3
ms.openlocfilehash: ea4a2b304dc30ec167f8a9094bcf278ff0d31f77
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946562"
---
# <a name="_strtime-_wstrtime"></a>_strtime, _wstrtime

Zkopírujte čas do vyrovnávací paměti. K dispozici jsou bezpečnější verze těchto funkcí; viz [_strtime_s, _wstrtime_s](strtime-s-wstrtime-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *_strtime(
   char *timestr
);
wchar_t *_wstrtime(
   wchar_t *timestr
);
template <size_t size>
char *_strtime(
   char (&timestr)[size]
); // C++ only
template <size_t size>
wchar_t *_wstrtime(
   wchar_t (&timestr)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*timestr*<br/>
Řetězec času.

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na výsledný řetězec znaků *timestr*.

## <a name="remarks"></a>Poznámky

Funkce **_strtime** kopíruje aktuální místní čas do vyrovnávací paměti, na kterou ukazuje *timestr*. Čas je formátován jako **HH: mm: SS** , kde **HH** je dvě číslice představující hodinu ve 24hodinovém zápisu, **mm** jsou dvě číslice představující minuty po hodinách a **SS** jsou dvě číslice představující sekundy. Například řetězec **18:23:44** představuje 23 minut a 44 sekund za 6 hodin. Vyrovnávací paměť musí být alespoň 9 bajtů dlouhá.

**_wstrtime** je **_strtime**verze s velkým znakem; argument a návratová hodnota **_wstrtime** jsou řetězce s velkým počtem znaků. Tyto funkce se chovají identicky jinak. Pokud je *timestr* ukazatel s **hodnotou null** , nebo pokud je *timestr* formátován nesprávně, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud může výjimka pokračovat, tyto funkce vrátí **hodnotu null** a nastaví **errno** na **EINVAL** , pokud *Timestr* bylo **null** nebo nastavte **errno** na **ERANGE** , pokud je *timestr* formátován nesprávně.

V C++nástroji mají tyto funkce přetížení šablony, které vyvolávají novější a zabezpečené protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime**|**_strtime**|**_strtime**|**_wstrtime**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strtime**|\<time.h>|
|**_wstrtime**|\<Time. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strtime.c
// compile with: /W3

#include <time.h>
#include <stdio.h>

int main( void )
{
   char tbuffer [9];
   _strtime( tbuffer ); // C4996
   // Note: _strtime is deprecated; consider using _strtime_s instead
   printf( "The current time is %s \n", tbuffer );
}
```

```Output
The current time is 14:21:44
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
