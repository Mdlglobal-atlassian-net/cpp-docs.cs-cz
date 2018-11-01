---
title: _CrtSetAllocHook
ms.date: 11/04/2016
apiname:
- _CrtSetAllocHook
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
- _CrtSetAllocHook
- CrtSetAllocHook
helpviewer_keywords:
- _CrtSetAllocHook function
- CrtSetAllocHook function
ms.assetid: 405df37b-2fd1-42c8-83bc-90887f17f29d
ms.openlocfilehash: cfa466ec4bce6034c15a627ccab4ee4bb0ef8f5b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533676"
---
# <a name="crtsetallochook"></a>_CrtSetAllocHook

Nainstaluje funkce klienta definované přidělení zapojení do proces přidělení paměti ladění za běhu jazyka C (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
_CRT_ALLOC_HOOK _CrtSetAllocHook(
   _CRT_ALLOC_HOOK allocHook
);
```

### <a name="parameters"></a>Parametry

*allocHook*<br/>
Nové funkce klienta definované přidělení k připojení do procesu přidělení paměti ladění za běhu C.

## <a name="return-value"></a>Návratová hodnota

Vrátí funkce háku předem definované přidělení, nebo **NULL** Pokud *allocHook* je **NULL**.

## <a name="remarks"></a>Poznámky

**_CrtSetAllocHook** umožňuje aplikaci připojit svou vlastní funkci rozdělení do procesu přidělení paměti knihovny C ladění za běhu. Díky tomu všechna volání funkce přidělení ladění přidělit, přidělit jinému uživateli nebo bez triggerů bloku paměti během volání funkce háku vaší aplikace. **_CrtSetAllocHook** umožní snadno pro metodu testování, způsob, jakým aplikace zpracovává situace nedostatku paměti, schopnost zkoumat vzory přidělování a možnost později protokolovat informace o přidělení paměti pro aplikaci analýzy. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, jsou volání **_CrtSetAllocHook** odstraněna během předběžného zpracování.

**_CrtSetAllocHook** funkce nainstaluje novou funkci klienta definované přidělení podle *allocHook* a vrací funkci dříve definované připojení. Následující příklad ukazuje, jak by měla být prototypem háku přidělení definované klienta:

```C
int YourAllocHook( int allocType, void *userData, size_t size,
                   int blockType, long requestNumber,
                   const unsigned char *filename, int lineNumber);
```

**AllocType** argument určuje typ operace přidělení (**_HOOK_ALLOC**, **_HOOK_REALLOC**, a **_HOOK_FREE**), který volání funkce háku přidělení pro aktivaci. Pokud je spouštěcí typ přidělení **_HOOK_FREE**, *userData* je ukazatel na část dat uživatele bloku paměti se být uvolněna. Nicméně, pokud je spouštěcí typ přidělení **_HOOK_ALLOC** nebo **_HOOK_REALLOC**, *userData* je **NULL** protože bloku paměti nebyl dosud přidělen.

*velikost* určuje blokovat velikost paměti v bajtech, *blockType* označuje typ bloku paměti *requestNumber* je číslo pořadí přidělení objektu bloku paměti a v případě k dispozici, *filename* a **lineNumber** zadat zdrojového souboru název a číslo řádku kde spouštěcí přidělení operace se iniciovala.

Po dokončení zpracování funkce háku musí vrátit logickou hodnotu, která informuje proces hlavní přidělování za běhu C, jak chcete pokračovat. Když chce, aby funkce háku přidělení hlavní postup pokračovat, protože pokud kdyby funkce háku nikdy volána, pak by měl vrátit funkce háku **TRUE**. To způsobí, že původní operace spouštěcí přidělení má být proveden. Pomocí této implementaci funkce háku shromáždit a uložit informace o přidělení paměti pro pozdější analýzu, aniž by zasahovala do aktuální operaci správy přidělení nebo stavu haldy ladění.

Pokud funkce háku požaduje hlavní přidělení procesu pokračovat jako spouštěcí přidělení operace byla volána a se nezdařilo, pak by měl vrátit funkce háku **FALSE**. Pomocí této implementaci funkce háku simulace širokou škálu paměti a ladění haldy stavy k otestování způsob, jakým aplikace zpracovává každé situaci.

Chcete-li zaškrtnutí háku funkce, předejte **NULL** k **_CrtSetAllocHook**.

Další informace o tom, **_CrtSetAllocHook** jde použít s dalšími funkcemi správy paměti nebo o zápis funkce háku definované klienta najdete v tématu [zápis funkce háku ladění](/visualstudio/debugger/debug-hook-function-writing).

> [!NOTE]
> **_CrtSetAllocHook** není podporován v rámci **/CLR: pure**. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a odebrat v sadě Visual Studio 2017.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtSetAllocHook**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="example"></a>Příklad

Pro ukázku toho, jak používat **_CrtSetAllocHook**, naleznete v tématu [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetAllocHook](crtgetallochook.md)<br/>
