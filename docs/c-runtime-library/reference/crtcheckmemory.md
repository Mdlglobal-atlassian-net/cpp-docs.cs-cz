---
title: _CrtCheckMemory
ms.date: 11/04/2016
apiname:
- _CrtCheckMemory
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
- CrtCheckMemory
- _CrtCheckMemory
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
ms.openlocfilehash: cb39a76c140934dabdd1269c02aba6018691f917
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537147"
---
# <a name="crtcheckmemory"></a>_CrtCheckMemory

Potvrdí její integritu bloky paměti přidělené v haldě ladění (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C

int _CrtCheckMemory( void );
```

## <a name="return-value"></a>Návratová hodnota

V případě úspěšného ověření **_CrtCheckMemory** vrátí hodnotu TRUE; v opačném případě vrátí hodnotu FALSE.

## <a name="remarks"></a>Poznámky

**_CrtCheckMemory** funkce ověřuje paměti přidělí správce hald ladění ověřování základní základní haldy a kontrola každý blok paměti. Pokud je v podkladové základní haldy, informace hlavičky ladění nebo přepsat vyrovnávací paměti, chyby nebo paměti nekonzistence **_CrtCheckMemory** generuje sestavu ladění s informace, které popisují chybového stavu. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, jsou volání **_CrtCheckMemory** odstraněna během předběžného zpracování.

Chování **_CrtCheckMemory** můžete řídit pomocí nastavení bitové pole [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) příznak pomocí [_CrtSetDbgFlag](crtsetdbgflag.md) funkce. Zapíná **_CRTDBG_CHECK_ALWAYS_DF** bit ON výsledky v poli **_CrtCheckMemory** volána pokaždé, když se požadovaná operace přidělení paměti. I když tato metoda se zpomalí provádění, je užitečné pro rychlé zachycení chyb. Zapíná **_CRTDBG_ALLOC_MEM_DF** bitová pole OFF způsobí, že **_CrtCheckMemory** se ověřit haldy a ihned vrátit **TRUE**.

Protože tato funkce vrací **TRUE** nebo **FALSE**, mohou být předány do jednoho z [_ASSERT](assert-asserte-assert-expr-macros.md) makra vytvořit jednoduchý mechanismus zpracování ladění chyb. Následující příklad způsobí selhání kontrolního výrazu, pokud bylo zjištěno poškození haldy:

```C
_ASSERTE( _CrtCheckMemory( ) );
```

Další informace o tom, **_CrtCheckMemory** lze použít s jinými funkcemi ladění, naleznete v tématu [funkce vykazování stavu haldy](/visualstudio/debugger/crt-debug-heap-details). Přehled správy paměti a halda ladění, naleznete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtCheckMemory**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="example"></a>Příklad

Pro ukázku toho, jak používat **_CrtCheckMemory**, naleznete v tématu [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1).

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
