---
title: -vmb, - vmg (metoda reprezentace) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /vmb
- /vmg
dev_langs: C++
helpviewer_keywords:
- vmb compiler option [C++]
- -vmg compiler option [C++]
- vmg compiler option [C++]
- -vmb compiler option [C++]
- /vmb compiler option [C++]
- representation method compiler options [C++]
- /vmg compiler option [C++]
ms.assetid: ecdb391c-7dab-40b1-916b-673d10889fd4
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4a9d64f8b1035f731adef79356d24eeb3e4f7ee3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="vmb-vmg-representation-method"></a>/vmb, /vmg (metoda reprezentace)
Vyberte metodu, kterou kompilátor používá k reprezentaci ukazatelů na členy třídy.  
  
 Použití **/vmb** Pokud vždy před je definovat třídu deklarovat ukazatele na člena třídy.  
  
 Použití **/vmg** deklarovat ukazatele na člena třídy před definováním třídy. Pokud definujete členy v dvěma různými třídami, které odkazují na sobě navzájem, může dojít k tohoto požadavku. Pro tyto třídy vzájemně odkazující musí odkazovat jednu třídu dříve, než je definován.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/vmb  
/vmg  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete také použít [pointers_to_members –](../../preprocessor/pointers-to-members.md) nebo [klíčová slova dědičnosti](../../cpp/inheritance-keywords.md) ve vašem kódu k určení znázornění ukazatele.  
  
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