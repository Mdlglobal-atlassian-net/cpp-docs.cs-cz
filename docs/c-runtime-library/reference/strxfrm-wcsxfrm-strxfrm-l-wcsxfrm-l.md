---
title: strxfrm –, wcsxfrm –, _strxfrm_l –, _wcsxfrm_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4bc9746d2c98f1799cbdd244e7fc4d465fd705fa
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451716"
---
# <a name="strxfrm-wcsxfrm-strxfrml-wcsxfrml"></a>strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l

Transformace řetězec v závislosti na informace specifické pro národní prostředí.

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
Maximální počet znaků k umístění v *strDest*.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Vrátí délku transformovaných řetězec, není počítání ukončující znak hodnoty null. Pokud vrácená hodnota je větší než nebo rovna hodnotě *počet*, obsah *strDest* předpovědět. Při chybě jednotlivé funkce nastaví **errno** a vrátí **INT_MAX**. Pro neplatný znak **errno** je nastaven na **eilseq –**.

## <a name="remarks"></a>Poznámky

**Strxfrm –** funkce transformuje řetězec, na kterou odkazuje *strSource* do nového kompletován formulář, který je uložen v *strDest*. Více než *počet* jsou transformuje a umístí do výsledný řetězec znaků, včetně znak hodnoty null. Transformace se uskuteční pomocí jako národní prostředí **lc_collate –** kategorie nastavení. Další informace o **lc_collate –**, najdete v části [setlocale](setlocale-wsetlocale.md). **strxfrm –** používá aktuální národní prostředí pro své chování závislých na národním prostředí; **_strxfrm_l –** se shoduje s tím rozdílem, že používá národní prostředí předaná místo aktuální národní prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

Po transformaci volání **strcmp –** s dva řetězce transformovaných dává výsledky, které jsou stejné jako ty volání **strcoll –** u původního dva řetězce. Stejně jako u **strcoll –** a **stricoll –**, **strxfrm –** automaticky zpracovává řetězců vícebajtových znaků podle potřeby.

**wcsxfrm –** je verze široká charakterová **strxfrm –**; argumenty řetězce **wcsxfrm –** jsou široká charakterová ukazatele. Pro **wcsxfrm –**, po transformaci řetězec, volání **wcscmp –** s dva řetězce transformovaných dává výsledky, které jsou stejné jako ty volání **wcscoll –** u původní dva řetězce. **wcsxfrm –** a **strxfrm –** chovat jinak shodně. **wcsxfrm –** používá aktuální národní prostředí pro své chování závislých na národním prostředí; **_wcsxfrm_l –** používá národní prostředí předaná místo aktuální národní prostředí.

Tyto funkce ověřit jejich parametrů. Pokud *strSource* je ukazatel s hodnotou null, nebo *strDest* je **NULL** ukazatele (Pokud počet není nula), nebo pokud *počet* je větší než **INT_MAX**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno spuštění pokračovat, nastavte tyto funkce **errno** k **einval –** a vrátit **INT_MAX**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm –**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

Pořadí znaky znakové sady (znaková sada ASCII) v národním prostředí "C", je stejná jako lexicographic pořadí znaky. V jiným národním prostředím, ale může pořadí znaků ve znakové sadě liší od pořadí lexicographic znaků. Například v některých evropských národní prostředí znak "a" (hodnota 0x61) předchází znak ' &\#x00E4;. (hodnota 0xE4) v znaková sada, ale znak 'ä' předchází znak "a" lexicographically.

V národní prostředí, pro které se liší znakovou sadu a znak lexicographic pořadí, použijte **strxfrm –** na původní řetězce a potom **strcmp –** výsledné řetězce vytvořil lexicographic řetězec porovnání podle aktuální národní prostředí **lc_collate –** kategorie nastavení. Proto k porovnání dvou řetězců lexicographically ve výše uvedené národním prostředí použijte **strxfrm –** na původní řetězce, pak **strcmp –** výsledné řetězce. Alternativně můžete použít **strcoll –** místo **strcmp –** na původní řetězce.

**strxfrm –** je v podstatě představuje obálku kolem [LCMapString](http://msdn.microsoft.com/library/windows/desktop/dd318700) s **LCMAP_SORTKEY**.

Následující výraz hodnotu velikost pole potřebné k uchování **strxfrm –** transformace řetězec zdroje:

`1 + strxfrm( NULL, string, 0 )`

V národním prostředí "C", **strxfrm –** je ekvivalentní k následujícímu:

```C
strncpy( _string1, _string2, _count );
return( strlen( _string1 ) );
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strxfrm**|\<String.h >|
|**wcsxfrm**|\<String.h > nebo \<wchar.h >|
|**_strxfrm_l**|\<String.h >|
|**_wcsxfrm_l**|\<String.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll – funkce](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
