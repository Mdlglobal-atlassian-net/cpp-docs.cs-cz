---
title: /Gm (Povolit minimální opětovné sestavení)
ms.date: 11/12/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
ms.openlocfilehash: 9b928f3add0a2ec10257bf63fe61a824336c19b8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439642"
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm (Povolit minimální opětovné sestavení)

Zastaralé Povoluje minimální opětovné sestavení, které určuje, C++ zda je nutné znovu zkompilovat C++ zdrojové soubory, které obsahují změněné definice tříd (uložené v hlavičkových souborech (. h)).

## <a name="syntax"></a>Syntaxe

```
/Gm
```

## <a name="remarks"></a>Poznámky

**/GM** je zastaralá. Nemusí aktivovat sestavení pro určitý druh změny souboru hlaviček. Tuto možnost můžete z vašich projektů bezpečně odebrat. Pro zlepšení časů sestavení doporučujeme místo toho použít předkompilované hlavičky a přírůstkové a paralelní možnosti sestavení. Seznam zastaralých možností kompilátoru naleznete v části **zastaralé a odebrané možnosti kompilátoru** v tématu [Možnosti kompilátoru uvedené podle kategorie](compiler-options-listed-by-category.md).

Kompilátor ukládá informace o závislostech mezi zdrojovými soubory a definicemi tříd v souboru. IDB projektu během první kompilace. (Informace o závislostech určují, který zdrojový soubor závisí na definici třídy a který soubor. h definice je umístěna v.) Další kompilace používají informace uložené v souboru. IDB k určení, zda zdrojový soubor musí být zkompilován, i když obsahuje upravený soubor. h.

> [!NOTE]
> Minimální opětovné sestavení spoléhá na definice tříd, které mezi soubory zahrnutí nemění. Definice tříd musí být globální pro projekt (měla by existovat pouze jedna definice dané třídy), protože informace o závislostech v souboru. IDB jsou vytvořeny pro celý projekt. Pokud máte více než jednu definici pro třídu ve vašem projektu, vypněte minimální opětovné sestavení.

Vzhledem k tomu, že přírůstkový linker nepodporuje metadata Windows obsažená v souborech. obj pomocí možnosti [/ZW (prostředí Windows Runtime Compilation)](zw-windows-runtime-compilation.md) , možnost **/GM** není kompatibilní s **/ZW**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace** > stránka vlastností **generování kódu** **C++ jazyka C/**  > .

1. Upravte vlastnost **Povolit minimální opětovné sestavení** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>.

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
