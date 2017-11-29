---
title: "Textového a binárního režimu soubor I-O | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.io
dev_langs: C++
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
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0bd2eb90ad8498daa318ffecacd7b32f3f3d3eca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="text-and-binary-mode-file-io"></a>I/O soubor textového a binárního režimu
Soubor vstupně-výstupních operací provést v jednom ze dvou překlad režimy, textu nebo binárních, v závislosti na režimu, ve kterém je otevřen soubor. Datové soubory jsou obvykle zpracovávány v textovém režimu. Pokud chcete řídit režim překladu souboru, umožňují:  
  
-   Zachovat aktuální výchozí nastavení a zadejte alternativní režimu pouze v případě, že otevřete vybrané soubory.  
  
-   Pomocí funkce [_set_fmode –](../c-runtime-library/reference/set-fmode.md) Chcete-li změnit výchozí režim pro nově otevřené soubory. Použití [_get_fmode –](../c-runtime-library/reference/get-fmode.md) najít aktuální výchozí režim. Počáteční výchozím nastavením je režim textové (`_O_TEXT`).  
  
-   Změnit režim překladu výchozí přímo nastavením globální proměnné [_fmode –](../c-runtime-library/fmode.md) v programu. Funkce `_set_fmode` nastaví hodnotu této proměnné, ale můžete nastavit také přímo.  
  
 Při volání funkce otevření souboru, jako [_Otevřít](../c-runtime-library/reference/open-wopen.md), [fopen –](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s –](../c-runtime-library/reference/fopen-s-wfopen-s.md), [freopen –](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s –](../c-runtime-library/reference/freopen-s-wfreopen-s.md), [_fsopen –](../c-runtime-library/reference/fsopen-wfsopen.md) nebo [_sopen_s –](../c-runtime-library/reference/sopen-s-wsopen-s.md), aktuální výchozí nastavení můžete přepsat `_fmode` tak, že zadáte argument příslušné funkce [_set_fmode – ](../c-runtime-library/reference/set-fmode.md). `stdin`, `stdout`, A `stderr` datové proudy vždy otevřít v režimu textových ve výchozím nastavení; můžete také přepsat toto výchozí nastavení při otevírání některý z těchto souborů. Použití [_setmode –](../c-runtime-library/reference/setmode.md) ke změně režimu překlad pomocí popisovače souborů po otevření souboru.  
  
## <a name="see-also"></a>Viz také  
 [Vstup a výstup](../c-runtime-library/input-and-output.md)   
 [Běhové rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)