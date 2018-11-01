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
ms.openlocfilehash: 3e820791b651a029f048423daacf50ddc8b74a1d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620620"
---
# <a name="gx-enable-exception-handling"></a>/GX (povolení zpracování výjimek)

Zastaralé Povolí synchronní zpracování výjimek pomocí za předpokladu, že funkce deklarované s použitím `extern "C"` nikdy nevyvolají výjimku.

## <a name="syntax"></a>Syntaxe

```
/GX
```

## <a name="remarks"></a>Poznámky

**/GX** je zastaralý. Použít ekvivalent [/EHsc](../../build/reference/eh-exception-handling-model.md) místo něj parametr. Seznam možností kompilátoru zastaralé, najdete v článku **zastaralé a odebrat možnosti kompilátoru** tématu [možnosti kompilátoru seřazené podle kategorie](../../build/reference/compiler-options-listed-by-category.md).

Ve výchozím nastavení **/EHsc**, ekvivalent **/GX**, je v platnosti při kompilaci s použitím vývojového prostředí sady Visual Studio. Při použití nástroje příkazového řádku, je zadán bez ošetření výjimek. Toto je ekvivalentem **/GX-**.

Další informace najdete v tématu [zpracování výjimek jazyka C++](../../cpp/cpp-exception-handling.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. V navigačním podokně zvolte **vlastnosti konfigurace**, **C/C++**, **příkazového řádku**.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[/EH (model ošetření výjimek)](../../build/reference/eh-exception-handling-model.md)