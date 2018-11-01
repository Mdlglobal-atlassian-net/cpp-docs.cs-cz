---
title: LINK – výstup
ms.date: 11/04/2016
f1_keywords:
- link
helpviewer_keywords:
- mapfiles [C++]
- ILK files
- output files [C++], linker
- files [C++], LINK
- .ilk files
- LINK tool [C++], output
- import libraries [C++], creating
- executable files [C++], as linker output
- mapfiles [C++], LINK output
- linker [C++], output files
- DLLs [C++], as linker output
- LINK tool [C++], mapfile
ms.assetid: a98b557c-1947-447a-be1f-616fb45a9580
ms.openlocfilehash: 819ac130d2f8ae45ff48a2f2c1941f717d5afd99
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464140"
---
# <a name="link-output"></a>LINK – výstup

Link – výstup zahrnuje soubory .exe, knihovny DLL, soubory mapování a zprávy.

##  <a name="_core_output_files"></a> Výstupní soubory

Výchozí výstupní soubor z odkazu je soubor s příponou .exe. Pokud [/dll](../../build/reference/dll-build-a-dll.md) zadána, odkazu: sestavení souboru .dll. Můžete upravit název výstupního souboru s [název výstupního souboru (/ OUT)](../../build/reference/out-output-file-name.md) možnost.

PROPOJENÍ v přírůstkovém režimu, vytvoří soubor .ilk k uložení informace o stavu pro později přírůstková sestavení programu. Podrobnosti o souborech .ilk najdete v tématu [soubory .ilk](../../build/reference/dot-ilk-files-as-linker-input.md). Další informace o přírůstkové propojování, najdete v článku [přírůstkové propojení (/ INCREMENTAL)](../../build/reference/incremental-link-incrementally.md) možnost.

Při propojení vytvoří program, který obsahuje exportuje (obvykle knihovny DLL), ale zároveň vytvoří soubor LIB, jedině v případě souboru .exp se používá v sestavení. Název souboru knihovny importu se můžete řídit [/IMPLIB](../../build/reference/implib-name-import-library.md) možnost.

Pokud [generovat soubor mapování (/ MAP)](../../build/reference/map-generate-mapfile.md) zadána, příkaz LINK vytvoří soubor mapfile.

Pokud [Generovat ladicí informace (/ DEBUG)](../../build/reference/debug-generate-debug-info.md) zadána, příkaz LINK vytvoří soubor PDB obsahovat informace o ladění programu.

##  <a name="_core_other_output"></a> Další výstup

Po zadání `link` bez jiného příkazového řádku vstupu, odkaz se zobrazí využití příkaz, který shrnuje jeho možnosti.

ODKAZ zobrazí zprávu o autorských právech a verze a vrátí soubor příkazů vstup, pokud [Potlačit úvodní nápis při spouštění (/ NOLOGO)](../../build/reference/nologo-suppress-startup-banner-linker.md) možnost se používá.

Můžete použít [tisk zpráv průběhu (/ VERBOSE)](../../build/reference/verbose-print-progress-messages.md) možnosti zobrazíte další podrobnosti o sestavení.

ODKAZ vydá chybové a výstražné zprávy ve formě LNK*nnnn*. Tato chyba předponu a rozsah čísel jsou také používány LIB, DUMPBIN a nástroje EDITBIN.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)