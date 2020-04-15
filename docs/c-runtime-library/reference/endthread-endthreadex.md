---
title: _endthread, _endthreadex
ms.date: 4/2/2020
api_name:
- _endthread
- _endthreadex
- _o__endthread
- _o__endthreadex
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
- _endthread
- endthreadex
- _endthreadex
- endthread
helpviewer_keywords:
- _endthread function
- endthread function
- terminating threads
- endthreadex function
- _endthreadex function
- threading [C++], terminating threads
ms.assetid: 18a91f2f-659e-40b4-b266-ec12dcf2abf5
ms.openlocfilehash: c76f479255080400e07678ef5dbde572b7a9dffc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348039"
---
# <a name="_endthread-_endthreadex"></a>_endthread, _endthreadex

Ukončí vlákno; **_endthread** ukončí vlákno, které je vytvořeno **_beginthread** a **_endthreadex** ukončí vlákno, které je vytvořeno **_beginthreadex**.

## <a name="syntax"></a>Syntaxe

```C
void _endthread( void );
void _endthreadex(
   unsigned retval
);
```

### <a name="parameters"></a>Parametry

*retval*<br/>
Ukončovací kód vlákna.

## <a name="remarks"></a>Poznámky

Můžete volat **_endthread** nebo **_endthreadex** explicitně ukončit vlákno; **_endthread** nebo **_endthreadex** je však volána automaticky, když se vlákno vrátí z rutiny předané jako parametr **_beginthread** nebo **_beginthreadex**. Ukončení podprocesu s voláním **endthread** nebo **_endthreadex** pomáhá zajistit správné obnovení prostředků přidělených pro vlákno.

> [!NOTE]
> U spustitelného souboru propojeného s libcmt.lib nevolejte rozhraní WIN32 [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) API; To zabrání systému run-time v rekultivaci přidělených prostředků. **_endthread** a **_endthreadex** znovu získat přidělené prostředky vlákna a potom volat **ExitThread**.

**_endthread** automaticky zavře úchyt závitu. (Toto chování se liší od rozhraní API **win32 exitthread.)** Proto při použití **_beginthread** a **_endthread**, není explicitně zavřete popisovač vlákna voláním rozhraní API [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) Win32.

Stejně jako rozhraní API **win32 exitthread** **_endthreadex** nezavře popisovač vlákna. Proto při použití **_beginthreadex** a **_endthreadex**, je nutné zavřít popisovač vlákna voláním rozhraní API **CloseHandle** Win32.

> [!NOTE]
> **_endthread** a **_endthreadex** způsobit, že destruktory Jazyka C++ čekající na vyřízení ve vlákně nebudou volány.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_endthread**|\<process.h>|
|**_endthreadex**|\<process.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Verze s více vlákny pouze [knihoven c run-time.](../../c-runtime-library/crt-library-features.md)

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_beginthread](beginthread-beginthreadex.md).

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
