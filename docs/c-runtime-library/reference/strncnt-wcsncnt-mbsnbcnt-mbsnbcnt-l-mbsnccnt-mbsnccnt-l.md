---
title: _strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l
ms.date: 4/2/2020
api_name:
- _mbsnbcnt_l
- _mbsnccnt
- _wcsncnt
- _strncnt
- _mbsnccnt_l
- _mbsnbcnt
- _o__mbsnbcnt
- _o__mbsnbcnt_l
- _o__mbsnccnt
- _o__mbsnccnt_l
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
- _mbsnbcnt
- wcsncnt
- _tcsnbcnt
- _mbsnccnt
- _ftcsnbcnt
- mbsnbcnt
- strncnt
- mbsnbcnt_l
- mbsnccnt_l
- mbsnccnt
- _strncnt
- _wcsncnt
helpviewer_keywords:
- _strncnt function
- _mbsnbcnt function
- _mbsnbcnt_l function
- _mbsnccnt_l function
- mbsnbcnt_l function
- mbsnbcnt function
- tcsnbcnt function
- mbsnccnt_l function
- strncnt function
- _tcsnbcnt function
- mbsnccnt function
- wcsncnt function
- _mbsnccnt function
- _wcsncnt function
ms.assetid: 2a022e9e-a307-4acb-a66b-e56e5357f848
ms.openlocfilehash: bfd339a38dd5df30ece72059525860603ee10748
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364174"
---
# <a name="_strncnt-_wcsncnt-_mbsnbcnt-_mbsnbcnt_l-_mbsnccnt-_mbsnccnt_l"></a>_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l

Vrátí počet znaků nebo bajtů v rámci zadaného počtu.

> [!IMPORTANT]
> **_mbsnbcnt**, **_mbsnbcnt_l**, **_mbsnccnt**a **_mbsnccnt_l** nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
size_t _strncnt(
   const char *str,
   size_t count
);
size_t _wcsncnt(
   const wchar_t *str,
   size_t count
);
size_t _mbsnbcnt(
   const unsigned char *str,
   size_t count
);
size_t _mbsnbcnt_l(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
size_t _mbsnccnt(
   const unsigned char *str,
   size_t count
);
size_t _mbsnccnt_l(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Řetězec, který má být zkoumán.

*Počet*<br/>
Počet znaků nebo bajtů, které mají být zkontrolovány v *str*.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

**_mbsnbcnt** a **_mbsnbcnt_l** vrátí počet bajtů nalezených v prvním *počtu* vícebajtových znaků *str*. **_mbsnccnt** a **_mbsnccnt_l** vrátí počet znaků nalezených v prvním *počtu* bajtů *str*. Pokud je před dokončením kontroly *str* zjištěn znak null, vrátí počet bajtů nebo znaků nalezených před znakem null. Pokud *str* se skládá z méně než *počet* znaků nebo bajtů, vrátí počet znaků nebo bajtů v řetězci. Pokud *počet* je menší než nula, vrátí 0. V předchozích verzích měly tyto funkce vrácenou hodnotu typu **int** spíše než **size_t**.

**_strncnt** vrátí počet znaků v prvním *počtu* bajtů jednobajtového řetězce *str*. **_wcsncnt** vrátí počet znaků v prvním *počtu* široké znaky široký znak řetězce *str*.

## <a name="remarks"></a>Poznámky

**_mbsnbcnt** a **_mbsnbcnt_l** spočítat počet bajtů nalezených v prvním *počtu* vícebajtových znaků *str*. **_mbsnbcnt** a **_mbsnbcnt_l** nahradit **mtob** a měl by být použit místo **mtob**.

**_mbsnccnt** a **_mbsnccnt_l** spočítat počet znaků nalezených v prvním *počtu* bajtů *str*. Pokud **_mbsnccnt** a **_mbsnccnt_l** setkat s prázdným znakem v druhém bajtu dvoubajtového znaku, první bajt je také považován za nulu a není zahrnut v hodnotě vráceného počtu. **_mbsnccnt** a **_mbsnccnt_l** nahradit **btom** a měl by být použit místo **btom**.

Pokud *str* je **ukazatel NULL** nebo je *počet* je 0, tyto funkce vyvolat neplatný parametr obslužné rutiny, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md), **errno** je nastavena na **EINVAL**a funkce vrátí 0.

Výstupní hodnota je ovlivněna nastavením nastavení **LC_CTYPE** kategorie národního prostředí; další informace naleznete [v tématu setlocale.](setlocale-wsetlocale.md) Verze těchto funkcí bez **přípony _l** pro toto chování závislé na národním prostředí používají aktuální národní prostředí. verze s **příponou _l** jsou identické s tím rozdílem, že místo toho používají parametr národního prostředí. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|-------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnbcnt**|**_strncnt**|**_mbsnbcnt**|**_wcsncnt**|
|**_tcsnccnt**|**_strncnt**|**_mbsnbcnt**|neuvedeno|
|**_wcsncnt**|neuvedeno|neuvedeno|**_mbsnbcnt**|
|**_wcsncnt**|neuvedeno|neuvedeno|**_mbsnccnt**|
|neuvedeno|neuvedeno|**_mbsnbcnt_l**|**_mbsnccnt_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsnbcnt**|\<mbstring.h>|
|**_mbsnbcnt_l**|\<mbstring.h>|
|**_mbsnccnt**|\<mbstring.h>|
|**_mbsnccnt_l**|\<mbstring.h>|
|**_strncnt**|\<tchar.h>|
|**_wcsncnt**|\<tchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_mbsnbcnt.c

#include  <mbstring.h>
#include  <stdio.h>

int main( void )
{
   unsigned char str[] = "This is a multibyte-character string.";
   unsigned int char_count, byte_count;
   char_count = _mbsnccnt( str, 10 );
   byte_count = _mbsnbcnt( str, 10 );
   if ( byte_count - char_count )
      printf( "The first 10 characters contain %d multibyte characters\n", char_count );
   else
      printf( "The first 10 characters are single-byte.\n");
}
```

### <a name="output"></a>Výstup

```Output
The first 10 characters are single-byte.
```

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
