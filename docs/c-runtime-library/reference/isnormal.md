---
title: isnormal –
ms.date: 01/31/2019
f1_keywords:
- isnormal
- math/isnormal
helpviewer_keywords:
- isnormal function
ms.openlocfilehash: e426fbce71efff1e810a03b8347e7c48aa0d91d2
ms.sourcegitcommit: 14b292596bc9b9b883a9c58cd3e366b282a1f7b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "60124678"
---
# <a name="isnormal"></a>isnormal –

Určuje, zda hodnotu s plovoucí desetinnou čárkou je běžné hodnoty.

## <a name="syntax"></a>Syntaxe

```C
int isnormal(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isnormal(
   FloatingType x
) throw(); /* C++-only function template */
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou k testování.

## <a name="return-value"></a>Návratová hodnota

**isnormal –** vrací nenulovou hodnotu (**true** v C++ kód) Pokud tento argument *x* není nula, subnormal, nekonečno, ani NaN. V opačném případě **isnormal –** vrátí hodnotu 0 (**false** v C++ kód).

## <a name="remarks"></a>Poznámky

**isnormal –** je makro při kompilaci jako C a šablonu vložené funkce při kompilaci jako C++.

## <a name="requirements"></a>Požadavky

|Funkce|Požadované záhlaví (C)|Požadované záhlaví (C++)|
|--------------|---------------------------|-------------------------------|
|**isnormal**|\<math.h>|\<Math.h > nebo \<cmath >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
