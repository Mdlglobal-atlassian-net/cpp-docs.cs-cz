---
title: "-V (číslo verze) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /v
dev_langs: C++
helpviewer_keywords:
- embedding version strings
- /V compiler option [C++]
- version numbers, specifying for .obj
- V compiler option [C++]
- -V compiler option [C++]
ms.assetid: 3e93fb7a-5dfd-49a6-bd49-3dca8052e0f3
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8d206db7699b955d1440da53731d4c8574fdf81c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="v-version-number"></a>/V (Číslo verze)
Zastaralé Vloží textového řetězce v souboru .obj.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Vstring  
```  
  
## <a name="arguments"></a>Arguments  
 `string`  
 Řetězec určující číslo verze nebo o autorských právech, který má být vložen v souboru .obj.  
  
## <a name="remarks"></a>Poznámky  
 Popisek stringcan souboru .obj číslo verze nebo o autorských právech. Znaky místa nebo kartě musí být uzavřena v uvozovkách ("), pokud jsou součástí řetězec. Zpětné lomítko (\\) musí předcházet žádné uvozovky, pokud jsou součástí řetězec. Mezery mezi **/V** a `string` je volitelný.  
  
 Můžete také použít [komentáře (C/C++)](../../preprocessor/comment-c-cpp.md) s argumentem typu komentáře kompilátoru umístit název a číslo verze kompilátoru v souboru .obj.  
  
 **/V** možnost je zastaralé od verze Visual Studio 2005; **/V** se primárně používají k zajištění podpory vytvoření virtuální ovladače zařízení (VxD) a vytváření ovladače VxD se už nepodporuje sady nástrojů Visual C++. Seznam – možnosti kompilátoru zastaralé, najdete v části **zastaralé a odebrat – možnosti kompilátoru** v [kompilátoru možnosti uvedené podle kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Možnosti kompilátoru v typu **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)