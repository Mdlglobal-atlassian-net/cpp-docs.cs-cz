---
title: offsetof – makro
ms.date: 11/04/2016
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
apitype: DLLExport
f1_keywords:
- offsetof
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
ms.openlocfilehash: a0f367dbe6fa2681a7d413304f32b5699b8f7cee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458317"
---
# <a name="offsetof-macro"></a>offsetof – makro

Načte posun člen od začátku své nadřazené struktury.

## <a name="syntax"></a>Syntaxe

```C
size_t offsetof(
   structName,
   memberName
);
```

### <a name="parameters"></a>Parametry

*structName*<br/>
Název nadřazené struktury data.

*Jméno*<br/>
Název členu v nadřazené struktury dat pro který chcete určit posun.

## <a name="return-value"></a>Návratová hodnota

**offsetof** Vrátí posun od začátku své nadřazené struktury dat v bajtech zadaného člena. Je definováno pro bitové pole.

## <a name="remarks"></a>Poznámky

**Offsetof** – makro vrací posun v bajtech *memberName* od začátku této struktuře určené *structName* jako hodnotu typu **size_ t**. Můžete určit typy s **struktura** – klíčové slovo.

> [!NOTE]
> **offsetof** není funkce a nemůže být popisují pomocí prototyp C.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**offsetof**|\<stddef.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
