---
title: "LINK – výstup | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: link
dev_langs: C++
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
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 567a87ab5cb4badd5f32423b8fb3067b21c46e9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="link-output"></a>LINK – výstup
Link – výstup zahrnuje soubory .exe, knihovny DLL, soubory mapování a zprávy.  
  
##  <a name="_core_output_files"></a>Výstupní soubory  
 Výstupní soubor výchozí odkaz je soubor s příponou .exe. Pokud [/dll](../../build/reference/dll-build-a-dll.md) je zadána možnost, odkaz sestavení souboru .dll. Můžete řídit název výstupního souboru se [názvu výstupního souboru (/ OUT)](../../build/reference/out-output-file-name.md) možnost.  
  
 ODKAZ v přírůstkové režimu, vytvoří soubor .ilk pro uložení informace o stavu pro později přírůstkové sestavení programu. Podrobnosti o soubory .ilk najdete v tématu [soubory .ilk](../../build/reference/dot-ilk-files-as-linker-input.md). Další informace o přírůstkové propojování najdete v tématu [přírůstkově odkaz (/ PŘÍRŮSTKOVÉ)](../../build/reference/incremental-link-incrementally.md) možnost.  
  
 Při propojení vytvoří program, který obsahuje exportuje (obvykle DLL), také vytvoří soubor LIB Pokud soubor .exp byl použit v buildu. Můžete řídit název souboru knihovny importu s [/IMPLIB](../../build/reference/implib-name-import-library.md) možnost.  
  
 Pokud [generovat soubor mapování (/ MAP)](../../build/reference/map-generate-mapfile.md) je zadána možnost, vytvoří odkaz soubor mapování.  
  
 Pokud [Generovat ladicí informace (/ DEBUG)](../../build/reference/debug-generate-debug-info.md) je zadána možnost, vytvoří odkaz PDB obsahovat informace o ladění programu.  
  
##  <a name="_core_other_output"></a>Další výstup  
 Pokud zadáte `link` bez jiného příkazového řádku vstupu, odkaz zobrazí využití příkaz, který shrnuje jeho možnosti.  
  
 ODKAZ zobrazí zprávu o autorských právech a verze a vrátí soubor příkazů vstup, pokud [Potlačit úvodní nápis při spouštění (/ NOLOGO)](../../build/reference/nologo-suppress-startup-banner-linker.md) možnost se používá.  
  
 Můžete použít [tisk zpráv průběhu (/ VERBOSE)](../../build/reference/verbose-print-progress-messages.md) možnosti zobrazíte další podrobnosti o sestavení.  
  
 Chybové a výstražné zprávy ve formě LNK problémy odkaz*nnnn*. Tato chyba předponu a rozsah čísel jsou také používány LIB DUMPBIN a nástroje EDITBIN.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)