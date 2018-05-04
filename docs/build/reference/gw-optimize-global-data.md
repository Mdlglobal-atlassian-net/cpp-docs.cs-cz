---
title: -Gw (optimalizovat globální Data) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Gw
dev_langs:
- C++
helpviewer_keywords:
- /Gw compiler option [C++]
- -Gw compiler option [C++]
ms.assetid: 6f90f4e9-5eb8-4c47-886e-631278a5a4a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 173b9499477ee02cbb1f052d3d85445a9ffb7732
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="gw-optimize-global-data"></a>/Gw (Optimalizovat globální data)
Globální data balíčku v částech sekvence COMDAT pro optimalizaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Gw[-]  
```  
  
## <a name="remarks"></a>Poznámky  
 **/Gw** možnost způsobí, že kompilátor globální data balíčku v jednotlivých částech sekvence COMDAT. Ve výchozím nastavení **/Gw** je vypnutý a musí být explicitně povolené. Chcete-li jej explicitně zakázat, použijte **/Gw-**. Pokud obě **/Gw** a [/GL](../../build/reference/gl-whole-program-optimization.md) jsou povolené, linkeru používá k porovnání sekvence COMDAT části napříč více soubory objektů, aby bylo možné vyloučit neregistrované globální data nebo sloučit optimalizace celého programu identické jen pro čtení globální data. To může výrazně snížit velikost výsledný binární soubor spustitelný soubor.  
  
 Při kompilování a propojit samostatně, můžete použít [/OPT:REF](../../build/reference/opt-optimizations.md) – možnost linkeru chcete vyloučit z neregistrované globální data v souborech objekt kompilovat s spustitelný soubor **/Gw** možnost.  
  
 Můžete také [/OPT:ICF](../../build/reference/opt-optimizations.md) a [/ltgc](../../build/reference/ltcg-link-time-code-generation.md) možnosti linkeru dohromady a merge v jakékoli identické jen pro čtení globální data napříč více souborů objekt kompilovat s spustitelný soubor **/Gw** možnost.  
  
 Další informace najdete v tématu [představení /Gw přepínače kompilátoru](http://blogs.msdn.com/b/vcblog/archive/2013/09/11/introducing-gw-compiler-switch.aspx) na blogu týmu Visual C++.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **C/C++** složky.  
  
3.  Vyberte **příkazového řádku** stránku vlastností.  
  
4.  Změnit **další možnosti** vlastnost, aby zahrnovala **/Gw** a potom zvolte **OK**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)