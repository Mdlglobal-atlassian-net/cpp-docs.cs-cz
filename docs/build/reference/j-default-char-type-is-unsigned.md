---
title: "-J (výchozí znakový typ není podepsán) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned
- VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned
- /j
dev_langs: C++
helpviewer_keywords:
- defaults, char type
- char data type
- -J compiler option [C++]
- /J compiler option [C++]
- J compiler option [C++]
- default char type is unsigned
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6a49220bf5ee4d990096140f4b2139992b03ad95
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="j-default-char-type-is-unsigned"></a>/J (Výchozí znakový typ není podepsán)
Změní výchozí `char` typu z `signed char` k `unsigned char`a `char` typ se rozšířené nula. Pokud je rozšířit do `int` typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/J  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud `char` hodnota je explicitně deklarován jako `signed`, **/J** možnost neovlivňuje a hodnota je s rozšířeným při je rozšířit do `int` typu.  
  
 **/J** možnost definuje `_CHAR_UNSIGNED`, který se používá s `#ifndef` v souboru Limits.h – definujte rozsah výchozí `char` typu.  
  
 ANSI C a C++ nevyžadují na konkrétní implementace `char` typu. Tato možnost je užitečná při práci s daty znak, který se nakonec převedeny do jiného jazyka než angličtiny.  
  
> [!NOTE]
>  Pokud použijete tuto možnost kompilátoru pomocí knihovny ATL a MFC, může být generována chyba. I když se tato chyba může zakázat tak, že definujete `_ATL_ALLOW_CHAR_UNSIGNED`, toto řešení není podporována a nemusí vždy fungovat.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  V **Průzkumníku řešení**, otevřete místní nabídky projektu a zvolte **vlastnosti**.  
  
2.  V projektu **stránky vlastností** dialogové okno, v levém podokně v části **vlastnosti konfigurace**, rozbalte položku **C/C++** a pak vyberte **příkazového řádku**.  
  
3.  V **další možnosti** podokně, zadejte **/J** – možnost kompilátoru.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [Práce s vlastnostmi projektu](../../ide/working-with-project-properties.md)