---
title: /FC (úplná cesta k souboru zdrojového kódu v diagnostice)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UseFullPaths
- /FC
helpviewer_keywords:
- /FC compiler option [C++]
- -FC compiler option [C++]
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
ms.openlocfilehash: 96809f09efd068b80f04a70d4356c1ceaf5f113c
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422478"
---
# <a name="fc-full-path-of-source-code-file-in-diagnostics"></a>/FC (úplná cesta k souboru zdrojového kódu v diagnostice)

Způsobí, že kompilátor zobrazí úplnou cestu k souborům zdrojového kódu předaných do kompilátoru v diagnostice.

## <a name="syntax"></a>Syntaxe

> /FC

## <a name="remarks"></a>Poznámky

Vezměte v úvahu následující ukázka kódu:

```cpp
// compiler_option_FC.cpp
int main( ) {
   int i   // C2143
}
```

Bez **/FC**, by vypadalo podobně jako tento diagnostický text diagnostického textu:

- compiler_option_FC.cpp(5): chyba C2143: Chyba syntaxe: chybí ";" před "}"

S **/FC**, by vypadalo podobně jako tento diagnostický text diagnostického textu:

- c:\test\compiler_option_fc.cpp(5): chyba C2143: Chyba syntaxe: chybí ";" před "}"

**/FC** je také potřeba, pokud chcete zobrazit úplnou cestu název souboru při použití &#95; &#95;souboru&#95; &#95; – makro. Zobrazit [předdefinovaná makra](../../preprocessor/predefined-macros.md) Další informace o &#95; &#95;souboru&#95;&#95;.

**/FC** možnost předpokládá **/zi**. Další informace o **/zi**, naleznete v tématu [/Z7, / zi, /ZI (formát informací o ladění)](../../build/reference/z7-zi-zi-debug-information-format.md).

**/FC** výstupy úplné cesty v malými písmeny.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **Upřesnit** stránku vlastností.

1. Upravit **použít úplné cesty** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
