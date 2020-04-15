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
ms.openlocfilehash: 253f88ed50b9f064edf976277a4618e4f101ec7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331794"
---
# <a name="link-output"></a>LINK – výstup

Výstup odkazu obsahuje soubory EXE, knihovny DLL, mapové soubory a zprávy.

## <a name="output-files"></a><a name="_core_output_files"></a>Výstupní soubory

Výchozí výstupní soubor z link je soubor EXE. Pokud je zadána možnost [/DLL,](dll-build-a-dll.md) link vytvoří soubor DLL. Název výstupního souboru můžete ovládat pomocí volby [Output File Name (/OUT).](out-output-file-name.md)

V přírůstkovém režimu link vytvoří soubor ILK pro uložení informací o stavu pro pozdější přírůstková sestavení programu. Podrobnosti o souborech Ilk naleznete v tématu [.ilk Files](dot-ilk-files-as-linker-input.md). Další informace o přírůstkovém propojení naleznete v tématu [Možnost Postupně (/PŘÍRŮSTKOVÉ) propojení.](incremental-link-incrementally.md)

Když link vytvoří program, který obsahuje exporty (obvykle DLL), vytvoří také soubor LIB, pokud nebyl v sestavení použit soubor EXP. Název souboru importu knihovny můžete řídit pomocí možnosti [/IMPLIB.](implib-name-import-library.md)

Pokud je zadána možnost [Generovat mapový soubor (/MAP),](map-generate-mapfile.md) LINK vytvoří soubor mapy.

Pokud je zadána možnost [Generovat informace o ladění (/DEBUG),](debug-generate-debug-info.md) link vytvoří PDB obsahující informace o ladění pro program.

## <a name="other-output"></a><a name="_core_other_output"></a>Jiný výstup

Při psaní `link` bez jiného vstupu příkazového řádku link zobrazí příkaz usage, který shrnuje jeho možnosti.

LINK zobrazí zprávu o autorských právech a verzi a ozve vstup příkazového souboru, pokud není použita možnost [Potlačit spouštěcí banner (/NOLOGO).](nologo-suppress-startup-banner-linker.md)

Můžete použít [možnost Průběhu tisku zprávy (/VERBOSE)](verbose-print-progress-messages.md) zobrazit další podrobnosti o sestavení.

LINK vydává chybové a varovné zprávy ve formuláři LNK*nnnn*. Tato předpona chyby a rozsah čísel jsou také používány LIB, DUMPBIN a EDITBIN.

## <a name="see-also"></a>Viz také

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti propojovacího zařízení MSVC](linker-options.md)
