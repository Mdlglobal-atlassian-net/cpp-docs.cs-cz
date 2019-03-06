---
title: / vmb, - vmg (metoda reprezentace)
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
ms.openlocfilehash: 9bb355635181c3db53e1171aaf18cd665e6504ae
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426352"
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

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do kompilátoru **další možnosti** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
