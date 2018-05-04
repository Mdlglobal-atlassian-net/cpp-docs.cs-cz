---
title: offsetof – makro | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 308aac2493751cfe2147187ed9848347124a90d6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="offsetof-macro"></a>offsetof – makro

Načte posun členem od začátku jeho nadřazené struktury.

## <a name="syntax"></a>Syntaxe

```C
size_t offsetof(
   structName,
   memberName
);
```

### <a name="parameters"></a>Parametry

*structName*<br/>
Název nadřazeného datovou strukturu.

*Členské jméno*<br/>
Název člena v nadřazené datovou strukturu pro které chcete určit posun.

## <a name="return-value"></a>Návratová hodnota

**offsetof –** Vrátí posun od začátku její nadřazená struktura dat v bajtech zadaného člena. Je definován pro bitových polí.

## <a name="remarks"></a>Poznámky

**Offsetof –** makro Vrátí posun v bajtech *memberName* od začátku struktury určeného *structName* jako hodnota typu **size_ t**. Můžete určit typy s **struktura** – klíčové slovo.

> [!NOTE]
> **offsetof –** není funkce a nelze popsat pomocí C prototypu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**offsetof –**|\<stddef.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
