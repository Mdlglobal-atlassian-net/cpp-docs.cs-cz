---
title: "-CLRTHREADATTRIBUTE (atribut vlákna modulu CLR sada) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCLinkerTool.CLRThreadAttribute
dev_langs: C++
helpviewer_keywords:
- /CLRTHREADATTRIBUTE linker option
- -CLRTHREADATTRIBUTE linker option
ms.assetid: 4907e9ef-5031-446c-aecf-0a0b32fae1e8
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e928d24c6257bc64303d667e66cd1f968e003450
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="clrthreadattribute-set-clr-thread-attribute"></a>/CLRTHREADATTRIBUTE (Nastavit atribut vlákna modulu CLR)
Zadejte explicitně atribut vláken pro vstupní bod aplikace CLR.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/CLRTHREADATTRIBUTE:{STA|MTA|NONE}  
```  
  
#### <a name="parameters"></a>Parametry  
 PROSTŘEDÍ MTA  
 Atribut MTAThreadAttribute platí pro vstupní bod aplikace.  
  
 NONE  
 Stejné jako není zadání /CLRTHREADATTRIBUTE.  Umožňuje CLR Common Language Runtime () nastavit výchozí atribut vlákna.  
  
 STA  
 Atribut STAThreadAttribute platí pro vstupní bod aplikace.  
  
## <a name="remarks"></a>Poznámky  
 Nastavení atribut vlákna je platný pouze při vytváření .exe, protože to nepříznivě ovlivňuje vstupní bod hlavního vlákna.  
  
 Pokud použijete výchozí vstupní bod (hlavní nebo wmain, např.) zadejte model vláken buď pomocí /CLRTHREADATTRIBUTE nebo tím, že dělení na vlákna atribut (STAThreadAttribute nebo MTAThreadAttribute) na funkci výchozí položku.  
  
 Pokud používáte jiné než výchozí vstupní bod, zadejte model vláken buď pomocí /CLRTHREADATTRIBUTE nebo tím, že dělení na vlákna atribut na funkci jiné než výchozí položku a pak zadejte jiné než výchozí vstupní bod s [/Entry](../../build/reference/entry-entry-point-symbol.md) .  
  
 Pokud model vláken zadaný ve zdrojovém kódu nesouhlasí s modelem vláken zadaným /CLRTHREADATTRIBUTE, linkeru bude ignorovat /CLRTHREADATTRIBUTE a použít model vláken zadaný ve zdrojovém kódu.  
  
 Bude potřeba k použití jednoho vlákna, například, pokud váš program CLR hostuje objekt COM, který používá jedním threading.  Pokud vaše CLR program používá více vláken, nemůže být hostitelem objektu COM, který používá jedním threading.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **Linkeru** uzlu.  
  
4.  Vyberte **Upřesnit** stránku vlastností.  
  
5.  Změnit **atribut vlákna modulu CLR** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRThreadAttribute%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)