---
title: _mbsnbset, _mbsnbset_l
ms.date: 4/2/2020
api_name:
- _mbsnbset
- _mbsnbset_l
- _o__mbsnbset
- _o__mbsnbset_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsnbset
- mbsnbset_l
- _mbsnbset
- _mbsnbset_l
helpviewer_keywords:
- tcsnset function
- _tcsnset_l function
- _mbsnbset function
- _tcsnset function
- _mbsnbset_l function
- mbsnbset_l function
- tcsnset_l function
- mbsnbset function
ms.assetid: 8e46ef75-9a56-42d2-a522-a08450c67c19
ms.openlocfilehash: 57c6d1a81c9aac817b0028e8eccad38d03b0eef7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340548"
---
# <a name="_mbsnbset-_mbsnbset_l"></a>_mbsnbset, _mbsnbset_l

Nastaví první **n** bajtů vícebajtového znakového řetězce na zadaný znak. K dispozici jsou bezpečnější verze těchto funkcí. viz [_mbsnbset_s, _mbsnbset_s_l](mbsnbset-s-mbsnbset-s-l.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned char *_mbsnbset(
   unsigned char *str,
   unsigned int c,
   size_t count
);
unsigned char *_mbsnbset_l(
   unsigned char *str,
   unsigned int c,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Řetězec, který má být změněn.

*C*<br/>
Jednobajtové nebo vícebajtové znakové nastavení.

*Počet*<br/>
Počet bajtů, které mají být nastaveny.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

**_mbsnbset** vrátí ukazatel na změněný řetězec.

## <a name="remarks"></a>Poznámky

Funkce **_mbsnbset** a **_mbsnbset_l** nastavují maximálně první *bajty počtu* *bajtů str* až *c*. Pokud *je počet* větší než délka *str*, použije se místo *počtu*délka *str* . Pokud *c* je vícebajtový znak a nelze jej nastavit zcela do posledního bajtu určeného *počtem*, je poslední bajt doplněn prázdným znakem. **_mbsnbset** a **_mbsnbset_l** neumístí ukončující null na konec *str*.

**_mbsnbset** a **_mbsnbset_l** je podobná **_mbsnset**, s tím rozdílem, že nastavuje *počet* bajtů spíše než *počet* znaků *c*.

Pokud *str* je **NULL** nebo *count* je nula, tato funkce generuje neplatný parametr výjimku, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, **je chybné číslo** nastaveno na **hodnotu EINVAL** a funkce vrátí **hodnotu NULL**. Také pokud *c* není platný vícebajtový znak, **errno** je nastavena na **EINVAL** a místo toho se použije mezera.

Výstupní hodnota je ovlivněna nastavením nastavení **LC_CTYPE** kategorie národního prostředí; další informace naleznete [v tématu setlocale.](setlocale-wsetlocale.md) Verze **_mbsnbset** této funkce používá aktuální národní prostředí pro toto chování závislé na národním prostředí; **verze _mbsnbset_l** je identická s tím rozdílem, že místo toho používá parametr národního prostředí. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

**Poznámka k zabezpečení** Toto rozhraní API vznikne potenciální hrozbu způsobené problém přetečení vyrovnávací paměti. Problémy s přetečením vyrovnávací paměti jsou častou metodou systémového útoku, což vede k neoprávněnému zvýšení oprávnění. Další informace naleznete v [tématu Zabránění přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnset**|**_strnset**|**_mbsnbset**|**_wcsnset**|
|**_tcsnset_l**|**_strnset_l**|**_mbsnbset_l**|**_wcsnset_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsnbset**|\<mbstring.h>|
|**_mbsnbset_l**|\<mbstring.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_mbsnbset.c
// compile with: /W3
#include <mbstring.h>
#include <stdio.h>

int main( void )
{
   char string[15] = "This is a test";
   /* Set not more than 4 bytes of string to be *'s */
   printf( "Before: %s\n", string );
   _mbsnbset( string, '*', 4 ); // C4996
   // Note; _mbsnbset is deprecated; consider _mbsnbset_s
   printf( "After:  %s\n", string );
}
```

### <a name="output"></a>Výstup

```Output
Before: This is a test
After:  **** is a test
```

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
