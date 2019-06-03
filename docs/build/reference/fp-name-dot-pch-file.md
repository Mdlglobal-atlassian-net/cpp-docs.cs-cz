---
title: /Fp (název &period;soubor pch)
description: Pomocí možnosti kompilátoru /Fp zadejte název souboru předkompilované hlavičky.
ms.date: 05/31/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.PrecompiledHeaderFile
- /fp
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
ms.openlocfilehash: 6e7faa934d14acb5d129173c5e0c7ee67d6caf2b
ms.sourcegitcommit: 540fa2f5015de1adfa7b6bf823f6eb4ed5a6a4bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/03/2019
ms.locfileid: "66460872"
---
# <a name="fp-name-periodpch-file"></a>/Fp (název &period;soubor pch)

Poskytuje název cesty pro předkompilované hlavičky místo použití výchozí název cesty.

## <a name="syntax"></a>Syntaxe

> **/Fp**<em>pathname</em>

## <a name="remarks"></a>Poznámky

Použití **/FP** spolu s možností [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](yc-create-precompiled-header-file.md) nebo [/Yu (Použít předkompilovaný hlavičkový soubor)](yu-use-precompiled-header-file.md) a zadat název a cesta k souboru předkompilované hlavičky (PCH) soubor. Ve výchozím nastavení **/Yc** možnost vytvoří název souboru PCH s použitím základní název zdrojového souboru a *pch* rozšíření.

Pokud nezadáte jako součást rozšíření *cesta*, rozšířením *pch* se předpokládá, že. Pokud zadáte název adresáře pomocí lomítko ( **/** ) na konci *cesta*, výchozí název souboru je vc*verze*0.pch, kde  *verze* je hlavní verzi sady nástrojů Visual Studio. Tento adresář musí existovat nebo je vygenerována chyba C1083.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Otevřít **vlastnosti konfigurace** > **C /C++**  > **předkompilované hlavičky** stránku vlastností.

1. Upravit **výstupní soubor předkompilované hlavičky** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="examples"></a>Příklady

Vytvoření samostatné verze souboru předkompilované hlavičky pro sestavení pro ladění programu s názvem, můžete zadat příkaz jako:

```CMD
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

Následující příkaz určuje použití předkompilovaného hlavičkového souboru s názvem MYPCH.pch. Kompilátor překompiluje zdrojový kód v PROG.cpp až do konce MYAPP.h a umístí předkompilovaný kód MYPCH.pch. Pak používá obsah MYPCH.pch a zkompiluje rest PROG.cpp k vytvoření souboru .obj. Výstup tohoto příkladu je soubor s názvem PROG.exe.

```CMD
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>Viz také:

[Možnosti výstupního souboru (/F)](output-file-f-options.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[Určení názvu cesty](specifying-the-pathname.md)
