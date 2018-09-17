---
title: . Lib soubory jako vstup Linkeru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalDependencies
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 774fe236b66bbe6222956de05efbfe89fab3de9f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706495"
---
# <a name="lib-files-as-linker-input"></a>Soubory .Lib jako vstup linkeru

ODKAZ přijímá standardních knihoven COFF a COFF import knihoven, které obvykle s příponou. lib. Standardní knihovny obsahují objekty a jsou vytvářeny nástroj LIB. Import knihovny obsahují informace o exportech v jiných aplikacích a vytvoří se buď podle propojení vytvoří program, který obsahuje exporty nebo nástroj LIB. Informace o používání LIB vytvořit standardní nebo importovat knihovny najdete v tématu [LIB Reference](../../build/reference/lib-reference.md). Podrobnosti o použití odkazu pro vytvoření knihovny importu, najdete v článku [/dll](../../build/reference/dll-build-a-dll.md) možnost.

Knihovny je zadán odkaz jako argument název souboru nebo výchozí knihovny. ODKAZ překladu externích odkazů tak, že nejprve v knihovnách zadané na příkazovém řádku a potom ve výchozích knihoven zadaným [/DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md) možnost, a potom ve výchozích knihoven s názvem v souborech .obj. Pokud je cesta zadaná s parametrem knihovnu s názvem, hledá odkaz knihovny v tomto adresáři. Pokud není zadaná žádná cesta, odkaz vyhledá první v adresáři, propojení se službou z a pak v jakékoli adresáře určené v proměnné prostředí LIB.

## <a name="to-add-lib-files-as-linker-input-in-the-development-environment"></a>Chcete-li přidat soubory .lib jako vstup linkeru ve vývojovém prostředí

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Zvolte **vstup** stránku vlastností v **Linkeru** složky.

1. Upravit **Další závislosti** vlastnost přidat soubory .lib.

## <a name="to-programmatically-add-lib-files-as-linker-input"></a>Chcete-li programově přidat soubory .lib jako vstup linkeru

- Zobrazit [AdditionalDependencies](https://msdn.microsoft.com/library/microsoft.visualstudio.vcprojectengine.vclinkertool.additionaldependencies.aspx).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvářet a používat soubor LIB. Nejdříve vytvořte souborů .lib:

```cpp
// lib_link_input_1.cpp
// compile by using: cl /LD lib_link_input_1.cpp
__declspec(dllexport) int Test() {
   return 213;
}
```

A zkompilujte tuto ukázku s použitím .lib soubor, který jste právě vytvořili:

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

[Vstupní soubory LINK](../../build/reference/link-input-files.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)