---
title: "-FC (úplná cesta k souboru zdrojového kódu v diagnostice) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.UseFullPaths
- /FC
dev_langs: C++
helpviewer_keywords:
- /FC compiler option [C++]
- -FC compiler option [C++]
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c9c612dfa300ff42d90988edb77601619fdd4b3c
ms.sourcegitcommit: ce115fcfb20b4fbc198f0f7b6d0ca3e94d7ce947
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2017
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

- c:\test\compiler_option_FC.cpp(5): chyba C2143: Chyba syntaxe: chybějící ';' než '}'

**/FC** je také nutný v případě, že chcete zobrazit úplnou cestu název souboru, při použití &#95; &#95; SOUBOR &#95; &#95; makro.  V tématu [předdefinovaná makra](../../preprocessor/predefined-macros.md) pro další informace o &#95; &#95; SOUBOR &#95; &#95;.

**/FC** možnost je zahrnuto v **/ZI**. Další informace o **/ZI**, najdete v části [/Z7, / zi, /ZI (formát informace ladění)](../../build/reference/z7-zi-zi-debug-information-format.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace** uzlu.

1. Rozbalte **C/C++** uzlu.

1. Vyberte **Upřesnit** stránku vlastností.

1. Změnit **použití úplné cesty** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)   
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)