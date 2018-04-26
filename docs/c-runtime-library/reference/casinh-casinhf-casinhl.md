---
title: casinh, casinhf, casinhl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- casinh
- casinhl
- casinhf
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
- casinh
- casinhf
- casinhl
- complex/casinh
- complex/casinhf
- complex/casinhl
dev_langs:
- C++
helpviewer_keywords:
- casinh function
- casinhf function
- casinhl function
ms.assetid: bd18340b-21dd-4c86-a14e-e8e15dd97e3b
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 71f57f097ae66b6849bf3c2bd532c39d02aae2b3
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="casinh-casinhf-casinhl"></a>casinh, casinhf, casinhl

Načte inverzní hyperbolický sinus čísla komplexní s větve kusy mimo interval [-i, + i] pomyslná osy.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex casinh(
   _Dcomplex z
);
_Fcomplex casinh(
   _Fcomplex z
);  // C++ only
_Lcomplex casinh(
   _Lcomplex z
);  // C++ only
_Fcomplex casinhf(
   _Fcomplex z
);
_Lcomplex casinhl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Parametry

*z*<br/>
Komplexní číslo, které představuje úhel v radiánech.

## <a name="return-value"></a>Návratová hodnota

Inverzní hyperbolický sinus *z*, v radiánech. Výsledkem nevázaný skutečné osy a v intervalu [-iπ/2 + iπ/2] pomyslná osy.

## <a name="remarks"></a>Poznámky

Protože C++ umožňuje, aby přetížení, můžete volat přetížení **casinh** , přijmout a vrátit **_Fcomplex** a **_Lcomplex** hodnoty. V programu C **casinh** vždy provede a vrátí **_Dcomplex** hodnotu.

## <a name="requirements"></a>Požadavky

|Rutina|Hlavička C|Hlavička C++|
|-------------|--------------|------------------|
|**casinh**, **casinhf**, **casinhl**|\<complex.h>|\<ccomplex >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[catanh, catanhf, catanhl](catanh-catanhf-catanhl.md)<br/>
[ctanh, ctanhf, ctanhl](ctanh-ctanhf-ctanhl.md)<br/>
[catan, catanf, catanl](catan-catanf-catanl.md)<br/>
[csinh, csinhf, csinhl](csinh-csinhf-csinhl.md)<br/>
[ccosh, ccoshf, ccoshl](ccosh-ccoshf-ccoshl.md)<br/>
[cacosh, cacoshf, cacoshl](cacosh-cacoshf-cacoshl.md)<br/>
[cacos, cacosf, cacosl](cacos-cacosf-cacosl.md)<br/>
[ctan, ctanf, ctanl](ctan-ctanf-ctanl.md)<br/>
[csin, csinf, csinl](csin-csinf-csinl.md)<br/>
[casin, casinf, casinl](casin-casinf-casinl.md)<br/>
[ccos, ccosf, ccosl](ccos-ccosf-ccosl.md)<br/>
[csqrt, csqrtf, csqrtl](csqrt-csqrtf-csqrtl.md)<br/>
