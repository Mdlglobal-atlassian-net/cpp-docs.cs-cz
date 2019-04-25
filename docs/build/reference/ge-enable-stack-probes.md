---
title: /Ge (Povolit sondy zásobníku)
ms.date: 11/04/2016
f1_keywords:
- /ge
helpviewer_keywords:
- -Ge compiler option [C++]
- enable stack probes
- /Ge compiler option [C++]
- stack, stack probes
- stack probes
- stack checking calls
- Ge compiler option [C++]
ms.assetid: 4b54deae-4e3c-4bfa-95f3-ba23590f7258
ms.openlocfilehash: a785ec041370e0bcbb2ce8b698bfba89235a0a0c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292182"
---
# <a name="ge-enable-stack-probes"></a>/Ge (Povolit sondy zásobníku)

Aktivuje sondy zásobníku pro každé volání funkce, která vyžaduje úložiště pro místní proměnné.

## <a name="syntax"></a>Syntaxe

```
/Ge
```

## <a name="remarks"></a>Poznámky

Tento mechanismus je užitečné, pokud přepsání funkce sondy zásobníku. Doporučuje se, že používáte [/Gh (povolení _penter funkce háku)](gh-enable-penter-hook-function.md) místo přepisování adres sondy zásobníku.

[/GS (ovládací prvek zásobníku kontrolu volání)](gs-control-stack-checking-calls.md) má stejný účinek.

**/Ge** je zastaralé; od v sadě Visual Studio 2005, kompilátor automaticky generuje kontrolou zásobníku. Seznam zastaralých kompilátoru možnosti najdete v tématu **zastaralé a odebrat možnosti kompilátoru** v [možnosti kompilátoru seřazené podle kategorie](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
