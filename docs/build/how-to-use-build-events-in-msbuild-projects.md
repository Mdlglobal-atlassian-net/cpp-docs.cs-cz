---
title: 'Postupy: použití událostí sestavení v projektech MSBuild | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.howto.usebuildevents
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2367c85dbd4a4ef7b10d927592c0fb10a417f0e6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369770"
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>Postupy: Použití událostí sestavení v projektech MSBuild
Události sestavení je příkaz který [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] provádí v konkrétní fázi v procesu sestavení. *Před sestavením* události dojde před začátkem sestavování; *před propojením* před spuštěním kroku odkaz; dojde k události a *po sestavení* k události po sestavení úspěšně se ukončí. Události sestavení dojde pouze v případě, že dojde k krok přidružené sestavení. Událost před propojením například nedochází, pokud nejde spustit krok propojení.  
  
 Každá z událostí tři sestavení je reprezentována ve skupině Definice command element (`<Command>`), se spustí a elementu zprávy (`<Message>`) to znamená zobrazí, když **MSBuild** provede události sestavení. Každý prvek je volitelný a pokud zadáte stejného elementu vícekrát, poslední výskyt přednost.  
  
 Volitelný *použití v sestavení* – element (`<`* sestavení-událostí ***UseInBuild**`>`) lze zadat ve skupině vlastností indikující, zda je provádět události sestavení. Hodnota obsahu *použití v sestavení* element je buď `true` nebo `false`. Ve výchozím nastavení, je událost sestavení provést, dokud jeho odpovídající *použití v sestavení* element je nastaven na hodnotu `false`.  
  
 Následující tabulka uvádí každý element XML událostí sestavení:  
  
|XML Element|Popis|  
|-----------------|-----------------|  
|`PreBuildEvent`|Tato událost se spustí před začátkem sestavení.|  
|`PreLinkEvent`|Tato událost se spustí před začátkem krok propojení.|  
|`PostBuildEvent`|Tato událost se spustí po dokončení sestavení.|  
  
 Následující tabulka obsahuje seznam všech *použití v sestavení* element:  
  
|XML Element|Popis|  
|-----------------|-----------------|  
|`PreBuildEventUseInBuild`|Určuje, zda chcete spustit *před sestavením* událostí.|  
|`PreLinkEventUseInBuild`|Určuje, zda chcete spustit *před propojením* událostí.|  
|`PostBuildEventUseInBuild`|Určuje, zda chcete spustit *po sestavení* událostí.|  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu lze přidat uvnitř elementu projektu vytvořené v souboru myproject.vcxproj [návod: použití nástroje MSBuild k vytvoření projektu Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md). A *před sestavením* událostí díky kopii main.cpp; *před propojením* událostí díky kopii main.obj; a *po sestavení* událostí vytvoří kopii myproject.exe. Pokud projekt je sestaven pomocí konfigurace verze, události sestavení jsou spuštěny. Pokud projekt je sestaven pomocí konfiguraci ladění, nebudou provedeny událostí sestavení.  
  
```  
<ItemDefinitionGroup>  
  <PreBuildEvent>  
    <Command>copy $(ProjectDir)main.cpp $(ProjectDir)copyOfMain.cpp</Command>  
    <Message>Making a copy of main.cpp </Message>  
  </PreBuildEvent>  
  <PreLinkEvent>  
 <Command>copy $(ProjectDir)$(Configuration)\main.obj $(ProjectDir)$(Configuration)\copyOfMain.obj</Command>  
    <Message>Making a copy of main.obj</Message>  
  </PreLinkEvent>  
  <PostBuildEvent>  
 <Command>copy $(ProjectDir)$(Configuration)\$(TargetFileName) $(ProjectDir)$(Configuration)\copyOfMyproject.exe</Command>  
    <Message>Making a copy of myproject.exe</Message>  
  </PostBuildEvent>  
</ItemDefinitionGroup>  
  
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">  
  <PreBuildEventUseInBuild>true</PreBuildEventUseInBuild>  
  <PreLinkEventUseInBuild>true</PreLinkEventUseInBuild>  
  <PostBuildEventUseInBuild>true</PostBuildEventUseInBuild>  
</PropertyGroup>  
  
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">  
  <PreBuildEventUseInBuild>false</PreBuildEventUseInBuild>  
  <PreLinkEventUseInBuild>false</PreLinkEventUseInBuild>  
  <PostBuildEventUseInBuild>false</PostBuildEventUseInBuild>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Viz také  
 [MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)   
 [Návod: Vytvoření projektu jazyka Visual C++ pomocí nástroje MSBuild](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)