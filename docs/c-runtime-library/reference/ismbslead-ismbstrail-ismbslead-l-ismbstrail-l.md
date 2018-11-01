---
title: _ismbslead, _ismbstrail, _ismbslead_l, _ismbstrail_l
ms.date: 11/04/2016
apiname:
- _ismbstrail
- _ismbslead_l
- _ismbslead
- _ismbstrail_l
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
ms.openlocfilehash: 5b4d3f371f4be640cc22a1bdc3d920acf88e2585
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468910"
---
# <a name="ismbslead-ismbstrail-ismbsleadl-ismbstraill"></a>_ismbslead, _ismbstrail, _ismbslead_l, _ismbstrail_l

Provede kontextové testy pro zájemce řetězec vícebajtových znaků a záznam pro bajty a určuje, zda daný podřetězec ukazatel odkazuje na vedoucí bajt nebo druhý bajt.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Ukazatel na začátku řetězce nebo předchozí známé vedoucí bajt.

*aktuální*<br/>
Ukazatel pozice v řetězci, který má být testována.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

**_ismbslead –** vrátí hodnotu -1, pokud znak je vedoucí bajt a **_ismbstrail –** vrátí hodnotu -1, pokud znak je druhý bajt. Pokud vstupní řetězce jsou platné, ale nejsou vedoucím bajtem nebo bajt, tyto funkce vrací nulu. Pokud je některý z nich **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **NULL** a nastavte **errno** k **EINVAL**.

## <a name="remarks"></a>Poznámky

**_ismbslead –** a **_ismbstrail –** jsou pomalejší než **_ismbblead** a **_ismbbtrail** verze protože berou v úvahu kontext řetězce.

Verze těchto funkcí, které mají **_l** přípona jsou stejné s tím rozdílem, že pro své chování závislé na národním prostředí používají předané národní prostředí namísto aktuálního národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_ismbslead**|\<Mbctype.h > nebo \<mbstring.h >|\<ctype.h >, * \<limits.h >, \<stdlib.h >|
|**_ismbstrail –**|\<Mbctype.h > nebo \<mbstring.h >|\<ctype.h >, * \<limits.h >, \<stdlib.h >|
|**_ismbslead_l**|\<Mbctype.h > nebo \<mbstring.h >|\<ctype.h >, * \<limits.h >, \<stdlib.h >|
|**_ismbstrail_l**|\<Mbctype.h > nebo \<mbstring.h >|\<ctype.h >, * \<limits.h >, \<stdlib.h >|

\* Pro konstanty manifestu pro zkušební podmínky.

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[_ismbc – rutiny](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
