---
title: -EXPORT (Export funkce) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.ExportFunctions
- /export
dev_langs: C++
helpviewer_keywords:
- /EXPORT linker option
- EXPORT linker option
- -EXPORT linker option
ms.assetid: 0920fb44-a472-4091-a8e6-73051f494ca0
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0d3b1dd8f3bac22fc2359b447a69f42d7bcfafdb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="export-exports-a-function"></a>/EXPORT (export funkce)
```  
/EXPORT:entryname[,@ordinal[,NONAME]][,DATA]  
```  
  
## <a name="remarks"></a>Poznámky  
 Pomocí této možnosti můžete exportovat funkce z vaší aplikace tak, aby ostatní programy můžete volat funkci. Můžete také exportovat data. Exportuje jsou obvykle definovány v knihovně DLL.  
  
 *Název_položky* je název položky funkce nebo data, jako je které volací program používat. `ordinal`Určuje index do tabulky exportuje v rozsahu od 1 do 65 535; Pokud nezadáte `ordinal`, odkaz přiřadí jeden. **NONAME** – klíčové slovo exportuje funkce pouze jako pořadí, bez *Název_položky*.  
  
 **DATA** – klíčové slovo určuje, že je položka exportovaný datové položky. Datová položka v programu klienta musí být deklarován pomocí **deklarace __declspec(dllimport) extern**.  
  
 Existují tři metody pro export definici uvedené v doporučené pořadí podle používání:  
  
1.  [__declspec(dllexport)](../../cpp/dllexport-dllimport.md) ve zdrojovém kódu  
  
2.  [EXPORTUJE](../../build/reference/exports.md) – příkaz souboru .def  
  
3.  Specifikace/export v příkazu odkaz  
  
 Všechny tři metody lze použít ve stejný program. Při propojení sestavení program, který obsahuje exportuje, vytvoří také knihovnu importu, pokud soubor .exp není použit v sestavení.  
  
 ODKAZ používá dekorované formy identifikátory. Kompilátor upraví identifikátor při vytváření souboru .obj. Pokud *Název_položky* je určena k linkeru v jeho upraveného formuláři (jak se objevuje v zdrojový kód), odkaz se pokusí o porovnání název. Pokud nemůže najít jedinečný shoda, vydá odkaz chybovou zprávu. Použití [DUMPBIN](../../build/reference/dumpbin-reference.md) nástroj získat [dekorované názvy](../../build/reference/decorated-names.md) formuláře identifikátoru, pokud je třeba zadat linkeru.  
  
> [!NOTE]
>  Nezadávejte dekorované formu identifikátory jazyka C, které jsou deklarovány `__cdecl` nebo `__stdcall`.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **příkazového řádku** stránku vlastností.  
  
4.  Zadejte možnost do **další možnosti** pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)