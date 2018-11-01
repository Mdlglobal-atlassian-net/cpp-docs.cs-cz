---
title: ctan ctanf, ctanl
ms.date: 11/04/2016
apiname:
- ctan
- ctanf
- ctanl
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
- ctan
- ctanf
- ctanl
- complex/ctan
- complex/ctanf
- complex/ctanl
helpviewer_keywords:
- ctan function
- ctanf function
- ctanl function
ms.assetid: d3cbd25c-1e93-4a6d-8154-da42921f7223
ms.openlocfilehash: 2d4da5a39658e46bc633ae3bd9c8f6f0a01555aa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661744"
---
# <a name="ctan-ctanf-ctanl"></a>ctan ctanf, ctanl

Načte tangens komplexního čísla.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex ctan(
   _Dcomplex z
);
_Fcomplex ctan(
   _Fcomplex z
);  // C++ only
_Lcomplex ctan(
   _Lcomplex z
);  // C++ only
_Fcomplex ctanf(
   _Fcomplex z
);
_Lcomplex ctanl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Parametry

*z*<br/>
Komplexní čísla, která představuje úhel v radiánech.

## <a name="return-value"></a>Návratová hodnota

Tangens *z*.

|Vstup|Výjimka SEH|**_matherr** výjimky|
|-----------|-------------------|--------------------------|
|ROZMEZÍ ∞, QNAN, AJÍT|žádná|_DOMÉNA|
|Rozmezí ∞ (**tan**, **tanf –**)|NEPLATNÝ|_DOMÉNA|

## <a name="remarks"></a>Poznámky

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení **ctan** , která používají a vrací **_Fcomplex** a **_Lcomplex** hodnoty. V programu jazyka C **ctan** vždy převezme a vrátí **_Dcomplex** hodnotu.

## <a name="requirements"></a>Požadavky

|Rutina|Záhlaví C|Hlaviček jazyka C++|
|-------------|--------------|------------------|
|**ctan**, **ctanf**, **ctanl**|\<complex.h>|\<ccomplex >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[catanh, catanhf, catanhl](catanh-catanhf-catanhl.md)<br/>
[ctanh, ctanhf, ctanhl](ctanh-ctanhf-ctanhl.md)<br/>
[catan, catanf, catanl](catan-catanf-catanl.md)<br/>
[csinh, csinhf, csinhl](csinh-csinhf-csinhl.md)<br/>
[casinh, casinhf, casinhl](casinh-casinhf-casinhl.md)<br/>
[ccosh, ccoshf, ccoshl](ccosh-ccoshf-ccoshl.md)<br/>
[cacosh, cacoshf, cacoshl](cacosh-cacoshf-cacoshl.md)<br/>
[cacos, cacosf, cacosl](cacos-cacosf-cacosl.md)<br/>
[csin, csinf, csinl](csin-csinf-csinl.md)<br/>
[casin, casinf, casinl](casin-casinf-casinl.md)<br/>
[ccos, ccosf, ccosl](ccos-ccosf-ccosl.md)<br/>
[csqrt, csqrtf, csqrtl](csqrt-csqrtf-csqrtl.md)<br/>
