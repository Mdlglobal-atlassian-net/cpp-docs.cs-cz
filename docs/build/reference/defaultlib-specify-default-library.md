---
title: /DEFAULTLIB (Zadat výchozí knihovnu)
ms.date: 05/29/2018
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
ms.openlocfilehash: 408507bf0683ea3434ab138fd5ca3a815a1c6a33
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494234"
---
# <a name="defaultlib-specify-default-library"></a>/DEFAULTLIB (Zadat výchozí knihovnu)

Zadání výchozí knihovny pro vyhledávání pro přeložení externí odkazy.

## <a name="syntax"></a>Syntaxe

> **/ DEFAULTLIB**:_knihovny_

### <a name="arguments"></a>Arguments

|Argument|Popis|
|-|-|
*Knihovna*|Název knihovny pro hledání při překladu externích odkazů.

## <a name="remarks"></a>Poznámky

**/DEFAULTLIB** možnost přičítá *knihovny* do seznamu knihoven, na které odkaz prohledává při překladu odkazů. Knihovna zadaným **/DEFAULTLIB** prohledáván po explicitně zadané na příkazovém řádku a před výchozí knihovny s názvem v souborech .obj knihovny.

Při použití bez argumentů, [: / NODEFAULTLIB (ignorovat všechny výchozí knihovny)](../../build/reference/nodefaultlib-ignore-libraries.md) možnost přepíše všechny **/DEFAULTLIB**:*knihovny* možnosti. **: / NODEFAULTLIB**:*knihovny* možnost přepsání **/DEFAULTLIB**:*knihovny* při stejné *knihovny*název je zadán v obou.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. V **další možnosti**, zadejte **/DEFAULTLIB**:*knihovny* možnost pro každou knihovnu pro hledání. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

- [Nastavení možností linkeru](../../build/reference/setting-linker-options.md)
- [Možnosti linkeru](../../build/reference/linker-options.md)
