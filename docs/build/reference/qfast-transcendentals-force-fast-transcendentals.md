---
title: "-Qfast_transcendentals (vynutit rychlé Transcendentní objekty) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /Qfast_transcendentals
dev_langs: C++
helpviewer_keywords:
- /Qfast_transcendentals
- Force Fast Transcendentals
ms.assetid: 4de24bd1-38e6-49d4-9a05-04c9937d24ac
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6f5242621074f956c258957297bb1b220e086e70
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="qfasttranscendentals-force-fast-transcendentals"></a>/Qfast_transcendentals (Vynutit rychlé transcendentní objekty)
Generuje kód vložený přechodový funkcí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Qfast_transcendentals  
```  
  
## <a name="remarks"></a>Poznámky  
 Tato možnost kompilátoru vynutí přechodový funkce má být převeden na vloženého kódu, aby se zvýšila rychlost provádění. Tato možnost má vliv pouze v případě, že byl spárován s **/fp: kromě** nebo **/fp: přesné**. Generování kódu vloženého pro přechodový funkce je již výchozí chování v části **/fp:fast**.  
  
 Tato možnost není kompatibilní s **/fp: striktní**. V tématu [/fp (zadejte Floating-Point chování)](../../build/reference/fp-specify-floating-point-behavior.md) Další informace o plovoucí – možnosti kompilátoru bodu.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **C/C++** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Možnosti kompilátoru v typu **další možnosti** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [/Q – možnosti (operace nízké úrovně)](../../build/reference/q-options-low-level-operations.md)   
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)