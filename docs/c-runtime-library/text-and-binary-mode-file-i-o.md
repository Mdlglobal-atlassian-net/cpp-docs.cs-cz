---
title: I/O soubor textového a binárního režimu
ms.date: 04/11/2018
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
ms.openlocfilehash: 75d302e625747d6e02e1d904c21542530d70d02f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444624"
---
# <a name="text-and-binary-mode-file-io"></a>I/O soubor textového a binárního režimu

Vstupně-výstupní operace se soubory probíhají v jednom ze dvou režimů překladu, *textu* nebo *binárních*souborů v závislosti na režimu, ve kterém je soubor otevřený. Datové soubory jsou obvykle zpracovávány v textovém režimu. Pro řízení režimu překladu souborů může jeden:

- Ponechat aktuální výchozí nastavení a zadat alternativní režim pouze v případě, že jste otevřeli vybrané soubory.

- Použijte funkci [_set_fmode](../c-runtime-library/reference/set-fmode.md) ke změně výchozího režimu pro nově otevřené soubory. K vyhledání aktuálního výchozího režimu použijte [_get_fmode](../c-runtime-library/reference/get-fmode.md) . Počáteční výchozí nastavení je textový režim ( **_O_TEXT**).

- Výchozí režim překladu změňte přímo nastavením globální proměnné [_fmode](../c-runtime-library/fmode.md) v programu. Funkce **_set_fmode** nastaví hodnotu této proměnné, ale lze ji také nastavit přímo.

Při volání funkce otevřeného souboru, například [_open](../c-runtime-library/reference/open-wopen.md), [fopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md), [freopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md), [_fsopen](../c-runtime-library/reference/fsopen-wfsopen.md) nebo [_sopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md), můžete přepsat aktuální výchozí nastavení **_fmode** zadáním vhodného argumentu [_set_fmode](../c-runtime-library/reference/set-fmode.md)funkce. Datové proudy **stdin**, **stdout**a **stderr** se ve výchozím nastavení vždy otevírají v textovém režimu. Můžete také přepsat toto výchozí nastavení při otevírání kteréhokoli z těchto souborů. Pomocí [_setmode](../c-runtime-library/reference/setmode.md) můžete změnit režim překladu pomocí popisovače souboru po otevření souboru.

## <a name="see-also"></a>Viz také

[Vstup a výstup](../c-runtime-library/input-and-output.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
