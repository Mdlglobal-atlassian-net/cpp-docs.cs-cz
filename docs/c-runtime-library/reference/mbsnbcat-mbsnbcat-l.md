---
title: _mbsnbcat – _mbsnbcat_l – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _mbsnbcat_l
- _mbsnbcat
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
- mbsnbcat
- mbsnbcat_l
- _mbsnbcat
- _mbsnbcat_l
dev_langs:
- C++
helpviewer_keywords:
- tcsncat_l function
- _tcsncat function
- mbsnbcat_l function
- mbsnbcat function
- _mbsnbcat_l function
- _tcsncat_l function
- _mbsnbcat function
- tcsncat function
ms.assetid: aa0f1d30-0ddd-48d1-88eb-c6884b20fd91
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f6d75df13263c0eb6a239f2fe6f4f5a400e03d3
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210079"
---
# <a name="mbsnbcat-mbsnbcatl"></a>_mbsnbcat, _mbsnbcat_l

Připojí maximálně prvních **n** bajtů jednoho řetězec vícebajtových znaků na jiný. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [_mbsnbcat_s – _mbsnbcat_s_l –](mbsnbcat-s-mbsnbcat-s-l.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned char *_mbsnbcat(
   unsigned char *dest,
   const unsigned char *src,
   size_t count
);
unsigned char *_mbsnbcat_l(
   unsigned char *dest,
   const unsigned char *src,
   size_t count,
   _locale_t locale
);
template <size_t size>
unsigned char *_mbsnbcat(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count
); // C++ only
template <size_t size>
unsigned char *_mbsnbcat_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*cíl*<br/>
Řetězec cíle zakončený hodnotou Null vícebajtového znaku.

*src*<br/>
Řetězec zakončený hodnotou Null zdroje vícebajtového znaku.

*Počet*<br/>
Počet bajtů z *src* pro připojení k *dest*.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

**_mbsnbcat –** vrací ukazatel na cílový řetězec. Žádná návratová hodnota je vyhrazená k indikaci chyby.

## <a name="remarks"></a>Poznámky

**_Mbsnbcat –** funkce připojí maximálně prvních *počet* bajtů *src* k *dest*. Pokud bajt bezprostředně předchází znak null v *dest* je vedoucí bajt úvodní bajt *src* přepíše tento úvodní bajt. Jinak úvodní bajt *src* přepíše ukončující znak null proměnné *dest*. Pokud se objeví nulový bajt v *src* před *počet* bajtů se připojují, **_mbsnbcat –** připojí všechny bajty z *src*, až po znak null. Pokud *počet* je větší než délka *src*, délka *src* je použito místo *počet*. Výsledný řetězec je ukončen znakem null. Pokud se kopírování dojde mezi řetězci, které se překrývají, chování není definováno.

Výstupní hodnota je ovlivněna nastavením **LC_CTYPE** nastavením kategorie národního prostředí; viz [setlocale](setlocale-wsetlocale.md) Další informace. **_Mbsnbcat –** verzi funkce používá aktuální národní prostředí pro toto chování závislé na národním prostředí **_mbsnbcat_l –** verze je stejná s tím rozdílem, že používají Předaný parametr národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

**Poznámka k zabezpečení** použijte řetězec zakončený hodnotou null. Řetězec zakončený hodnotou null nesmí překročit velikost cílové vyrovnávací paměti. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns).

Pokud *dest* nebo *src* je **NULL**, funkce generuje chybu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud je chyba zpracována, funkce vrátí **EINVAL** a nastaví **errno** k **EINVAL**.

V jazyce C++ mají tyto funkce přetížení šablon, která vyvolávají novější, zabezpečené protějšky těchto funkcí. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncat –**|[strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|**_mbsnbcat**|[wcsncat –](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|
|**_tcsncat_l –**|**_strncat_l**|**_mbsnbcat_l**|**_wcsncat_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_mbsnbcat**|\<Mbstring.h >|
|**_mbsnbcat_l**|\<Mbstring.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbcpy, _mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[_mbsnbcat_s, _mbsnbcat_s_l](mbsnbcat-s-mbsnbcat-s-l.md)<br/>
