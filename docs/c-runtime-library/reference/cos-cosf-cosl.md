---
title: cos, cosf, cosl
ms.date: 04/05/2018
api_name:
- cos
- cosf
- cosl
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- cos
- cosf
- cosl
helpviewer_keywords:
- cosines
- cosl function
- calculating cosine
- cosf function
- cos function
- trigonometric functions
- cosines, calculating
ms.assetid: ae90435e-6b68-4a47-a81f-be87d5c08f16
ms.openlocfilehash: 9ec612aa9f8c6eaf1731d62b654d45841cdfa159
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170252"
---
# <a name="cos-cosf-cosl"></a>cos, cosf, cosl

Vypočítá kosinus.

## <a name="syntax"></a>Syntaxe

```C
double cos( double x );
float cosf( float x );
long double cosl( long double x );
```

```cpp
float cos( float x );  // C++ only
long double cos( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*znak*<br/>
Úhel v radiánech.

## <a name="return-value"></a>Návratová hodnota

Kosinus hodnoty *x*. Pokud *x* je větší nebo rovno 263 nebo menší než nebo rovno-263, dojde ke ztrátě významnosti ve výsledku.

|Vstup|Výjimka SEH|Výjimka matherr|
|-----------|-------------------|-----------------------|
|QNAN, ZASÁHNOUT|Žádná|**_DOMAIN**|
|± INF|**NENÍ**|**_DOMAIN**|

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení ovládacího programu **cos** , který přijímá a vrací hodnoty **typu float** nebo **Long** **Double** . V programu v jazyce C provede funkce **cos** vždycky a vrátí hodnotu **Double**.

## <a name="requirements"></a>Požadavky

|Rutina|Povinné záhlaví jazyka C|Požadovaná C++ hlavička|
|-------------|---------------------|-|
|**cos**, **cosh –** , **cosf –**|\<Math. h >|\<cmath > nebo \<Math. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad ve [Sin, sinf –, Sinl](sin-sinf-sinl.md).

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
[_CIcos](../../c-runtime-library/cicos.md)<br/>
