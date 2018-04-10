---
title: -F (nastavení velikosti zásobníku) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5b464a4fb28eb83ef0570416d0cb18fd8f965e0a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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