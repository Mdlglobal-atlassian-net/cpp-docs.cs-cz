---
title: strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l
ms.date: 4/2/2020
api_name:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
- _o__strxfrm_l
- _o__wcsxfrm_l
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strxfrm
- _tcsxfrm
- wcsxfrm
helpviewer_keywords:
- strxfrm_l function
- _tcsxfrm function
- _strxfrm_l function
- strxfrm function
- wcsxfrm_l function
- wcsxfrm function
- string comparison [C++], transforming strings
- tcsxfrm function
- strings [C++], comparing locale
- _wcsxfrm_l function
ms.assetid: 6ba8e1f6-4484-49aa-83b8-bc2373187d9e
ms.openlocfilehash: aabe7e7c2e44f558b936e0fd4c6fa4a85dc582f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362974"
---
# <a name="strxfrm-wcsxfrm-_strxfrm_l-_wcsxfrm_l"></a>strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l

Transformujte řetězec na základě informací specifických pro národní prostředí.

## <a name="syntax"></a>Syntaxe

```C
size_t strxfrm(
   char *strDest,
   const char *strSource,
   size_t count
);
size_t wcsxfrm(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count
);
size_t _strxfrm_l(
   char *strDest,
   const char *strSource,
   size_t count,
   _locale_t locale
);
size_t wcsxfrm_l(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*strDest*<br/>
Cílový řetězec.

*strSource*<br/>
Zdrojový řetězec.

*Počet*<br/>
Maximální počet znaků, které mají být umístit *do strDest*.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Vrátí délku transformovaného řetězce, nepočítá ukončující znak null. Pokud je vrácená hodnota větší nebo rovna *count*, obsah *strDest* je nepředvídatelné. Při chybě každá funkce nastaví **errno** a vrátí **INT_MAX**. Pro neplatný znak je **errno** nastaveno na **EILSEQ**.

## <a name="remarks"></a>Poznámky

Funkce **strxfrm** transformuje řetězec odkazovaný *strSource* na novou kompletovanou formu, která je uložena v *strDest*. Ne více než *počet* znaků, včetně znaku null, jsou transformovány a umístěny do výsledného řetězce. Transformace se provádí pomocí nastavení **kategorie LC_COLLATE** národního prostředí. Další informace o **LC_COLLATE**naleznete v [tématu setlocale](setlocale-wsetlocale.md). **strxfrm** používá aktuální národní prostředí pro jeho chování závislé na národním prostředí; **_strxfrm_l** je identické s tím rozdílem, že používá národní prostředí předané v namísto aktuální národní prostředí. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Po transformaci volání **strcmp** se dvěma transformovanými řetězci dává výsledky identické s výsledky volání **strcoll** aplikované na původní dva řetězce. Stejně jako **u strcoll** a **stricoll** **strxfrm** automaticky zpracovává vícebajtové řetězce znaků podle potřeby.

**wcsxfrm** je širokoznaková verze **strxfrm**; argumenty řetězce **wcsxfrm** jsou ukazatele širokých znaků. Pro **wcsxfrm**, po transformaci řetězce, volání **wcscmp** se dvěma transformovanými řetězci dává výsledky shodné s výsledky volání **wcscoll** aplikované na původní dva řetězce. **wcsxfrm** a **strxfrm** se chovají stejně jinak. **wcsxfrm** používá aktuální národní prostředí pro jeho chování závislé na národním prostředí; **_wcsxfrm_l** místo aktuálního národního prostředí používá národní prostředí předané.

Tyto funkce ověřují jejich parametry. Pokud *strSource* je ukazatel null nebo *strDest* je **ukazatel NULL** (pokud počet je nula), nebo pokud *počet* je větší než **INT_MAX**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je spuštění povoleno pokračovat, tyto funkce nastavit **errno** na **EINVAL** a vrátit **INT_MAX**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

V národním prostředí "C" je pořadí znaků v znakové sadě (znaková sada ASCII) stejné jako lexikografické pořadí znaků. V jiných národních prostředích se však pořadí znaků v znakové sadě může lišit od lexikografického pořadí znaků. Například v některých evropských národních prostředích znak 'a' (hodnota 0x61) předchází znaku '&\#x00E4;" (hodnota 0xE4) v znakové sadě, ale znak 'ä' předchází znak 'a' lexicographically.

V národních prostředích, pro která se liší znaková sada a lexikografické pořadí znaků, použijte **strxfrm** na původnířetězce a potom **strcmp** na výsledných řetězcích k vytvoření lexikografického porovnání řetězců podle nastavení LC_COLLATE **kategorie** aktuálního národního prostředí. Chcete-li tedy porovnat dva řetězce lexicographically ve výše uvedeném národním prostředí, použijte **strxfrm** na původní řetězce, pak **strcmp** na výsledné řetězce. Alternativně můžete použít **strcoll** spíše než **strcmp** na původní řetězce.

**strxfrm** je v podstatě obal kolem [LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw) s **LCMAP_SORTKEY**.

Hodnota následujícího výrazu je velikost pole potřebného k uložení transformace **strxfrm** zdrojového řetězce:

`1 + strxfrm( NULL, string, 0 )`

Pouze v národním prostředí "C" je **strxfrm** ekvivalentní následujícímu:

```C
strncpy( _string1, _string2, _count );
return( strlen( _string1 ) );
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strxfrm**|\<string.h>|
|**wcsxfrm**|\<string.h> \<nebo wchar.h>|
|**_strxfrm_l**|\<string.h>|
|**_wcsxfrm_l**|\<string.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
