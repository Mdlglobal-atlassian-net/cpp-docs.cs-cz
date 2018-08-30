---
title: 'Postupy: použití událostí sestavení v projektech MSBuild | Dokumentace Microsoftu'
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
ms.openlocfilehash: cdc5ea4c2cd1e02e6894d2dedf8470641021f0b2
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214466"
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>Postupy: Použití událostí sestavení v projektech MSBuild
Události sestavení je příkaz, který provádí MSBuild v určité fázi v procesu sestavení. *Před sestavením* před začátkem sestavování dojde k události; *před propojením* před spuštěním kroku odkazu; dojde k události a *po sestavení* výskytu události po sestavení úspěšně se ukončí. Události sestavení dojde pouze v případě, že nastane přidružené sestavení. Například událost před propojením nedojde, pokud krok propojení se nespustí.  
  
 Všech událostí tři sestavení je reprezentován ve skupině definice příkazu elementu (`<Command>`), který je proveden a elementu zprávy (`<Message>`), který je zobrazí, když **MSBuild** provádí události sestavení. Každý element je volitelný a pokud chcete zadat více než jednou stejného elementu, posledního výskytu přednost.  
  
 Volitelně *použít v sestavení* – element (`<`*události sestavení*`UseInBuild>`) lze zadat ve skupině vlastností k označení, zda je událost sestavení spustit. Hodnota obsahu *použít v sestavení* element je buď `true` nebo `false`. Ve výchozím nastavení, je provedena události sestavení, pokud jeho odpovídajícím *použít v sestavení* prvek je nastaven na `false`.  
  
 V následující tabulce jsou uvedeny jednotlivých prvků XML události sestavení:  
  
|– Element XML|Popis|  
|-----------------|-----------------|  
|`PreBuildEvent`|Tato událost se spustí před začátkem sestavení.|  
|`PreLinkEvent`|Tato událost se spustí před zahájením krok propojování.|  
|`PostBuildEvent`|Tato událost se spustí po dokončení sestavení.|  
  
 V následující tabulce jsou uvedeny jednotlivé *použít v sestavení* element:  
  
|– Element XML|Popis|  
|-----------------|-----------------|  
|`PreBuildEventUseInBuild`|Určuje, jestli se má spustit *před sestavením* událostí.|  
|`PreLinkEventUseInBuild`|Určuje, jestli se má spustit *před propojením* událostí.|  
|`PostBuildEventUseInBuild`|Určuje, jestli se má spustit *po sestavení* událostí.|  
  
## <a name="example"></a>Příklad  
 Následující příklad je možné přidat uvnitř elementu projektu MyProject.vcxproj za soubor vytvořený v [návod: použití nástroje MSBuild k vytvoření projektu jazyka Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md). A *před sestavením* události vytvoří kopii main.cpp; *před propojením* události vytvoří kopii main.obj; a s *po sestavení* události vytvoří kopii tohoto myproject.exe. Je-li projekt se vytvořil pomocí konfiguraci vydané verze, jsou spuštěny událostí sestavení. Pokud projekt se vytvořil pomocí konfiguraci ladění, nebudou provedeny události sestavení.  
  
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
 [Nástroj MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)   
 [Návod: Vytvoření projektu jazyka Visual C++ pomocí nástroje MSBuild](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)