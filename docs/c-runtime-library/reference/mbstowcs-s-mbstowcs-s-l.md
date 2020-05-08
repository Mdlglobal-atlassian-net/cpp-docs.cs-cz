---
title: mbstowcs_s, _mbstowcs_s_l
ms.date: 4/2/2020
api_name:
- _mbstowcs_s_l
- mbstowcs_s
- _o__mbstowcs_s_l
- _o_mbstowcs_s
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbstowcs_s_l
- mbstowcs_s
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
ms.openlocfilehash: 4a6e86e1122a7392862fa34a59042c32560fd69d
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915456"
---
# <a name="mbstowcs_s-_mbstowcs_s_l"></a>mbstowcs_s, _mbstowcs_s_l

Převede sekvenci vícebajtových znaků na odpovídající sekvenci velkých znaků. Verze [mbstowcs se _mbstowcs_l](mbstowcs-mbstowcs-l.md) s vylepšeními zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Počet převedených znaků.

*wcstr*<br/>
Adresa vyrovnávací paměti pro výsledný Konvertovaný řetězec s velkým počtem znaků.

*sizeInWords*<br/>
Velikost vyrovnávací paměti *wcstr* ve slovech.

*mbstr*<br/>
Adresa posloupnosti null ukončených vícebajtových znaků.

*výpočtu*<br/>
Maximální počet velkých znaků, které mají být uloženy do vyrovnávací paměti *wcstr* , včetně ukončující hodnoty null nebo [_TRUNCATE](../../c-runtime-library/truncate.md).

*locale*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, chybový kód při selhání.

|Chybový stav|Návratová hodnota a **errno**|
|---------------------|------------------------------|
|*wcstr* má **hodnotu NULL** a *sizeInWords* > 0|**EINVAL**|
|*mbstr* má **hodnotu null** .|**EINVAL**|
|Cílová vyrovnávací paměť je příliš malá, aby obsahovala převedený řetězec (Pokud není *počet* **_TRUNCATE**; viz poznámky níže)|**ERANGE**|
|*wcstr* není **null** a *sizeInWords* = = 0.|**EINVAL**|

Pokud nastane kterákoli z těchto podmínek, je vyvolána výjimka neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, vrátí funkce kód chyby a nastaví **errno** , jak je uvedeno v tabulce.

## <a name="remarks"></a>Poznámky

Funkce **mbstowcs_s** převede řetězec vícebajtových znaků, na které odkazoval *mbstr* do velkých znaků uložených ve vyrovnávací paměti, na kterou odkazuje *wcstr*. Převod bude pro každý znak pokračovat, dokud nebude splněna jedna z těchto podmínek:

- Byl zjištěn vícebajtový znak null.

- Zjistil se neplatný vícebajtový znak.

- Počet velkých znaků uložených ve vyrovnávací paměti *wcstr* se rovná *počtu*.

Cílový řetězec je vždycky zakončený hodnotou null (i v případě chyby).

Pokud *Count* je speciální hodnota [_TRUNCATE](../../c-runtime-library/truncate.md), **mbstowcs_s** se převede jako velká část řetězce, aby se vešla do cílové vyrovnávací paměti, zatímco pořád opouští místo pro ukončovací znak null.

Pokud **mbstowcs_s** úspěšně převede zdrojový řetězec, umístí velikost v rámci převedených řetězců, včetně ukončovacího znaku null, do *&#42;pReturnValue* (poskytnutý *pReturnValue* není **null**). K tomu dojde i v případě, že argument *wcstr* má **hodnotu null** a poskytuje způsob, jak určit požadovanou velikost vyrovnávací paměti. Všimněte si, že pokud má *Wcstr* **hodnotu null**, je *počet* ignorován a *sizeInWords* musí být 0.

Pokud **mbstowcs_s** narazí na neplatný vícebajtový znak, umístí 0 do *&#42;pReturnValue*, nastaví cílovou vyrovnávací paměť na prázdný řetězec, nastaví **errno** na **EILSEQ**a vrátí **EILSEQ**.

Pokud se sekvence, na které ukazuje *mbstr* a *wcstr* , překrývají, chování **mbstowcs_s** není definováno.

> [!IMPORTANT]
> Zajistěte, aby se *wcstr* a *mbstr* nepřekrývaly, a tento *počet* správně odráží počet vícebajtových znaků, které se mají převést.

**mbstowcs_s** používá aktuální národní prostředí pro jakékoli chování závislé na národním prostředí; **_mbstowcs_s_l** je totožný s tím rozdílem, že místo toho používá národní prostředí předané. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon; přetížení můžou odvodit délku vyrovnávací paměti automaticky (eliminují nutnost zadat argument velikosti) a můžou automaticky nahradit starší nezabezpečené funkce jejich novějšími, zabezpečenými protějšky. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**mbstowcs_s**|\<Stdlib. h>|
|**_mbstowcs_s_l**|\<Stdlib. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Jazyka](../../c-runtime-library/locale.md)<br/>
[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
