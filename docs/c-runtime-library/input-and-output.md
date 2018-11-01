---
title: Vstup a výstup
ms.date: 11/04/2016
f1_keywords:
- c.io
helpviewer_keywords:
- input routines
- I/O [CRT]
- I/O routines
- I/O [CRT], routines
- output routines
ms.assetid: 1c177301-e341-4ca0-aedc-0a87fe1c75ae
ms.openlocfilehash: 26d527f7afad544b051a2ad765af09c430782083
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590382"
---
# <a name="input-and-output"></a>Vstup a výstup

Funkce vstupně-výstupních operací čtení a zápis dat do a ze souborů a zařízení. Soubor vstupně-výstupní operace můžou probíhat v textovém nebo binárním režimu. Běhové knihovny Microsoft má tři typy vstupních/výstupních funkcí:

- [Stream vstupně-výstupních operací](../c-runtime-library/stream-i-o.md) funkce zacházet s daty jako datový proud jednotlivých znaků.

- [I/O nízké úrovně](../c-runtime-library/low-level-i-o.md) funkce vyvolání operačního systému přímo pro operaci nižší úrovně, než poskytuje datový proud vstupně-výstupních operací.

- [Konzoly a portu vstupně-výstupních operací](../c-runtime-library/console-and-port-i-o.md) funkce číst nebo zapisovat přímo do konzoly (klávesnice a obrazovky) nebo port vstupně-výstupních operací (například port tiskárny).

   > [!NOTE]
   > Protože jsou tyto funkce datového proudu do vyrovnávací paměti a nejsou funkce nízké úrovně, tyto dva typy funkcí jsou obecně kompatibilní. Pro zpracováním určitého souboru, použijte výhradně datového proudu nebo funkce nízké úrovně.

## <a name="see-also"></a>Viz také

[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
