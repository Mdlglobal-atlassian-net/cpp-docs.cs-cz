---
title: _strinc, _wcsinc, _mbsinc, _mbsinc_l
ms.date: 4/2/2020
api_name:
- _mbsinc
- _wcsinc
- _mbsinc_l
- _strinc
- _o__mbsinc
- _o__mbsinc_l
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
- mbsinc_l
- _strinc
- strinc
- _mbsinc
- _wcsinc
- wcsinc
- mbsinc
- _mbsinc_l
helpviewer_keywords:
- _mbsinc function
- wcsinc function
- mbsinc_l function
- _strinc function
- strinc function
- _mbsinc_l function
- mbsinc function
- _wcsinc function
- _tcsinc function
- tcsinc function
ms.assetid: 54685943-8e2c-45e9-a559-2d94930dc6b4
ms.openlocfilehash: 0cfbe857ec8bbcdec887d4594cee0bf2b66de380
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362900"
---
# <a name="_strinc-_wcsinc-_mbsinc-_mbsinc_l"></a>_strinc, _wcsinc, _mbsinc, _mbsinc_l

Posune ukazatel řetězce o jeden znak.

> [!IMPORTANT]
> **_mbsinc** a **_mbsinc_l** nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *_strinc(
   const char *current,
   _locale_t locale
);
wchar_t *_wcsinc(
   const wchar_t *current,
   _locale_t locale
);
unsigned char *_mbsinc(
   const unsigned char *current
);
unsigned char *_mbsinc_l(
   const unsigned char *current,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*aktuální*<br/>
Ukazatel znaku.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrátí ukazatel na znak, který bezprostředně následuje *aktuální*.

## <a name="remarks"></a>Poznámky

Funkce **_mbsinc** vrátí ukazatel na první bajt vícebajtového znaku, který bezprostředně následuje za *aktuálním*. **_mbsinc** rozpozná vícebajtové sekvence znaků podle [vícebajtové znakové stránky,](../../c-runtime-library/code-pages.md) která se právě používá; **_mbsinc_l** je totožný s tím rozdílem, že místo toho používá parametr národního prostředí, který je předán. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Funkce obecného textu **_tcsinc**, definované v Tchar.h, mapuje **na _mbsinc,** **pokud** _MBCS byla definována, nebo **_wcsinc,** pokud byla definována **_UNICODE.** V opačném případě **_tcsinc** mapuje na **_strinc**. **_strinc** a **_wcsinc** jsou jednobajtové a širokoznakové verze **_mbsinc**. **_strinc** a **_wcsinc** jsou k dispozici pouze pro toto mapování a jinak by neměly být používány. Další informace naleznete [v tématu Použití mapování obecného textu](../../c-runtime-library/using-generic-text-mappings.md) a mapování [obecného textu](../../c-runtime-library/generic-text-mappings.md).

Pokud je *proud* **NULL**, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, vrátí tato funkce **funkce EINVAL** a nastaví **errno** na **EINVAL**.

> [!IMPORTANT]
> Tyto funkce mohou být náchylné k hrozbám přetečení vyrovnávací paměti. Přetečení vyrovnávací paměti lze použít pro systémové útoky, protože mohou způsobit neoprávněné zvýšení oprávnění. Další informace naleznete v [tématu Zabránění přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsinc**|\<mbstring.h>|
|**_mbsinc_l**|\<mbstring.h>|
|**_strinc**|\<tchar.h>|
|**_wcsinc**|\<tchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strdec, _wcsdec, _mbsdec, _mbsdec_l](strdec-wcsdec-mbsdec-mbsdec-l.md)<br/>
[_strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l](strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)<br/>
[_strninc, _wcsninc, _mbsninc, _mbsninc_l](strninc-wcsninc-mbsninc-mbsninc-l.md)<br/>
