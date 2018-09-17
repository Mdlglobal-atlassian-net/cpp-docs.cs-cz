---
title: -GX (povolení zpracování výjimek) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gx
dev_langs:
- C++
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 095db3db73f2be4012efe39f3b8cd8e645ad46c3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718321"
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

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[/EH (model ošetření výjimek)](../../build/reference/eh-exception-handling-model.md)