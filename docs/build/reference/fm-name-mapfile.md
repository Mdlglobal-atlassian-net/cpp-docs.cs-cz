---
title: "-Fm (název souboru mapování) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /fm
dev_langs: C++
helpviewer_keywords:
- -Fm compiler option [C++]
- mapfiles [C++], creating linker
- files [C++], creating map
- Fm compiler option [C++]
- /Fm compiler option [C++]
ms.assetid: 8154448a-93a7-4546-8e4c-5c44d0aff45d
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 153a91d25a45a86f01885b679f039f41390dc291
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fm-name-mapfile"></a>/Fm (název souboru mapování)
Informuje linkeru k vytvoření mapfile, který obsahuje seznam segmentů v pořadí, ve kterém se zobrazují v odpovídající soubor .exe nebo knihovny DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Fmpathname  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, je zadána souboru mapování základní název odpovídající jazyka C nebo C++ zdrojový soubor s. MAPOVÁNÍ rozšíření.  
  
 Určení **/Fm** funguje stejně, jako kdyby byl zadán [/map (Generovat soubor mapování)](../../build/reference/map-generate-mapfile.md) – možnost linkeru.  
  
 Pokud zadáte [/c (Kompilovat bez propojení)](../../build/reference/c-compile-without-linking.md) potlačit propojení, **/Fm** nemá žádný vliv.  
  
 Globální symboly v souboru mapování obvykle mají jeden nebo více úvodní podtržítka, protože kompilátor přidá úvodní podtržítka názvy proměnných. Mnoho globální symboly, které se zobrazují v souboru mapování se používá interně kompilátor a standardní knihovny.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Možnosti kompilátoru v typu **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Výstupního souboru (/ F) možnosti](../../build/reference/output-file-f-options.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [Určení názvu cesty](../../build/reference/specifying-the-pathname.md)