---
title: Konstanty potvrzení na disku
ms.date: 11/04/2016
f1_keywords:
- vc.constants
helpviewer_keywords:
- commit-to-disk constants
ms.assetid: 0b903b23-b4fa-431e-a937-51d95f695ecf
ms.openlocfilehash: f4da66c913cd8a046257158e837e5bdb20ed71c0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581389"
---
# <a name="commit-to-disk-constants"></a>Konstanty potvrzení na disku

**Specifické pro Microsoft**

## <a name="syntax"></a>Syntaxe

```
#include <stdio.h>
```

## <a name="remarks"></a>Poznámky

Tyto konstanty specifické pro společnost Microsoft určit, zda vyrovnávací paměť přidružené k otevření souboru vyprázdní vyrovnávací paměť operačního systému nebo na disk. Režim je součástí řetězce, který specifikuje typ přístup pro čtení/zápis (**"r"**, **"w"**, **"a"**, **"r +"**, **"w +"** , **"a +"**).

Režimy potvrzení na disku jsou následující:

- **c**

   Zapíše nepsaná obsah zadané vyrovnávací paměti na disk. Tato funkce potvrzení na disku dochází jenom explicitního volání na buď [fflush –](../c-runtime-library/reference/fflush.md) nebo [_flushall –](../c-runtime-library/reference/flushall.md) funkce. Tento režim je užitečný při práci s důvěrnými osobními údaji. Například, pokud váš program se ukončí po volání `fflush` nebo `_flushall`, můžete si být jistí, že vaše data dosáhla vyrovnávací paměť operačního systému. Nicméně pokud je soubor otevřen s **c** možnost, data může nikdy být na disk operačního systému také ukončí.

- **n**

   Zapíše nepsaná obsah zadané vyrovnávací paměti do vyrovnávací paměti operačního systému. Operační systém můžete ukládat data do mezipaměti a potom určit optimální doba na zápis na disk. Mnoho podmínek toto chování je pro efektivní program chování. Nicméně pokud uchovávání dat je velmi důležité (například bankovních transakcí nebo informace lístku letecká společnost) zvažte použití **c** možnost. **n** režim je výchozí hodnota.

> [!NOTE]
> **c** a **n** možnosti, které nejsou součástí standardu ANSI `fopen`, ale jsou rozšíření společnosti Microsoft a neměl by se používat, kde je žádoucí přenositelnost ANSI.

## <a name="using-the-commit-to-disk-feature-with-existing-code"></a>Pomocí funkce potvrzení na Disk s existujícím kódem

Ve výchozím nastavení, volání [fflush –](../c-runtime-library/reference/fflush.md) nebo [_flushall –](../c-runtime-library/reference/flushall.md) funkce knihovny zapsat data do vyrovnávací paměti udržovány v operačním systému. Operačního systému určuje optimální čas, ve skutečnosti zapisovat data na disk. Funkce potvrzení na disku knihovny run-time umožňuje zajistit, že důležitá data se zapisují přímo na disk, nikoli do vyrovnávací paměti operačního systému. Tuto funkci můžete rozdat existující program bez přepsání propojením jeho objekt soubory s COMMODE.OBJ.

Výsledný spustitelný soubor volá do `fflush` zapsat obsah vyrovnávací paměti přímo na disk a volání `_flushall` zapisovat obsah všech vyrovnávací paměti na disk. Tyto dvě funkce jsou pouze ty, které jsou ovlivněny COMMODE.OBJ.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Stream vstupně-výstupních operací](../c-runtime-library/stream-i-o.md)<br/>
[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)
