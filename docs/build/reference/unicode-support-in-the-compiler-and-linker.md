---
title: Podpora kódování Unicode v kompilátoru a linkeru
ms.date: 12/15/2017
f1_keywords:
- VC.Project.VCLinkerTool.UseUnicodeResponseFiles
- VC.Project.VCLibrarianTool.UseUnicodeResponseFiles
- VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles
- VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles
helpviewer_keywords:
- Unicode, Visual C++
ms.openlocfilehash: 420b01263320cf86df3f99da4523cc2b8bb4d4b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168834"
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>Podpora kódování Unicode v kompilátoru a linkeru

Většina nástrojů C++ pro Visual Build podporuje vstupy a výstupy Unicode.

## <a name="filenames"></a>Názvy souborů

Názvy souborů zadané v příkazovém řádku nebo direktivy kompilátoru (například `#include`) můžou obsahovat znaky Unicode.

## <a name="source-code-files"></a>Soubory zdrojového kódu

Znaky Unicode jsou podporovány v identifikátorech, makrech, řetězcových a znakových literálech a v komentářích.  Podporují se taky univerzální názvy znaků.

Unicode lze zadat do souboru zdrojového kódu v následujících kódováních:

- UTF-16 Little endian s nebo bez označení pořadí bajtů (BOM)

- UTF-16 big endian s BOM nebo bez něj

- UTF-8 s BOM

## <a name="output"></a>Výstup

Během kompilace kompilátor vyprodukuje diagnostiku do konzoly v kódování UTF-16.  Znaky, které lze zobrazit v konzole, závisí na vlastnostech okna konzoly.  Výstup kompilátoru přesměrovaný na soubor je v aktuální znakové stránce konzoly ANSI.

## <a name="linker-response-files-and-def-files"></a>Soubory odpovědí linkeru a. Soubory DEF

Soubory odpovědí a soubory s příponou DEF můžou být UTF-16 pomocí kusovníku nebo ANSI.

## <a name="asm-and-cod-dumps"></a>výpisy. asm a. COD

výpisy. asm a. COD jsou ve výchozím nastavení standard ANSI pro kompatibilitu s MASM. Použijte [/FAU](fa-fa-listing-file.md) k výstupu znakové sady UTF-8. Všimněte si, že pokud zadáte **/FAS**, bude se zdroj smíšené jednoduše tisknout a může vypadat jako nečitelný, například pokud je zdrojový kód UTF-8 a nezadali jste **/FAsu**.

## <a name="see-also"></a>Viz také

[Použití sady nástrojů MSVC z příkazového řádku](../building-on-the-command-line.md)
