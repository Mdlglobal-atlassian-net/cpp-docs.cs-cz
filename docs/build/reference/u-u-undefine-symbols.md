---
title: /U, /u (nedefinované symboly)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLWCECompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLCompilerTool.UndefineAllPreprocessorDefinitions
- /u
- VC.Project.VCCLWCECompilerTool.UndefineAllPreprocessorDefinitions
helpviewer_keywords:
- -U compiler option [C++]
- Undefine Symbols compiler option
- /U compiler option [C++]
- U compiler option [C++]
ms.assetid: 7bc0474f-6d1f-419b-807d-0d8816763b2a
ms.openlocfilehash: bfc03ebd5c900bf8bf81b4a50eed02111baf85ee
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822482"
---
# <a name="u-u-undefine-symbols"></a>/U, /u (nedefinované symboly)

**/U** – možnost kompilátoru nedefinovaných hodnot preprocesoru zadaný symbol. **/U** – možnost kompilátoru nedefinovaných hodnot, které kompilátor definuje symboly specifické pro společnost Microsoft.

## <a name="syntax"></a>Syntaxe

```
/U[ ]symbol
/u
```

## <a name="arguments"></a>Arguments

*symbol*<br/>
Symbol preprocesoru definice.

## <a name="remarks"></a>Poznámky

Ani **/U** nebo **/u** možnost můžete nedefinovat symbol vytvářeny instalační sadou **#define** směrnice.

**/U** možnost můžete nedefinovat symbol, který byl předtím definovaný s použitím **/D** možnost.

Ve výchozím nastavení kompilátor definuje následující symboly specifické pro společnost Microsoft.

|Symbol|Funkce|
|------------|--------------|
|_CHAR_UNSIGNED|Výchozí znakový typ není podepsaný. Definováno, pokud [/J](j-default-char-type-is-unsigned.md) je zadána možnost.|
|_CPPRTTI|Definováno pro kód zkompilovaný s [GR](gr-enable-run-time-type-information.md) možnost.|
|_CPPUNWIND|Definováno pro kód zkompilovaný s [/EHsc](eh-exception-handling-model.md) možnost.|
|_DLL|Definováno, pokud [/MD](md-mt-ld-use-run-time-library.md) je zadána možnost.|
|_M_IX86|Ve výchozím nastavení, které jsou definované na 600 pro x86 cíle.|
|_MSC_VER|Další informace najdete v tématu [předdefinovaná makra](../../preprocessor/predefined-macros.md).|
|_WIN32|Definováno pro aplikace WIN32. Vždy definováno.|
|_MT|Definováno, pokud [/MD nebo/MT](md-mt-ld-use-run-time-library.md) je zadána možnost.|

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **Upřesnit** stránku vlastností.

1. Upravit **zrušit Definice preprocesoru** nebo **zrušit všechny definice preprocesoru** vlastnosti.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A> nebo <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[/J (výchozí znakový typ není podepsaný)](j-default-char-type-is-unsigned.md)<br/>
[/GR (povolení informací o typu za běhu)](gr-enable-run-time-type-information.md)<br/>
[/EH (model ošetření výjimek)](eh-exception-handling-model.md)<br/>
[/MD, /MT, /LD (použití knihovny run-time)](md-mt-ld-use-run-time-library.md)
