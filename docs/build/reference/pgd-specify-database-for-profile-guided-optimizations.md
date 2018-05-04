---
title: / PGD (určit databázi pro optimalizace na základě profilu) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ProfileGuidedDatabase
dev_langs:
- C++
helpviewer_keywords:
- -PGD linker option
- /PGD linker option
ms.assetid: 9f312498-493b-461f-886f-92652257e443
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7685f99137a1b599a5f9020fac9e3cae4ba3bc3c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="pgd-specify-database-for-profile-guided-optimizations"></a>/PGD (Určit databázi pro optimalizace na základě profilu)

**Možnost /PGD je zastaralý.** Spouštění v sadě Visual Studio 2015, raději [/GENPROFILE nebo /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) možnosti linkeru místo. Tato možnost slouží k zadání názvu souboru .pgd používá proces optimalizace na základě profilu.

## <a name="syntax"></a>Syntaxe

> **/ PGD:**_filename_

## <a name="argument"></a>Argument

*Název souboru*<br/>
Určuje název souboru .pgd, který se používá k ukládání informací o spuštěného programu.

## <a name="remarks"></a>Poznámky

Při použití nepoužívané [/LTCG:PGINSTRUMENT](../../build/reference/ltcg-link-time-code-generation.md) možnost, použijte **/PGD** určete jiný než výchozí název nebo umístění souboru .pgd. Pokud nezadáte **/PGD**, .pgd základní název souboru je stejný jako název výstupního souboru (.exe nebo .dll) základní a je vytvořen ve stejném adresáři, ze kterého byl vyvolán odkaz.

Při použití nepoužívané **/LTCG:PGOPTIMIZE** možnost, použijte **/PGD** možnost zadat název souboru .pgd sloužící k vytvoření optimalizované bitové kopie. *Filename* argument by měl odpovídat *filename* zadaný na **/LTCG:PGINSTRUMENT**.

Další informace najdete v tématu [optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **optimalizace** stránku vlastností.

1. Změnit **databáze na základě profilu** vlastnost. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)<br/>
