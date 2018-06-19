---
title: _Crtisvalidpointer – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CrtIsValidPointer function
- _CrtIsValidPointer function
ms.assetid: 91c35590-ea5e-450f-a15d-ad8d62ade1fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb78f8dee494fd213df6db16e2800cb9090bdf3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397263"
---
# <a name="crtisvalidpointer"></a>_CrtIsValidPointer

Ověřuje, že ukazatel není null. Ve verzích běhové knihovny jazyka C před Visual Studio 2010 ověřuje, že zadaná paměťová rozsah je platný pro čtení a zápis (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
int _CrtIsValidPointer(
   const void *address,
   unsigned int size,
   int access
);
```

### <a name="parameters"></a>Parametry

*Adresa*<br/>
Bodů na začátek rozsahu paměti k testování platnosti.

*Velikost*<br/>
Velikost zadaná paměťová rozsahu (v bajtech).

*Přístup*<br/>
Usnadnění přístupu pro čtení a zápis k určení rozsahu paměti.

## <a name="return-value"></a>Návratová hodnota

**_Crtisvalidpointer –** vrátí hodnotu TRUE, pokud není zadaný ukazatele null. Ve verzi knihovny CRT před Visual Studio 2010 vrátí hodnotu TRUE, pokud paměti rozsah je platný pro zadanou operaci nebo operace. Funkce, jinak vrátí hodnotu FALSE.

## <a name="remarks"></a>Poznámky

Od verze knihovny CRT v sadě Visual Studio 2010 *velikost* a *přístup* parametry jsou ignorovány, a **_crtisvalidpointer –** pouze ověřuje, že zadaný *adresu* není null. Protože tento test je snadné provést sami, nedoporučujeme používat tuto funkci. Ve verzi před Visual Studio 2010, funkce ověřuje, že rozsah paměti začínající na *adresu* a rozšíření pro *velikost* bajty je platný pro zadaný usnadnění operaci nebo operace. Když *přístup* je nastavena na hodnotu TRUE, rozsah paměti ověření pro čtení i zápis. Když *přístup* hodnotu FALSE, rozsah paměti je ověřen pouze pro čtení. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání **_crtisvalidpointer –** jsou odebrány při předběžném zpracování.

Protože tato funkce vrátí hodnotu TRUE nebo FALSE, mohla být předána do jednoho z [_ASSERT](assert-asserte-assert-expr-macros.md) makra pro vytváření jednoduchých ladění chyba mechanismu pro zpracování. Následující příklad způsobí, že výraz je neplatný. Pokud oblast paměti není platná pro čtení i zápis operace:

```C
_ASSERTE( _CrtIsValidPointer( address, size, TRUE ) );
```

Další informace o tom, **_crtisvalidpointer –** lze použít s další funkce ladění a makra najdete v tématu [makra pro vytváření sestav](/visualstudio/debugger/macros-for-reporting). Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtIsValidPointer**|\<crtdbg.h>|

**_Crtisvalidpointer –** je rozšíření Microsoft. Informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="example"></a>Příklad

Podívejte se příklad [_crtisvalidheappointer –](crtisvalidheappointer.md) tématu.

## <a name="see-also"></a>Viz také

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
