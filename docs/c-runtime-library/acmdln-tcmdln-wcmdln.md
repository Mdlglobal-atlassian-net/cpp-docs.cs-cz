---
title: _acmdln – _tcmdln –, _wcmdln – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _wcmdln
- _acmdln
apilocation:
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _acmdln
- acmdln
- _wcmdln
- wcmdln
- _tcmdln
- tcmdln
dev_langs:
- C++
helpviewer_keywords:
- _wcmdln global variable
- wcmdln global variable
- _acmdln global variable
- _tcmdln global variable
- tcmdln global variable
- acmdln global variable
ms.assetid: 4fc0a6a0-3f93-420a-a19f-5276061ba539
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c9dd8af9b55ab022277737f2349b27eb257810f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46135864"
---
# <a name="acmdln-tcmdln-wcmdln"></a>_acmdln, _tcmdln, _wcmdln

Interní globální proměnné CRT. Příkazový řádek.

## <a name="syntax"></a>Syntaxe

```
char * _acmdln;
wchar_t * _wcmdln;

#ifdef WPRFLAG
   #define _tcmdln _wcmdln
#else
   #define _tcmdln _acmdln
```

## <a name="remarks"></a>Poznámky

Tyto interní proměnné CRT ukládání úplný příkazový řádek. Jsou přístupné na exportované symboly pro CRT, ale nejsou určeny pro použití ve vašem kódu. `_acmdln` ukládá data jako řetězec znaků. `_wcmdln` ukládá data jako řetězec širokých znaků. `_tcmdln` může být definována buď jako `_acmdln` nebo `_wcmdln`podle toho, které je vhodné.

## <a name="see-also"></a>Viz také

[Globální proměnné](../c-runtime-library/global-variables.md)