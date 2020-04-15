---
title: _get_terminate
ms.date: 4/2/2020
api_name:
- _get_terminate
- _o__get_terminate
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_terminate
- _get_terminate
- __get_terminate
helpviewer_keywords:
- __get_terminate function
- get_terminate function
- _get_terminate function
ms.assetid: c8f168c4-0ad5-4832-a522-dd1ef383c208
ms.openlocfilehash: fff90037851b23f3525f514aba0f6f913f9dd776
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344923"
---
# <a name="_get_terminate"></a>_get_terminate

Vrátí rutinu ukončení, která má být volána **hodnotou terminate**.

## <a name="syntax"></a>Syntaxe

```C
terminate_function _get_terminate( void );
```

## <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na funkci registrovanou [společností set_terminate](set-terminate-crt.md). Pokud nebyla nastavena žádná funkce, vrácená hodnota může být použita k obnovení výchozího chování; tato hodnota může být **NULL**.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_terminate**|\<eh.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Rutiny zpracování výjimek](../../c-runtime-library/exception-handling-routines.md)<br/>
[Přerušení](abort.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[Ukončit](terminate-crt.md)<br/>
[Neočekávané](unexpected-crt.md)<br/>
