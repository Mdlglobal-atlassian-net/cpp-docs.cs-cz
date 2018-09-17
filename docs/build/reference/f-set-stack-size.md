---
title: -F (nastavení velikosti zásobníku) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /f
dev_langs:
- C++
helpviewer_keywords:
- set stack size compiler option
- F compiler option [C++]
- -F compiler option [C++]
- /F compiler option [C++]
- stack, setting size
ms.assetid: 17320b6f-8305-445b-9ec2-75833f4b29e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 244fea4b776f0713b6fb2281563e39d27a910a2d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704242"
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

- Použití **/STACK** – možnost linkeru. Další informace najdete v tématu [/STACK](../../build/reference/stack.md).

- Pomocí nástroje EDITBIN na soubor .exe. Další informace najdete v tématu [Editbin – referenční dokumentace](../../build/reference/editbin-reference.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)