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
ms.openlocfilehash: 34799529517e0263f71ce4f6f29537bf4b59056f
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415419"
---
# <a name="ge-enable-stack-probes"></a>/Ge (Povolit sondy zásobníku)

Aktivuje sondy zásobníku pro každé volání funkce, která vyžaduje úložiště pro místní proměnné.

## <a name="syntax"></a>Syntaxe

```
/Ge
```

## <a name="remarks"></a>Poznámky

Tento mechanismus je užitečné, pokud přepsání funkce sondy zásobníku. Doporučuje se, že používáte [/Gh (povolení _penter funkce háku)](../../build/reference/gh-enable-penter-hook-function.md) místo přepisování adres sondy zásobníku.

[/GS (ovládací prvek zásobníku kontrolu volání)](../../build/reference/gs-control-stack-checking-calls.md) má stejný účinek.

**/Ge** je zastaralé; od v sadě Visual Studio 2005, kompilátor automaticky generuje kontrolou zásobníku. Seznam zastaralých kompilátoru možnosti najdete v tématu **zastaralé a odebrat možnosti kompilátoru** v [možnosti kompilátoru seřazené podle kategorie](../../build/reference/compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
