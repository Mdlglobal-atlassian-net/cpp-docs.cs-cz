---
title: spawn – konstanty | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _P_NOWAIT
- _P_OVERLAY
- _P_WAIT
- _P_DETACH
- _P_NOWAITO
dev_langs:
- C++
helpviewer_keywords:
- _P_OVERLAY constant
- P_DETACH constant
- P_OVERLAY constant
- P_NOWAIT constant
- _P_DETACH constant
- _P_NOWAIT constant
- _P_NOWAITO constant
- P_NOWAITO constant
- spawn constants
- P_WAIT constant
- _P_WAIT constant
ms.assetid: e0533e88-d362-46fc-b53c-5f193226d879
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8daaf38e60ca48b4a34deb2086bbd14eb45651e4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116929"
---
# <a name="spawn-constants"></a>spawn – konstanty

## <a name="syntax"></a>Syntaxe

```
#include <process.h>
```

## <a name="remarks"></a>Poznámky

`mode` Argument určuje akci provedenou na základě volajícího procesu před nasazením a během operace vytvořit podřízený proces. Následující hodnoty pro `mode` jsou možné:

|Konstanta|Význam|
|--------------|-------------|
|`_P_OVERLAY`|Překryvy volající proces se nový proces, zničení volajícího procesu (stejný vliv jako `_exec` volání).|
|`_P_WAIT`|Pozastaví volající vlákno, dokud se nedokončí spuštění nového procesu (synchronní `_spawn`).|
|`_P_NOWAIT`, `_P_NOWAITO`|Pokračuje v provádění volající proces současně nový proces (asynchronní `_spawn`).|
|`_P_DETACH`|Pokračuje v provádění volajícího procesu. Nový proces běží na pozadí bez přístupu konzoly nebo klávesnice. Volání `_cwait` proti nový proces se nezdaří. Toto je asynchronní `_spawn`.|

## <a name="see-also"></a>Viz také

[_spawn, _wspawn – funkce](../c-runtime-library/spawn-wspawn-functions.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)