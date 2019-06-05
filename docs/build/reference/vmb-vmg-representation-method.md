---
title: /vmb, /vmg (metoda reprezentace)
ms.date: 11/04/2016
f1_keywords:
- /vmb
- /vmg
helpviewer_keywords:
- vmb compiler option [C++]
- -vmg compiler option [C++]
- vmg compiler option [C++]
- -vmb compiler option [C++]
- /vmb compiler option [C++]
- representation method compiler options [C++]
- /vmg compiler option [C++]
ms.assetid: ecdb391c-7dab-40b1-916b-673d10889fd4
ms.openlocfilehash: 25d24d7f92537f16e36213b8a8fd7b945fda7f5a
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504300"
---
# <a name="vmb-vmg-representation-method"></a>/vmb, /vmg (metoda reprezentace)

Vyberte metodu, kterou kompilátor používá k reprezentaci ukazatele na členy třídy.

Použití **/vmb** Pokud vždy definujete třídu před deklarovat ukazatel na člen třídy.

Použití **/vmg** k deklaraci ukazatele na člen třídy před definováním třídy. Tyto potřeby může nastat, pokud definujete členy ve dvou různých tříd, které odkazují na sebe navzájem. Jednu třídu pro takové vzájemně referenční třídy, musí se odkazovat dříve, než je definován.

## <a name="syntax"></a>Syntaxe

```
/vmb
/vmg
```

## <a name="remarks"></a>Poznámky

Můžete také použít [pointers_to_members](../../preprocessor/pointers-to-members.md) nebo [klíčová slova dědičnosti](../../cpp/inheritance-keywords.md) v kódu k určení reprezentaci ukazatele.

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
