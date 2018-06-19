---
title: -Gm (povolit minimální opětovné sestavení) | Microsoft Docs
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
ms.openlocfilehash: 7e0b83c34b0ff8cacbca9d21a40c6c9572f516d1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374567"
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm (Povolit minimální opětovné sestavení)
Umožňuje minimální opětovné sestavení, která určuje, jestli C++ zdrojové soubory, které zahrnují změněné definice tříd jazyka C++ (uložené v souborech hlavičky ()), který je potřeba zopakovat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Gm  
```  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor ukládá informace o závislostech mezi zdrojové soubory a definice tříd v souboru projektu IDB během první kompilace. (Informace o závislostech určen, které zdrojový soubor je závislá na které definice třídy, a které .h soubor definice nachází ve.) Následné zkompiluje informace uložené v souboru IDB pomůže určit, zda zdrojový soubor musí být zkompilovány, i v případě, že obsahuje soubor upravené h.  
  
> [!NOTE]
>  Minimální opětovné sestavení spoléhá na – třída definice není změna mezi zahrnout soubory. Definice tříd musí být globální pro projekt (měla by existovat pouze jednu definici dané třídy), protože informace o závislostech v souboru IDB je vytvořena pro celý projekt. Pokud máte více než jednu definici pro třídu do projektu, zakažte minimální opětovné sestavení.  
  
 Protože přírůstkové linkeru nepodporuje metadat Windows součástí soubory .obj pomocí [/ZW (kompilace Windows Runtime)](../../build/reference/zw-windows-runtime-compilation.md) možnost, **/Gm** možnost není kompatibilní s  **/ZW**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **generování kódu** stránku vlastností.  
  
4.  Změnit **povolit minimální opětovné sestavení** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)