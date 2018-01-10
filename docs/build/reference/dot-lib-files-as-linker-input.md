---
title: . Lib soubory jako vstup Linkeru | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCLinkerTool.AdditionalDependencies
dev_langs: C++
helpviewer_keywords:
- OMF libraries
- linking [C++], OMF libraries
- import libraries, linker files
- libraries [C++], .lib files as linker input
- COFF files, import libraries
- default libraries [C++], linker output
- default libraries [C++]
- defaults [C++], libraries
- .lib files
ms.assetid: dc5d2b1c-2487-41fa-aa71-ad1e0647958b
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 181c8c3e5e762f2f20d99ca2acadaf285e717b6c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="lib-files-as-linker-input"></a>Soubory .Lib jako vstup linkeru
ODKAZ přijímá standardní knihoven COFF a COFF importovat knihovny, které obvykle mají příponu. lib. Standardní knihovny obsahovat objekty a jsou vytvořené pomocí nástroje LIB. Import knihovny obsahují informace o export v ostatních aplikacích a vytvoří se buď odkaz k sestavení program, který obsahuje exportuje nebo nástrojem LIB. Informace o používání LIB vytvořit standardní nebo importovat knihovny najdete v tématu [LIB odkaz](../../build/reference/lib-reference.md). Podrobnosti o použití odkaz k vytvoření knihovnu importu najdete v tématu [/dll](../../build/reference/dll-build-a-dll.md) možnost.  
  
Knihovny je odkaz na zadaný jako argument názvu souboru nebo výchozí knihovna. ODKAZ přeloží externí odkazy tak, že nejprve v knihovnách zadat na příkazovém řádku a potom ve výchozích knihovny zadaným [/DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md) možnost, a potom ve výchozích knihovny s názvem v soubory .obj. Pokud je cesta zadána s název knihovny, hledá odkaz knihovny v tomto adresáři. Pokud není zadána žádná cesta, odkaz vypadá první v adresáři, odkaz se službou z a pak v všechny adresáře určeném v proměnné prostředí LIB.  
  
## <a name="to-add-lib-files-as-linker-input-in-the-development-environment"></a>Chcete-li přidat soubory .lib jako vstup linkeru ve vývojovém prostředí  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **vstup** stránka vlastností v **Linkeru** složky.  
  
3.  Změnit **Další závislosti** vlastnost přidat soubory .lib.  
  
## <a name="to-programmatically-add-lib-files-as-linker-input"></a>Chcete-li prostřednictvím kódu programu přidat soubory .lib jako vstup linkeru  
  
-   V tématu [AdditionalDependencies](https://msdn.microsoft.com/library/microsoft.visualstudio.vcprojectengine.vclinkertool.additionaldependencies.aspx).  
  
## <a name="example"></a>Příklad  
Následující příklad ukazuje, jak vytvářet a používat soubor LIB. Nejprve vytvoříte soubor LIB:  
  
```cpp  
// lib_link_input_1.cpp  
// compile by using: cl /LD lib_link_input_1.cpp  
__declspec(dllexport) int Test() {  
   return 213;  
}  
```  
  
A pak tato ukázka zkompilovat pomocí .lib soubor, který jste právě vytvořili:  
  
```cpp  
// lib_link_input_2.cpp  
// compile by using: cl /EHsc lib_link_input_1.lib lib_link_input_2.cpp   
__declspec(dllimport) int Test();  
#include <iostream>  
int main() {  
   std::cout << Test() << std::endl;  
}  
```  
  
```Output  
213  
```  
  
## <a name="see-also"></a>Viz také  
 [Vstupní soubory LINK](../../build/reference/link-input-files.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)