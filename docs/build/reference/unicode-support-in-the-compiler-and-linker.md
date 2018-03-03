---
title: "Podpora kódování Unicode v kompilátoru a Linkeru | Microsoft Docs"
ms.custom: 
ms.date: 12/15/2017
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.UseUnicodeResponseFiles
- VC.Project.VCLibrarianTool.UseUnicodeResponseFiles
- VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles
- VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles
dev_langs:
- C++
helpviewer_keywords:
- Unicode, Visual C++
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fe775a53914089648a868a94aa2c863ee87790c5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>Podpora kódování Unicode v kompilátoru a linkeru

Většina nástrojů Visual C++ sestavení podporují kódování Unicode vstupy a výstupy.

## <a name="filenames"></a>Názvy souborů

Názvy souborů zadané na příkazovém řádku nebo direktivy kompilátoru (například `#include`) může obsahovat znaky Unicode.

## <a name="source-code-files"></a>Soubory zdrojového kódu

Znaky znakové sady Unicode jsou podporovány v identifikátory, makra, literály řetězce a znak a komentáře.  Univerzální názvy znaků jsou také podporovány.

Unicode můžete zadat do souboru zdrojového kódu v kódování následující:

- Znakové sady UTF-16 little endian s nebo bez značka pořadí bajtů (BOM)

- Znakové sady UTF-16 big endian s nebo bez BOM

- Znakové sady UTF-8 s BOM

## <a name="output"></a>Výstup

Během kompilace kompilátor výstupy diagnostiky na konzole v UTF-16.  Znaky, které lze zobrazit v konzole nástroje závisí na vlastnosti okna konzoly.  Výstup kompilátoru přesměrován na soubor je v aktuální konzole codepage ANSI.

## <a name="linker-response-files-and-def-files"></a>Soubory linkeru odezvy a. DEF soubory

Soubory odezvy a DEF soubory můžou být buď UTF-16 BOM nebo ANSI.

## <a name="asm-and-cod-dumps"></a>.asm a .cod výpisy

výpisy .asm a .cod jsou ve výchozím nastavení pro kompatibilitu s MASM ve ANSI. Použití [/FAu](../../build/reference/fa-fa-listing-file.md) výstup ve formátu UTF-8. Všimněte si, že pokud zadáte **/FAs**, intermingled zdroj právě přímo vytištění a vypadat zkomolené, například pokud zdrojový kód je UTF-8 a jste neurčili **/FAsu**.

## <a name="see-also"></a>Viz také

[Sestavení kódu C/C++ na příkazovém řádku](../../build/building-on-the-command-line.md)