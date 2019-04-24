---
title: _strtime, _wstrtime
ms.date: 11/04/2016
apiname:
- _wstrtime
- _strtime
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 9d874321418854a703886eb80ee23ac1cba57fa4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223088"
---
# <a name="strtime-wstrtime"></a>_strtime, _wstrtime

Kopírování času do vyrovnávací paměti. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [_strtime_s – _wstrtime_s –](strtime-s-wstrtime-s.md).

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
Řetězce času.

## <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na výsledný řetězec znak *timestr*.

## <a name="remarks"></a>Poznámky

**_Strtime –** funkce kopíruje do vyrovnávací paměti, na které odkazuje aktuálním místním časem *timestr*. Čas je formátován jako **hh: mm:** kde **hh** dvou číslic představující hodiny ve 24hodinovém formátu, je **mm** je dvou číslic představující minut za hodinu a **ss** je dvou číslic představující sekund. Například řetězec **18:23:44** představuje 23 minut a 44 sekund po 6 hodin Vyrovnávací paměť musí být dlouhý aspoň 9 bajtů.

**_wstrtime –** je verze širokého znaku **_strtime –**; argument a návratová hodnota funkce **_wstrtime –** jsou širokoznaké řetězce. Tyto funkce chovají identicky jinak. Pokud *timestr* je **NULL** ukazatele nebo pokud *timestr* je v nesprávném formátu, neplatný je vyvolána obslužná rutina parametru, jak je popsáno v [parametr Ověření](../../c-runtime-library/parameter-validation.md). Pokud se výjimka může pokračovat, vrátí tyto funkce **NULL** a nastavte **errno** k **EINVAL** Pokud *timestr* byla **NULL** nebo nastavte **errno** k **ERANGE** Pokud *timestr* je v nesprávném formátu.

V jazyce C++ mají tyto funkce přetížení šablon, která vyvolávají novější, zabezpečené protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime**|**_strtime**|**_strtime**|**_wstrtime**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strtime**|\<time.h>|
|**_wstrtime**|\<Time.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
