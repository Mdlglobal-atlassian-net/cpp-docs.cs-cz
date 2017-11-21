---
title: "Určení vlastního nástroje sestavení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCustomBuildTool.CustomBuildToolBeforeTargets
- VC.Project.VCCustomBuildTool.Outputs
- VC.Project.VCCustomBuildTool.Command
- VC.Project.VCCustomBuildTool.CommandLine
- VC.Project.VCCustomBuildTool.AdditionalDependencies
- VC.Project.VCCustomBuildTool.Message
- VC.Project.VCCustomBuildTool.CustomBuildToolAfterTargets
- VC.Project.VCCustomBuildTool.Description
- VC.Project.VCCustomBuildTool.AdditionalInputs
dev_langs: C++
helpviewer_keywords:
- build tools (C++), specifying
- custom build tools (C++), specifying
- builds (C++), custom build tools
ms.assetid: e5161946-8002-418d-991e-219e6a8586f5
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c65664e6c09028f1f15ded917a59ad013868f841
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="specifying-custom-build-tools"></a>Určení vlastních sestavovacích nástrojů
A *vlastní sestavovací nástroje* systém sestavení poskytne informace, musí se vytvořit konkrétní vstupní soubory. Nástroj pro vlastní sestavení určuje příkaz ke spuštění, seznam vstupní soubory, seznam výstupní soubory, které jsou generovány příkazem a volitelný popis nástroje.  
  
 Obecné informace o vlastní sestavovací nástroje a vlastní kroky sestavení najdete v tématu [Principy vlastní kroky sestavení a události sestavení](../ide/understanding-custom-build-steps-and-build-events.md).  
  
### <a name="to-specify-a-custom-build-tool"></a>Chcete-li určit vlastní sestavovací nástroje  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Další informace najdete v tématu [nastavení vlastností projektu Visual C++](../ide/working-with-project-properties.md).  
  
2.  Klikněte na tlačítko **vlastnosti konfigurace** povolit **konfigurace** pole. V **konfigurace** vyberte konfigurace, pro který chcete určit vlastní sestavovací nástroje.  
  
3.  V **Průzkumníku**, vyberte vstupní soubor pro nástroj pro vlastní sestavení.  
  
     Pokud **nástroj pro vlastní sestavení** složka nezobrazí, přípona souboru vybraný soubor je přidružen výchozí nástroj. Například výchozí nástroj pro soubory .c a sada je kompilátor. Přepsat výchozí nastavení nástroje v **vlastnosti konfigurace** uzlu v **Obecné** složky v **typ položky** vlastnost, klikněte na tlačítko **vlastní sestavení Nástroj**. Klikněte na tlačítko **použít** a **nástroj pro vlastní sestavení** uzel se zobrazí.  
  
