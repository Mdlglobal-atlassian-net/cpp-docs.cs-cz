---
title: _local_unwind2
ms.date: 11/04/2016
api_name:
- _local_unwind2
api_location:
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _local_unwind2
- local_unwind2
helpviewer_keywords:
- _local_unwind2 function
- local_unwind2 function
ms.assetid: 44f1fa82-e01e-490f-a6e6-18fc6811c28c
ms.openlocfilehash: 64ed92af32caaf579e7c6951250e3bf692d1cf43
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944213"
---
# <a name="_local_unwind2"></a>_local_unwind2

Vnitřní funkce CRT. Spustí všechny obslužné rutiny ukončení, které jsou uvedeny v tabulce určeného oboru.

## <a name="syntax"></a>Syntaxe

```
void _local_unwind2(
   PEXCEPTION_REGISTRATION xr,
   int stop
);
```

#### <a name="parameters"></a>Parametry

*xr*<br/>
pro Záznam registrace, který je přidružen k jedné tabulce oborů.

*Stop*<br/>
pro Lexikální úroveň, která označuje, `_local_unwind2` kde se má zastavit.

## <a name="remarks"></a>Poznámky

Tato metoda je používána pouze v prostředí Runtime. Nevolejte metodu ve vašem kódu.

Pokud tato metoda spouští obslužné rutiny ukončení, začíná na aktuální lexikální úrovni a pracuje na jejich cestě v lexikálních úrovních, dokud nedosáhne úrovně, která je `stop`uvedena v. Neprovádí obslužné rutiny ukončení na úrovni, která je uvedena `stop`v.

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)
