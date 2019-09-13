---
title: _CrtCheckMemory
ms.date: 11/04/2016
api_name:
- _CrtCheckMemory
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CrtCheckMemory
- _CrtCheckMemory
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
ms.openlocfilehash: 7e458825a81b7032310458ccda52d9299e126a35
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938864"
---
# <a name="_crtcheckmemory"></a>_CrtCheckMemory

Potvrdí integritu paměťových bloků přidělených v haldě ladění (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C

int _CrtCheckMemory( void );
```

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí **_CrtCheckMemory** hodnotu true; v opačném případě vrátí funkce hodnotu FALSE.

## <a name="remarks"></a>Poznámky

Funkce **_CrtCheckMemory** ověřuje paměť přidělenou správcem haldy ladění tím, že ověřuje základní základní haldu a kontroluje všechny bloky paměti. Pokud dojde k chybě nebo nekonzistenci paměti v základní haldě, vygeneruje informace v hlavičce ladění nebo vyrovnávací paměti přepsání, **_CrtCheckMemory** sestavu s informacemi popisujícími chybový stav. Když není definovaný [_DEBUG](../../c-runtime-library/debug.md) , volání **_CrtCheckMemory** se během předběžného zpracování odeberou.

Chování **_CrtCheckMemory** lze ovládat nastavením bitových polí příznaku [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) pomocí funkce [_CrtSetDbgFlag](crtsetdbgflag.md) . Přepnutí **_CRTDBG_CHECK_ALWAYS_DF** bitového pole na výsledky v **_CrtCheckMemory** se volá pokaždé, když se požaduje operace přidělení paměti. I když tato metoda zpomaluje spouštění, je užitečná pro rychlé zachycení chyb. Zapnutí **_CRTDBG_ALLOC_MEM_DF** bitového pole způsobí, že **_CrtCheckMemory** neověří haldu a okamžitě vrátí **hodnotu true**.

Vzhledem k tomu, že tato funkce vrací **hodnotu true** nebo **false**, může být předána jednomu z [_ASSERT](assert-asserte-assert-expr-macros.md) maker pro vytvoření jednoduchého mechanismu pro zpracování chyb ladění. Následující příklad způsobí selhání kontrolního výrazu, pokud je zjištěno poškození haldy:

```C
_ASSERTE( _CrtCheckMemory( ) );
```

Další informace o tom, jak lze **_CrtCheckMemory** použít s jinými funkcemi ladění, naleznete v tématu [funkce vytváření sestav o stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Přehled správy paměti a haldy ladění najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtCheckMemory**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Příklad

Ukázku použití **_CrtCheckMemory**naleznete v tématu [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
