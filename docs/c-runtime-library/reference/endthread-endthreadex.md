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
ms.openlocfilehash: 5afbc907356d4c5b14b749de5de0c8d36280891e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499965"
---
# <a name="_endthread-_endthreadex"></a>_endthread, _endthreadex

Ukončí vlákno. **_endthread** ukončí vlákno vytvořené pomocí **_beginthread** a **_endthreadex** ukončí vlákno vytvořené pomocí **_beginthreadex**.

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

Můžete volat **_endthread** nebo **_endthreadex** explicitně pro ukončení vlákna; **_endthread** nebo **_endthreadex** se ale zavolá automaticky, když se vlákno vrátí z rutiny předané jako parametr do **_beginthread** nebo **_beginthreadex**. Ukončení vlákna s voláním **endthread** nebo **_endthreadex** pomáhá zajistit správné obnovení prostředků přidělených pro vlákno.

> [!NOTE]
> Pro spustitelný soubor propojený s Libcmt. lib Nevolejte rozhraní Win32 [ExitThread –](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) API; Tím se zabrání tomu, aby systém za běhu znovu vydělil přidělené prostředky. **_endthread** a **_endthreadex** uvolní prostředky přiděleného vlákna a pak zavolají **ExitThread –** .

**_endthread** automaticky zavře popisovač vlákna. (Toto chování se liší od rozhraní Win32 **ExitThread –** API.) Proto při použití **_beginthread** a **_endthread**explicitně uzavřete popisovač vlákna voláním rozhraní Win32 [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) API.

Podobně jako rozhraní Win32 **ExitThread –** API **_endthreadex** neuzavře popisovač vlákna. Proto při použití **_beginthreadex** a **_endthreadex**je nutné ukončit popisovač vlákna voláním rozhraní Win32 API pro **CloseHandle** .

> [!NOTE]
> **_endthread** a **_endthreadex** způsobí C++ , že destruktory čekají ve vlákně, které nechcete volat.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_endthread**|\<Process. h >|
|**_endthreadex**|\<Process. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Pouze vícevláknové verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_beginthread](beginthread-beginthreadex.md).

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
