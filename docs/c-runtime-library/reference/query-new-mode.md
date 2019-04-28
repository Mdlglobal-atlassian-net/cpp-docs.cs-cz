---
title: _query_new_mode
ms.date: 11/04/2016
apiname:
- _query_new_mode
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- query_new_mode
- _query_new_mode
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
ms.openlocfilehash: 327f22c847793316bd126721b4a66846d7da84dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358070"
---
# <a name="querynewmode"></a>_query_new_mode

Vrátí celé číslo udávající nový režim obslužné rutiny nastavil **_set_new_mode** pro **malloc**.

## <a name="syntax"></a>Syntaxe

```C
int _query_new_mode(
   void
);
```

## <a name="return-value"></a>Návratová hodnota

Vrátí aktuální nový režim obslužné rutiny, konkrétně 0 nebo 1, pro **malloc**. Návratová hodnota 1 značí, že při selhání přidělení paměti, **malloc** volá nové rutiny obsluhy; vrácená hodnota 0 označuje, že tomu tak není.

## <a name="remarks"></a>Poznámky

C++ **_Query_new_mode –** funkce vrátí celé číslo, které označuje nový režim obslužné rutiny, kterou je nastavit C++ [_set_new_mode](set-new-mode.md) fungovat [malloc](malloc.md). Nový režim obslužné rutiny Určuje, zda je při selhání přidělení paměti, **malloc** je volat nové rutiny obsluhy úmluvu [_set_new_handler](set-new-handler.md). Ve výchozím nastavení **malloc** nevolá nové rutiny obsluhy při selhání. Můžete použít **_set_new_mode** tak přepsat toto chování, které při selhání **malloc** volá nové rutiny obsluhy ve stejném způsobu, jakým **nové** operátor provede, když se nepodaří přidělení paměti. Další informace najdete v diskuzi o [nové a odstranit operátory](../../cpp/new-and-delete-operators.md) v referenci jazyka C++.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_query_new_mode**|\<new.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
