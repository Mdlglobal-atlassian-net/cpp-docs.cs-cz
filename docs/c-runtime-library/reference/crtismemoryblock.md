---
title: _Crtismemoryblock – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _CrtIsMemoryBlock function
- CrtIsMemoryBlock function
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 45331186cca5aab3c7971ba404d7b6da98139130
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450729"
---
# <a name="crtismemoryblock"></a>_CrtIsMemoryBlock

Ověřuje, zda blok zadaný paměti je v lokální haldy a který obsahuje identifikátor typ bloku platný ladění haldy (pouze ladicí verze).

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

*UserData*<br/>
Ukazatel na začátku bloku paměti k ověření.

*Velikost*<br/>
Velikost zadaný blok (v bajtech).

*requestNumber*<br/>
Ukazatel na číslo přidělení bloku nebo **NULL**.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který požadovaný blok nebo **NULL**.

*lineNumber*<br/>
Ukazatel na číslo řádku ve zdrojovém souboru nebo **NULL**.

## <a name="return-value"></a>Návratová hodnota

**_Crtismemoryblock –** vrátí **TRUE** Pokud bloku zadaná paměťová se nachází v rámci lokální haldy a má platný ladění haldy bloku typ identifikátor; jinak vrátí **FALSE**.

## <a name="remarks"></a>Poznámky

**_Crtismemoryblock –** funkce ověřuje, zda blok zadaná paměťová se nachází v rámci aplikace lokální haldy a že má identifikátor platný blok typem. Tato funkce slouží také k získání objektu přidělení pořadové číslo a číslo zdrojového souboru název nebo čáry kde původně požádal bloku přidělení paměti. Předávání jinou hodnotu než**NULL** hodnoty *requestNumber*, *filename*, nebo *linenumber* parametry příčiny **_ Crtismemoryblock –** pro tyto parametry nastavit na hodnoty v hlavičce ladění bloku paměti, pokud najde bloku v haldě místní. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, volání **_crtismemoryblock –** jsou odebrány při předběžném zpracování.

Pokud **_crtismemoryblock –** nezdaří, vrátí **FALSE** a výstupní parametry se inicializovat výchozí hodnoty: *requestNumber* a **lineNumber**  jsou nastavena na hodnotu 0 a *filename* je nastaven na **NULL**.

Protože funkce vrátí hodnotu **TRUE** nebo **FALSE**, mohla být předána do jednoho z [_ASSERT](assert-asserte-assert-expr-macros.md) makra pro vytváření jednoduchých ladění chyba mechanismu pro zpracování. V následujícím příkladu způsobí chybu assertion Pokud zadaná adresa není umístěn v lokální haldy:

```C
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,
          &filename, &linenumber ) );
```

Další informace o tom, **_crtismemoryblock –** lze použít s další funkce ladění a makra najdete v tématu [makra pro vytváření sestav](/visualstudio/debugger/macros-for-reporting). Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtIsMemoryBlock**|\<crtdbg.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.

## <a name="example"></a>Příklad

Podívejte se příklad [_crtisvalidheappointer –](crtisvalidheappointer.md) tématu.

## <a name="see-also"></a>Viz také

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
