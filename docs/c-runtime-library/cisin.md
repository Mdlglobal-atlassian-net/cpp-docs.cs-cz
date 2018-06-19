---
title: _Cisin – | Microsoft Docs
ms.custom: ''
ms.date: 04/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _CIsin
apilocation:
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
apitype: DLLExport
f1_keywords:
- CIsin
- _CIsin
dev_langs:
- C++
helpviewer_keywords:
- _CIsin intrinsic
- CIsin intrinsic
ms.assetid: f215f39a-2341-4f1c-ba8e-cb522451ceb2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d4593b02b08b1828ff4b29c8f55bfcaf4baa0c9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387444"
---
# <a name="cisin"></a>_CIsin

Vypočítá sinus nejvyšší hodnotu v zásobníku s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
void __cdecl _CIsin();
```

## <a name="remarks"></a>Poznámky

Tato verze vnitřní [sin](../c-runtime-library/reference/sin-sinf-sinl.md) funkce má specializované konvence volání, která funguje s technologií kompilátoru. Ji urychluje spuštění, protože kopie brání generován a pomáhá s přidělení registru.

Výsledná hodnota se posune do horní části zásobníku s plovoucí desetinnou čárkou.

## <a name="requirements"></a>Požadavky

**Platforma:** x86

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[sin, sinf, sinl](../c-runtime-library/reference/sin-sinf-sinl.md)<br/>
