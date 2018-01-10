---
title: "-FS (vynutit synchronní PDB zápisy) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /FS
dev_langs: C++
helpviewer_keywords:
- -FS compiler option [C++]
- /FS compiler option [C++]
ms.assetid: b2caaffe-f6e1-4963-b068-648f06b105e0
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cec8aa3d1b3417b6bfcb35757ac4a4a51961e16b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fs-force-synchronous-pdb-writes"></a>/FS (Vynutit synchronní zápisy do souboru PDB)
Vynutí zapisuje do souboru databáze (PDB) programu – vytvořené [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) nebo [/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)– k serializaci prostřednictvím MSPDBSRV. SOUBOR EXE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/FS  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení když **/Zi** nebo **/ZI** není zadaný, kompilátor zamkne soubory PDB zápis informací o typu a symbolické ladicí informace. To může výrazně snížit čas, který potřebuje kompilátoru generovat informace o typu při velký počet typů. Pokud jiný proces dočasně uzamkne soubor PDB – například antivirový program – zápisy kompilátorem může selhat a může dojít k závažné chybě. Tento problém může také dojít v případě více kopií cl.exe přistupovat ke stejnému souboru PDB – například pokud má vaše řešení nezávislé projekty, které používají stejné mezilehlé adresáře nebo výstupního adresáře, a paralelní sestavení jsou povolené. **/FS** zabrání kompilátoru zamykání soubor PDB – možnost kompilátoru a vynutí zápisy projít MSPDBSRV. Soubor EXE, který serializuje přístup. To může být výrazně delší sestavení a nezabrání všechny chyby, které mohou nastat při více instancí cl.exe přístup k souboru PDB ve stejnou dobu. Doporučujeme změnit řešení, tak, aby zápis nezávislé projekty k oddělení zprostředkující a výstupní umístění, nebo které jste si ho projektů závislá na druhé pro sestavení projektu platnost serializován.  
  
 [/MP](../../build/reference/mp-build-with-multiple-processes.md) možnost umožňuje **/FS** ve výchozím nastavení.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **C/C++** složky.  
  
3.  Vyberte **příkazového řádku** stránku vlastností.  
  
4.  Změnit **další možnosti** vlastnost, aby zahrnovala `/FS` a potom zvolte **OK**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)