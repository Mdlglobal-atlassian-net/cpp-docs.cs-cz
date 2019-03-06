---
title: /INCLUDE (Vynutit odkazy na symboly)
ms.date: 11/04/2016
f1_keywords:
- /include
- VC.Project.VCLinkerTool.ForceSymbolReferences
helpviewer_keywords:
- INCLUDE linker option
- force symbol references linker option
- symbol references linker force
- /INCLUDE linker option
- symbols, add to symbol table
- -INCLUDE linker option
ms.assetid: 4a039677-360a-480f-bd0b-448e239b449c
ms.openlocfilehash: 389bd16829c2466b02cb879c8bc8d43c9efa6fb4
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421217"
---
# <a name="include-force-symbol-references"></a>/INCLUDE (Vynutit odkazy na symboly)

```
/INCLUDE:symbol
```

## <a name="parameters"></a>Parametry

*symbol*<br/>
Určuje symbol, který chcete přidat do tabulky symbolů.

## <a name="remarks"></a>Poznámky

Parametr/include přikáže linkeru, aby přidal zadaný symbol do tabulky symbolů.

Pokud chcete zadat více symbolů, zadejte čárku (,), středník (;) nebo mezery mezi názvy symbolů. Na příkazovém řádku, zadejte parametr/include:`symbol` s jednou registrací u každé symbol.

Linker řeší `symbol` přidáním objekt, který obsahuje definici symbolu do programu. Tato funkce je užitečná pro zahrnutí knihovny objekt, který by jinak propojit do programu.

Zadání symbolu pomocí této možnosti přepsání odebrání tohoto symbolu pomocí [OPT](../../build/reference/opt-optimizations.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **vstup** stránku vlastností.

1. Upravit **vynutit odkazy na symboly** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ForceSymbolReferences%2A>.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
