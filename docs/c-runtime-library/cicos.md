---
title: _Cicos – | Microsoft Docs
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CIcos
apilocation:
- msvcr90.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- CIcos
- _CIcos
dev_langs:
- C++
helpviewer_keywords:
- _CIcos intrinsic
- CIcos intrinsic
ms.assetid: 6fc203fb-66f3-4ead-9784-f85833c26f1b
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cb399a25bacd7fc288ad881625589e240009068a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="cicos"></a>_CIcos

Výpočet kosinu nejvyšší hodnotu v zásobníku s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
void __cdecl _CIcos();
```

## <a name="remarks"></a>Poznámky

Tato verze [cos](../c-runtime-library/reference/cos-cosf-cosl.md) funkce má specializované konvence volání, která funguje s technologií kompilátoru. Ji urychluje spuštění, protože kopie brání generován a pomáhá s přidělení registru.

Výsledná hodnota se posune do horní části zásobníku s plovoucí desetinnou čárkou.

## <a name="requirements"></a>Požadavky

**Platforma:** x86

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[Cos, cosf –, cosl –](../c-runtime-library/reference/cos-cosf-cosl.md)<br/>
