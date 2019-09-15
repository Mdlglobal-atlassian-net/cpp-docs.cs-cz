---
title: _mbsnbcpy, _mbsnbcpy_l
ms.date: 11/04/2016
api_name:
- _mbsnbcpy
- _mbsnbcpy_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsnbcpy
- _ftcsncpy
- _mbsnbcpy
- mbsnbcpy_l
- _mbsnbcpy_l
helpviewer_keywords:
- mbsnbcpy function
- _mbsnbcpy_l function
- _mbsnbcpy function
- _tcsncpy function
- tcsncpy_l function
- _tcsncpy_l function
- mbsnbcpy_l function
- tcsncpy function
ms.assetid: 83d17b50-3cbf-4df9-bce8-3b6d52f85d04
ms.openlocfilehash: 9b8a5884b646baf582e6bb9868136ffe7c2a24cf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952255"
---
# <a name="_mbsnbcpy-_mbsnbcpy_l"></a>_mbsnbcpy, _mbsnbcpy_l

Zkopíruje **n** bajtů řetězce do cílového řetězce. Bezpečnější verze těchto funkcí jsou k dispozici – viz [_mbsnbcpy_s, _mbsnbcpy_s_l](mbsnbcpy-s-mbsnbcpy-s-l.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned char * _mbsnbcpy(
   unsigned char * strDest,
   const unsigned char * strSource,
   size_t count
);
unsigned char * _mbsnbcpy_l(
   unsigned char * strDest,
   const unsigned char * strSource,
   size_t count,
   _locale_t locale
);
template <size_t size>
unsigned char * _mbsnbcpy(
   unsigned char (&strDest)[size],
   const unsigned char * strSource,
   size_t count
); // C++ only
template <size_t size>
unsigned char * _mbsnbcpy_l(
   unsigned char (&strDest)[size],
   const unsigned char * strSource,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*strDest*<br/>
Cíl pro textový řetězec, který se má zkopírovat

*strSource*<br/>
Řetězec znaků, který se má zkopírovat

*výpočtu*<br/>
Počet bajtů, které mají být zkopírovány.

*jazyka*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

**_mbsnbcpy** vrací ukazatel na cílový textový řetězec. Žádná návratová hodnota není vyhrazena pro indikaci chyby.

## <a name="remarks"></a>Poznámky

Funkce **_mbsnbcpy** kopíruje *počet* bajtů z *strSource* do *strDest*. Pokud *počet* překročí velikost *strDest* nebo se překrývá zdrojový a cílový řetězec, chování **_mbsnbcpy** není definováno.

Pokud je *strSource* nebo *strDest* ukazatel s hodnotou null, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí funkce **hodnotu null** a nastaví **errno** na **EINVAL**.

Výstupní hodnota je ovlivněna nastavením kategorie **LC_CTYPE** národního prostředí; Další informace najdete v tématu [setlocale, _wsetlocale](setlocale-wsetlocale.md) . Verze těchto funkcí jsou identické, s tím rozdílem, že ty, které nemají příponu **_l** , používají aktuální národní prostředí a verze, které mají příponu **_l** , místo toho používají předaný parametr národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

> [!IMPORTANT]
> Tyto funkce můžou být zranitelné vůči hrozbám přetečení vyrovnávací paměti. K provedení libovolného kódu útočníka lze použít přetečení vyrovnávací paměti, což může způsobit neoprávněné zvýšení oprávnění a ohrozit systém. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

V C++nástroji mají tyto funkce přetížení šablony, které vyvolávají novější a bezpečnější protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncpy**|[strncpy](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)|**_mbsnbcpy**|[wcsncpy](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)|
|**_tcsncpy_l**|**_strncpy_l**|**_mbsnbcp_l**|**_wcsncpy_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsnbcpy**|\<Mbstring. h >|
|**_mbsnbcpy_l**|\<Mbstring. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Manipulace s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
