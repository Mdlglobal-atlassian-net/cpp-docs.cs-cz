---
title: _CrtIsValidPointer
ms.date: 11/04/2016
apiname:
- _CrtIsValidPointer
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
apitype: DLLExport
f1_keywords:
- CrtlsValidPointer
- _CrtIsValidPointer
helpviewer_keywords:
- CrtIsValidPointer function
- _CrtIsValidPointer function
ms.assetid: 91c35590-ea5e-450f-a15d-ad8d62ade1fa
ms.openlocfilehash: 64197d460cdb7dd26d22196c08151be09df48573
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339322"
---
# <a name="crtisvalidpointer"></a>_CrtIsValidPointer

Ověřuje, že ukazatel není null. Ve verzích běhové knihovny jazyka C před Visual Studio 2010 ověří, zda je zadaná paměťová rozsahu platný pro čtení a zápis (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
int _CrtIsValidPointer(
   const void *address,
   unsigned int size,
   int access
);
```

### <a name="parameters"></a>Parametry

*address*<br/>
Odkazuje na začátku rozsahu paměti pro testování platnosti.

*Velikost*<br/>
Velikost zadaná paměťová rozsahu (v bajtech).

*access*<br/>
Usnadnění přístupu pro čtení a zápis k určení rozsahu paměti.

## <a name="return-value"></a>Návratová hodnota

**_Crtisvalidpointer –** vrátí TRUE, pokud není zadaný ukazatel null. Ve verzi knihovny CRT před Visual Studio 2010 vrátí hodnotu TRUE, pokud je platný pro zadanou operaci nebo operace oblasti paměti. V opačném případě vrátí funkce hodnotu FALSE.

## <a name="remarks"></a>Poznámky

Spouští se pomocí knihovny CRT v sadě Visual Studio 2010 *velikost* a *přístup* parametry budou ignorovány, a **_crtisvalidpointer –** pouze ověří, zda zadaný *adresu* nemá hodnotu null. Protože tento test je snadné provést sami, nedoporučujeme používat tuto funkci. Ve verzích před Visual Studio 2010, funkce ověří, zda rozsah paměti začínající na *adresu* a rozšíření pro *velikost* bajtů je platný pro zadaný usnadnění operaci nebo operace. Když *přístup* je nastavena na hodnotu TRUE, rozsahu paměti je ověřený pro čtení i zápis. Když *přístup* má hodnotu FALSE, rozsahu paměti proběhne pouze pro čtení. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, jsou volání **_crtisvalidpointer –** odstraněna během předběžného zpracování.

Protože tato funkce vrací hodnotu TRUE nebo FALSE, může být předán do jednoho z [_ASSERT](assert-asserte-assert-expr-macros.md) makra vytvořit jednoduchý mechanismus zpracování ladění chyb. Následující příklad způsobí selhání kontrolního výrazu, je-li paměť rozsah není platný pro čtení i zápis operace:

```C
_ASSERTE( _CrtIsValidPointer( address, size, TRUE ) );
```

Další informace o tom, **_crtisvalidpointer –** jde použít s další funkce ladění a makra, najdete v článku [makra pro vytváření sestav](/visualstudio/debugger/macros-for-reporting). Informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtIsValidPointer**|\<crtdbg.h>|

**_Crtisvalidpointer –** je rozšířením společnosti Microsoft. Informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_crtisvalidheappointer –](crtisvalidheappointer.md) tématu.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
