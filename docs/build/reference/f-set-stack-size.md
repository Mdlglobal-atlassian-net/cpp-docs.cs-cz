---
title: /F (nastavení velikosti zásobníku)
ms.date: 11/04/2016
f1_keywords:
- /f
helpviewer_keywords:
- set stack size compiler option
- F compiler option [C++]
- -F compiler option [C++]
- /F compiler option [C++]
- stack, setting size
ms.assetid: 17320b6f-8305-445b-9ec2-75833f4b29e0
ms.openlocfilehash: 9db595daa7de7820b594a8515ece7481b4382c98
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293092"
---
# <a name="f-set-stack-size"></a>/F (nastavení velikosti zásobníku)

Nastaví velikost zásobníku aplikace v bajtech.

## <a name="syntax"></a>Syntaxe

> **/F** *číslo*

## <a name="arguments"></a>Arguments

*Číslo*<br/>
Velikost zásobníku v bajtech.

## <a name="remarks"></a>Poznámky

Bez této možnosti výchozí velikost zásobníku 1 MB. *Číslo* argument může být v desítkovém zápisu nebo v zápisu jazyka. Argument musí být v rozsahu 1 až maximální velikost zásobníku přijal linkeru. Linker se zaokrouhlí nahoru zadanou hodnotu do nejbližší 4 bajty. Mezera mezi **/F** a *číslo* je volitelný.

Budete muset zvětšete velikost zásobníku, pokud se program dostane zprávy přetečení zásobníku.

Můžete také nastavit velikost zásobníku:

- Použití **/STACK** – možnost linkeru. Další informace najdete v tématu [/STACK](stack.md).

- Pomocí nástroje EDITBIN na soubor .exe. Další informace najdete v tématu [Editbin – referenční dokumentace](editbin-reference.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
