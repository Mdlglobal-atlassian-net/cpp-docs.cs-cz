---
title: -INCLUDE (vynucení odkazů na symboly) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /include
- VC.Project.VCLinkerTool.ForceSymbolReferences
dev_langs:
- C++
helpviewer_keywords:
- INCLUDE linker option
- force symbol references linker option
- symbol references linker force
- /INCLUDE linker option
- symbols, add to symbol table
- -INCLUDE linker option
ms.assetid: 4a039677-360a-480f-bd0b-448e239b449c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6528f6edc51a2dd01e8f91107827b570a44785de
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715777"
---
# <a name="include-force-symbol-references"></a>/INCLUDE (Vynutit odkazy na symboly)

```
/INCLUDE:symbol
```

## <a name="parameters"></a>Parametry

*Symbol*<br/>
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

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ForceSymbolReferences%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)