---
title: feraiseexcept
ms.date: 04/05/2018
api_name:
- feraiseexcept
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
api_type:
- HeaderDef
f1_keywords:
- feraiseexcept
- fenv/feraiseexcept
helpviewer_keywords:
- feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
ms.openlocfilehash: 40ff315c179a6b62a3073d4f07e4e6a6d1c1acab
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941132"
---
# <a name="feraiseexcept"></a>feraiseexcept

Vyvolává zadané výjimky s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
int feraiseexcept(
   int excepts
);
```

### <a name="parameters"></a>Parametry

*s výjimkou*<br/>
Výjimky s plovoucí desetinnou čárkou k vyvolání.

## <a name="return-value"></a>Návratová hodnota

Pokud jsou všechny zadané výjimky vyvolány úspěšně, vrátí hodnotu 0.

## <a name="remarks"></a>Poznámky

Funkce **feraiseexcept** se pokusí vyvolat výjimky s plovoucí desetinnou čárkou, které jsou určené *výjimkou*.   Funkce **feraiseexcept** podporuje tato makra výjimek definovaná v \<fenv. h >:

|Makro výjimky|Popis|
|---------------------|-----------------|
|FE_DIVBYZERO|V dřívější operaci s plovoucí desetinnou čárkou došlo k chybě v záčísle nebo objektu. byla vytvořena hodnota nekonečno.|
|FE_INEXACT|Funkce byla nucena zaokrouhlit uložený výsledek předchozí operace s plovoucí desetinnou čárkou.|
|FE_INVALID|V dřívější operaci s plovoucí desetinnou čárkou došlo k chybě domény.|
|FE_OVERFLOW|Došlo k chybě rozsahu; předchozí výsledek operace s plovoucí desetinnou čárkou byl pro reprezentaci příliš velký.|
|FE_UNDERFLOW|Předchozí výsledek operace s plovoucí desetinnou čárkou byl příliš malý, aby byl reprezentován s plnou přesností. byla vytvořena deběžná hodnota.|
|FE_ALLEXCEPT|Bitové nebo všechny podporované výjimky s plovoucí desetinnou čárkou.|

Argument *excepts* může být nula, jedna z hodnot makra výjimky nebo bitová nebo druhá z podporovaných maker výjimek. Pokud je jedno ze zadaných maker výjimek FE_OVERFLOW nebo FE_UNDERFLOW, může být výjimka FE_INEXACT vyvolána jako vedlejší efekt.

Chcete-li použít tuto funkci, je nutné vypnout optimalizace plovoucí desetinné čárky, které by mohly zabránit přístupu `#pragma fenv_access(on)` pomocí direktivy před voláním. Další informace najdete v tématu [fenv_access](../../preprocessor/fenv-access.md).

**Specifické pro společnost Microsoft:** Výjimky určené v *s výjimkou* jsou vyvolány v pořadí FE_INVALID, FE_DIVBYZERO, FE_OVERFLOW, FE_UNDERFLOW, FE_INEXACT. Nicméně FE_INEXACT lze vyvolat, když je vyvolána FE_OVERFLOW nebo FE_UNDERFLOW, i když není zadáno v *s výjimkou*. **Specifické pro konec Microsoftu**

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|*feraiseexcept*|\<fenv. h >|\<cfenv>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
