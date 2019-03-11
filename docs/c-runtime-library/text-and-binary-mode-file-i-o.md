---
title: I/O soubor textového a binárního režimu
ms.date: 04/11/2018
f1_keywords:
- c.io
helpviewer_keywords:
- files [C++], open functions
- I/O [CRT], text files
- functions [CRT], file access
- binary access, binary mode file I/O
- translation, modes
- I/O [CRT], binary
- text files, I/O
- I/O [CRT], translation modes
- translation modes (file I/O)
- binary access
ms.assetid: 3196e321-8b87-4609-b302-cd6f3c516051
ms.openlocfilehash: 2c875350aedadb55d8f96fb682d6215030be2198
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738580"
---
# <a name="text-and-binary-mode-file-io"></a>I/O soubor textového a binárního režimu

Vstupně-výstupní operace můžou probíhat v jednom ze dvou režimů používaných překlad *text* nebo *binární*, v závislosti na režimu, ve kterém je soubor otevřen. Datové soubory jsou obvykle zpracovávány v textovém režimu. Pokud chcete řídit režim překladu souboru, umožňují:

- Zachovat aktuální výchozí nastavení a zadejte alternativní režimu pouze v případě otevíráte vybrané soubory.

- Použijte funkci [_set_fmode –](../c-runtime-library/reference/set-fmode.md) Chcete-li změnit výchozí režim pro nově otevřené soubory. Použití [_get_fmode –](../c-runtime-library/reference/get-fmode.md) najít aktuální výchozí režim. Počáteční výchozí nastavení je režimu textu (**_O_TEXT**).

- Změnit výchozí režim překladu přímo nastavením globální proměnné [_fmode](../c-runtime-library/fmode.md) ve svém programu. Funkce **_set_fmode –** nastaví hodnotu této proměnné, ale můžete nastavit také přímo.

Při volání funkce otevření souboru jako [_Otevřít](../c-runtime-library/reference/open-wopen.md), [fopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md), [freopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s –](../c-runtime-library/reference/freopen-s-wfreopen-s.md), [_fsopen –](../c-runtime-library/reference/fsopen-wfsopen.md) nebo [_sopen_s –](../c-runtime-library/reference/sopen-s-wsopen-s.md), přepíšete aktuální výchozí nastavení **_fmode** tak, že zadáte odpovídající argument pro funkci [_set_fmode –](../c-runtime-library/reference/set-fmode.md). **Stdin**, **stdout**, a **stderr** streamů se vždy otevře v režimu textu ve výchozím nastavení, můžete také přepsat toto výchozí nastavení při otevírání některý z těchto souborů. Použití [_setmode](../c-runtime-library/reference/setmode.md) Chcete-li změnit režim překladu po otevření souboru pomocí popisovače souboru.

## <a name="see-also"></a>Viz také:

[Vstup a výstup](../c-runtime-library/input-and-output.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
