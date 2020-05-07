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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 3ab3f978d4162f968f518272612c18767247f2fb
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912353"
---
# <a name="strxfrm-wcsxfrm-_strxfrm_l-_wcsxfrm_l"></a>strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l

Transformuje řetězec na základě informací specifických pro národní prostředí.

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
Cílový řetězec

*strSource*<br/>
Zdrojový řetězec

*výpočtu*<br/>
Maximální počet znaků, které mají být umístěny v *strDest*.

*locale*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Vrátí délku transformované řetězce, který nepočítá ukončující znak null. Pokud je vrácená hodnota větší než nebo rovna *Count*, obsah *strDest* je nepředvídatelné. Při chybě každá funkce nastaví **errno** a vrátí **INT_MAX**. Pro neplatný znak je **errno** nastaven na **EILSEQ**.

## <a name="remarks"></a>Poznámky

Funkce **strxfrm** transformuje řetězec, na který odkazuje *strSource* do nové Kompletované formuláře, který je uložený v *strDest*. Transformují a umístí do výsledného řetězce více než znaků *Count* , včetně znaku null. Transformace se provádí pomocí nastavení **LC_COLLATE** kategorie národního prostředí. Další informace o **LC_COLLATE**najdete v tématu [setlocale](setlocale-wsetlocale.md). **strxfrm** používá aktuální národní prostředí pro své chování závislé na národním prostředí; **_strxfrm_l** je totožný s tím rozdílem, že používá předané národní prostředí namísto aktuálního národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Po transformaci volání **strcmp** s těmito dvěma transformovanými řetězci vrátí výsledky identické s voláním **strcoll –** použitým pro původní dva řetězce. Stejně jako u **strcoll –** a **stricoll** **strxfrm** automaticky zpracovává řetězce vícebajtových znaků podle potřeby.

**Wcsxfrm** je **strxfrm**verze s velkým znakem; řetězcové argumenty **Wcsxfrm** jsou ukazatele na šířku znaků. Pro **Wcsxfrm**, po transformaci řetězce, volání **wcscmp** s těmito dvěma transformovanými řetězci vrátí výsledky identické s voláním **wcscoll** použitým pro původní dva řetězce. **Wcsxfrm** a **strxfrm** se chovají stejně jinak. **Wcsxfrm** používá aktuální národní prostředí pro své chování závislé na národním prostředí; **_wcsxfrm_l** používá předané národní prostředí namísto aktuálního národního prostředí.

Tyto funkce ověřují své parametry. Pokud je *strSource* ukazatel s hodnotou null, nebo je *StrDest* ukazatel s **hodnotou null** (Pokud není počet nula), nebo pokud je *počet* větší než **INT_MAX**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, tyto funkce nastaví **errno** na **EINVAL** a vrátí **INT_MAX**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

V národním prostředí "C" je pořadí znaků ve znakové sadě (znaková sada ASCII) stejné jako lexikografickým pořadím pořadí znaků. V jiných národních prostředích se však pořadí znaků ve znakové sadě může lišit od pořadí znaků lexikografickým pořadím. Například v určitých evropských národních prostředích před znakem "a" (Value 0x61) předchází znak "&\#x00E4;" (Value 0xE4) ve znakové sadě, ale znak "ä" předchází znaku "a" lexikograficky.

V národních prostředích, pro která se liší znaková sada a lexikografickým pořadím znaků, použijte **strxfrm** u původních řetězců a potom **strcmp** výsledných řetězců k vytvoření porovnání řetězců lexikografickým pořadím podle nastavení kategorie **LC_COLLATE** aktuálního národního prostředí. Proto pro porovnání dvou řetězců lexikograficky ve výše uvedeném národním prostředí použijte **strxfrm** na původních řetězcích a pak **strcmp** na výsledných řetězcích. Alternativně můžete použít **strcoll –** místo **strcmp** na původních řetězcích.

**strxfrm** je v podstatě Obálka kolem [LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw) s **LCMAP_SORTKEY**.

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
|**strxfrm**|\<String. h>|
|**wcsxfrm**|\<String. h> nebo \<WCHAR. h>|
|**_strxfrm_l**|\<String. h>|
|**_wcsxfrm_l**|\<String. h> nebo \<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Jazyka](../../c-runtime-library/locale.md)<br/>
[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
