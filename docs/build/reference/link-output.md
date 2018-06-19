---
title: LINK – výstup | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- link
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae68de707ece35825a32a404ce14032d4bbd3141
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376725"
---
# <a name="link-output"></a>LINK – výstup
Link – výstup zahrnuje soubory .exe, knihovny DLL, soubory mapování a zprávy.  
  
##  <a name="_core_output_files"></a> Výstupní soubory  
 Výstupní soubor výchozí odkaz je soubor s příponou .exe. Pokud [/dll](../../build/reference/dll-build-a-dll.md) je zadána možnost, odkaz sestavení souboru .dll. Můžete řídit název výstupního souboru se [názvu výstupního souboru (/ OUT)](../../build/reference/out-output-file-name.md) možnost.  
  
 ODKAZ v přírůstkové režimu, vytvoří soubor .ilk pro uložení informace o stavu pro později přírůstkové sestavení programu. Podrobnosti o soubory .ilk najdete v tématu [soubory .ilk](../../build/reference/dot-ilk-files-as-linker-input.md). Další informace o přírůstkové propojování najdete v tématu [přírůstkově odkaz (/ PŘÍRŮSTKOVÉ)](../../build/reference/incremental-link-incrementally.md) možnost.  
  
 Při propojení vytvoří program, který obsahuje exportuje (obvykle DLL), také vytvoří soubor LIB Pokud soubor .exp byl použit v buildu. Můžete řídit název souboru knihovny importu s [/IMPLIB](../../build/reference/implib-name-import-library.md) možnost.  
  
 Pokud [generovat soubor mapování (/ MAP)](../../build/reference/map-generate-mapfile.md) je zadána možnost, vytvoří odkaz soubor mapování.  
  
 Pokud [Generovat ladicí informace (/ DEBUG)](../../build/reference/debug-generate-debug-info.md) je zadána možnost, vytvoří odkaz PDB obsahovat informace o ladění programu.  
  
##  <a name="_core_other_output"></a> Další výstup  
 Pokud zadáte `link` bez jiného příkazového řádku vstupu, odkaz zobrazí využití příkaz, který shrnuje jeho možnosti.  
  
 ODKAZ zobrazí zprávu o autorských právech a verze a vrátí soubor příkazů vstup, pokud [Potlačit úvodní nápis při spouštění (/ NOLOGO)](../../build/reference/nologo-suppress-startup-banner-linker.md) možnost se používá.  
  
 Můžete použít [tisk zpráv průběhu (/ VERBOSE)](../../build/reference/verbose-print-progress-messages.md) možnosti zobrazíte další podrobnosti o sestavení.  
  
 Chybové a výstražné zprávy ve formě LNK problémy odkaz*nnnn*. Tato chyba předponu a rozsah čísel jsou také používány LIB DUMPBIN a nástroje EDITBIN.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)