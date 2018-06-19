---
title: _chgsign – _chgsignf –, _chgsignl – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _chgsignl
- _chgsign
- _chgsignf
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
- _chgsignf
- chgsign
- _chgsignl
- _chgsign
dev_langs:
- C++
helpviewer_keywords:
- _chgsignl function
- _chgsignf function
- chgsign function
- _chgsign function
ms.assetid: a6646f8e-213d-4564-8617-f43bc66f989f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 781359972b67b2634f8f762fac98bf9216ef5ab5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393440"
---
# <a name="chgsign-chgsignf-chgsignl"></a>_chgsign, _chgsignf, _chgsignl

Obrátí znaménko čísla s plovoucí desetinnou čárkou argument.

## <a name="syntax"></a>Syntaxe

```C
double _chgsign(
   double x
);
float _chgsignf(
   float x
);
long double _chgsignl(
   long double x
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou se musí změnit.

## <a name="return-value"></a>Návratová hodnota

**_Chgsign –** funkce vrátí hodnotu, která je rovna s plovoucí desetinnou čárkou argument *x*, ale s jeho přihlašovací vrátit zpět. Neexistuje žádný návratový chyby.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_chgsign**|\<float.h – >|
|**_chgsignf –**, **_chgsignl –**|\<Math.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl](copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)<br/>
