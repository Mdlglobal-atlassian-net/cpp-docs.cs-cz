---
title: isnormal –
ms.date: 01/31/2019
f1_keywords:
- isnormal
- math/isnormal
helpviewer_keywords:
- isnormal function
ms.openlocfilehash: 93e3b8912ddf20bf8e190bb42e8413e6d909bbcc
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703362"
---
# <a name="isnormal"></a>isnormal –

Určuje, zda s plovoucí desetinnou čárkou hodnota nekonečno.

## <a name="syntax"></a>Syntaxe

```C
int isnormal(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isnormal(
   FloatingType x
) throw(); /* C++-only template function */
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou k testování.

## <a name="return-value"></a>Návratová hodnota

**isnormal –** vrací nenulovou hodnotu (**true** v kódu jazyka C++) Pokud argument *x* je omezené a ne subnormal. **isnormal –** vrátí hodnotu 0 (**false** v kódu jazyka C++) Pokud je argumentem subnormal nekonečno a NAN.

## <a name="remarks"></a>Poznámky

**isnormal –** je makro při kompilaci jako C a vložené funkce šablony při kompilaci jako C++.

## <a name="requirements"></a>Požadavky

|Funkce|Požadované záhlaví (C)|Požadované záhlaví (C++)|
|--------------|---------------------------|-------------------------------|
|**isnormal**|\<math.h>|\<Math.h > nebo \<cmath >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf –](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
