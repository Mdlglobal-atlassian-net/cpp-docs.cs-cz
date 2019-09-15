---
title: _mbccpy_s, _mbccpy_s_l
ms.date: 11/04/2016
api_name:
- _mbccpy_s
- _mbccpy_s_l
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
ms.openlocfilehash: 26fad83c5b7847e0050fe490cad30e0643aefd74
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952637"
---
# <a name="_mbccpy_s-_mbccpy_s_l"></a>_mbccpy_s, _mbccpy_s_l

Zkopíruje jeden vícebajtový znak z řetězce do jiného řetězce. Tyto verze [_mbccpy, _mbccpy_l](mbccpy-mbccpy-l.md) mají vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*propojovací*<br/>
Cíl kopírování.

*buffSizeInBytes*<br/>
Velikost cílové vyrovnávací paměti.

*pCopied*<br/>
Vyplněno počtem zkopírovaných bajtů (1 nebo 2, pokud bylo úspěšné). Pokud si číslo nezáleží, předejte **hodnotu null** .

*src*<br/>
Vícebajtový znak pro kopírování.

*jazyka*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; chybový kód při selhání. Pokud má *Src* nebo cíl **hodnotu null**nebo pokud by *byl do cíle*zkopírováno více než **buffSizeinBytes** bajtů, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce vrátí **EINVAL** a **errno** je nastaven na **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **_mbccpy_s** kopíruje jeden vícebajtový znak z *Src* na *cíl*. Pokud *Src* neodkazuje na vedoucí bajt vícebajtového znaku, jak je určeno implicitním voláním [_ismbblead](ismbblead-ismbblead-l.md), pak je zkopírován jeden bajt, na který *Src* odkazuje. Pokud *Src* odkazuje na vedoucí bajt, ale následující bajt je 0 a tedy neplatný, pak 0 se zkopíruje na *cíl*, **errno** je nastaven na **EILSEQ**a funkce vrátí **EILSEQ**.

**_mbccpy_s** nepřipojuje ukončovací znak null; Pokud však *Src* odkazuje na znak null, pak je tato hodnota null zkopírována do *cíle (Jedná se pouze* o běžnou jednobajtovou kopii).

Hodnota v *pCopied* se vyplní počtem zkopírovaných bajtů. Možné hodnoty jsou 1 a 2, pokud je operace úspěšná. Pokud je předána **hodnota null** , tento parametr je ignorován.

|*src*|zkopírováno na *cíl*|*pCopied*|Návratová hodnota|
|-----------|----------------------|---------------|------------------|
|jiný než vedoucí bajt|jiný než vedoucí bajt|1|0|
|0|0|1|0|
|vedoucí bajt následovaný jiným než 0|vedoucí bajt následovaný jiným než 0|2|0|
|vedoucí – bajt následovaný 0|0|1|**EILSEQ**|

Všimněte si, že druhý řádek je pouze zvláštním případem prvního. Všimněte si také, že tabulka předpokládá *buffSizeInBytes* >= *pCopied*.

**_mbccpy_s** používá aktuální národní prostředí pro jakékoli chování závislé na národním prostředí. **_mbccpy_s_l** je shodná s **_mbccpy_s** s tím rozdílem, že **_mbccpy_s_l** používá národní prostředí předané pro jakékoli chování závislé na národním prostředí.

V C++systému je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky a eliminují nutnost zadat argument Size. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy_s**|Provede mapování na makro nebo vloženou funkci.|**_mbccpy_s**|Provede mapování na makro nebo vloženou funkci.|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbccpy_s**|\<Mbstring. h >|
|**_mbccpy_s_l**|\<Mbstring. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
