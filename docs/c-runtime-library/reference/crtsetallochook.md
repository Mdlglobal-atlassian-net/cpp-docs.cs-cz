---
title: _CrtSetAllocHook
ms.date: 11/04/2016
api_name:
- _CrtSetAllocHook
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
- _CrtSetAllocHook
- CrtSetAllocHook
helpviewer_keywords:
- _CrtSetAllocHook function
- CrtSetAllocHook function
ms.assetid: 405df37b-2fd1-42c8-83bc-90887f17f29d
ms.openlocfilehash: 303f682b54abc5e44cb7fdd4c89012dd9913288b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938487"
---
# <a name="_crtsetallochook"></a>_CrtSetAllocHook

Nainstaluje uživatelsky definovanou funkci alokace tím, že se připojí k procesu přidělování paměti ladění C za běhu (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
_CRT_ALLOC_HOOK _CrtSetAllocHook(
   _CRT_ALLOC_HOOK allocHook
);
```

### <a name="parameters"></a>Parametry

*allocHook*<br/>
Nová funkce alokace definovaná u klienta, která se připojí k procesu přidělování paměti ladění C Runtime.

## <a name="return-value"></a>Návratová hodnota

Vrátí dříve definovanou funkci přidělujícího zavěšení nebo **hodnotu null** , pokud má *allocHook* **hodnotu null**.

## <a name="remarks"></a>Poznámky

**_CrtSetAllocHook** umožňuje aplikaci zapojit svou vlastní funkci přidělení do procesu přidělování paměti knihovny ladění jazyka C. V důsledku toho každé volání funkce alokace ladění pro přidělení, opětovné přidělení nebo uvolnění bloku paměti aktivuje volání funkce zavěšení aplikace. **_CrtSetAllocHook** poskytuje aplikaci s snadnou metodou testování způsobu, jakým aplikace zpracovává nedostatečné paměťové situace, možnost kontrolovat vzory přidělení a možnost zaznamenávat informace o přidělení pro pozdější analýzu. Když není definovaný [_DEBUG](../../c-runtime-library/debug.md) , volání **_CrtSetAllocHook** se během předběžného zpracování odeberou.

Funkce **_CrtSetAllocHook** nainstaluje novou funkci přidělení definovanou pro klienta zadanou v *allocHook* a vrátí dříve definovanou funkci Hooku. Následující příklad ukazuje, jakým způsobem by měl být prototypem přiděleného zavěšení definovaného klientem:

```C
int YourAllocHook( int allocType, void *userData, size_t size,
                   int blockType, long requestNumber,
                   const unsigned char *filename, int lineNumber);
```

Argument **allocType** určuje typ operace přidělení ( **_HOOK_ALLOC**, **_HOOK_REALLOC**a **_HOOK_FREE**), která aktivovala volání funkce Hooku přidělení. Když je typ přidělení triggeru **_HOOK_FREE**, *UserData* je ukazatel na oddíl data uživatele v bloku paměti, který se chystá uvolnit. Pokud je však aktivační typ přidělení **_HOOK_ALLOC** nebo **_HOOK_REALLOC**, *UserData* má **hodnotu null** , protože blok paměti nebyl dosud přidělen.

*Velikost* určuje velikost bloku paměti v bajtech, *blockType* označuje typ bloku paměti, *requestNumber* je číslo pořadí přidělení objektu bloku paměti a, pokud je k dispozici, *filename* a **číslo řádku** zadejte název zdrojového souboru a číslo řádku, kde byla inicializována operace přidělení aktivační události.

Po dokončení zpracování funkce zavěšení musí vrátit logickou hodnotu, která oznamuje hlavnímu procesu přidělování za běhu jazyka C, jak pokračovat. Když funkce Hooku požaduje, aby hlavní proces přidělení pokračoval, jako kdyby funkce Hooku nebyla nikdy volána, měla by funkce Hooku vracet **hodnotu true**. To způsobí, že se spustí původní operace přidělení. Pomocí této implementace může funkce zavěšení shromáždit a uložit informace o přidělení pro pozdější analýzu, aniž by došlo ke konfliktu s aktuální operací přidělení nebo stavem haldy ladění.

Když funkce zavěšení chce, aby hlavní proces přidělení pokračoval, jako kdyby byla volána operace přidělení, a selhala, funkce Hooku by měla vrátit **hodnotu false**. Pomocí této implementace může funkce zavěšení simulovat velký rozsah stavů paměti a ladit stavy haldy k otestování toho, jak aplikace zpracovává jednotlivé situace.

Chcete-li vymazat funkci Hooku, předejte **hodnotu null** do **_CrtSetAllocHook**.

Další informace o tom, jak se dá **_CrtSetAllocHook** použít s dalšími funkcemi pro správu paměti nebo jak napsat vlastní funkce zavěšení definované klientem, najdete v článku [psaní funkcí vidlice ladění](/visualstudio/debugger/debug-hook-function-writing).

> [!NOTE]
> **_CrtSetAllocHook** není podporován v rámci **/clr: Pure**. Možnosti **/clr: Pure** a **/clr: Safe** jsou v aplikaci Visual Studio 2015 zastaralé a odebrané v aplikaci Visual Studio 2017.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtSetAllocHook**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Příklad

Ukázku použití **_CrtSetAllocHook**naleznete v tématu [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2).

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetAllocHook](crtgetallochook.md)<br/>
