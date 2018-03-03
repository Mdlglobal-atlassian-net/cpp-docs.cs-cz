---
title: -DLL (sestavit knihovnu DLL) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /dll
dev_langs:
- C++
helpviewer_keywords:
- -DLL linker option
- /DLL linker option [C++]
- exporting DLLs [C++], specifying exports
- DLLs [C++], building
- DLL linker option [C++]
ms.assetid: c7685aec-31d0-490f-9503-fb5171a23609
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 28a501590e127e5f27a465366611b4dbf3be175c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="dll-build-a-dll"></a>/DLL (Sestavit knihovnu DLL)
```  
/DLL  
```  
  
## <a name="remarks"></a>Poznámky  
 Možnost/DLL sestavení knihovny DLL jako hlavní výstupní soubor. Knihovny DLL obvykle obsahuje export, které lze použít v jiném programu. Existují tři metody pro určení exportů, uvedené v doporučené pořadí podle používání:  
  
1.  [__declspec(dllexport)](../../cpp/dllexport-dllimport.md) ve zdrojovém kódu  
  
2.  [EXPORTUJE](../../build/reference/exports.md) – příkaz souboru .def  
  
3.  [/EXPORT](../../build/reference/export-exports-a-function.md) specifikace v příkazu odkaz  
  
 Program můžete použít více než jednu metodu.  
  
 Je také možné sestavení knihovny DLL s **KNIHOVNY** příkaz definice modulu. Možnosti /BASE a/DLL společně odpovídají **KNIHOVNY** příkaz.  
  
 Neurčujte tuto možnost v rámci vývojového prostředí; Tato možnost je použít jenom na příkazovém řádku. Tato možnost nastavená při vytváření projektu knihovny DLL pomocí Průvodce aplikací.  
  
 Všimněte si, že když vytvoříte své knihovny importu v předběžný krok před vytvořením vaší .dll, je nutné předat stejnou sadu soubory objektů při sestavování .dll, jako předaný při sestavení knihovny importu.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **vlastnosti konfigurace** složky.  
  
3.  Klikněte **Obecné** stránku vlastností.  
  
4.  Změnit **typ konfigurace** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCPropertySheet.ConfigurationType%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)