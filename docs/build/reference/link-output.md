---
title: LINK – výstup
ms.date: 11/04/2016
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
ms.openlocfilehash: 8323723f2049d3db469e874c91b99f4cfb561c72
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439324"
---
# <a name="link-output"></a>LINK – výstup

Výstup odkazu zahrnuje soubory. exe, knihovny DLL, soubory mapování a zprávy.

##  <a name="_core_output_files"></a>Výstupní soubory

Výchozí výstupní soubor z odkazu je soubor. exe. Pokud je zadána možnost [/DLL](dll-build-a-dll.md) , vytvoří odkaz sestavení souboru. dll. Můžete ovládat název výstupního souboru pomocí možnosti [název výstupního souboru (/out)](out-output-file-name.md) .

V přírůstkovém režimu vytvoří odkaz soubor. ilk, který bude obsahovat informace o stavu pro pozdější přírůstkové sestavení tohoto programu. Podrobnosti o souborech. ilk naleznete v [souboru. ilk](dot-ilk-files-as-linker-input.md). Další informace o přírůstkovém propojování naleznete v možnosti [odkaz přírůstkově (/INCREMENTAL)](incremental-link-incrementally.md) .

Když propojení vytvoří program, který obsahuje export (obvykle knihovna DLL), vytvoří také soubor. lib, pokud se v sestavení nepoužil soubor. exp. Název souboru knihovny pro import můžete řídit pomocí možnosti [/IMPLIB](implib-name-import-library.md) .

Pokud je zadána možnost [Generate souboru mapování (/map)](map-generate-mapfile.md) , vytvoří odkaz vytvořit souboru mapování.

Pokud je zadána možnost [vygenerovat informace o ladění (/debug)](debug-generate-debug-info.md) , vytvoří odkaz na soubor PDB, který obsahuje ladicí informace pro program.

##  <a name="_core_other_output"></a>Další výstup

Když zadáte `link` bez dalšího vstupu příkazového řádku, odkaz zobrazí příkaz použití, který shrnuje své možnosti.

ODKAZ zobrazí zprávu o autorských právech a verzích a vrátí vstup do příkazového souboru, pokud se nepoužije možnost [Potlačit úvodní nápis (/nologo)](nologo-suppress-startup-banner-linker.md) .

Pomocí možnosti zprávy o [průběhu tisku (/verbose)](verbose-print-progress-messages.md) můžete zobrazit další podrobnosti o sestavení.

Propojí chybu a varovné zprávy ve formuláři LNK*nnnn*. Tato chybová předpona a rozsah čísel jsou také používány LIB, DUMPBIN a nástroje Editbin.

## <a name="see-also"></a>Viz také

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
