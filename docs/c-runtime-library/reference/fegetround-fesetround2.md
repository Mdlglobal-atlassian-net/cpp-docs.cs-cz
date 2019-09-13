---
title: fegetround, fesetround
ms.date: 04/05/2018
api_name:
- fegetround
- fesetround
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fegetround
- fesetround
- fenv/fegetround
- fenv/fesetround
helpviewer_keywords:
- fegetround function
- fesetround function
ms.assetid: 596af00b-be2f-4f57-b2f5-460485f9ff0b
ms.openlocfilehash: b210dbce3104820f667d4ad0b4421277567b279f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941199"
---
# <a name="fegetround-fesetround"></a>fegetround, fesetround

Získá nebo nastaví aktuální režim zaokrouhlení s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
int fegetround(void);

int fesetround(
   int round_mode
);
```

### <a name="parameters"></a>Parametry

*round_mode*<br/>
Režim zaokrouhlení, který se má nastavit, jako jedno z makra zaokrouhlení s plovoucí desetinnou čárkou. Pokud hodnota není rovna jednomu z makra zaokrouhlení s plovoucí desetinnou čárkou, režim zaokrouhlení se nezmění.

## <a name="return-value"></a>Návratová hodnota

Po úspěchu **fegetround** vrátí režim zaokrouhlení jako jednu z hodnot makra zaokrouhlení s plovoucí desetinnou čárkou. Vrátí zápornou hodnotu, pokud nelze určit aktuální režim zaokrouhlení.

Po úspěchu **fesetround** vrátí hodnotu 0. V opačném případě se vrátí nenulová hodnota.

## <a name="remarks"></a>Poznámky

Operace s plovoucí desetinnou čárkou můžou používat jeden z několika režimů zaokrouhlení. Tyto ovládací prvky, které směrují výsledky operací s plovoucí desetinnou čárkou, jsou zaokrouhleny směrem k době uložení výsledků. Jedná se o názvy a chování pro makra zaokrouhlení s plovoucí desetinnou čárkou definovaná v \<fenv. h >:

|– Makro|Popis|
|-----------|-----------------|
|FE_DOWNWARD|Zaokrouhlí směrem k zápornému nekonečnu.|
|FE_TONEAREST|Zaokrouhlit směrem k nejbližšímu.|
|FE_TOWARDZERO|Zaokrouhlí směrem k nule.|
|FE_UPWARD|Zaokrouhlit směrem k kladnému nekonečnu.|

Výchozím chováním FE_TONEAREST je zaokrouhlit výsledky uprostřed mezi reprezentovatelné hodnoty směrem k nejbližší hodnotě a sudým (0) nejméně významným bitem.

Aktuální režim zaokrouhlení má vliv na tyto operace:

- Převody řetězců.

- Výsledky aritmetických operátorů plovoucí desetinné čárky mimo konstantní výrazy.

- Funkce zaokrouhlování knihovny, například **isknout** a **nearbyint –** .

- Vrátí hodnoty ze standardních matematických funkcí knihovny Standard.

Aktuální režim zaokrouhlení nemá vliv na tyto operace:

- Funkce knihovny **TRUNC –** , **ceil –** , **Floor**a **lround** .

- Implicitní přetypování a převody s plovoucí desetinnou čárkou na celé číslo, které vždycky zaokrouhlí směrem nahoru na nulu.

- Výsledky aritmetických operátorů s plovoucí desetinnou čárkou v konstantních výrazech, které se vždycky zaokrouhlují na nejbližší hodnotu.

Chcete-li použít tyto funkce, je nutné vypnout optimalizace s plovoucí desetinnou čárkou, které by mohly `#pragma fenv_access(on)` zabránit přístupu pomocí direktivy před voláním. Další informace najdete v tématu [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|**fegetround**, **fesetround**|\<fenv. h >|\<cfenv>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[nearbyint, nearbyintf, nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[rint, rintf, rintl](rint-rintf-rintl.md)<br/>
[lrint, lrintf, lrintl, llrint, llrintf, llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
