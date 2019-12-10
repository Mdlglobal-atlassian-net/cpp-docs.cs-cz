---
title: /C (Zachovat komentáře při předběžném zpracování)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.KeepComments
- /c
- VC.Project.VCCLWCECompilerTool.KeepComments
helpviewer_keywords:
- comments, not stripping during preprocessing
- preserve comments during preprocessing
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 944567ca-16bc-4728-befe-d414a7787f26
ms.openlocfilehash: 6d0cf8e5f628f3f5301f54d7c853bfc2ab63cb7e
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988367"
---
# <a name="c-preserve-comments-during-preprocessing"></a>/C (Zachovat komentáře při předběžném zpracování)

Zachová komentáře při předzpracování.

## <a name="syntax"></a>Syntaxe

```
/C
```

## <a name="remarks"></a>Poznámky

Tato možnost kompilátoru vyžaduje možnost **/e**, **/p**nebo **/EP** .

Následující ukázka kódu zobrazí komentář ke zdrojovému kódu.

```cpp
// C_compiler_option.cpp
// compile with: /E /C /c
int i;   // a variable
```

Tato ukázka vytvoří následující výstup.

```
#line 1 "C_compiler_option.cpp"
int i;   // a variable
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na složku **CC++ /a** .

1. Klikněte na stránku vlastností **preprocesoru** .

1. Upravte vlastnost **Zachovat komentáře** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Podívejte se na téma <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[/E (předzpracování do stdout)](e-preprocess-to-stdout.md)<br/>
[/P (předzpracování do souboru)](p-preprocess-to-a-file.md)<br/>
[/EP (předzpracování do stdout bez direktiv #line)](ep-preprocess-to-stdout-without-hash-line-directives.md)
