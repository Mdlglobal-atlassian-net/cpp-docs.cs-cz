---
title: _acmdln, _tcmdln, _wcmdln
ms.date: 11/04/2016
api_name:
- _wcmdln
- _acmdln
api_location:
- msvcrt.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _acmdln
- acmdln
- _wcmdln
- wcmdln
- _tcmdln
- tcmdln
helpviewer_keywords:
- _wcmdln global variable
- wcmdln global variable
- _acmdln global variable
- _tcmdln global variable
- tcmdln global variable
- acmdln global variable
ms.assetid: 4fc0a6a0-3f93-420a-a19f-5276061ba539
ms.openlocfilehash: 07061244e06256341a6da7d04e5487e81c4b9378
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940622"
---
# <a name="_acmdln-_tcmdln-_wcmdln"></a>_acmdln, _tcmdln, _wcmdln

Interní globální proměnná CRT Příkazový řádek.

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

Tyto interní proměnné CRT ukládají úplný příkazový řádek. Jsou zpřístupněny v exportovaných symbolech pro CRT, ale nejsou určeny pro použití ve vašem kódu. `_acmdln`ukládá data jako řetězec znaků. `_wcmdln`ukládá data jako řetězec s velkým znakem. `_tcmdln`lze definovat buď `_acmdln` nebo `_wcmdln`, v závislosti na tom, který z nich je vhodný.

## <a name="see-also"></a>Viz také:

[Globální proměnné](../c-runtime-library/global-variables.md)
