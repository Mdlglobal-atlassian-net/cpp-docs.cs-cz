---
title: -U, -u (nedefinované symboly) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLWCECompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLCompilerTool.UndefineAllPreprocessorDefinitions
- /u
- VC.Project.VCCLWCECompilerTool.UndefineAllPreprocessorDefinitions
dev_langs:
- C++
helpviewer_keywords:
- -U compiler option [C++]
- Undefine Symbols compiler option
- /U compiler option [C++]
- U compiler option [C++]
ms.assetid: 7bc0474f-6d1f-419b-807d-0d8816763b2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 34030a8ef91e5a25bdb1a13981925c5ddf1f05df
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721549"
---
# <a name="u-u-undefine-symbols"></a>/U, /u (nedefinované symboly)

**/U** – možnost kompilátoru nedefinovaných hodnot preprocesoru zadaný symbol. **/U** – možnost kompilátoru nedefinovaných hodnot, které kompilátor definuje symboly specifické pro společnost Microsoft.

## <a name="syntax"></a>Syntaxe

```
/U[ ]symbol
/u
```

## <a name="arguments"></a>Arguments

*Symbol*<br/>
Symbol preprocesoru definice.

## <a name="remarks"></a>Poznámky

Ani **/U** nebo **/u** možnost můžete nedefinovat symbol vytvářeny instalační sadou **#define** směrnice.

**/U** možnost můžete nedefinovat symbol, který byl předtím definovaný s použitím **/D** možnost.

Ve výchozím nastavení kompilátor definuje následující symboly specifické pro společnost Microsoft.

|Symbol|Funkce|
|------------|--------------|
|_CHAR_UNSIGNED|Výchozí znakový typ není podepsaný. Definováno, pokud [/J](../../build/reference/j-default-char-type-is-unsigned.md) je zadána možnost.|
|_CPPRTTI|Definováno pro kód zkompilovaný s [GR](../../build/reference/gr-enable-run-time-type-information.md) možnost.|
|_CPPUNWIND|Definováno pro kód zkompilovaný s [/EHsc](../../build/reference/eh-exception-handling-model.md) možnost.|
|_DLL|Definováno, pokud [/MD](../../build/reference/md-mt-ld-use-run-time-library.md) je zadána možnost.|
|_M_IX86|Ve výchozím nastavení, které jsou definované na 600 pro x86 cíle.|
|_MSC_VER|Další informace najdete v tématu [předdefinovaná makra](../../preprocessor/predefined-macros.md).|
|_WIN32|Definováno pro aplikace WIN32. Vždy definováno.|
|_MT|Definováno, pokud [/MD nebo/MT](../../build/reference/md-mt-ld-use-run-time-library.md) je zadána možnost.|

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **Upřesnit** stránku vlastností.

1. Upravit **zrušit Definice preprocesoru** nebo **zrušit všechny definice preprocesoru** vlastnosti.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A> nebo <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[/J (výchozí znakový typ není podepsán)](../../build/reference/j-default-char-type-is-unsigned.md)
[/GR (povolení běhové informace o typu)](../../build/reference/gr-enable-run-time-type-information.md)
[/EH (Model zpracování výjimek)](../../build/reference/eh-exception-handling-model.md) 
 [/ / MD, / MT, /LD (použití knihovny Run-Time)](../../build/reference/md-mt-ld-use-run-time-library.md)