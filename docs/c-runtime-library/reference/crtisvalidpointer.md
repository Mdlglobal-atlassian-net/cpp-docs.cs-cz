---
title: _CrtIsValidPointer
ms.date: 11/04/2016
api_name:
- _CrtIsValidPointer
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
- CrtlsValidPointer
- _CrtIsValidPointer
helpviewer_keywords:
- CrtIsValidPointer function
- _CrtIsValidPointer function
ms.assetid: 91c35590-ea5e-450f-a15d-ad8d62ade1fa
ms.openlocfilehash: 490d2dea097935dee2cd2a003aa28e32f1ced69d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938770"
---
# <a name="_crtisvalidpointer"></a>_CrtIsValidPointer

Ověřuje, že ukazatel nemá hodnotu null. Ve verzích knihovny run-time jazyka C před Visual Studio 2010 ověřuje, zda je zadaný rozsah paměti platný pro čtení a zápis (pouze ladicí verze).

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
Odkazuje na začátek rozsahu paměti pro otestování platnosti.

*hodnota*<br/>
Velikost zadaného rozsahu paměti (v bajtech).

*access*<br/>
Dostupnost pro čtení a zápis k určení rozsahu paměti.

## <a name="return-value"></a>Návratová hodnota

**_CrtIsValidPointer** vrací hodnotu true, pokud zadaný ukazatel není null. Ve verzích knihoven CRT před Visual Studio 2010 vrátí hodnotu TRUE, pokud je rozsah paměti platný pro zadanou operaci nebo operace. V opačném případě vrátí funkce hodnotu FALSE.

## <a name="remarks"></a>Poznámky

Počínaje knihovnou CRT v aplikaci Visual Studio 2010 jsou parametry *Size* a *Access* ignorovány a **_CrtIsValidPointer** pouze ověří, zda zadaná *adresa* není null. Vzhledem k tomu, že tento test je snadné provést sami, nedoporučujeme tuto funkci používat. Ve verzích před Visual Studio 2010 funkce ověřuje, že rozsah paměti začínající na *adrese* a rozšíření pro *Velikost* bajtů je platný pro zadané operace nebo operace přístupnosti. Je-li *přístup* nastaven na hodnotu true, je rozsah paměti ověřen pro čtení i zápis. Pokud má *přístup* hodnotu false, je rozsah paměti ověřen pouze pro čtení. Když není definovaný [_DEBUG](../../c-runtime-library/debug.md) , volání **_CrtIsValidPointer** se během předběžného zpracování odeberou.

Vzhledem k tomu, že tato funkce vrací hodnotu TRUE nebo FALSE, může být předána jednomu z [_ASSERT](assert-asserte-assert-expr-macros.md) maker pro vytvoření jednoduchého mechanismu pro zpracování chyb ladění. Následující příklad způsobí selhání kontrolního výrazu, pokud rozsah paměti není platný pro operace čtení i zápisu:

```C
_ASSERTE( _CrtIsValidPointer( address, size, TRUE ) );
```

Další informace o tom, jak lze **_CrtIsValidPointer** použít s dalšími funkcemi ladění a makry, naleznete v tématu [makra pro vytváření sestav](/visualstudio/debugger/macros-for-reporting). Informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtIsValidPointer**|\<crtdbg.h>|

**_CrtIsValidPointer** je rozšíření společnosti Microsoft. Informace o kompatibilitě najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Příklad

Podívejte se na příklad tématu [_CrtIsValidHeapPointer](crtisvalidheappointer.md) .

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
