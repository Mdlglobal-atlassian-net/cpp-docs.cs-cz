---
title: /Gm (Povolit minimální opětovné sestavení)
ms.date: 11/12/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- /FD
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
ms.openlocfilehash: 4a66dda37b84119a4b8bc23f7fc719d50e8786f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292063"
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm (Povolit minimální opětovné sestavení)

Zastaralé Povoluje minimální opětovné sestavení, která určuje, zda se musejí překompilovat zdrojové soubory C++ obsahující změněné definice tříd C++ (uložené v souborech hlaviček (.h)).

## <a name="syntax"></a>Syntaxe

```
/Gm
```

## <a name="remarks"></a>Poznámky

**/GM** je zastaralý. To nemusí aktivovat sestavení pro určité druhy změny v souboru záhlaví. Tuto možnost můžete bezpečně odstranit z vašich projektů. Pokud chcete zkrátit dobu sestavování, doporučujeme použití předkompilovaných hlaviček a přírůstkových a paralelní možnosti sestavení místo toho. Seznam možností kompilátoru zastaralé, najdete v článku **zastaralé a odebrat možnosti kompilátoru** tématu [možnosti kompilátoru seřazené podle kategorie](compiler-options-listed-by-category.md).

Kompilátor ukládá informace o závislostech mezi zdrojovými soubory a definice tříd v souboru IDB projektu během první kompilace. (Informace o závislostech říká, které zdrojový soubor je závislá na které definice třídy a které. h: soubor definice se nachází v.) Následné zkompiluje používat informace uložené v souboru IDB určit, zda zdrojový soubor musí ke kompilaci, i v případě obsahuje upravený. h: soubor.

> [!NOTE]
> Minimální opětovné sestavení závisí na třídě definice se nemění, mezi soubory k zahrnutí. Definice tříd musí být globální pro projekt (měl by existovat pouze jedna definice z dané třídy), protože informace o závislostech v souboru IDB se vytvoří pro celý projekt. Pokud máte více než jednu definici pro třídu ve vašem projektu, zakažte minimálního opětovného sestavení.

Protože přírůstkový linker nepodporuje metadat Windows zahrnuty v souborech .obj pomocí [/ZW (kompilace Windows Runtime)](zw-windows-runtime-compilation.md) možnost, **/Gm** možnost není kompatibilní s  **/ZW**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **generování kódu** stránku vlastností.

1. Upravit **povolení minimálního opětovného sestavení** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
