---
title: mbstowcs_s –, _mbstowcs_s_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbstowcs_s_l
- mbstowcs_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbstowcs_s_l
- mbstowcs_s
dev_langs:
- C++
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f366e01fbaa8da5c0dbc96ff4da324611e132f1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403918"
---
# <a name="mbstowcss-mbstowcssl"></a>mbstowcs_s, _mbstowcs_s_l

Převede posloupnost více-bajtové znaky na odpovídající posloupnost široké znaky. Verze [mbstowcs –, _mbstowcs_l –](mbstowcs-mbstowcs-l.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count
);
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*pReturnValue*<br/>
Počet znaků převést.

*wcstr*<br/>
Adresa vyrovnávací paměti pro výsledný řetězec převedený široká znaková.

*sizeInWords*<br/>
Velikost *wcstr* vyrovnávací paměti v slova.

*mbstr*<br/>
Adresu pořadí Null byla ukončena více-bajtové znaky.

*Počet*<br/>
Maximální počet široké znaky a uložit v *wcstr* vyrovnávací paměti není včetně ukončující null, nebo [_truncate –](../../c-runtime-library/truncate.md).

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, kód chyby při selhání.

|Chybový stav|Vrátí hodnotu a **kód chyby**|
|---------------------|------------------------------|
|*wcstr* je **NULL** a *sizeInWords* > 0|**EINVAL –**|
|*mbstr* je **hodnotu NULL.**|**EINVAL –**|
|Cílová vyrovnávací paměť je příliš malá tak, aby obsahovala převedený řetězec (Pokud *počet* je **_truncate –**; viz poznámky níže)|**ERANGE –**|
|*wcstr* není **NULL** a *sizeInWords* == 0|**EINVAL –**|

Pokud dojde k některé z těchto podmínek, jak je popsáno v je vyvolána výjimka neplatný parametr [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno provádění pokračovat, funkce vrátí kód chyby a nastaví **errno** , které je uvedené v tabulce.

## <a name="remarks"></a>Poznámky

**Mbstowcs_s –** funkce převede řetězec vícebajtové znaky, na kterou odkazuje *mbstr* do široké znaky, které jsou uložené ve vyrovnávací paměti, na kterou odkazuje *wcstr*. Převod bude pokračovat pro jednotlivé znaky, dokud je splněna jedna z těchto podmínek:

- Vyskytl se vícebajtových znaků hodnotu null

- Je zjištěna neplatná vícebajtových znaků

- Počet široké znaky, které jsou uložené v *wcstr* vyrovnávací paměti je rovno *počet*.

Cílový řetězec je vždy ukončený hodnotou null (i v případě chyby).

Pokud *počet* je speciální hodnota [_truncate –](../../c-runtime-library/truncate.md), pak **mbstowcs_s –** převede co nejvíc řetězec jako bude začlenit do cílové vyrovnávací paměti, a přesto nechat místnosti s hodnotou Null ukončovací znak.

Pokud **mbstowcs_s –** úspěšně převede zdrojový řetězec, uloží je velikost v široké znaky převedený řetězec, včetně null ukončení do  *&#42;pReturnValue* (zadat *pReturnValue* není **NULL**). K tomu dojde i v případě *wcstr* argument je **NULL** a poskytuje způsob, jak určit velikost požadované vyrovnávací paměti. Všimněte si, že pokud *wcstr* je **NULL**, *počet* je ignorován a *sizeInWords* musí být 0.

Pokud **mbstowcs_s –** zaznamená neplatný vícebajtových znaků, uloží je 0  *&#42;pReturnValue*, nastaví cílové vyrovnávací paměti na prázdný řetězec, nastaví **errno** k  **Eilseq –** a vrátí **eilseq –**.

Pokud daná pořadí na kterou odkazuje *mbstr* a *wcstr* překrývají, chování **mbstowcs_s –** není definován.

> [!IMPORTANT]
> Ujistěte se, že *wcstr* a *mbstr* se nepřekrývají a že *počet* správně odpovídá počtu více-bajtové znaky převést.

**mbstowcs_s –** používá aktuální národní prostředí pro chování všech závislých na národním prostředí; **_mbstowcs_s_l –** se shoduje s tím rozdílem, že používá národní prostředí předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení automaticky odvození délka vyrovnávací paměti (takže není nutné zadat argument velikost) a starší, nezabezpečené funkce můžou automaticky nahradit se svými protějšky novější a zabezpečené. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**mbstowcs_s –**|\<stdlib.h>|
|**_mbstowcs_s_l**|\<stdlib.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
