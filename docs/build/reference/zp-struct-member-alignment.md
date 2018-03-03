---
title: "-Zp (zarovnání členů struktury) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /zp
- VC.Project.VCCLCompilerTool.StructMemberAlignment
- VC.Project.VCCLWCECompilerTool.StructMemberAlignment
dev_langs:
- C++
helpviewer_keywords:
- Struct Member Alignment compiler option
- Zp compiler option
- /Zp compiler option [C++]
- -Zp compiler option [C++]
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d387e0ab020e96afb3e2975b5c8686b668cbc10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="zp-struct-member-alignment"></a>/Zp (zarovnání členů struktury)
Řídí, jak jsou členy struktury zabaleny do paměti a určuje stejné okolních pro všechny struktury v modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Zp[1|2|4|8|16]  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud určíte tuto možnost, každý člen struktura po první je uložený na velikost typ člena nebo `n`-hranice bajtů (kde `n` je 1, 2, 4, 8 nebo 16), než je menší.  
  
 Dostupné hodnoty jsou popsané v následující tabulce.  
  
 1  
 Balíčky struktury v rozsahu 1bajtů. Stejné jako **/Zp**.  
  
 2  
 Balíčky struktury na hranicích 2bajtová.  
  
 4  
 Balíčky struktury na hranicích 4bajtový.  
  
 8  
 Balíčky struktury na hranicích 8bajtový (výchozí).  
  
 16  
 Balíčky struktury na hranicích 16 bajtů.  
  
 Tuto možnost byste neměli používat, pokud máte požadavky na konkrétní souvislost.  
  
 Můžete také použít [pack](../../preprocessor/pack.md) k okolních struktura ovládacího prvku. Další informace o zarovnání naleznete v následujících tématech:  
  
-   [Zarovnat](../../cpp/align-cpp.md)  
  
-   [__alignof – operátor](../../cpp/alignof-operator.md)  
  
-   [__unaligned](../../cpp/unaligned.md)  
  
-   [Příklady zarovnání struktur](../../build/examples-of-structure-alignment.md) (x64 konkrétní)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **generování kódu** stránku vlastností.  
  
4.  Změnit **Strukturování členských přidružení** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)