---
title: /GX (povolení zpracování výjimek)
ms.date: 11/19/2019
f1_keywords:
- /gx
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
ms.openlocfilehash: 171ff0d0dfb1dec41bae5f6be63c941802c402a4
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245092"
---
# <a name="gx-enable-exception-handling"></a>/GX (povolení zpracování výjimek)

Zastaralé Umožňuje synchronní zpracování výjimek pomocí předpokladu, že funkce deklarované pomocí `extern "C"` nikdy nevyvolají výjimku.

## <a name="syntax"></a>Syntaxe

```
/GX
```

## <a name="remarks"></a>Poznámky

**/GX** je zastaralá. Místo toho použijte odpovídající možnost [/EHsc](eh-exception-handling-model.md) . Seznam zastaralých možností kompilátoru naleznete v části **zastaralé a odebrané možnosti kompilátoru** v tématu [Možnosti kompilátoru uvedené podle kategorie](compiler-options-listed-by-category.md).

Ve výchozím nastavení je ekvivalentem **/GX** **/EHsc**platný při kompilaci pomocí vývojového prostředí sady Visual Studio. Při použití nástrojů příkazového řádku není určena žádná manipulace s výjimkami. To je ekvivalent **/GX-** .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. V navigačním podokně vyberte možnost **Vlastnosti konfigurace**, **CC++/** , **příkazový řádek**.

1. Zadejte možnost kompilátoru do pole **Další možnosti** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Podívejte se na téma <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[/EH (model ošetření výjimek)](eh-exception-handling-model.md)
