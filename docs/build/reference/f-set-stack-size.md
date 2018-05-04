---
title: -F (nastavení velikosti zásobníku) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /f
dev_langs:
- C++
helpviewer_keywords:
- set stack size compiler option
- F compiler option [C++]
- -F compiler option [C++]
- /F compiler option [C++]
- stack, setting size
ms.assetid: 17320b6f-8305-445b-9ec2-75833f4b29e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed0ad03d18493cc5618f9aad2a16b07e4a01717f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="f-set-stack-size"></a>/F (nastavení velikosti zásobníku)
Nastaví velikost zásobníku program v bajtech.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/F number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Velikost zásobníku v bajtech.  
  
## <a name="remarks"></a>Poznámky  
 Bez této možnosti výchozí velikost zásobníku 1 MB. `number` Argument může být v desetinné nebo jazyka C zápis. Argument musí být v rozsahu 1 až maximální velikost zásobníku akceptovat linkeru. Linkeru zaokrouhlí na nejbližší 4 bajtů zadanou hodnotu. Mezery mezi **/F** a `number` je volitelný.  
  
 Potřebujete zvětšete velikost zásobníku, pokud váš program získá zprávy přetečení zásobníku.  
  
 Můžete také nastavit velikost zásobníku pomocí:  
  
-   Pomocí **/zásobníku** – možnost linkeru. Další informace najdete v tématu [/zásobníku](../../build/reference/stack.md).  
  
-   Pomocí nástroje EDITBIN na soubor .exe. Další informace najdete v tématu [Editbin – odkaz](../../build/reference/editbin-reference.md).  
  
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