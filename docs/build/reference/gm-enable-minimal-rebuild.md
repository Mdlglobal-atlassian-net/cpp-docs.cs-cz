---
title: -Gm (povolení minimálního opětovného sestavení) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- /FD
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
dev_langs:
- C++
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f18881e79a3f82941f04dccbde210b2c62dcbca
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725761"
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm (Povolit minimální opětovné sestavení)

Povoluje minimální opětovné sestavení, která určuje, zda se musejí překompilovat zdrojové soubory C++ obsahující změněné definice tříd C++ (uložené v souborech hlaviček (.h)).

## <a name="syntax"></a>Syntaxe

```
/Gm
```

## <a name="remarks"></a>Poznámky

Kompilátor ukládá informace o závislostech mezi zdrojovými soubory a definice tříd v souboru IDB projektu během první kompilace. (Informace o závislostech říká, které zdrojový soubor je závislá na které definice třídy a které. h: soubor definice se nachází v.) Následné zkompiluje používat informace uložené v souboru IDB určit, zda zdrojový soubor musí ke kompilaci, i v případě obsahuje upravený. h: soubor.

> [!NOTE]
>  Minimální opětovné sestavení závisí na třídě definice se nemění, mezi soubory k zahrnutí. Definice tříd musí být globální pro projekt (měl by existovat pouze jedna definice z dané třídy), protože informace o závislostech v souboru IDB se vytvoří pro celý projekt. Pokud máte více než jednu definici pro třídu ve vašem projektu, zakažte minimálního opětovného sestavení.

Protože přírůstkový linker nepodporuje metadat Windows zahrnuty v souborech .obj pomocí [/ZW (kompilace Windows Runtime)](../../build/reference/zw-windows-runtime-compilation.md) možnost, **/Gm** možnost není kompatibilní s  **/ZW**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **generování kódu** stránku vlastností.

1. Upravit **povolení minimálního opětovného sestavení** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)