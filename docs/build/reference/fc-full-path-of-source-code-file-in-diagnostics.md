---
title: -FC (úplná cesta k souboru zdrojového kódu v diagnostice) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UseFullPaths
- /FC
dev_langs:
- C++
helpviewer_keywords:
- /FC compiler option [C++]
- -FC compiler option [C++]
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d34fe85354d218d2499dbece70964c2e55e2592
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702704"
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

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
