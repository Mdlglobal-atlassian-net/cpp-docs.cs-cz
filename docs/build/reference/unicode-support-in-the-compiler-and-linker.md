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
ms.openlocfilehash: 71458ab345670c0a5715576a7da80c4e6ff2955b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807499"
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>Podpora kódování Unicode v kompilátoru a linkeru

Většina nástrojů sestavení Visual C++ podporují Unicode vstupy a výstupy.

## <a name="filenames"></a>Názvy souborů

Názvy souborů, které jsou zadané na příkazovém řádku nebo v direktivách kompilátoru (například `#include`) může obsahovat znaky Unicode.

## <a name="source-code-files"></a>Soubory zdrojového kódu

Znaky Unicode jsou podporovány v identifikátorech, makrech, literálech řetězců a znaků a v komentářích.  Univerzální názvy znaků jsou také podporovány.

Kódování Unicode lze vložit do souboru zdrojového kódu v následujícím kódování:

- UTF-16 little endian s nebo bez značky pořadí bajtů (BOM)

- UTF-16 big endian s nebo bez BOM

- UTF-8 s BOM

## <a name="output"></a>Výstup

Během kompilace výstup kompilátoru diagnostikuje konzolu v kódování UTF-16.  Znaky, které se dají zobrazit v konzole závisí na vlastnostech okna konzoly.  Výstup kompilátoru do souboru přesměrování je v aktuální znakové stránce ANSI konzoly.

## <a name="linker-response-files-and-def-files"></a>Soubory odpovědí linkeru a. DEF soubory

Soubory odpovědí a soubory DEF mohou být buď UTF-16 s BOM nebo ANSI.

## <a name="asm-and-cod-dumps"></a>výpisy .asm a .cod

výpisy .asm a .cod jsou ve výchozím nastavení pro kompatibilitu s MASM ve standardu ANSI. Použití [/fau vytvořte](fa-fa-listing-file.md) pro výstup kódování UTF-8. Všimněte si, že pokud zadáte **/FAS**, smíšené zdroje budou pouze přímo vytištěny a mohou vypadat neúhledně, například pokud zdrojový kód je UTF-8 a jste neurčili, nevložily **/FAsu**.

## <a name="see-also"></a>Viz také:

[Použití nástrojů MSVC z příkazového řádku](../building-on-the-command-line.md)