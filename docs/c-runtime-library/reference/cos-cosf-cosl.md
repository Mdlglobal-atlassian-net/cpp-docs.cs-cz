---
title: Cos cosf –, cosl –
ms.date: 04/05/2018
apiname:
- cos
- cosf
- cosl
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: b050fd98a35028b121def8b665fce62ad58ec437
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335357"
---
# <a name="cos-cosf-cosl"></a>Cos cosf –, cosl –

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

*x*<br/>
Úhel v radiánech.

## <a name="return-value"></a>Návratová hodnota

Kosinus *x*. Pokud *x* je větší než nebo rovno 263 nebo menší než nebo rovna hodnotě-263, dojde ke ztrátě významu výsledku.

|Vstup|Výjimka SEH|Výjimka Matherr|
|-----------|-------------------|-----------------------|
|ROZMEZÍ QNAN, AJÍT|žádná|**_DOMAIN**|
|± INF|**NEPLATNÝ**|**_DOMAIN**|

## <a name="remarks"></a>Poznámky

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení **cos** , která používají a vrací **float** nebo **dlouhé** **double** hodnoty. V programu jazyka C **cos** vždy převezme a vrátí **double**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička C|Požadované hlaviček jazyka C++|
|-------------|---------------------|-|
|**cos**, **cosh**, **cosf**|\<math.h>|\<cmath > nebo \<math.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v [sin, sinf –, sinl –](sin-sinf-sinl.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[asin, asinf, asinl](asin-asinf-asinl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
[_CIcos](../../c-runtime-library/cicos.md)<br/>