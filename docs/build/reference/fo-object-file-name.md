---
title: /Fo (název souboru objektů)
description: Referenční příručka k možnosti kompilátoru Microsoft C++ /Fo (název souboru objektu) v sadě Visual Studio.
ms.date: 04/20/2020
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
ms.openlocfilehash: cd22ba745128fe1df67853d98c1495491b9ca840
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748972"
---
# <a name="fo-object-file-name"></a>/Fo (název souboru objektů)

Určuje název souboru nebo*`.obj`* adresáře, který má být použit místo výchozího objektu .

## <a name="syntax"></a>Syntaxe

> **`/Fo`**_Cesta_

## <a name="remarks"></a>Poznámky

Pomocí možnosti **`/Fo`** kompilátoru můžete nastavit výstupní adresář pro všechny soubory objektů generované příkazem kompilátoru CL. Nebo jej můžete použít k přejmenování jednoho souboru objektu.

Ve výchozím nastavení jsou soubory objektů generované kompilátorem umístěny do aktuálního adresáře. Jsou uvedeny základní název zdrojového souboru a přípona. *`.obj`*

Chcete-li **`/Fo`** použít možnost přejmenování souboru objektu, zadejte jako argument *cesty* název výstupního souboru. Při přejmenování souboru objektu můžete použít libovolný název a příponu, *`.obj`* ale doporučenou konvencí je použití . Kompilátor vygeneruje chybu příkazového řádku D8036, pokud zadáte název souboru, pokud **`/Fo`** jste zadali více než jeden zdrojový soubor ke kompilaci.

Chcete-li **`/Fo`** použít možnost nastavení výstupního adresáře pro všechny soubory objektů vytvořené příkazem CL, zadejte adresář jako argument *cesty.* Adresář je označen koncovým lomítkem v argumentu *cesty.* Zadaný adresář musí existovat. není vytvořena automaticky.

## <a name="example"></a>Příklad

Následující příkazový řádek vytvoří soubor objektu s názvem *sample.obj* v existujícím adresáři, * \\zprostředkujícím*, na jednotce D.

```cmd
CL /Fo"D:\intermediate\" /EHsc /c sample.cpp
```

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>Nastavení možnosti v sadě Visual Studio nebo programově

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **Stránky vlastností** projektu. Podrobnosti naleznete v [tématu Nastavení kompilátoru jazyka C++ a vlastnosti sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku **vlastností Vlastnosti** > konfigurace**C/C++** > **Výstupní soubory.**

1. Upravte vlastnost **Název objektu** a nastavte výstupní adresář. V ide musí mít soubor objektu *`.obj`* příponu .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>.

## <a name="see-also"></a>Viz také

[Možnosti výstupního souboru (/F)](output-file-f-options.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[Určení názvu cesty](specifying-the-pathname.md)
