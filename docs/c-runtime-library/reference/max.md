---
title: __max
ms.date: 04/05/2018
apiname:
- __max
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
- max
- __max
helpviewer_keywords:
- max macro
- maximum macro
- __max macro
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
ms.openlocfilehash: 32e1207ea4bb030ac5303de32c0566f98e0596a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613756"
---
# <a name="max"></a>__max

Makro preprocesoru, které vrátí větší ze dvou hodnot.

## <a name="syntax"></a>Syntaxe

```C
#define __max(a,b) (((a) > (b)) ? (a) : (b))
```

### <a name="parameters"></a>Parametry

*a*, *b*<br/>
Hodnoty libovolného číselného typu, který se má porovnat.

## <a name="return-value"></a>Návratová hodnota

**__max** vrátí větší z jejích argumentů.

## <a name="remarks"></a>Poznámky

**__Max** – makro porovná dvě hodnoty a vrátí hodnotu větší z nich. Argumenty může být libovolný číselný datový typ, podepsaný nebo nepodepsaný řetězec. Argumenty a vrácené hodnoty musí být stejného datového typu.

Argument vrátil je dvakrát vyhodnocovaný makra. To může vést k neočekávaným výsledkům, pokud je argument výrazu, který se mění její hodnotu, když je vyhodnocen, jako například `*p++`.

## <a name="requirements"></a>Požadavky

|– Makro|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**__max**|\<stdlib.h>|

## <a name="example"></a>Příklad

Další informace, podívejte se na příklad pro [__min](min.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[__min](min.md)<br/>