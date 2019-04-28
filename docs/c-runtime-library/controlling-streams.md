---
title: Řídicí proudy
ms.date: 11/04/2016
f1_keywords:
- Controlling Streams
helpviewer_keywords:
- streams, controlling
- controlling streams
- streams
ms.assetid: 267e9013-9afc-45f6-91e3-ca093230d9d9
ms.openlocfilehash: 85c7e1b22519287fbd03d89487d6639f197a8b63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344627"
---
# <a name="controlling-streams"></a>Řídicí proudy

[fopen –](../c-runtime-library/reference/fopen-wfopen.md) vrátí adresu objektu typu `FILE`. Použijte tuto adresu, jako `stream` argument pro několik funkcí knihovna můžete provádět různé operace na otevřený soubor. Pro datový proud bajtů, všechny vstupní probíhá jakoby každý znak je pro čtení voláním [fgetc –](../c-runtime-library/reference/fgetc-fgetwc.md), a všechny výstupní probíhá jakoby každý znak je vytvořená systémem volání [fputc](../c-runtime-library/reference/fputc-fputwc.md). Pro celou datový proud, všechny vstupní probíhá jakoby každý znak je pro čtení voláním [fgetwc –](../c-runtime-library/reference/fgetc-fgetwc.md), a všechny výstupní probíhá jakoby každý znak je vytvořená systémem volání [fputwc –](../c-runtime-library/reference/fputc-fputwc.md).

Soubor můžete zavřít voláním [fclose –](../c-runtime-library/reference/fclose-fcloseall.md), po jejímž uplynutí adresu `FILE` objekt je neplatný.

A `FILE` ukládá stav datového proudu, včetně:

- Indikátor chyby nastavit nenulové funkci, která se zaznamená čtení nebo zápisu došlo k chybě.

- Ve funkci, která narazí na konec souboru při čtení nastavení nenulovou indikátor konce souboru.

- Indikátor pozice v souboru Určuje další bajt v datovém proudu pro čtení nebo zápis, pokud ho může podporovat požadavky na umístění.

- A [Streamovat stav](../c-runtime-library/stream-states.md) Určuje, zda datový proud bude přijímat operací čtení a/nebo zápisy a určuje, zda je datový proud odvázat, orientovaný bajtů, nebo celý orientovaný.

- Stav převodu zapamatuje si, že stav kteréhokoli částečně týkajícím se této nebo vygenerovat zobecněn vícebajtového znaku, stejně jako jakýkoli stav shift pro pořadí bajtů v souboru).

- Vyrovnávací paměť souboru Určuje adresu a velikost pole objektu, který funkce knihovny můžete použít ke zlepšení výkonu pro čtení a operace zápisu do datového proudu.

Neměňte libovolná hodnota uložená v `FILE` objektu nebo ve vyrovnávací paměti souboru, který zadáte pro použití s tímto objektem. Nelze zkopírovat `FILE` objektu a přenositelnosti použijte adresu kopii jako `stream` argument pro funkci knihovny.

## <a name="see-also"></a>Viz také:

[Soubory a proudy](../c-runtime-library/files-and-streams.md)
