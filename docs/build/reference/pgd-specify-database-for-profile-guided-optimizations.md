---
title: /PGD (Určit databázi pro optimalizace na základě profilu)
ms.date: 03/14/2018
f1_keywords:
- VC.Project.VCLinkerTool.ProfileGuidedDatabase
helpviewer_keywords:
- -PGD linker option
- /PGD linker option
ms.assetid: 9f312498-493b-461f-886f-92652257e443
ms.openlocfilehash: e1d7c9fcb94a9351ce94b66e04b4bfc523248f4e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319795"
---
# <a name="pgd-specify-database-for-profile-guided-optimizations"></a>/PGD (Určit databázi pro optimalizace na základě profilu)

**Možnost /PGD je zastaralý.** Spouští se v sadě Visual Studio 2015, raději [/genprofile nebo /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) místo možnosti linkeru. Tato možnost slouží k zadání názvu souboru .pgd používá proces optimalizace na základě profilu.

## <a name="syntax"></a>Syntaxe

> **/ PGD:**_název souboru_

## <a name="argument"></a>Argument

*Název souboru*<br/>
Určuje název, který se používá k ukládání informací o spuštění programu soubor .pgd.

## <a name="remarks"></a>Poznámky

Při použití zastaralá [/LTCG:PGINSTRUMENT](ltcg-link-time-code-generation.md) možnost, použijte **/PGD** a zadejte jiný než výchozí název nebo umístění pro soubor .pgd. Pokud nezadáte **/PGD**, základní název souboru .pgd je stejný jako název výstupního souboru (.exe nebo .dll) základní a je vytvořena ve stejném adresáři, ze kterého byla vyvolána na odkaz.

Při použití zastaralá **/LTCG:PGOPTIMIZE** možnost, použijte **/PGD** můžete zadat název souboru .pgd použít k vytvoření optimalizované bitové kopie. *Filename* argument by měl odpovídat *filename* zadaná **/LTCG:PGINSTRUMENT**.

Další informace najdete v tématu [Profile-Guided optimalizace](../profile-guided-optimizations.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **optimalizace** stránku vlastností.

1. Upravit **databáze na základě profilu** vlastnost. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)<br/>
