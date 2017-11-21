---
title: "-CLRIMAGETYPE (zadat typ obrázku CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
dev_langs: C++
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6f11684f71e874d2dbb439ed1f9dfc46b543a63e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (Zadat typ obrázku CLR)
```  
/CLRIMAGETYPE:{IJW|PURE|SAFE|SAFE32BITPREFERRED}  
```  
  
## <a name="remarks"></a>Poznámky  
 Linkeru přijme nativních objektů a také MSIL objekty, které jsou kompilovaná pomocí [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), / CLR: pure, nebo/CLR: safe. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015. Při předávání smíšený objektů ve stejném sestavení, je, ověřitelnosti výsledné výstupního souboru, ve výchozím nastavení rovna nejnižší úroveň ověřitelnosti vstupní modulů. Například pokud předat sejfu i modul čistý linkeru výstupní soubor bude čistý. Pokud předáte nativní image a image ve smíšeném režimu (zkompilovat pomocí **/CLR**), bude výsledný obraz bitové kopie ve smíšeném režimu.  
  
 /CLRIMAGETYPE slouží k určení s nižší úrovní ověřitelnosti, pokud je to, co potřebujete.  
  
 V rozhraní .NET 4.5 podporuje /CLRIMAGETYPE SAFE32BITPREFERRED možnost. Nastaví tato – v záhlaví PE Image – příznaky, které znamenat, že objekty MSIL jsou bezpečné a lze spustit na všech platformách, ale, že spuštění 32bitové prostředí jsou upřednostňované. Tato možnost umožňuje aplikace běžet na platformách ARM a také určuje, že se má spustit WOW64 na 64bitové operační systémy místo použití prostředí pro spuštění 64-bit.  
  
 Když .exe byl kompilován s použitím **/CLR** nebo **/CLR: pure** běží na 64bitový operační systém, je aplikace spuštěna v rámci WOW64, která umožňuje 32bitová aplikace ke spuštění na 64bitový operační systém. Ve výchozím nastavení .exe kompiluje pomocí **/CLR: safe** běží v rámci podpory 64bitová verze operačního systému. Je však možné, že aplikace bezpečné načte komponentu 32-bit. V takovém případě bitovou kopii bezpečné spuštění v rámci podpory 64bitová verze operačního systému se nezdaří, když načte 32bitovou aplikaci. Aby se zajistilo, že bezpečné bitové kopie i nadále spouštět, když ho načte 32bitové součást na 64bitový operační systém, použijte možnost /CLRIMAGETYPE:SAFE32BITPREFERRED. Pokud váš kód nemá běžet na platformách ARM, můžete zadat /CLRIMAGETYPE: PURE možnost změny metadata (.corflags), označení, aby byla spuštěna WOW64 (a nahraďte vlastní symbol vstupního):  
  
 **cl/CLR: safe t.cpp/Link /clrimagetype: pure /entry:?main@@$$HYMHXZ /subsystem:console**  
  
 Informace o tom, jak určit typ obrázku CLR souboru najdete v tématu [/CLRHEADER](../../build/reference/clrheader.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **Linkeru** uzlu.  
  
4.  Vyberte **Upřesnit** stránku vlastností.  
  
5.  Změnit **typ obrázku CLR** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)