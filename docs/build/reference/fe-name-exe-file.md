---
title: "-Fe (název souboru EXE) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /fe
dev_langs: C++
helpviewer_keywords:
- -Fe compiler option [C++]
- executable files, renaming
- rename file compiler option [C++]
- /Fe compiler option [C++]
- Fe compiler option [C++]
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b66c473c49527dff395d206594a314b527c4f914
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fe-name-exe-file"></a>/Fe (název souboru EXE)
Určuje název a adresář pro soubor .exe nebo knihovny DLL vytvořené kompilátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Fepathname  
```  
  
## <a name="remarks"></a>Poznámky  
 Bez této možnosti kompilátoru poskytuje soubor výchozí název pomocí základní název prvního zdroje nebo objekt souboru zadat na příkazovém řádku a příponou .exe nebo .dll.  
  
 Pokud zadáte[/c (Kompilovat bez propojení)](../../build/reference/c-compile-without-linking.md), kompilovat bez propojení, **/Fe** nemá žádný vliv.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **Obecné**stránku vlastností.  
  
4.  Změnit **výstupní soubor** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příkazový řádek zkompiluje a propojuje všechny zdrojové soubory C v aktuálním adresáři. Výsledný spustitelný soubor je s názvem PROCESS.exe a je vytvořen v adresáři C:\BIN.  
  
```  
CL /FeC:\BIN\PROCESS *.C  
```  
  
## <a name="example"></a>Příklad  
 Následující příkaz vytvoří spustitelný soubor v `C:\BIN` se stejným názvem základní jako první soubor zdroje nebo objekt:  
  
```  
CL /FeC:\BIN\ *.C  
```  
  
## <a name="see-also"></a>Viz také  
 [Výstupního souboru (/ F) možnosti](../../build/reference/output-file-f-options.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [Určení názvu cesty](../../build/reference/specifying-the-pathname.md)