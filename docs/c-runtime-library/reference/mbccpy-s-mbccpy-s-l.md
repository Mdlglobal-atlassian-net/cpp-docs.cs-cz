---
title: _mbccpy_s, _mbccpy_s_l
ms.date: 4/2/2020
api_name:
- _mbccpy_s
- _mbccpy_s_l
- _o__mbccpy_s
- _o__mbccpy_s_l
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
- _mbccpy_s_l
- mbccpy_s_l
- mbccpy_s
- _mbccpy_s
helpviewer_keywords:
- tccpy_s_l function
- _tccpy_s function
- _mbccpy_s function
- mbccpy_s function
- tccpy_s function
- mbccpy_s_l function
- _tccpy_s_l function
- _mbccpy_s_l function
ms.assetid: b6e965fa-53c1-4ec3-85ef-a1c4b4f2b2da
ms.openlocfilehash: 08df395c6978c84b3f53ed0b07ce988afd0249f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341238"
---
# <a name="_mbccpy_s-_mbccpy_s_l"></a>_mbccpy_s, _mbccpy_s_l

Zkopíruje jeden vícebajtový znak z řetězce do jiného řetězce. Tyto verze [_mbccpy, _mbccpy_l](mbccpy-mbccpy-l.md) mají vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _mbccpy_s(
   unsigned char *dest,
   size_t buffSizeInBytes,
   int * pCopied,
   const unsigned char *src
);
errno_t _mbccpy_s_l(
   unsigned char *dest,
   size_t buffSizeInBytes,
   int * pCopied,
   const unsigned char *src,
   locale_t locale
);
template <size_t size>
errno_t _mbccpy_s(
   unsigned char (&dest)[size],
   int * pCopied,
   const unsigned char *src
); // C++ only
template <size_t size>
errno_t _mbccpy_s_l(
   unsigned char (&dest)[size],
   int * pCopied,
   const unsigned char *src,
   locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*Dest*<br/>
Zkopírujte cíl.

*buffSizeInBytes*<br/>
Velikost cílové vyrovnávací paměti.

*PCopied*<br/>
Vyplněno počtem zkopírovaných bajtů (1 nebo 2 v případě úspěchu). Pass **NULL,** pokud se nestaráte o číslo.

*src*<br/>
Vícebajtový znak ke kopírování.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; kód chyby při selhání. Pokud *src* nebo *dest* je **NULL**, nebo pokud více než **buffSizeinBytes bajtů** by být zkopírovány do *dest*, pak je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [parametru Ověření](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, funkce vrátí **EINVAL** a **errno** je nastavena na **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **_mbccpy_s** zkopíruje jeden vícebajtový znak z *src* na *dest*. Pokud *src* neodkazuje na úvodní bajt vícebajtového znaku určeného implicitním voláním [_ismbblead](ismbblead-ismbblead-l.md), je zkopírován jeden bajt, na který *src* odkazuje. Pokud *src* odkazuje na úvodní bajt, ale následující bajt je 0 a tedy neplatný, pak 0 je zkopírován do *dest*, **errno** je nastavena na **EILSEQ**a funkce vrátí **EILSEQ**.

**_mbccpy_s** nepřipojí zakončení null; pokud *však src* odkazuje na znak null, pak je tato hodnota null zkopírována do *dest* (jedná se pouze o běžnou jednobajtovanou kopii).

Hodnota v *pCopied* je vyplněna počtem zkopírovaných bajtů. Možné hodnoty jsou 1 a 2, pokud je operace úspěšná. Pokud je **předána hodnota NULL,** je tento parametr ignorován.

|*src*|zkopírována *do*|*PCopied*|Návratová hodnota|
|-----------|----------------------|---------------|------------------|
|nezájemce o bydž|nezájemce o bydž|1|0|
|0|0|1|0|
|olovo-byte následuje non-0|olovo-byte následuje non-0|2|0|
|olova byte následované 0|0|1|**EILSEQ**|

Všimněte si, že druhý řádek je jen zvláštní případ prvního. Všimněte si také, že tabulka předpokládá *buffSizeInBytes* >= *pCopied*.

**_mbccpy_s** používá aktuální národní prostředí pro jakékoli chování závislé na národním prostředí. **_mbccpy_s_l** je shodné s **_mbccpy_s** s tím rozdílem, že **_mbccpy_s_l** používá národní prostředí předané pro jakékoli chování závislé na národním prostředí.

V jazyce C++ je použití těchto funkcí zjednodušeno přetížením šablony; přetížení lze odvodit délku vyrovnávací paměti automaticky, což eliminuje potřebu zadat argument velikosti. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy_s**|Mapuje na makro nebo vsazenou funkci.|**_mbccpy_s**|Mapuje na makro nebo vsazenou funkci.|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbccpy_s**|\<mbstring.h>|
|**_mbccpy_s_l**|\<mbstring.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
