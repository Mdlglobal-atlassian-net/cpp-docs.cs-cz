---
title: -vmb, - vmg (metoda reprezentace) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /vmb
- /vmg
dev_langs:
- C++
helpviewer_keywords:
- vmb compiler option [C++]
- -vmg compiler option [C++]
- vmg compiler option [C++]
- -vmb compiler option [C++]
- /vmb compiler option [C++]
- representation method compiler options [C++]
- /vmg compiler option [C++]
ms.assetid: ecdb391c-7dab-40b1-916b-673d10889fd4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a95081dfb417711002039727b04d1916c5fe0a14
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720574"
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

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)