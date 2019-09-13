---
title: _CIatan
ms.date: 11/04/2016
api_name:
- _CIatan
api_location:
- msvcr120.dll
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CIatan
- CIatan
helpviewer_keywords:
- CIatan intrinsic
- _CIatan intrinsic
ms.assetid: 3baa0429-fe46-4bab-8b00-868e2186dc8c
ms.openlocfilehash: a932f305f43ecf1d6df978e733f39d7fa91f3e78
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940606"
---
# <a name="_ciatan"></a>_CIatan

Vypočítá arkustangens horní hodnoty v zásobníku.

## <a name="syntax"></a>Syntaxe

```
void __cdecl _CIatan();
```

## <a name="remarks"></a>Poznámky

Tato verze `atan` funkce má specializovanou konvenci volání, kterou kompilátor rozumí. Zrychluje spouštění, protože brání vygenerování kopií a pomáhá s přidělením registru.

Výsledná hodnota je vložena do horní části zásobníku.

## <a name="requirements"></a>Požadavky

**Platforma:** x86

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)
