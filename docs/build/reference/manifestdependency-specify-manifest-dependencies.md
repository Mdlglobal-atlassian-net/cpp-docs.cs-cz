---
title: "-MANIFESTDEPENDENCY (určit závislosti manifestu) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCLinkerTool.AdditionalManifestDependencies
dev_langs: C++
helpviewer_keywords:
- MANIFESTDEPENDENCY linker option
- /MANIFESTDEPENDENCY linker option
- -MANIFESTDEPENDENCY linker option
ms.assetid: e4b68313-33a2-4c3e-908e-ac2b9f7d6a73
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 070adfa51103d2ab91b371918107aa432ee5aa70
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="manifestdependency-specify-manifest-dependencies"></a>/MANIFESTDEPENDENCY (Určit závislosti manifestu)
```  
/MANIFESTDEPENDENCY:manifest_dependency  
```  
  
## <a name="remarks"></a>Poznámky  
 / MANIFESTDEPENDENCY umožňuje určit atributy, které bude uložena v umístění \<závislostí > konfiguračního souboru manifestu.  
  
 V tématu [/MANIFEST (Manifest vytvořit-souběžného sestavení)](../../build/reference/manifest-create-side-by-side-assembly-manifest.md) informace o tom, jak vytvořit soubor manifestu.  
  
 Další informace o \<závislostí > části souboru manifestu, najdete v části [vydavatele konfigurační soubory](http://msdn.microsoft.com/library/aa375682).  
  
 / MANIFESTDEPENDENCY informace se dá předat do linkeru v jednom ze dvou způsobů:  
  
-   Přímo na příkazový řádek (nebo soubor odezvy) s /MANIFESTDEPENDENCY.  
  
-   Prostřednictvím [komentář](../../preprocessor/comment-c-cpp.md) – Direktiva pragma.  
  
 Následující příklad ukazuje komentář /MANIFESTDEPENDENCY předány prostřednictvím – Direktiva pragma,  
  
```  
#pragma comment(linker, "\"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"")  
```  
  
 Výsledkem následující položku v souboru manifestu:  
  
```  
<dependency>  
  <dependentAssembly>  
    <assemblyIdentity type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*' />  
  </dependentAssembly>  
</dependency>  
```  
  
 Stejné /MANIFESTDEPENDENCY komentáře lze předat v příkazovém řádku následujícím způsobem:  
  
```  
"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"  
```  
  
 Linkeru bude shromažďovat /MANIFESTDEPENDENCY komentáře, odstranění duplicitních záznamů a pak přidejte výsledný řetězec XML do souboru manifestu.  Pokud linkeru vyhledá konfliktních záznamů, v souboru manifestu se stane poškozen a aplikace se nepodaří spustit (položka lze přidat do protokolu událostí, označující zdroj selhání).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **Linkeru** uzlu.  
  
4.  Vyberte **souboru Manifest** stránku vlastností.  
  
5.  Změnit **Další závislosti manifestu** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)