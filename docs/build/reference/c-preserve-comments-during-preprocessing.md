---
title: /C (Zachovat komentáře při předběžném zpracování)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.KeepComments
- VC.Project.VCCLWCECompilerTool.KeepComments
helpviewer_keywords:
- comments, not stripping during preprocessing
- preserve comments during preprocessing
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 944567ca-16bc-4728-befe-d414a7787f26
ms.openlocfilehash: f80ebf45dd396a3f92d9b755c56522d4731bb2d0
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440271"
---
# <a name="c-preserve-comments-during-preprocessing"></a>/C (Zachovat komentáře při předběžném zpracování)

Zachovává komentáře během předběžného zpracování.

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

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>.

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[/E (předzpracování do stdout)](e-preprocess-to-stdout.md)<br/>
[/P (předzpracování do souboru)](p-preprocess-to-a-file.md)<br/>
[/EP (předzpracování do stdout bez direktiv #line)](ep-preprocess-to-stdout-without-hash-line-directives.md)
