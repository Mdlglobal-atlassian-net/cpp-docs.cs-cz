---
title: __max – | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- max macro
- maximum macro
- __max macro
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5bc89f74bb98b8fb51dc652ab57c57d37a46d5a0
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="max"></a>__max

Makro preprocesoru, který vrací větší ze dvou hodnot.

## <a name="syntax"></a>Syntaxe

```C
#define __max(a,b) (((a) > (b)) ? (a) : (b))
```

### <a name="parameters"></a>Parametry

*a*, *b*<br/>
Hodnoty všech číselného typu, který se má porovnat.

## <a name="return-value"></a>Návratová hodnota

**__max –** vrátí větší argumentů.

## <a name="remarks"></a>Poznámky

**__Max –** makro porovná dvě hodnoty a vrátí hodnotu typu větší. Argumenty, které může být jakékoli číselný datový typ, podepsané nebo bez znaménka. Argumenty a návratová hodnota musí být stejného datového typu.

Argument vrátil je vyhodnocován dvakrát makro. To může vést k neočekávaným výsledkům, pokud je argument výraz, který mění jeho hodnota při vyhodnotí, jako například `*p++`.

## <a name="requirements"></a>Požadavky

|– Makro|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**__max**|\<stdlib.h>|

## <a name="example"></a>Příklad

Další informace, podívejte se na příklad pro [__min –](min.md).

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[__min](min.md)<br/>