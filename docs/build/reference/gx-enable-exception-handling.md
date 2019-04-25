---
title: /GX (povolení zpracování výjimek)
ms.date: 11/04/2016
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
ms.openlocfilehash: 43be8f6d0f080f0d85568ce5b089751fc68f0e8e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292000"
---
# <a name="gx-enable-exception-handling"></a>/GX (povolení zpracování výjimek)

Zastaralé Povolí synchronní zpracování výjimek pomocí za předpokladu, že funkce deklarované s použitím `extern "C"` nikdy nevyvolají výjimku.

## <a name="syntax"></a>Syntaxe

```
/GX
```

## <a name="remarks"></a>Poznámky

**/GX** je zastaralý. Použít ekvivalent [/EHsc](eh-exception-handling-model.md) místo něj parametr. Seznam možností kompilátoru zastaralé, najdete v článku **zastaralé a odebrat možnosti kompilátoru** tématu [možnosti kompilátoru seřazené podle kategorie](compiler-options-listed-by-category.md).

Ve výchozím nastavení **/EHsc**, ekvivalent **/GX**, je v platnosti při kompilaci s použitím vývojového prostředí sady Visual Studio. Při použití nástroje příkazového řádku, je zadán bez ošetření výjimek. Toto je ekvivalentem **/GX-**.

Další informace najdete v tématu [zpracování výjimek jazyka C++](../../cpp/cpp-exception-handling.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. V navigačním podokně zvolte **vlastnosti konfigurace**, **C/C++**, **příkazového řádku**.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[/EH (model ošetření výjimek)](eh-exception-handling-model.md)
