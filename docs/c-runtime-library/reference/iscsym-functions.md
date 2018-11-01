---
title: iscsym –, iscsymf –, __iscsym –, __iswcsym –, __iscsymf –, __iswcsymf –, _iscsym_l –, _iswcsym_l –, _iscsymf_l –, _iswcsymf_l –
ms.date: 11/04/2016
apiname:
- _iswcsym_l
- __iswcsym
- __iscsym
- _iswcsymf_l
- _iscsym_l
- __iswcsymf
- __iscsymf
- _iscsymf_l
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _iswcsym_l
- _iswcsymf_l
- iscsymf
- iswcsymf
- __iswcsym
- __iswcsymf
- iscsym
- iswcsym
- __iscsym
- _iscsym_l
- _iscsymf_l
- __iscsymf
- ctype/iscsym
- ctype/iscsymf
- ctype/__iscsym
- ctype/__iscsymf
- ctype/__iscsym_l
- ctype/__iscsymf_l
- ctype/__iswcsym
- ctype/__iswcsymf
- ctype/__iswcsym_l
- ctype/__iswcsymf_l
helpviewer_keywords:
- iscsymf_l function
- iswsym_l function
- _iswcsym_l function
- iscsym_l function
- _iscsymf_l function
- _iswcsymf_l function
- _iscsym_l function
- __iscsym function
- __iswcsymf function
- iswsymf_l function
- __iscsymf function
- __iswcsym function
- iscsym function
- iscsymf function
ms.assetid: 944dfb99-f2b8-498c-9f55-dbcf370d0a2c
ms.openlocfilehash: 8ee84243b98c08504ac0bb63593e39c32230b706
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617854"
---
# <a name="iscsym-iscsymf-iscsym-iswcsym-iscsymf-iswcsymf-iscsyml-iswcsyml-iscsymfl-iswcsymfl"></a>iscsym –, iscsymf –, __iscsym –, __iswcsym –, __iscsymf –, __iswcsymf –, _iscsym_l –, _iswcsym_l –, _iscsymf_l –, _iswcsymf_l –

Určete, pokud celočíselná hodnota představuje znak, který může být použit v identifikátoru.

## <a name="syntax"></a>Syntaxe

```C
int __iscsym(
   int c
);
int __iswcsym(
   wint_t c
);
int __iscsymf(
   int c
);
int __iswcsymf(
   wint_t c
);
int _iscsym_l(
   int c,
   _locale_t locale
);
int _iswcsym_l(
   wint_t c,
   _locale_t locale
);
int _iscsymf_l(
   int c,
   _locale_t locale
);
int _iswcsymf_l(
   wint_t c,
   _locale_t locale
);
#define iscsym __iscsym
#define iscsymf __iscsymf
```

### <a name="parameters"></a>Parametry

*c*<br/>
Celé číslo k testování. *c* musí být v rozsahu 0 – 255 úzkými znaky verze funkce.

*Národní prostředí*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Obě **__iscsym –** a **__iswcsym –** vrátí nenulovou hodnotu, pokud *c* je písmeno, znak podtržení nebo číslice. Obě **__iscsymf –** a **__iswcsymf –** vrátí nenulovou hodnotu, pokud *c* písmenem nebo podtržítkem. Každá z těchto rutin vrátí hodnotu 0, pokud *c* nesplňuje testovací podmínku. Verze těchto funkcí s **_l** přípona jsou stejné s tím rozdílem, že používají *národní prostředí* předaný namísto aktuálního národního prostředí pro své chování závislé na národním prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Poznámky

Tyto rutiny jsou definovány jako makra, pokud je definován _CTYPE_DISABLE_MACROS preprocesor makro. Při použití verze – makro z těchto rutin argumenty mohou být vyhodnoceny více než jednou. Buďte opatrní při použití výrazů, které mají vedlejší účinky v rámci seznamu argumentů.

Z důvodu zpětné kompatibility **iscsym –** a **iscsymf –** jsou definovány jako makra pouze tehdy, když [ &#95; &#95;STDC&#95; &#95; ](../../preprocessor/predefined-macros.md) není definované nebo je definován jako 0; v opačném případě nejsou definovány.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**iscsym –**, **iscsymf –**, **__iscsym –**, **__iswcsym –**, **__iscsymf –**, **__iswcsymf –**, **_iscsym_l –**, **_iswcsym_l –**, **_iscsymf_l –**, **_iswcsymf_l –**|C: \<ctype.h ><br /><br /> Jazyk C++: \<cctype – > nebo \<ctype.h >|

**Iscsym –**, **iscsymf –**, **__iscsym –**, **__iswcsym –**, **__iscsymf –**, **__ iswcsymf**, **_iscsym_l –**, **_iswcsym_l –**, **_iscsymf_l –**, a **_iswcsymf_l –** jsou rutiny Specifické pro Microsoft. Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)<br/>
