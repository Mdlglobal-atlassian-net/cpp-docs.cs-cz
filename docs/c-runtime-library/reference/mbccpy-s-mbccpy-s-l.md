---
title: _mbccpy_s, _mbccpy_s_l
ms.date: 11/04/2016
apiname:
- _mbccpy_s
- _mbccpy_s_l
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
ms.openlocfilehash: f9a7554630bd3b46196358c01c21b99978c53e53
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575040"
---
# <a name="mbccpys-mbccpysl"></a>_mbccpy_s, _mbccpy_s_l

Zkopíruje jeden vícebajtový znak z řetězce do jiného řetězce. Tyto verze [_mbccpy _mbccpy_l –](mbccpy-mbccpy-l.md) mají rozšíření zabezpečení popsaná v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*cíl*<br/>
Cíl kopírování.

*buffSizeInBytes*<br/>
Velikost cílové vyrovnávací paměti.

*pCopied*<br/>
Vyplněno počtem bajtů zkopírovaný (1 nebo 2 v případě úspěchu). Předejte **NULL** Pokud vám nezáleží číslo.

*src*<br/>
Vícebajtový znak pro kopírování.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; Kód chyby při selhání. Pokud *src* nebo *dest* je **NULL**, nebo pokud více než **buffSizeinBytes** bajtů má být zkopírováno do *dest*, pak je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí funkce **EINVAL** a **errno** je nastavena na **EINVAL**.

## <a name="remarks"></a>Poznámky

**_Mbccpy_s –** funkce kopíruje jeden vícebajtový znak *src* k *dest*. Pokud *src* neodkazuje na úvodní bajt vícebajtového znaku, jako je určeno implicitním voláním [_ismbblead](ismbblead-ismbblead-l.md), jeden bajt, který *src* odkazuje na zkopírován. Pokud *src* ukazuje na vedoucí bajt, ale následující bajt je 0 a tedy neplatný, pak 0 je zkopírována do *dest*, **errno** je nastavena na **EILSEQ**a Funkce vrátí **EILSEQ**.

**_mbccpy_s –** není znak zakončení null; nicméně, pokud *src* odkazuje na prázdný znak, pak tato hodnota null je zkopírována do *dest* (to je jen regulární jednobajtová kopie).

Hodnota v *pCopied* je vyplněna počtem zkopírovaných. Možné hodnoty jsou 1 a 2, pokud je operace úspěšná. Pokud **NULL** je předán, tento parametr je ignorován.

|*src*|zkopírovat do *dest*|*pCopied*|Návratová hodnota|
|-----------|----------------------|---------------|------------------|
|vedoucí bajt|vedoucí bajt|1|0|
|0|0|1|0|
|vedoucí znak následovaný jiným znakem než 0|vedoucí znak následovaný jiným znakem než 0|2|0|
|vedoucí znak následovaný 0|0|1|**EILSEQ**|

Všimněte si, že druhý řádek je pouze zvláštním případem prvního. Všimněte si také, že tabulka předpokládá *buffSizeInBytes* >= *pCopied*.

**_mbccpy_s –** používá aktuální národní prostředí pro všechna závislá chování. **_mbccpy_s_l –** je stejný jako **_mbccpy_s –** s tím rozdílem, že **_mbccpy_s_l –** používá pro všechna chování závislé na národním prostředí předané národní prostředí.

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení mohou odvodit délku vyrovnávací paměti automaticky, takže odpadá nutnost určit velikost argumentu. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tccpy_s –**|Mapuje se na makro nebo vloženou funkci.|**_mbccpy_s**|Mapuje se na makro nebo vloženou funkci.|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbccpy_s**|\<Mbstring.h >|
|**_mbccpy_s_l**|\<Mbstring.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
