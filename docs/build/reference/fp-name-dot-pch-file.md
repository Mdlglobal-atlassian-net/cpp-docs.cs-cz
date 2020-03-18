---
title: /FP (název &period;souboru PCH)
description: Pomocí možnosti kompilátoru/FP určete název souboru předkompilované hlavičky.
ms.date: 05/31/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.PrecompiledHeaderFile
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderFile
helpviewer_keywords:
- Fp compiler option [C++]
- -Fp compiler option [C++]
- naming precompiler header files
- PCH files, naming
- names [C++], PCH
- .pch files, naming
- precompiled header files, naming
- /Fp compiler option [C++]
ms.assetid: 0fcd9cbd-e09f-44d3-9715-b41efb5d0be2
ms.openlocfilehash: d62c5bd9fc7920c0a2a5530879680fad2a01d39a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439779"
---
# <a name="fp-name-periodpch-file"></a>/FP (název &period;souboru PCH)

Poskytuje název cesty pro předkompilovanou hlavičku namísto použití výchozího názvu cesty.

## <a name="syntax"></a>Syntaxe

> **/FP**<em>cesta</em>

## <a name="remarks"></a>Poznámky

Použijte možnost **/FP** s [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](yc-create-precompiled-header-file.md) nebo [/Yu (použijte soubor předkompilované hlavičky)](yu-use-precompiled-header-file.md) k určení cesty a názvu souboru předkompilované hlavičky (PCH). Ve výchozím nastavení možnost **/YC** vytvoří název souboru PCH pomocí základního názvu zdrojového souboru a rozšíření *PCH* .

Pokud neurčíte rozšíření jako součást *cesty*, předpokládá se rozšíření *PCH* . Když zadáte název adresáře pomocí lomítka ( **/** ) na konci *cesty*, výchozí název souboru je VC*verze*0. pch, kde *Version* je hlavní verzí sady nástrojů sady Visual Studio. Tento adresář musí existovat, nebo je vygenerována chyba C1083.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Otevřete **Vlastnosti konfigurace** > stránka vlastností **Předkompilovaná hlavička** **C/C++**  > .

1. Upravte vlastnost **výstupní soubor předkompilované hlavičky** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="examples"></a>Příklady

Chcete-li vytvořit samostatnou pojmenovanou verzi souboru předkompilované hlavičky pro ladicí sestavení programu, můžete zadat příkaz jako:

```CMD
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

Následující příkaz určuje použití předkompilovaného hlavičkového souboru s názvem MYPCH. pch. Kompilátor předkompiluje zdrojový kód v souboru auto. cpp až do konce MYAPP. h a vloží předkompilovaný kód do souboru MYPCH. pch. Pak použije obsah souboru MYPCH. pch a zkompiluje zbytek programu auto. cpp a vytvoří soubor. obj. Výstupem tohoto příkladu je soubor s názvem auto. exe.

```CMD
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>Viz také

[Možnosti výstupního souboru (/F)](output-file-f-options.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[Určení názvu cesty](specifying-the-pathname.md)
