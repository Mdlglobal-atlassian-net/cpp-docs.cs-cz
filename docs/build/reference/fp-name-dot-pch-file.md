---
title: /Fp (název souboru .Pch)
ms.date: 11/04/2016
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
ms.openlocfilehash: 8384aa1ee27fee0bc42e023b78b948d9acd384e8
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414093"
---
# <a name="fp-name-pch-file"></a>/Fp (název souboru .Pch)

Poskytuje název cesty pro předkompilované hlavičky místo použití výchozí název cesty.

## <a name="syntax"></a>Syntaxe

> **/Fp**<em>pathname</em>

## <a name="remarks"></a>Poznámky

Tuto možnost použijte spolu s [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md) nebo [/Yu (Použít předkompilovaný hlavičkový soubor)](../../build/reference/yu-use-precompiled-header-file.md) k zadání názvu cesty pro předkompilované hlavičky místo použití výchozí název cesty. Můžete také použít **/FP** s **/Yc** zadat použití předkompilovaného hlavičkového souboru, který se liší od **/Yc**<em>filename</em> argument a Základní název zdrojového souboru.

Pokud nezadáte rozšíření jako součást názvu cesty, předpokládá se příponou .pch. Pokud chcete zadat adresář bez názvu souboru, výchozí název souboru je VC*x*0.pch, kde *x* je hlavní verze Visual C++ používá.

Můžete také použít **/FP** spolu s možností **/Yu**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **předkompilované hlavičky** stránku vlastností.

1. Upravit **předkompilovaný soubor hlaviček** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderFile%2A>.

## <a name="example"></a>Příklad

Pokud chcete vytvořit předkompilovaný hlavičkový soubor pro ladicí verzi aplikace a kompilujete hlavičkové soubory a zdrojový kód, můžete například zadat příkaz:

```
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

## <a name="example"></a>Příklad

Následující příkaz určuje použití předkompilovaného hlavičkového souboru s názvem MYPCH.pch. Kompilátor předpokládá, že zdrojový kód v PROG.cpp obsahuje byla předkompilována prostřednictvím MYAPP.h a že předkompilovaný kód nachází v MYPCH.pch. Používá obsah MYPCH.pch a zkompiluje rest PROG.cpp k vytvoření souboru .obj. Výstup tohoto příkladu je soubor s názvem PROG.exe.

```
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>Viz také:

[Možnosti výstupního souboru (/F)](../../build/reference/output-file-f-options.md)<br/>
[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[Určení názvu cesty](../../build/reference/specifying-the-pathname.md)
