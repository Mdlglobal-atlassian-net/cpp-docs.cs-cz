---
title: fegetround fesetround
ms.date: 04/05/2018
apiname:
- fegetround
- fesetround
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fegetround
- fesetround
- fenv/fegetround
- fenv/fesetround
helpviewer_keywords:
- fegetround function
- fesetround function
ms.assetid: 596af00b-be2f-4f57-b2f5-460485f9ff0b
ms.openlocfilehash: 061f0c9563d284396e85c6de70a2fe0911218eb3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334369"
---
# <a name="fegetround-fesetround"></a>fegetround fesetround

Získá nebo nastaví aktuální režimu zaokrouhlení s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
int fegetround(void);

int fesetround(
   int round_mode
);
```

### <a name="parameters"></a>Parametry

*round_mode*<br/>
Režim zaokrouhlování nastavit jako jeden z makra zaokrouhlení s plovoucí desetinnou čárkou. Pokud hodnota není roven jedné makra zaokrouhlení s plovoucí desetinnou čárkou, se nezmění režimu zaokrouhlování.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu **fegetround** vrátí režimu zaokrouhlování jako jedno zaokrouhlení – makro hodnoty s plovoucí desetinnou čárkou bodu. Pokud nelze určit aktuální režim vrátí zápornou hodnotu.

V případě úspěchu **fesetround** vrátí hodnotu 0. Jinak se vrátí nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

Operace s plovoucí desetinnou čárkou, můžete použít jednu z několika režimech zaokrouhlení. Tyto ovládací prvek směru výsledky operací s plovoucí desetinnou čárkou jsou zaokrouhleny směrem k, pokud se mají výsledky ukládat. Jedná se o názvy a chování plovoucí desetinné čárky zaokrouhlení maker definované v \<fenv.h >:

|– Makro|Popis|
|-----------|-----------------|
|FE_DOWNWARD|Zaokrouhlí směrem k záporné nekonečno.|
|FE_TONEAREST|Zaokrouhlí na nejbližší.|
|FE_TOWARDZERO|Zaokrouhlí směrem k nule.|
|FE_UPWARD|Zaokrouhlí směrem k kladné nekonečno.|

Výchozí chování FE_TONEAREST se má zaokrouhlit výsledků uprostřed mezi reprezentovatelných hodnot na nejbližší hodnotu s i (0) nejméně významných bitů.

Aktuální režim má vliv na tyto operace:

- Převody typu řetězec.

- Výsledky s plovoucí desetinnou čárkou aritmetické operátory mimo konstantní výrazy.

- Knihovna zaokrouhlení funkce, jako například **isknout** a **nearbyint –**.

- Vrácení hodnoty z standardní knihovnu matematických funkcí.

Aktuální režim neovlivní tyto operace:

- **Trunc**, **ceil –**, **floor**, a **lround –** funkce knihovny.

- S plovoucí desetinnou čárkou na celé číslo implicitní přetypování a převody, které vždy zaokrouhlení směrem k nule.

- Výsledky v konstantních výrazech, které vždy zaokrouhlit na nejbližší hodnotu s plovoucí desetinnou čárkou aritmetické operátory.

Pokud chcete použít tyto funkce, je nutné vypnout s plovoucí desetinnou čárkou optimalizace, které by mohla zabránit přístupu pomocí `#pragma fenv_access(on)` direktiv před voláním. Další informace najdete v tématu [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Záhlaví C|Hlaviček jazyka C++|
|--------------|--------------|------------------|
|**fegetround**, **fesetround**|\<fenv.h>|\<cfenv>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[nearbyint, nearbyintf, nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[rint, rintf, rintl](rint-rintf-rintl.md)<br/>
[lrint, lrintf, lrintl, llrint, llrintf, llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
