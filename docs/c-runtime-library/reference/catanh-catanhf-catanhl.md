---
title: catanh, catanhf, catanhl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- catanh
- catanhf
- catanhl
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
- catanh
- catanhf
- catanhl
- complex/catanh
- complex/catanhf
- complex/catanhl
dev_langs:
- C++
helpviewer_keywords:
- catanh function
- catanhf function
- catanhl function
ms.assetid: 1b6021cb-647a-41b4-9d7f-919cc8b57b86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd74d00e7f5be5e7631bc33fb9b7ea13eb32a407
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="catanh-catanhf-catanhl"></a>catanh, catanhf, catanhl

Načte inverzní hyperbolický tangens čísla komplexní s větve kusy mimo interval [-1; + 1] pro skutečné osu.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex catanh(
   _Dcomplex z
);
_Fcomplex catanh(
   _Fcomplex z
);  // C++ only
_Lcomplex catanh(
   _Lcomplex z
);  //  C++ only
_Fcomplex catanhf(
   _Fcomplex z
);
_Lcomplex catanhl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Parametry

*z*<br/>
Komplexní číslo, které představuje úhel v radiánech.

## <a name="return-value"></a>Návratová hodnota

Inverzní hyperbolický tangens *z*, v radiánech. Výsledkem je, bez vazby skutečné osy a v intervalu [-iπ/2; + iπ/2] pomyslná osy. Chyba domény dojde v případě *z* je mimo interval [-1, + 1]. Pokud dojde k chybě pólu *z* -1 nebo + 1.

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **catanh** , přijmout a vrátit **_Fcomplex** a **_Lcomplex** hodnoty. V programu C **catanh** vždy provede a vrátí **_Dcomplex** hodnotu.

## <a name="requirements"></a>Požadavky

|Rutina|Hlavička C|Hlavička C++|
|-------------|--------------|------------------|
|**catanh**, **catanhf**, **catanhl**|\<complex.h>|\<ccomplex >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[ctanh, ctanhf, ctanhl](ctanh-ctanhf-ctanhl.md)<br/>
[catan, catanf, catanl](catan-catanf-catanl.md)<br/>
[csinh, csinhf, csinhl](csinh-csinhf-csinhl.md)<br/>
[casinh, casinhf, casinhl](casinh-casinhf-casinhl.md)<br/>
[ccosh, ccoshf, ccoshl](ccosh-ccoshf-ccoshl.md)<br/>
[cacosh, cacoshf, cacoshl](cacosh-cacoshf-cacoshl.md)<br/>
[cacos, cacosf, cacosl](cacos-cacosf-cacosl.md)<br/>
[ctan, ctanf, ctanl](ctan-ctanf-ctanl.md)<br/>
[csin, csinf, csinl](csin-csinf-csinl.md)<br/>
[casin, casinf, casinl](casin-casinf-casinl.md)<br/>
[ccos, ccosf, ccosl](ccos-ccosf-ccosl.md)<br/>
[csqrt, csqrtf, csqrtl](csqrt-csqrtf-csqrtl.md)<br/>
