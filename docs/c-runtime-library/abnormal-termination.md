---
title: _abnormal_termination | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _abnormal_termination
apilocation:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _abnormal_termination
dev_langs:
- C++
helpviewer_keywords:
- _abnormal_termination
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e311c27d61eca82019f8069b0984557af02c74a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028204"
---
# <a name="abnormaltermination"></a>_abnormal_termination

Označuje, zda `__finally` bloku [try-finally – příkaz](../cpp/try-finally-statement.md) se zadá při provádění vnitřního seznam obslužné rutiny ukončení systému.

## <a name="syntax"></a>Syntaxe

```cpp
int   _abnormal_termination(
   );
```

## <a name="return-value"></a>Návratová hodnota

`true` Pokud je systém *odvíjení* zásobníku; v opačném případě `false`.

## <a name="remarks"></a>Poznámky

Toto je vnitřní funkce používané ke správě odvíjení výjimky a není určena k volání z uživatelského kódu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|_abnormal_termination|excpt.h|

## <a name="see-also"></a>Viz také

[try-finally – příkaz](../cpp/try-finally-statement.md)