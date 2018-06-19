---
title: -FC (úplná cesta k souboru zdrojového kódu v diagnostice) | Microsoft Docs
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
ms.openlocfilehash: 4a721b6887b6c5c07d96a79b06f05e6d7855250b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373202"
---
# <a name="fc-full-path-of-source-code-file-in-diagnostics"></a>/FC (úplná cesta k souboru zdrojového kódu v diagnostice)

Způsobí, že kompilátor zobrazit úplnou cestu předaný kompilátoru v diagnostice soubory zdrojového kódu.

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

Bez **/FC**, diagnostiky text by vypadat podobně jako tento diagnostický text:

- compiler_option_FC.cpp(5): chyba C2143: Chyba syntaxe: chybějící ';' než '}'

S **/FC**, diagnostiky text by vypadat podobně jako tento diagnostický text:

- c:\test\compiler_option_fc.cpp(5): chyba C2143: Chyba syntaxe: chybějící ';' než '}'

 **/FC** je také nutný v případě, že chcete zobrazit úplnou cestu název souboru, při použití &#95; &#95;soubor&#95; &#95; makro. V tématu [předdefinovaná makra](../../preprocessor/predefined-macros.md) Další informace o &#95; &#95;soubor&#95;&#95;.

**/FC** možnost je zahrnuto v **/ZI**. Další informace o **/ZI**, najdete v části [/Z7, / zi, /ZI (formát informace ladění)](../../build/reference/z7-zi-zi-debug-information-format.md).

**/FC** výstupy úplné cesty ve malá písmena.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **Upřesnit** stránku vlastností.

1. Změnit **použití úplné cesty** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)   
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
