---
title: fegetround fesetround | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- fegetround function
- fesetround function
ms.assetid: 596af00b-be2f-4f57-b2f5-460485f9ff0b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 137d886d557cbb1fee7db1dd60405b9557bf6bf2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="fegetround-fesetround"></a>fegetround fesetround

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
Režim zaokrouhlení nastavit jako jeden z s plovoucí desetinnou čárkou zaokrouhlení makra. Pokud hodnota není jednu s plovoucí desetinnou čárkou zaokrouhlení makra, nedojde ke změně režimu zaokrouhlení.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu **fegetround** vrátí hodnotu režimu zaokrouhlení jako jeden z plovoucí desetinné čárky zaokrouhlení makro hodnoty. Pokud je aktuální režim zaokrouhlení nelze určit vrátí zápornou hodnotu.

V případě úspěchu **fesetround** vrátí hodnotu 0. Jinak se vrátí nenulovou hodnotu.

## <a name="remarks"></a>Poznámky

Operace s plovoucí desetinnou čárkou můžete použít některou z několika režimech zaokrouhlení. Tyto řídit směru výsledky operací s plovoucí desetinnou čárkou se zaokrouhlí směrem k, když jsou uložené výsledky. Jedná se o názvy a chování s plovoucí desetinnou čárkou zaokrouhlení makra definované v \<fenv.h >:

|– Makro|Popis|
|-----------|-----------------|
|FE_DOWNWARD|Zaokrouhlí směrem záporné nekonečno.|
|FE_TONEAREST|Zaokrouhlí směrem na nejbližší.|
|FE_TOWARDZERO|Zaokrouhlí směrem k nule.|
|FE_UPWARD|Zaokrouhlí směrem kladné nekonečno.|

Výchozí chování FE_TONEAREST je zaokrouhlit výsledků uprostřed mezi reprezentovat hodnoty na nejbližší hodnotu s i (0) nejméně významný bit.

Aktuální režim zaokrouhlení ovlivňují tyto operace:

- Řetězec převody.

- Výsledky s plovoucí desetinnou čárkou aritmetické operátory mimo konstantní výrazy.

- Knihovna zaokrouhlení funkce, jako například **tisknout** a **nearbyint –**.

- Návratové hodnoty z matematické funkce standardní knihovny.

Aktuální režim zaokrouhlení nemá vliv na tyto operace:

- **Trunc**, **ceil**, **podlaží**, a **lround –** – funkce knihovny.

- S plovoucí desetinnou čárkou na celé číslo implicitní přetypování a převody, které vždy zaokrouhlí směrem k nule.

- Výsledky s plovoucí desetinnou čárkou aritmetických operátorů v konstantní výrazy, které vždy zaokrouhlí na nejbližší hodnotu.

Použití těchto funkcí, je nutné vypnout s plovoucí desetinnou čárkou optimalizace, které může zabránit přístupu pomocí `#pragma fenv_access(on)` direktivy před volání. Další informace najdete v tématu [fenv_access –](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**fegetround**, **fesetround**|\<fenv.h >|\<cfenv>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[nearbyint – nearbyintf –, nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[rint, rintf, rintl](rint-rintf-rintl.md)<br/>
[lrint, lrintf, lrintl, llrint, llrintf, llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
