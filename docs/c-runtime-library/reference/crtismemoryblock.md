---
title: _CrtIsMemoryBlock
ms.date: 11/04/2016
apiname:
- _CrtIsMemoryBlock
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
- CrtlsMemoryBlock
- _CrtIsMemoryBlock
helpviewer_keywords:
- _CrtIsMemoryBlock function
- CrtIsMemoryBlock function
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
ms.openlocfilehash: c4a85ebeb45552c6f5355853de2a45766d6bc984
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555738"
---
# <a name="crtismemoryblock"></a>_CrtIsMemoryBlock

Ověřuje, že je blok paměti zadaná v lokální haldy a má platný ladění haldy blok typu identifikátoru (pouze ladicí verze).

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
Ukazatel na začátku bloku paměti k ověření.

*Velikost*<br/>
Velikost zadaného bloku (v bajtech).

*requestNumber*<br/>
Ukazatel na číslo přidělení bloku nebo **NULL**.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který požaduje bloku nebo **NULL**.

*Číslo řádku*<br/>
Ukazatel na číslo řádku ve zdrojovém souboru nebo **NULL**.

## <a name="return-value"></a>Návratová hodnota

**_Crtismemoryblock –** vrátí **TRUE** pokud blok zadaný paměti se nachází v rámci lokální haldy a má platný ladění haldy blok typu identifikátor; v opačném případě vrátí funkce **FALSE**.

## <a name="remarks"></a>Poznámky

**_Crtismemoryblock –** funkce ověří, že zadaná paměťová bloku se nachází v rámci lokální haldy vaší aplikace a má platný blok typu identifikátoru. Tuto funkci můžete použít také k získání číslo pořadí přidělení objektu a název a řádek číslo zdrojového souboru, kde byla původně požadována přidělení bloku paměti. Předejte jinou hodnotu než**NULL** hodnoty *requestNumber*, *filename*, nebo *linenumber* způsobí, že parametry **_ Crtismemoryblock –** můžete nastavit tyto parametry pro hodnoty v záhlaví bloku paměti ladění, pokud najde blok v lokální haldy. Když [_DEBUG](../../c-runtime-library/debug.md) není definován, jsou volání **_crtismemoryblock –** odstraněna během předběžného zpracování.

Pokud **_crtismemoryblock –** selže, vrátí **FALSE** a výstupních parametrů, které jsou inicializovány na výchozí hodnoty: *requestNumber* a **číslo řádku**  jsou nastaveny na hodnotu 0 a *filename* je nastavena na **NULL**.

Protože tato funkce vrací **TRUE** nebo **FALSE**, mohou být předány do jednoho z [_ASSERT](assert-asserte-assert-expr-macros.md) makra vytvořit jednoduchý mechanismus zpracování ladění chyb. Následující příklad způsobí selhání kontrolního výrazu, pokud zadaná adresa není umístěn v rámci lokální haldy:

```C
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,
          &filename, &linenumber ) );
```

Další informace o tom, **_crtismemoryblock –** jde použít s další funkce ladění a makra, najdete v článku [makra pro vytváření sestav](/visualstudio/debugger/macros-for-reporting). Informace o způsobu jsou bloky paměti přidělené, inicializovat a správy v ladicí verzi základní haldy viz [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtIsMemoryBlock**|\<crtdbg.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [_crtisvalidheappointer –](crtisvalidheappointer.md) tématu.

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
