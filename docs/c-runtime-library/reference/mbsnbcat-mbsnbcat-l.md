---
title: _mbsnbcat –, _mbsnbcat_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbsnbcat_l
- _mbsnbcat
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
- mbsnbcat
- mbsnbcat_l
- _mbsnbcat
- _mbsnbcat_l
dev_langs:
- C++
helpviewer_keywords:
- tcsncat_l function
- _tcsncat function
- mbsnbcat_l function
- mbsnbcat function
- _mbsnbcat_l function
- _tcsncat_l function
- _mbsnbcat function
- tcsncat function
ms.assetid: aa0f1d30-0ddd-48d1-88eb-c6884b20fd91
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff7dc09e4305c16ebe710cb99c9e1bdd24490761
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405052"
---
# <a name="mbsnbcat-mbsnbcatl"></a>_mbsnbcat, _mbsnbcat_l

Připojí maximálně první **n** bajtů jednoho řetězce vícebajtových znaků do jiného. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [_mbsnbcat_s –, _mbsnbcat_s_l –](mbsnbcat-s-mbsnbcat-s-l.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned char *_mbsnbcat(
   unsigned char *dest,
   const unsigned char *src,
   size_t count
);
unsigned char *_mbsnbcat_l(
   unsigned char *dest,
   const unsigned char *src,
   size_t count,
   _locale_t locale
);
template <size_t size>
unsigned char *_mbsnbcat(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count
); // C++ only
template <size_t size>
unsigned char *_mbsnbcat_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*Cíle*<br/>
Řetězce ukončené hodnotou Null cílové vícebajtových znaků.

*src*<br/>
Řetězce ukončené hodnotou Null zdroj vícebajtových znaků.

*Počet*<br/>
Počet bajtů z *src* připojit k *cíle*.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

**_mbsnbcat –** vrací ukazatel na cílový řetězec. Žádnou návratovou hodnotu je vyhrazena indikující chybu.

## <a name="remarks"></a>Poznámky

**_Mbsnbcat –** funkce připojí maximálně první *počet* bajtů *src* k *cíle*. Pokud bajtů bezprostředně předcházející znak hodnoty null v *cíle* vedoucím bajtem, počáteční bajt *src* přepíše této úvodní bajt. V opačném počáteční bajt *src* přepíše ukončující znak null *cíle*. Pokud se objeví null bajtů v *src* před *počet* bajtů se připojují, **_mbsnbcat –** připojí všechny bajtů z *src*, až do znaku, hodnotu null. Pokud *počet* je větší než délka *src*, délka *src* slouží místě *počet*. Výsledný řetězec je byla ukončena s znak hodnoty null. Pokud kopírování probíhá mezi řetězce, které se překrývají, chování nedefinovaný.

Výstupní hodnota je ovlivňován nastavením **LC_CTYPE –** kategorie nastavení národního prostředí; viz [setlocale](setlocale-wsetlocale.md) Další informace. **_Mbsnbcat –** verzi funkce používá aktuální národní prostředí pro toto chování závislých na národním prostředí; **_mbsnbcat_l –** verze je stejná s tím rozdílem, že používají předaný v místo toho parametr národního prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

**Poznámka k zabezpečení** pomocí řetězce ukončené hodnotou null. Řetězce ukončené hodnotou null nesmí překročit velikost cílové vyrovnávací paměti. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).

Pokud *cíle* nebo *src* je **NULL**, funkce vygenerují chybu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud se zpracovává chyba, vrátí funkce **einval –** a nastaví **errno** k **einval –**.

V jazyce C++ tyto funkce mají šabloně přetížení, které vyvolání novější a zabezpečené svými protějšky tyto funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncat –**|[strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|**_mbsnbcat**|[wcsncat –](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|
|**_tcsncat_l –**|**_strncat_l**|**_mbsnbcat_l**|**_wcsncat_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsnbcat**|\<Mbstring.h >|
|**_mbsnbcat_l**|\<Mbstring.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbcpy, _mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[_mbsnbcat_s, _mbsnbcat_s_l](mbsnbcat-s-mbsnbcat-s-l.md)<br/>
