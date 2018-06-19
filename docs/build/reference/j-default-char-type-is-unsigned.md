---
title: -J (výchozí znakový typ není podepsán) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned
- VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned
- /j
dev_langs:
- C++
helpviewer_keywords:
- defaults, char type
- char data type
- -J compiler option [C++]
- /J compiler option [C++]
- J compiler option [C++]
- default char type is unsigned
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a93172296b0e2e6d54dc428ffc62812ad979b160
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374463"
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
 [Práce s vlastnostmi projektu](../../ide/working-with-project-properties.md)