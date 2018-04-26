---
title: _mbsnbcat_s –, _mbsnbcat_s_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _mbsnbcat_s_l
- _mbsnbcat_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbsnbcat_s
- mbsnbcat_s
- _mbsnbcat_s_l
- mbsnbcat_s_l
dev_langs:
- C++
helpviewer_keywords:
- _tcsncat function
- mbsnbcat_s function
- _mbsnbcat_s function
- _mbsnbcat_s_l function
- _tcsncat_s_l function
- tcsncat_s_l function
- mbsnbcat_s_l function
- tcsncat function
ms.assetid: 2c9e9be7-d979-4a54-8ada-23428b6648a9
caps.latest.revision: 28
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 78497f5915ec48afb677db9ee6850b733b28ae00
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="mbsnbcats-mbsnbcatsl"></a>_mbsnbcat_s, _mbsnbcat_s_l

Připojí k vícebajtový řetězec, maximálně první **n** bajtů jiné řetězce vícebajtových znaků. Toto jsou verze [_mbsnbcat –, _mbsnbcat_l –](mbsnbcat-mbsnbcat-l.md) vylepšení zabezpečení, které mají, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _mbsnbcat_s(
   unsigned char *dest,
   size_t sizeInBytes,
   const unsigned char *src,
   size_t count
);
errno_t _mbsnbcat_s_l(
   unsigned char *dest,
   size_t sizeInBytes,
   const unsigned char *src,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t _mbsnbcat_s(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbsnbcat_s_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*Cíle*<br/>
Řetězce ukončené hodnotou Null cílové vícebajtových znaků.

*sizeInBytes*<br/>
Velikost *cíle* vyrovnávací paměti v bajtech.

*src*<br/>
Řetězce ukončené hodnotou Null zdroj vícebajtových znaků.

*Počet*<br/>
Počet bajtů z *src* připojit k *cíle*.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěšného; jinak kód chyby.

### <a name="error-conditions"></a>Chybové stavy

|**Cíle**|*sizeInBytes*|*src*|Návratová hodnota|
|------------|-------------------|-----------|------------------|
|**HODNOTU NULL**|všechny|všechny|**EINVAL –**|
|všechny|<= 0|všechny|**EINVAL –**|
|všechny|všechny|**HODNOTU NULL**|**EINVAL –**|

Pokud některá z podmínek chybě dojde, funkce vygeneruje chybu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud se zpracovává chyba, vrátí funkce **einval –** a nastaví **errno** k **einval –**.

## <a name="remarks"></a>Poznámky

**_Mbsnbcat_s –** funkce připojí k *cíle*, maximálně první *počet* bajtů *src*. Pokud bajtů bezprostředně předchází znak hodnoty null v *cíle* je úvodní bajt je přepsány počáteční bajt *src*. V opačném počáteční bajt *src* přepíše ukončující znak null *cíle*. Pokud se objeví null bajtů v *src* před *počet* bajtů se připojují, **_mbsnbcat_s –** připojí všechny bajtů z *src*, až hodnotu null znak. Pokud *počet* je větší než délka *src*, délka *src* slouží místě *počet*. Výsledný řetězec se ukončila příkazem znak hodnoty null. Pokud kopírování probíhá mezi řetězce, které se překrývají, chování nedefinovaný.

Výstupní hodnota je ovlivňován nastavením **LC_CTYPE –** kategorie nastavení národního prostředí; viz [setlocale _wsetlocale](setlocale-wsetlocale.md) Další informace. Verze tyto funkce jsou identické, s tím rozdílem, že ty, které nejsou mít **_l** příponu použít aktuální národní prostředí a ty, které mají **_l** příponu, použijte parametr národního prostředí to je Předaná. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

V jazyce C++ použití tyto funkce se zjednodušilo díky šabloně přetížení; přetížení můžete automaticky odvození délka vyrovnávací paměti a eliminovat potřeba zadat argument velikost a jejich funkce novější se bezpečnější můžete automaticky použijí k nahrazení starší, méně bezpečné funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze těchto funkcí nejprve vyplnit vyrovnávací paměť s 0xFD. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncat –**|[strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|**_mbsnbcat_s**|[wcsncat –](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|
|**_tcsncat_s_l –**|**_strncat_s_l**|**_mbsnbcat_s_l**|**_wcsncat_s_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsnbcat_s**|\<Mbstring.h >|
|**_mbsnbcat_s_l**|\<Mbstring.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbcpy, _mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[_mbsnbcpy_s, _mbsnbcpy_s_l](mbsnbcpy-s-mbsnbcpy-s-l.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)<br/>
