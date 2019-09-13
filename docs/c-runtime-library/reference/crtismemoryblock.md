---
title: _CrtIsMemoryBlock
ms.date: 11/04/2016
api_name:
- _CrtIsMemoryBlock
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
- CrtlsMemoryBlock
- _CrtIsMemoryBlock
helpviewer_keywords:
- _CrtIsMemoryBlock function
- CrtIsMemoryBlock function
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
ms.openlocfilehash: f29745acd06f6f5b3fa96367444e800bdc3e8e3a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938735"
---
# <a name="_crtismemoryblock"></a>_CrtIsMemoryBlock

Ověří, zda je zadaný blok paměti v místní haldě a zda má platný identifikátor typu bloku haldy ladění (pouze ladicí verze).

## <a name="syntax"></a>Syntaxe

```C
int _CrtIsMemoryBlock(
   const void *userData,
   unsigned int size,
   long *requestNumber,
   char **filename,
   int *linenumber
);
```

### <a name="parameters"></a>Parametry

*userData*<br/>
Ukazatel na začátek bloku paměti, který chcete ověřit.

*hodnota*<br/>
Velikost zadaného bloku (v bajtech).

*requestNumber*<br/>
Ukazatel na číslo přidělení bloku nebo **hodnotu null**.

*Bitmap*<br/>
Ukazatel na název zdrojového souboru, který požadoval blok nebo **hodnotu null**.

*číslo řádku*<br/>
Ukazatel na číslo řádku ve zdrojovém souboru nebo **hodnota null**.

## <a name="return-value"></a>Návratová hodnota

**_CrtIsMemoryBlock** vrátí **hodnotu true** , pokud je zadaný blok paměti umístěný v rámci místní haldy a má platný identifikátor typu bloku haldy ladění. v opačném případě vrátí funkce **hodnotu false**.

## <a name="remarks"></a>Poznámky

Funkce **_CrtIsMemoryBlock** ověřuje, zda je zadaný blok paměti umístěn v rámci místní haldy aplikace a zda má platný identifikátor typu bloku. Pomocí této funkce lze také získat číslo pořadí přidělení objektu a název nebo číslo zdrojového souboru, kde bylo přidělení bloků paměti původně vyžádáno. Předání hodnot, které nejsou**null** pro parametry *requestNumber*, *filename*nebo *číslo řádku* způsobí, že **_CrtIsMemoryBlock** nastaví tyto parametry na hodnoty v hlavičce ladění paměťového bloku, pokud nalezne blok v lokální halda. Když není definovaný [_DEBUG](../../c-runtime-library/debug.md) , volání **_CrtIsMemoryBlock** se během předběžného zpracování odeberou.

Pokud **_CrtIsMemoryBlock** dojde k chybě, vrátí **hodnotu false** a výstupní parametry jsou inicializovány na výchozí hodnoty: *requestNumber* a **číslo řádku** jsou nastaveny na hodnotu 0 a *Parametr filename* je nastaven na **hodnotu null**.

Vzhledem k tomu, že tato funkce vrací **hodnotu true** nebo **false**, může být předána jednomu z [_ASSERT](assert-asserte-assert-expr-macros.md) maker pro vytvoření jednoduchého mechanismu pro zpracování chyb ladění. Následující příklad způsobí selhání kontrolního výrazu, pokud zadaná adresa není umístěna v místní haldě:

```C
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,
          &filename, &linenumber ) );
```

Další informace o tom, jak lze **_CrtIsMemoryBlock** použít s dalšími funkcemi ladění a makry, naleznete v tématu [makra pro vytváření sestav](/visualstudio/debugger/macros-for-reporting). Informace o způsobu přidělování, inicializace a správy paměťových bloků v ladicí verzi základní haldy najdete v [podrobnostech o haldě ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtIsMemoryBlock**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Příklad

Podívejte se na příklad tématu [_CrtIsValidHeapPointer](crtisvalidheappointer.md) .

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
