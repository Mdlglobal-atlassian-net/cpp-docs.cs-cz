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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: a3889adcc90bd62e766102b72aae68577915e55b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915074"
---
# <a name="_endthread-_endthreadex"></a>_endthread, _endthreadex

Ukončí vlákno. **_endthread** ukončí vlákno, které je vytvořeno pomocí **_beginthread** a **_endthreadex** ukončí vlákno, které je vytvořeno **_beginthreadex**.

## <a name="syntax"></a>Syntaxe

```C
void _endthread( void );
void _endthreadex(
   unsigned retval
);
```

### <a name="parameters"></a>Parametry

*retval*<br/>
Ukončovací kód vlákna

## <a name="remarks"></a>Poznámky

Můžete volat **_endthread** nebo **_endthreadex** explicitně pro ukončení vlákna; **_endthread** nebo **_endthreadex** se však zavolá automaticky, když se vlákno vrátí z rutiny předané jako parametr do **_beginthread** nebo **_beginthreadex**. Ukončení vlákna s voláním **endthread** nebo **_endthreadex** pomáhá zajistit správné obnovení prostředků přidělených pro vlákno.

> [!NOTE]
> Pro spustitelný soubor propojený s Libcmt. lib Nevolejte rozhraní Win32 [ExitThread –](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) API; Tím se zabrání tomu, aby systém za běhu znovu vydělil přidělené prostředky. **_endthread** a **_endthreadex** uvolní prostředky přiděleného vlákna a potom zavolá **ExitThread –**.

**_endthread** automaticky uzavře popisovač vlákna. (Toto chování se liší od rozhraní Win32 **ExitThread –** API.) Proto při použití **_beginthread** a **_endthread**neuzavřete popisovač vlákna explicitně voláním rozhraní Win32 [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) API.

Podobně jako rozhraní Win32 **ExitThread –** API, **_endthreadex** nezavřou popisovač vlákna. Proto pokud používáte **_beginthreadex** a **_endthreadex**, je nutné ukončit popisovač vlákna voláním rozhraní Win32 API pro **CloseHandle** .

> [!NOTE]
> **_endthread** a **_endthreadex** způsobí, že destruktory C++ čekají ve vlákně, které nechcete volat.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_endthread**|\<Process. h>|
|**_endthreadex**|\<Process. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Pouze vícevláknové verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Příklad

Podívejte se na příklad [_beginthread](beginthread-beginthreadex.md).

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
