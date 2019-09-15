---
title: OffsetOf – makro
ms.date: 11/04/2016
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
- DLLExport
topic_type:
- apiref
f1_keywords:
- offsetof
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
ms.openlocfilehash: 278fca89046fcfc98e8c3ff726918cb4319e4ab0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951251"
---
# <a name="offsetof-macro"></a>OffsetOf – makro

Načte posun člena od začátku jeho nadřazené struktury.

## <a name="syntax"></a>Syntaxe

```C
size_t offsetof(
   structName,
   memberName
);
```

### <a name="parameters"></a>Parametry

*structName*<br/>
Název nadřazené datové struktury

*memberName*<br/>
Název člena v nadřazené datové struktuře, pro který se má určit posun.

## <a name="return-value"></a>Návratová hodnota

**OffsetOf** vrací posun v bajtech zadaného člena od začátku své nadřazené datové struktury. Není definováno pro bitová pole.

## <a name="remarks"></a>Poznámky

Makro **OffsetOf** vrací posun v bajtech *člena* od začátku struktury určené parametrem *struct* jako hodnotu typu **size_t**. Můžete určit typy pomocí klíčového slova **struct** .

> [!NOTE]
> **OffsetOf** není funkce a nelze ji popsat pomocí prototypu jazyka C.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**OffsetOf**|\<stddef.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
