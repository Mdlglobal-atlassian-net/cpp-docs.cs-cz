---
title: "-cgthreads (vlákna generování kódu) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /cgthreads
dev_langs: C++
helpviewer_keywords:
- /cgthreads compiler option (C++)
- -cgthreads compiler option (C++)
- cgthreads compiler option (C++)
- cgthreads
ms.assetid: 64bc768c-6caa-4baf-9dea-7cfa1ffb01c2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 846e59b0c1303e70e4ed38b43e4869f1f044f64f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cgthreads-code-generation-threads"></a>/cgthreads (Vlákna generování kódu)
Nastaví počet vláken cl.exe pro optimalizaci a generování kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/cgthreads[1-8]  
```  
  
## <a name="arguments"></a>Arguments  
 číslo  
 Maximální počet vláken pro cl.exe pro použití v rozsahu 1 až 8.  
  
## <a name="remarks"></a>Poznámky  
 **/Cgthreads** možnost určuje maximální počet vláken cl.exe používá paralelně pro optimalizaci a kód generování fáze kompilace. Všimněte si, že může být žádné mezery mezi **/cgthreads** a `number` argument. Ve výchozím nastavení používá cl.exe čtyři vláken, jako kdyby **/cgthreads4** byly zadány. Pokud jsou k dispozici více jader procesoru větší `number` hodnotu můžete vylepšovat dobu sestavení. Tato možnost je obzvláště užitečná při kombinaci s [/GL (optimalizace celého programu)](../../build/reference/gl-whole-program-optimization.md).  
  
 Více úrovní paralelismus lze zadat pro sestavení. Přepínač msbuild.exe **/maxcpucount** určuje počet MSBuild procesy, které můžou běžet souběžně. [/MP (sestavení pomocí několika procesů)](../../build/reference/mp-build-with-multiple-processes.md) kompilátoru příznak určuje počet cl.exe procesy, které současně zkompilovat zdrojové soubory. **/Cgthreads** možnost určuje počet vláken používaných každý cl.exe procesem. Protože procesor může být spuštěna pouze libovolný počet vláken ve stejnou dobu jako jader procesoru, není užitečné k určení vyšší hodnoty pro všechny tyto možnosti ve stejnou dobu a může být kontraproduktivní. Další informace o tom, jak sestavit paralelně najdete v tématu [sestavování více projektů současně](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **vlastnosti konfigurace**, **C/C++** složky.  
  
3.  Vyberte **příkazového řádku** stránku vlastností.  
  
4.  Změnit **další možnosti** vlastnost, aby zahrnovala **/cgthreads**`N`, kde `N` je hodnotu od 1 do 8 a potom vyberte **OK**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)