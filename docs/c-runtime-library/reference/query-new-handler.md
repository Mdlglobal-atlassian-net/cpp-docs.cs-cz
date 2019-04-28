---
title: _query_new_handler
ms.date: 11/04/2016
apiname:
- _query_new_handler
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
- _query_new_handler
- query_new_handler
helpviewer_keywords:
- query_new_handler function
- handler routines
- error handling
- _query_new_handler function
ms.assetid: 9a84b5c3-fe33-4c01-83a0-be87dc3ec518
ms.openlocfilehash: febefbe46d95b7e5c8de026806a20d7eff74e7cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357874"
---
# <a name="querynewhandler"></a>_query_new_handler

Vrátí adresu aktuální nové rutiny obsluhy.

## <a name="syntax"></a>Syntaxe

```C
_PNH _query_new_handler(
   void
);
```

## <a name="return-value"></a>Návratová hodnota

Vrátí adresu aktuální nové rutiny obsluhy úmluvu **_set_new_handler**.

## <a name="remarks"></a>Poznámky

C++ **_Query_new_handler –** funkce vrátí adresu aktuální funkce zpracování výjimek nastavil C++ [_set_new_handler](set-new-handler.md) funkce. **_set_new_handler** slouží k určení funkce protokolem zpracování výjimek, který je získat kontrolu, pokud **nové** operátor selže přidělování paměti. Další informace najdete v diskuzi o [nové a odstranit operátory](../../cpp/new-and-delete-operators.md) v referenci jazyka C++.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_query_new_handler**|\<new.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[Přidělení paměti](../../c-runtime-library/memory-allocation.md)<br/>
[free](free.md)<br/>
