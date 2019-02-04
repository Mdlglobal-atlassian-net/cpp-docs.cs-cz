---
title: isgreater isgreaterequal, isless, islessequal, islessgreater, isunordered
ms.date: 01/31/2019
f1_keywords:
- isgreater
- math/isgreater
- isgreaterequal
- math/isgreaterequal
- isless
- math/isless
- islessequal
- math/islessequal
- islessgreater
- math/islessgreater
- isunordered
- math/isunordered
helpviewer_keywords:
- isgreater function
- isgreaterequal function
- isless function
- islessequal function
- islessgreater function
- isunordered function
ms.openlocfilehash: 748360cae1dd0ee43645dee369c60c835246ed03
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703364"
---
# <a name="isgreater-isgreaterequal-isless-islessequal-islessgreater-isunordered"></a>isgreater isgreaterequal, isless, islessequal, islessgreater, isunordered

Určuje pořadí vztah mezi dvěma hodnotami s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
int isgreater(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isgreaterequal(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isless(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int islessequal(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int islessgreater(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isunordered(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */
```

```C++
template <class FloatingType1, class FloatingType2>
inline bool isgreater(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isgreaterequal(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isless(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool islessequal(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool islessgreater(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isunordered(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */
```

### <a name="parameters"></a>Parametry

*x*, *y*<br/>
Hodnoty s plovoucí desetinnou čárkou k porovnání.

## <a name="return-value"></a>Návratová hodnota

Ve všech porovnání porovnat nekonečno stejné znaménko rovnosti. Záporné nekonečno je menší, než nabízí jakýkoli konečná hodnota nebo kladné nekonečno. Kladné nekonečno je větší než všechny konečné hodnoty nebo záporné nekonečno. Nuly jsou stejné bez ohledu na přihlášení. Hodnoty NaN nejsou menší než, rovna nebo větší než libovolnou hodnotu, včetně další NaN.

Když je ani argumentem NaN, pořadí makra **isgreater**, **isgreaterequal**, **isless**, a **islessequal** vrátit nenulové hodnotu, pokud zadané pořadí vztah mezi *x* a *y* platí. Tato makra vrátí 0, pokud jsou argumenty nebo obě hodnoty NaN, nebo pokud pořadí relace má hodnotu false. Formuláře funkce chovají stejným způsobem, ale vrátí **true** nebo **false**.

**Islessgreater** – makro vrací nenulovou hodnotu, pokud obě *x* a *y* nejsou hodnoty NaN, a *x* je buď menší než nebo rovna *y*. Pokud nebo oba argumenty jsou hodnoty NaN, nebo pokud jsou hodnoty stejné, vrátí hodnotu 0. Formulář funkce se chová stejně, ale vrátí **true** nebo **false**.

**Isunordered** – makro vrací nenulovou hodnotu, pokud buď *x*, *y*, nebo jsou obě hodnoty NaN. Jinak vrací 0. Formulář funkce se chová stejně, ale vrátí **true** nebo **false**.

## <a name="remarks"></a>Poznámky

Tyto operace porovnání jsou implementovány jako makra při kompilaci jako C a jako vložené šablony při kompilaci jako C++.

## <a name="requirements"></a>Požadavky

|Funkce|Požadované záhlaví (C)|Požadované záhlaví (C++)|
|--------------|---------------------------|-------------------------------|
| **isgreater**, **isgreaterequal**, **isless**,<br/>**islessequal**, **islessgreater**, **isunordered** | \<math.h> | \<Math.h > nebo \<cmath > |

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf –](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