4.  V **vlastního nástroje sestavení** uzlu v **Obecné** složku, zadejte vlastnosti přidružené k vlastní sestavení nástroje:  
  
    -   V **Další závislosti**, zadejte jakékoli další soubory nad rámec jeden, pro který je definovaný vlastní sestavovací nástroje (soubor přidružený k vlastní sestavovací nástroje se vstupem pro nástroj implicitně považuje). Mít další vstupní soubory není požadavek pro nástroj pro vlastní sestavení. Pokud máte více než jeden další vstup, oddělte je středníky.  
  
         Pokud **Další závislosti** datum souboru je novější než vstupní soubor a pak je spustit nástroj pro vlastní sestavení. Pokud všechny z **Další závislosti** jsou starší než vstupní soubor soubory a vstupní soubor je starší než **výstupy** soubor vlastnost a poté nástroj pro vlastní sestavení není spuštěna.  
  
         Předpokládejme například, že máte vlastní sestavovací nástroje, který přebírá MyInput.x jako vstup a vygeneruje MyInput.cpp, a pak MyInput.x zahrne soubor hlaviček MyHeader.h. MyHeader.h můžete zadat jako vstupní závislost na MyInput.x a systém sestavení bude sestavovat MyInput.cpp, když je zastaralé s ohledem na MyInput.x nebo MyHeader.h.  
  
         Vstupní závislosti také zajistit, že vlastní sestavovací nástroje spouštěny v pořadí, které potřebujete, aby. V předchozím příkladu předpokládejme, že MyHeader.h je ve skutečnosti výstup vlastní sestavovací nástroje. Protože MyHeader.h je závislost na MyInput.x, systém sestavení nejprve vytvoří Myheader.h před spuštěním vlastní sestavovací nástroje na MyInput.x.  
  
    -   V **příkazového řádku**, jako kdyby byly ho zadat na příkazovém řádku zadejte příkaz. Zadejte platný příkaz nebo dávkového souboru a libovolný požadovaný vstupní nebo výstupní soubory. Zadejte **volání** dávky příkazu před název souboru batch zaručit, že jsou všechny následné příkazy provedeny.  
  
         Více vstupních a výstupních souborů může být zadáno symbolicky s makry MSBuild. [!INCLUDE[crabout](../build/reference/includes/crabout_md.md)]zadání umístění souborů nebo názvy sad souborů, najdete v části [běžné makra pro příkazy sestavení a vlastnosti](../ide/common-macros-for-build-commands-and-properties.md).  
  
         Protože znak "%" je rezervován MSBuild, pokud zadáte proměnnou prostředí nahradit každý  **%**  znaku s **% 25** šestnáctková řídicí sekvence. Například nahradit **% WINDIR %** s **25WINDIR % 25**. MSBuild nahradí každý **% 25** pořadí se  **%**  znak před přistupuje k proměnné prostředí.  
  
    -   V **popis**, zadejte popisný zprávu o tomto nástroji vlastní sestavení. Zpráva tisku **výstup** okno, pokud systém sestavení zpracovává tento nástroj.  
  
    -   V **výstupy**, zadejte název souboru výstupního souboru. Toto je požadovaná položka; bez hodnoty pro tuto vlastnost nebude spustit nástroj pro vlastní sestavení. Pokud nástroj pro vlastní sestavení má více než jeden výstup, soubor názvy oddělte středníkem.  
  
         Název výstupního souboru, by měl být stejný jako jsou zadány v **příkazového řádku** vlastnost. Systém sestavení projektu se vyhledat soubor a zkontrolujte jeho data. Pokud výstupní soubor je novější než vstupní soubor nebo výstupní soubor nebyl nalezen, je spuštěn nástroj vlastní sestavení. Pokud všechny z **Další závislosti** jsou starší než vstupní soubor soubory a vstupní soubor je starší než v souboru určeném v **výstupy** vlastnost, nástroj pro vlastní sestavení není spuštěn.  
  
 Pokud chcete systém sestavení pracovat na soubor výstup generovaný nástrojem vlastní sestavení, je třeba ručně přidat do projektu. Vlastní sestavovací nástroje aktualizuje soubor během sestavení.  
  
## <a name="example"></a>Příklad  
 Předpokládejme, že chcete zahrnout do projektu soubor s názvem parser.l. Chcete lexikální analyzátor zpracovávat parser.l k vytvoření .c souboru, který má stejný název základní (parser.c).  
  
 Nejprve přidejte parser.l a parser.c do projektu. Pokud soubory ještě neexistují, stačí přidat odkaz na soubory. Můžete vytvořit vlastní sestavovací nástroje pro parser.l a zadejte následující příkaz v **příkazy** vlastnost:  
  
```  
lexer %(FullPath) .\%(Filename).c  
```  
  
 Tento příkaz spustí lexikální analyzátor parser.l a výstup parser.c do adresáře projektu.  
  
 V **výstupy** vlastnost, zadejte následující příkaz:  
  
```  
.\%(Filename).c  
```  
  
 Při sestavování projektu systém sestavení porovná časová razítka parser.l a parser.c. Pokud je novější parser.l nebo parser.c neexistuje, spustí systém sestavení hodnotu **příkazového řádku** vlastnost aby parser.c aktuální. Vzhledem k tomu, že parser.c se taky přidala do projektu, systém sestavení pak zkompiluje parser.c.  
  
## <a name="see-also"></a>Viz také  
 [Běžné makra pro příkazy a vlastnosti sestavení](../ide/common-macros-for-build-commands-and-properties.md)   
 [Řešení potíží s přizpůsobením sestavení](../ide/troubleshooting-build-customizations.md)