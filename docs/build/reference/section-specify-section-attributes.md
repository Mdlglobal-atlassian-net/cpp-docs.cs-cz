---
title: "-ČÁST (určit atributy oddílu) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /section
dev_langs: C++
helpviewer_keywords:
- SECTION linker option
- -SECTION linker option
- section attributes
- /SECTION linker option
ms.assetid: 92b69d81-e421-462e-b46f-7d0dff9b9d16
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e3fd7e844d77b9a92408c0708542a4f8f5edf304
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="section-specify-section-attributes"></a>/SECTION (Určit atributy oddílu)
```  
/SECTION:name,[[!]{DEKPRSW}][,ALIGN=#]  
```  
  
## <a name="remarks"></a>Poznámky  
 Možnost /SECTION změní atributy oddílu, přepsání atributy nastavená, pokud bylo kompilováno souboru .obj pro oddíl.  
  
 Oddíl do přenosného spustitelného souboru (PE) je přibližně ekvivalentem segment nebo prostředky v nové spustitelný soubor (NE). Části obsahují kódu nebo data. Na rozdíl od segmenty oddíly jsou bloky souvislé paměti s žádné omezení velikosti. Některé části obsahují kód nebo data, která váš program deklarovaný a používá přímo, zatímco ostatní datové části jsou pro vás vytvořené linkeru a Správce knihovny (lib.exe) a obsahují informace, které jsou zásadní pro operační systém. Další informace o NE soubory najdete v článku znalostní báze "Formát hlavičky souboru spustitelný soubor" (Q65122). Články znalostní báze můžete vyhledat v MSDN nebo v [http://support.microsoft.com](http://support.microsoft.com).  
  
 Zadejte dvojtečkou (:) a oddíl *název*. *Název* je malá a velká písmena.  
  
 Nepoužívejte následující názvy, jak se budou v konfliktu s standardní názvy. Například .sdata se používá na RISC platformách:  
  
-   .arch  
  
-   .BSS  
  
-   .data –  
  
-   .edata  
  
-   .idata  
  
-   .pdata  
  
-   .rdata  
  
-   .reloc  
  
-   .rsrc  
  
-   .sbss  
  
-   .sdata  
  
-   .srdata  
  
-   text  
  
-   .xdata  
  
 Zadejte jeden nebo více atributů pro oddíl. Atribut znaky, uvedené níže, se nerozlišují malá a velká písmena. Je nutné zadat všechny atributy, které chcete oddílu, který má být; znak není uveden atribut způsobí, že daný atribut bit vypnout. Pokud nezadáte R, W nebo E, existující pro čtení, zápisu nebo spustitelný soubor stavu zůstává beze změny.  
  
 Chcete-li negate atribut, uveďte před jeho znak s vykřičníkem (!). Níže jsou uvedeny významy atribut znaků.  
  
|Znak|Atribut|Význam|  
|---------------|---------------|-------------|  
|E|Spuštění|V části je spustitelný soubor|  
|R|Číst|Umožňuje operace čtení dat|  
|W|Write|Umožňuje operací zápisu na data|  
|S|Shared|Sdílené složky v části mezi všechny procesy, které načíst obrázek|  
|D|Discardable|Označí části jako discardable|  
|K|Lze uložit do mezipaměti|Označí části jako není lze uložit do mezipaměti|  
|P|Stránkovatelné|Označí části jako není stránkovatelné|  
  
 Tisíc a P se zvláštní, že jsou části Příznaky, které odpovídají jim v tom smyslu, záporné. Pokud jeden z nich zadáte v části text (nebo část: text, kB), budou existovat žádné rozdíly v části Příznaky při spuštění [DUMPBIN](../../build/reference/dumpbin-options.md) s [/HEADERS](../../build/reference/headers.md) možnost; byl již implicitně mezipaměti. Odebrání výchozího, zadejte /SECTION:.text! Tisíc a DUMPBIN zobrazíte vlastnosti oddílu, včetně "Není mezipaměti."  
  
 Oddíl v souboru PE, který nemá E, R nebo W nastavit je pravděpodobně neplatná.  
  
 ZAROVNAT *=#*  umožňuje určit hodnotu zarovnání pro konkrétní oddíl. V tématu [/ALIGN](../../build/reference/align-section-alignment.md) Další informace.  
  
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