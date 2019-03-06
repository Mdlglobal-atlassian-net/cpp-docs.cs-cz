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
ms.openlocfilehash: 5502cfda1afe05d8e4944de870349a8db2860f92
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416784"
---
# <a name="c-preserve-comments-during-preprocessing"></a>/C (Zachovat komentáře při předběžném zpracování)

Zachová komentáře při předzpracování.

## <a name="syntax"></a>Syntaxe

```
/C
```

## <a name="remarks"></a>Poznámky

Tato možnost kompilátoru vyžaduje **/E**, **/P**, nebo **/EP** možnost.

Následující příklad kódu se zobrazí komentář zdrojového kódu.

```
// C_compiler_option.cpp
// compile with: /E /C /c
int i;   // a variable
```

Tento příklad vytvoří následující výstup.

```
#line 1 "C_compiler_option.cpp"
int i;   // a variable
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **preprocesor** stránku vlastností.

1. Upravit **zachovat komentáře** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[/E (předzpracování do stdout)](../../build/reference/e-preprocess-to-stdout.md)<br/>
[/P (předzpracování do souboru)](../../build/reference/p-preprocess-to-a-file.md)<br/>
[/EP (předzpracování do stdout bez direktiv #line)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)
