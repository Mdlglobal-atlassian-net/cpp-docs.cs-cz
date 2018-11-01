---
title: _initterm, _initterm_e
ms.date: 11/04/2016
apiname:
- _initterm_e
- _initterm
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _initterm_e
- initterm
- _initterm
- initterm_e
helpviewer_keywords:
- initterm function
- initterm_e function
- _initterm function
- _initterm_e function
ms.assetid: 85131efe-c747-429a-8897-bcdedb000172
ms.openlocfilehash: 65963e95507d4d6444ebcc9038b5b8cf797f9feb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620711"
---
# <a name="initterm-initterme"></a>_initterm, _initterm_e

Vnitřní metody, které vás tabulku ukazatelů na funkce a jejich inicializaci.

Počáteční umístění v tabulce je ukazatel na první a druhý ukazatel je konečné umístění.

## <a name="syntax"></a>Syntaxe

```C
void __cdecl _initterm(
   PVFV *,
   PVFV *
);

int __cdecl _initterm_e(
   PVFV *,
   PVFV *
);
```

## <a name="return-value"></a>Návratová hodnota

Pokud se inicializace nezdaří a vyvolá chybu; kód chyby 0, pokud nenastane žádná chyba.

## <a name="remarks"></a>Poznámky

Tyto metody jsou volány interně pouze během inicializace programu v jazyce C++. Tyto metody volat není v programu.

Když tyto metody Procházet tabulku funkce položky, přeskočí **NULL** položky a pokračovat.

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
