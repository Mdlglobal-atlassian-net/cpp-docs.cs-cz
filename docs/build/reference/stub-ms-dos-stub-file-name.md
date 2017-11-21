---
title: "-STUB (název souboru zástupného kódu MS-DOS) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /stub
- VC.Project.VCLinkerTool.DosStub
dev_langs: C++
helpviewer_keywords:
- Win32 [C++], attaching MS-DOS stub program
- STUB linker option
- MS-DOS stub file name linker option
- /STUB linker option
- Windows API [C++], attaching MS-DOS stub program
- -STUB linker option
ms.assetid: 65221ffe-4f9a-4a14-ac69-3cfb79b40b5f
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 75d5d3d1eb362c893f3594e5d770111ddded01b9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="stub-ms-dos-stub-file-name"></a>/STUB (název souboru zástupného kódu MS-DOS)
```  
/STUB:filename  
```  
  
## <a name="remarks"></a>Poznámky  
 kde:  
  
 *Název souboru*  
 Aplikace, MS-DOS.  
  
## <a name="remarks"></a>Poznámky  
 Možnost/stub připojí programu zástupného kódu MS-DOS Win32 programu.  
  
 Program se zakázaným inzerováním je volána, pokud soubor je spuštěn v systému MS-DOS. Obvykle se zobrazí odpovídající zprávu; všechny platné MS-DOS aplikace však může být programem.  
  
 Zadejte *filename* programu se zakázaným inzerováním po dvojtečkou (:) na příkazovém řádku. Kontroly linkeru *filename* a chybové zprávy v případě, že soubor není spustitelný soubor. Program musí být soubor .exe; soubor .com je neplatný pro programem.  
  
 Pokud tato možnost se nepoužívá, připojí linkeru výchozí program se zakázaným inzerováním, která vydává se následující zpráva:  
  
```  
This program cannot be run in MS-DOS mode.  
```  
  
 Při sestavování ovladač virtuálního zařízení *filename* umožňuje uživateli zadat název souboru, který obsahuje strukturu IMAGE_DOS_HEADER (definovanou v WINNT. H) pro použití v ovladače VXD, nikoli výchozí záhlaví.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Zadejte možnost do **další možnosti** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)