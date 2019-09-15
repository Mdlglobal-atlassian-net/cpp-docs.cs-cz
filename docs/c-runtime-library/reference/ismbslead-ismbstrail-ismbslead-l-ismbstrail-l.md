---
title: _ismbslead, _ismbstrail, _ismbslead_l, _ismbstrail_l
ms.date: 11/04/2016
api_name:
- _ismbstrail
- _ismbslead_l
- _ismbslead
- _ismbstrail_l
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
- _ismbslead
- ismbs
- ismbslead_l
- _ismbs
- ismbstrail_l
- ismbslead
- _ismbstrail
- _ismbstrail_l
- ismbstrail
- _ismbslead_l
helpviewer_keywords:
- ismbstrail function
- _ismbslead function
- ismbslead function
- ismbslead_l function
- _ismbstrail function
- _ismbslead_l function
- ismbstrail_l function
- _ismbstrail_l function
ms.assetid: 86d2cd7a-3cff-443a-b713-14cc17a231e9
ms.openlocfilehash: 71a5d2a82c01a41f945ef3fa8c7652f846f05103
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953770"
---
# <a name="_ismbslead-_ismbstrail-_ismbslead_l-_ismbstrail_l"></a>_ismbslead, _ismbstrail, _ismbslead_l, _ismbstrail_l

Provádí testy závislé na kontextu pro řetězce a koncové bajty vícebajtových znaků a určuje, zda daný ukazatel dílčího řetězce ukazuje na vedoucí bajt nebo na koncový bajt.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _ismbslead(
   const unsigned char *str,
   const unsigned char *current
);
int _ismbstrail(
   const unsigned char *str,
   const unsigned char *current
);
int _ismbslead_l(
   const unsigned char *str,
   const unsigned char *current,
   _locale_t locale
);
int _ismbstrail_l(
   const unsigned char *str,
   const unsigned char *current,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Ukazatel na začátek řetězce nebo předchozí známý vedoucí bajt.

*aktivní*<br/>
Ukazatel na pozici v řetězci, který má být testován.

*jazyka*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**_ismbslead** vrátí hodnotu-1, pokud je znak vedoucí bajt a **_ismbstrail** vrátí-1, pokud je znakem koncový bajt. Pokud jsou vstupní řetězce platné, ale nejsou vedoucí bajt nebo koncový bajt, vrátí tyto funkce nulu. Pokud má některý argument **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **hodnotu null** a nastaví **errno** na **EINVAL**.

## <a name="remarks"></a>Poznámky

**_ismbslead** a **_ismbstrail** jsou pomalejší než verze **_ismbblead** a **_ismbbtrail** , protože převezmou kontext řetězce na účet.

Verze těchto funkcí, které mají příponu **_l** , jsou shodné s tím rozdílem, že pro své chování závislé na národním prostředí používají předané národní prostředí namísto aktuálního národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_ismbslead**|\<Mbctype. h > nebo \<Mbstring. h >|\<CType. h >, * \<Limits. h > \<, Stdlib. h >|
|**_ismbstrail**|\<Mbctype. h > nebo \<Mbstring. h >|\<CType. h >, * \<Limits. h > \<, Stdlib. h >|
|**_ismbslead_l**|\<Mbctype. h > nebo \<Mbstring. h >|\<CType. h >, * \<Limits. h > \<, Stdlib. h >|
|**_ismbstrail_l**|\<Mbctype. h > nebo \<Mbstring. h >|\<CType. h >, * \<Limits. h > \<, Stdlib. h >|

\*Pro konstanty manifestu pro podmínky testu.

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[_ismbc – rutiny](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
