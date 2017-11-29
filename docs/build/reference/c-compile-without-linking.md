---
title: "-c (Kompilovat bez propojení) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /c
dev_langs: C++
helpviewer_keywords:
- suppress link
- cl.exe compiler, compiling without linking
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 8017fc3d-e5dd-4668-a1f7-3120daa95d20
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a8f10aef6c2907d0730d358a6471c17bfd6a4cf8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-compile-without-linking"></a>/c (kompilovat bez propojení)
Brání automatické volání odkaz.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/c  
```  
  
## <a name="remarks"></a>Poznámky  
 Kompilování pomocí **/c** vytvoří pouze soubory .obj. ODKAZ musí volat explicitně s správné soubory a možnosti pro fázi vytváření sestavení.  
  
 Používá interní projekt ve vývojovém prostředí **/c** možnost ve výchozím nastavení.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
-   Tato možnost není k dispozici ve vývojovém prostředí.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   Pokud chcete nastavit tuto možnost kompilátoru prostřednictvím kódu programu, najdete v části <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileOnly%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příkaz vytvoří objekt soubory FIRST.obj a SECOND.obj. THIRD.obj se ignoruje.  
  
```  
CL /c FIRST.C SECOND.C THIRD.OBJ  
```  
  
 Pokud chcete vytvořit spustitelný soubor, je nutné vyvolat odkaz:  
  
```  
LINK firsti.obj second.obj third.obj /OUT:filename.exe  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)