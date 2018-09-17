---
title: -V (číslo verze) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /v
dev_langs:
- C++
helpviewer_keywords:
- embedding version strings
- /V compiler option [C++]
- version numbers, specifying for .obj
- V compiler option [C++]
- -V compiler option [C++]
ms.assetid: 3e93fb7a-5dfd-49a6-bd49-3dca8052e0f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4ad42a72a874537a6307cfc547852f812f4aaaa
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707964"
---
# <a name="v-version-number"></a>/V (Číslo verze)

Zastaralé Vloží textový řetězec v souboru .obj.

## <a name="syntax"></a>Syntaxe

```
/Vstring
```

## <a name="arguments"></a>Arguments

*string*<br/>
Řetězec určující číslo verze nebo o autorských právech, který má být vložen v souboru .obj.

## <a name="remarks"></a>Poznámky

Popisek stringcan souboru .obj se číslo verze nebo o autorských právech. Všechny znaky mezera nebo tabulátor musí být uzavřen do dvojitých uvozovek ("), pokud jsou součástí řetězce. Zpětné lomítko (\\) musí předcházet všechny dvojité uvozovky, pokud jsou součástí řetězce. Mezera mezi **/V** a `string` je volitelný.

Můžete také použít [komentáře (C/C++)](../../preprocessor/comment-c-cpp.md) s argumentem kompilátoru typ komentáře v souboru .obj umístit název a číslo verze kompilátoru.

**/V** možnost se už nepoužívá od v sadě Visual Studio 2005; **/V** se primárně používají k zajištění podpory vytvoření ovladačů virtuálních zařízení (VxD) a vytváření ovladače VxD je již nejsou podporovány na sadu nástrojů Visual C++. Seznam zastaralých kompilátoru možnosti najdete v tématu **zastaralé a odebrat možnosti kompilátoru** v [možnosti kompilátoru seřazené podle kategorie](../../build/reference/compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)