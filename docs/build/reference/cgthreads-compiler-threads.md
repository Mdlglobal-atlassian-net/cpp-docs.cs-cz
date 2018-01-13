---
title: "-CGTHREADS (vlákna kompilátoru) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- /CGTHREADS linker option
- -CGTHREADS linker option
- CGTHREADS linker option
ms.assetid: 4b52cfdb-3702-470b-9580-fabeb1417488
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 542e35ecbb5e56ae0d13861b9885936f3b47c9da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cgthreads-compiler-threads"></a>/CGTHREADS (Vlákna kompilátoru)
Nastaví počet vláken cl.exe pro optimalizaci a generování kódu pokud je zadán parametr generování kódu v době propojování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/CGTHREADS:[1-8]  
```  
  
## <a name="arguments"></a>Arguments  
 číslo  
 Maximální počet vláken pro cl.exe pro použití v rozsahu 1 až 8.  
  
## <a name="remarks"></a>Poznámky  
 **/Cgthreads** možnost určuje maximální počet vláken cl.exe používá paralelně pro fáze optimalizace a generování kódu při propojování kompilace generování kódu ([/ltgc](../../build/reference/ltcg-link-time-code-generation.md)) je zadat. Ve výchozím nastavení používá cl.exe čtyři vláken, jako kdyby **/CGTHREADS:4** byly zadány. Pokud jsou k dispozici více jader procesoru větší `number` hodnotu můžete vylepšovat dobu sestavení.  
  
 Více úrovní paralelismus lze zadat pro sestavení. Přepínač msbuild.exe **/maxcpucount** určuje počet MSBuild procesy, které můžou běžet souběžně. [/MP (sestavení pomocí několika procesů)](../../build/reference/mp-build-with-multiple-processes.md) kompilátoru příznak určuje počet cl.exe procesy, které současně zkompilovat zdrojové soubory. [/Cgthreads](../../build/reference/cgthreads-code-generation-threads.md) – možnost kompilátoru určuje počet vláken používaných každý cl.exe procesem. Protože procesor může být spuštěna pouze libovolný počet vláken ve stejnou dobu jako jader procesoru, není užitečné k určení vyšší hodnoty pro všechny tyto možnosti ve stejnou dobu a může být kontraproduktivní. Další informace o tom, jak sestavit paralelně najdete v tématu [sestavování více projektů současně](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **vlastnosti konfigurace**, **Linkeru** složky.  
  
3.  Vyberte **příkazového řádku** stránku vlastností.  
  
4.  Změnit **další možnosti** vlastnost, aby zahrnovala **/cgthreads:**`number`, kde `number` je hodnotu od 1 do 8 a potom zvolte **OK**.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti linkeru](../../build/reference/linker-options.md)   
 [Nastavení možností linkeru](../../build/reference/setting-linker-options.md)