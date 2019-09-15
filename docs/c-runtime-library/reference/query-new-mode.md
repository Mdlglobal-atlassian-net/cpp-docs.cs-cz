---
title: _query_new_mode
ms.date: 11/04/2016
api_name:
- _query_new_mode
api_location:
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
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- query_new_mode
- _query_new_mode
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
ms.openlocfilehash: 59724dafdc6488596478d0b44b254c4f498fce99
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950103"
---
# <a name="_query_new_mode"></a>_query_new_mode

Vrací celé číslo označující nový režim obslužné rutiny nastavené hodnotou **_set_new_mode** **pro typ**pole.

## <a name="syntax"></a>Syntaxe

```C
int _query_new_mode(
   void
);
```

## <a name="return-value"></a>Návratová hodnota

Vrátí aktuální režim obslužné rutiny, jmenovitě 0 nebo 1, pro **pole pro vytvoření**nového. Návratová hodnota 1 **znamená, že** při selhání přidělení paměti zavolá neplnění volání nové rutiny obslužné rutiny. Návratová hodnota 0 značí, že není.

## <a name="remarks"></a>Poznámky

C++ **_query_new_mode** vrací celé číslo, které označuje nový režim obslužné rutiny, který je nastaven C++ funkcí [_set_new_mode](set-new-mode.md) pro typ [objektu.](malloc.md) Nový režim obslužné rutiny označuje, zda při selhání přidělení paměti, **je třeba** volat novou rutinu obslužné rutiny nastavenou na [_set_new_handler](set-new-handler.md). Ve výchozím nastavení nezavolá při selhání novou rutinu obslužné rutiny. Můžete použít **_set_new_mode** k přepsání tohoto chování, aby při selhání zavolalo novou rutinu obslužné rutiny stejným způsobem jako operátor **New** **při selhání přidělení** paměti. Další informace naleznete v tématu věnovaném [operátorům New a DELETE](../../cpp/new-and-delete-operators.md) v referenční příručce C++ jazyka.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_query_new_mode**|\<New. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
