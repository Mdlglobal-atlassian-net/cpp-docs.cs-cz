---
title: /V (Číslo verze)
ms.date: 11/04/2016
f1_keywords:
- /v
helpviewer_keywords:
- embedding version strings
- /V compiler option [C++]
- version numbers, specifying for .obj
- V compiler option [C++]
- -V compiler option [C++]
ms.assetid: 3e93fb7a-5dfd-49a6-bd49-3dca8052e0f3
ms.openlocfilehash: 7bebd3ab9677bb340203bbf857e4ee9f287e36e6
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817605"
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

**/V** možnost se už nepoužívá od v sadě Visual Studio 2005; **/V** se primárně používají k zajištění podpory vytvoření ovladačů virtuálních zařízení (VxD) a vytváření ovladače VxD je již nejsou podporovány na sadu nástrojů Visual C++. Seznam zastaralých kompilátoru možnosti najdete v tématu **zastaralé a odebrat možnosti kompilátoru** v [možnosti kompilátoru seřazené podle kategorie](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
