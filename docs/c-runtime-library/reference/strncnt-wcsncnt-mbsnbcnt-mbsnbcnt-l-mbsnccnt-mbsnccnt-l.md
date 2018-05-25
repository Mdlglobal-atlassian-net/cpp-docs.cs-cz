---
title: _strncnt –, _wcsncnt –, _mbsnbcnt –, _mbsnbcnt_l –, _mbsnccnt –, _mbsnccnt_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbsnbcnt_l
- _mbsnccnt
- _wcsncnt
- _strncnt
- _mbsnccnt_l
- _mbsnbcnt
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 066431205ecd7aa2b193350ccda4a83decac0458
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
---
# <a name="strncnt-wcsncnt-mbsnbcnt-mbsnbcntl-mbsnccnt-mbsnccntl"></a>_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l

Vrátí počet znaků nebo bajtů v rámci zadaného počtu.

> [!IMPORTANT]
> **_mbsnbcnt –**, **_mbsnbcnt_l –**, **_mbsnccnt –**, a **_mbsnccnt_l –** nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*str –*<br/>
Řetězec prověřit.

*Počet*<br/>
Počet znaků nebo bajtů v *str*.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

**_mbsnbcnt –** a **_mbsnbcnt_l –** vrátí počet bajtů najít v prvním *počet* vícebajtové znaky z *str*. **_mbsnccnt –** a **_mbsnccnt_l –** vrátí počet znaků, najít v prvním *počet* bajtů *str*. Pokud je znak hodnoty null došlo před zkoumání *str* má dokončení vrátí počet bajtů nebo znaků, nalezeno před znak hodnoty null. Pokud *str* se skládá z méně než *počet* znaků nebo bajtů, vrátí počet znaků nebo bajtů v řetězci. Pokud *počet* je menší než nula, že budou vracet 0. V předchozích verzích se tyto funkce měl návratovou hodnotu typu **int** místo **size_t –**.

**_strncnt –** vrátí počet znaků v prvním *počet* bajtů řetězce jednobajtové *str*. **_wcsncnt –** vrátí počet znaků v prvním *počet* široké znaky řetězce široká charakterová *str*.

## <a name="remarks"></a>Poznámky

**_mbsnbcnt –** a **_mbsnbcnt_l –** počet bajtů najít v prvním *počet* vícebajtové znaky z *str*. **_mbsnbcnt –** a **_mbsnbcnt_l –** nahradit **mtob** a mělo by se místě **mtob**.

**_mbsnccnt –** a **_mbsnccnt_l –** určený počet znaků najít v prvním *počet* bajtů *str*. Pokud **_mbsnccnt –** a **_mbsnccnt_l –** stane znak hodnoty null v druhé bajt dvoubajtové znakové, první bajt považuje za také mít hodnotu null a není součástí hodnota vrácená počtu. **_mbsnccnt –** a **_mbsnccnt_l –** nahradit **btom** a mělo by se místě **btom**.

Pokud *str* je **NULL** ukazatel nebo *počet* je 0, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md), **errno** je nastaven na **einval –**, a funkce vrátí hodnotu 0.

Výstupní hodnota je ovlivňován nastavením **LC_CTYPE –** kategorie nastavení národního prostředí; viz [setlocale](setlocale-wsetlocale.md) Další informace. Verze tyto funkce bez **_l** příponu využívání aktuální národní prostředí pro toto chování závislých na národním prostředí, verze s **_l** příponu jsou shodné s tím rozdílem, že používají parametr národního prostředí Místo toho předaná. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|-------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnbcnt –**|**_strncnt**|**_mbsnbcnt**|**_wcsncnt**|
|**_tcsnccnt**|**_strncnt**|**_mbsnbcnt**|není k dispozici|
|**_wcsncnt**|není k dispozici|není k dispozici|**_mbsnbcnt**|
|**_wcsncnt**|není k dispozici|není k dispozici|**_mbsnccnt**|
|není k dispozici|není k dispozici|**_mbsnbcnt_l**|**_mbsnccnt_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsnbcnt**|\<Mbstring.h >|
|**_mbsnbcnt_l**|\<Mbstring.h >|
|**_mbsnccnt**|\<Mbstring.h >|
|**_mbsnccnt_l**|\<Mbstring.h >|
|**_strncnt**|\<tchar.h>|
|**_wcsncnt**|\<tchar.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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
