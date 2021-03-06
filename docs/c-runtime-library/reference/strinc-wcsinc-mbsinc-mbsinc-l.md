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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: a53102f991ec7467fd74e1997f8d5b7419b15aa1
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919982"
---
# <a name="_strinc-_wcsinc-_mbsinc-_mbsinc_l"></a>_strinc, _wcsinc, _mbsinc, _mbsinc_l

Posune ukazatel řetězce o jeden znak.

> [!IMPORTANT]
> **_mbsinc** a **_mbsinc_l** nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Ukazatel na znak.

*locale*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

Každá z těchto rutin vrací ukazatel na znak, který následuje hned za *aktuálním*.

## <a name="remarks"></a>Poznámky

Funkce **_mbsinc** vrací ukazatel na první bajt vícebajtového znaku, který bezprostředně následuje za *aktuálním*. **_mbsinc** rozpozná vícebajtové znakové sekvence podle [vícebajtové znakové stránky](../../c-runtime-library/code-pages.md) , která se právě používá; **_mbsinc_l** je totožný s tím rozdílem, že místo toho používá parametr národního prostředí, který je předán. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Funkce obecného textu **_tcsinc**definovaná v Tchar. h, je mapována na **_mbsinc** , pokud **_MBCS** definována, nebo na **_wcsinc** Pokud byl definován **_UNICODE** . V opačném případě **_tcsinc** namapuje na **_strinc**. **_strinc** a **_wcsinc** jsou jednobajtové verze **_mbsinc**a verze s velkým znakem. **_strinc** a **_wcsinc** jsou k dispozici pouze pro toto mapování a neměla by být používána jinak. Další informace najdete v tématu [použití mapování obecného textu](../../c-runtime-library/using-generic-text-mappings.md) a [Mapování obecného textu](../../c-runtime-library/generic-text-mappings.md).

Pokud *Current* má **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tato funkce **EINVAL** a nastaví **errno** na **EINVAL**.

> [!IMPORTANT]
> Tyto funkce můžou být zranitelné vůči hrozbám přetečení vyrovnávací paměti. Přetečení vyrovnávací paměti lze použít pro systémové útoky, protože mohou způsobit neoprávněné zvýšení oprávnění. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsinc**|\<Mbstring. h>|
|**_mbsinc_l**|\<Mbstring. h>|
|**_strinc**|\<Tchar. h>|
|**_wcsinc**|\<Tchar. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strdec, _wcsdec, _mbsdec, _mbsdec_l](strdec-wcsdec-mbsdec-mbsdec-l.md)<br/>
[_strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l](strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)<br/>
[_strninc, _wcsninc, _mbsninc, _mbsninc_l](strninc-wcsninc-mbsninc-mbsninc-l.md)<br/>
