---
title: "Podpora kódování Unicode v kompilátoru a Linkeru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.UseUnicodeResponseFiles
- VC.Project.VCLibrarianTool.UseUnicodeResponseFiles
- VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles
- VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles
dev_langs: C++
helpviewer_keywords: Unicode, Visual C++
ms.assetid: acc1d322-56b9-4696-a30e-2af891a4e288
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 15fefc4cc44edfd67bd8ba89ab68c6965c8639a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>Podpora kódování Unicode v kompilátoru a linkeru
Toto téma popisuje Podpora kódování Unicode v nástroji Visual C++ sestavení.  
  
 Názvy souborů  
 Názvy souborů zadané na příkazovém řádku nebo direktivy kompilátoru (například #include) může teď obsahují znaky znakové sady Unicode.  
  
 Soubory zdrojového kódu  
 Znaky znakové sady Unicode jsou nyní podporovány v identifikátory, makra, literály řetězce a znak a komentáře.  Univerzální názvy znaků jsou nyní také podporovány.  
  
 Unicode můžete zadat do souboru zdrojového kódu v kódování následující:  
  
-   Znakové sady UTF-16 little endian s nebo bez značka pořadí bajtů (BOM)  
  
-   Znakové sady UTF-16 big endian s nebo bez BOM  
  
-   Znakové sady UTF-8 s BOM  
  
 Výstup  
 Během kompilace výstupy kompilátoru diagnostiky na konzole v UTF-16.  Znaky, které lze zobrazit v konzole nástroje závisí na vlastnosti okna konzoly.  Výstup kompilátoru přesměrován na soubor je v aktuální konzole codepage ANSI.  
  
 Soubory linkeru odezvy a. DEF soubory  
 Soubory odezvy a DEF soubory můžou být buď UTF-16 značka pořadí bajtů nebo ANSI.  Dřív byla ANSI pouze podporované.  
  
 .asm a .cod výpisy  
 výpisy .asm a .cod jsou ve výchozím nastavení pro kompatibilitu s MASM ve ANSI.  Pomocí /FAu výstup ve formátu UTF-8.  Upozorňujeme, že pokud zadáte /FAs, intermingled zdroj právě přímo vytiskne se a vypadat zkomolené, například pokud zdrojový kód je UTF-8 a jste neurčili /FAsu.  
  
 Můžete povolit názvy souborů Unicode ve vývojovém prostředí (najdete v části [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md)) výběrem vhodného nástroje a výběrem **povolit soubory Unicode odezvy** vlastnost který je ve výchozím nastavení povolené. Jedním z důvodů, že můžete změnit toto výchozí nastavení je, pokud změníte vývojového prostředí používat kompilátoru, která nemá podporují kódování Unicode.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření kódu C/C++ v příkazovém řádku](../../build/building-on-the-command-line.md)