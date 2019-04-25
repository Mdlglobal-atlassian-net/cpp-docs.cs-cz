---
title: _mbsnbcpy, _mbsnbcpy_l
ms.date: 11/04/2016
apiname:
- _mbsnbcpy
- _mbsnbcpy_l
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
ms.openlocfilehash: 1f22e8066b5b32feef642b01ad82955935a450e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285569"
---
# <a name="mbsnbcpy-mbsnbcpyl"></a>_mbsnbcpy, _mbsnbcpy_l

Kopie **n** bajtů řetězce do cílového řetězce. Bezpečnější verze těchto funkcí jsou k dispozici, najdete v článku [_mbsnbcpy_s – _mbsnbcpy_s_l –](mbsnbcpy-s-mbsnbcpy-s-l.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Cíl pro řetězec znaků, které se mají zkopírovat.

*strSource*<br/>
Řetězec znaků, které se mají zkopírovat.

*Počet*<br/>
Počet bajtů, které mají být zkopírovány.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

**_mbsnbcpy –** vrací ukazatel na cílový řetězec znaků. Žádná návratová hodnota je vyhrazená k indikaci chyby.

## <a name="remarks"></a>Poznámky

**_Mbsnbcpy** funkce kopie *počet* bajtů z *strSource* k *strDest*. Pokud *počet* překračuje velikost *strDest* nebo zdrojový a cílový řetězec překrývají, chování **_mbsnbcpy** není definován.

Pokud *strSource* nebo *strDest* je ukazatel s hodnotou null, tato funkce vyvolá obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce vrátí **NULL** a nastaví **errno** k **EINVAL**.

Výstupní hodnota je ovlivněna nastavením **LC_CTYPE** nastavením kategorie národního prostředí; viz [setlocale _wsetlocale](setlocale-wsetlocale.md) Další informace. Verze těchto funkcí jsou identické, s výjimkou, že ty, které nemají **_l** přípona pomocí aktuálního národního prostředí a verze, které mají **_l** přípona místo toho používá parametr národního prostředí, která Předaný. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

> [!IMPORTANT]
> Tyto funkce by mohly být vystaveny ohrožení přetečení vyrovnávací paměti. Přetečení vyrovnávací paměti je možné ke spouštění kódu vytvořeného libovolného útočník, který může způsobit neoprávněné zvýšení úrovně oprávnění a ohrozit zabezpečení systému. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns).

V jazyce C++ mají tyto funkce přetížení šablon, která vyvolávají novější, lépe zabezpečené protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncpy**|[strncpy](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)|**_mbsnbcpy**|[wcsncpy](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)|
|**_tcsncpy_l**|**_strncpy_l**|**_mbsnbcp_l**|**_wcsncpy_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsnbcpy**|\<Mbstring.h >|
|**_mbsnbcpy_l**|\<Mbstring.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
