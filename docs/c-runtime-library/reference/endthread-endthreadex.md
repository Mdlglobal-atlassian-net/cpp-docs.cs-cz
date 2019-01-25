---
title: _endthread, _endthreadex
ms.date: 11/04/2016
apiname:
- _endthread
- _endthreadex
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
ms.openlocfilehash: 2f54ca9c4cd5e863ca960f1d9c3634b85e7896dd
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893298"
---
# <a name="endthread-endthreadex"></a>_endthread, _endthreadex

Ukončení podprocesu. **_endthread** ukončí podproces, který je vytvořen pomocí **_beginthread** a **_endthreadex** ukončí podproces, který je vytvořen pomocí **_beginthreadex**.

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

Můžete volat **_endthread** nebo **_endthreadex** explicitně k ukončení podprocesu; nicméně **_endthread** nebo **_endthreadex** nazývá Pokud se podproces vrací z rutiny automaticky předat jako parametr **_beginthread** nebo **_beginthreadex**. Ukončení vlákna s voláním **endthread –** nebo **_endthreadex** pomáhá zajistit správné obnovení prostředků k vláknu přiděleny.

> [!NOTE]
> Pro spustitelný soubor propojeného s Libcmt.lib Nevolejte rozhraní Win32 [ExitThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-exitthread) API; to zabrání systému za běhu recyklovat přidělené prostředky. **_endthread** a **_endthreadex** uvolní prostředky přidělené vláknu a následně zavolat **ExitThread**.

**_endthread** automaticky uzavře popisovač vlákna. (Toto chování se liší od rozhraní Win32 **ExitThread** rozhraní API.) Proto při použití **_beginthread** a **_endthread**, explicitně nezavře popisovač vlákna voláním rozhraní Win32 [CloseHandle](/windows/desktop/api/handleapi/nf-handleapi-closehandle) rozhraní API.

Win32, jako jsou **ExitThread** rozhraní API, **_endthreadex** nezavře popisovač vlákna. Proto při použití **_beginthreadex** a **_endthreadex**, je nutné zavřít popisovač vlákna voláním rozhraní Win32 **CloseHandle** rozhraní API.

> [!NOTE]
> **_endthread** a **_endthreadex** způsobit, že destruktory jazyka C++ čekající ve vláknu není, která se má volat.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_endthread**|\<process.h>|
|**_endthreadex**|\<process.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Verze s více vlákny [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_beginthread](beginthread-beginthreadex.md).

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
