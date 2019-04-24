---
title: strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l
ms.date: 11/04/2016
apiname:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 4e4f5bb6639cbeee0f004f94f09177c08394d43e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258712"
---
# <a name="strxfrm-wcsxfrm-strxfrml-wcsxfrml"></a>strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l

Převést řetězec na základě informací specifických pro národní prostředí.

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
Maximální počet znaků, které mají být umístěny *strDest*.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Vrátí délku objektu převedený řetězec výčtu nebudou započteny ukončující znak null. Pokud vrácená hodnota je větší než nebo rovna hodnotě *počet*, obsah *strDest* nepředvídatelné. V případě chyby každá funkce nastaví **errno** a vrátí **INT_MAX**. Pro neplatný znak **errno** je nastavena na **EILSEQ**.

## <a name="remarks"></a>Poznámky

**Strxfrm –** funkce transformuje řetězce odkazované *strSource* do nového porovnávány formulář, který je uložen v *strDest*. Více než *počet* znaků, včetně znaku null jsou transformovány a umístí do výsledného řetězce. Transformace se uskuteční pomocí národního prostředí **LC_COLLATE** nastavením kategorie. Další informace o **LC_COLLATE**, naleznete v tématu [setlocale](setlocale-wsetlocale.md). **strxfrm –** používá aktuální národní prostředí pro své chování závislé na národním prostředí **_strxfrm_l –** je totožný s tím rozdílem, že používá národní prostředí namísto aktuálního národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Po transformaci volání **strcmp –** s dva řetězce transformovaný vrací výsledky, které jsou stejné jako ty volání **strcoll –** u původní dva řetězce. Stejně jako u **strcoll –** a **stricoll –**, **strxfrm –** automaticky zpracovává vícebajtové znakové řetězce podle potřeby.

**wcsxfrm –** je verze širokého znaku **strxfrm –**; argumenty řetězce **wcsxfrm –** jsou širokoznaké ukazatele. Pro **wcsxfrm –**, po provedení transformace řetězce, volání **wcscmp –** s dva řetězce transformovaný vrací výsledky, které jsou stejné jako ty volání **wcscoll –** u původní dva řetězce. **wcsxfrm –** a **strxfrm –** se jinak chovají stejně. **wcsxfrm –** používá aktuální národní prostředí pro své chování závislé na národním prostředí **_wcsxfrm_l –** používá národní prostředí namísto aktuálního národního prostředí.

Tyto funkce ověřují své parametry. Pokud *strSource* je ukazatel s hodnotou null, nebo *strDest* je **NULL** ukazatel (Pokud je počet nula), nebo pokud *počet* je větší než **INT_MAX**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Pokud smí provádění pokračovat, tyto funkce nastaví **errno** k **EINVAL** a vrátit **INT_MAX**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

Pořadí znaků ve znakové sadě (znaková sada ASCII) v národním prostředí "C", je stejné jako lexikografické pořadí znaků. V ostatních národních prostředí, ale pořadí znaků ve znakové sadě může lišit od pořadí lexikografických znaků. Například v některých evropských národní prostředí, znak "a" (hodnota 0x61) předchází znak "&\#x00E4;. (hodnota 0xE4) do množiny znaků, ale znak "ä" předchází znak "a" lexicographically.

V prostředí, pro které se liší znakové sady a lexikografickým pořadím znaků, použijte **strxfrm –** na původním řetězců a potom **strcmp –** na výsledného řetězce vytvořit lexikografickým řetězec porovnání podle aktuálního národního prostředí **LC_COLLATE** nastavením kategorie. Díky tomu se porovná dva řetězce lexikograficky ve výše uvedené národní prostředí, použijte **strxfrm –** na původním řetězců, pak **strcmp –** na výsledného řetězce. Alternativně můžete použít **strcoll –** spíše než **strcmp –** na původním řetězců.

**strxfrm –** je v podstatě Obálka kolem [LCMapString](/windows/desktop/api/winnls/nf-winnls-lcmapstringa) s **LCMAP_SORTKEY**.

Následující výraz hodnotu velikosti pole potřebných k uchování **strxfrm –** transformace řetězec zdroje:

`1 + strxfrm( NULL, string, 0 )`

V národním prostředí "C" pouze **strxfrm –** je ekvivalentní následujícímu:

```C
strncpy( _string1, _string2, _count );
return( strlen( _string1 ) );
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strxfrm**|\<string.h>|
|**wcsxfrm**|\<String.h > nebo \<wchar.h >|
|**_strxfrm_l**|\<string.h>|
|**_wcsxfrm_l**|\<String.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
