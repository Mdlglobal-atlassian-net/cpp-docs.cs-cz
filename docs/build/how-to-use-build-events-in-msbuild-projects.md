---
title: 'Postupy: Použití událostí sestavení v projektech MSBuild'
ms.date: 11/04/2016
helpviewer_keywords:
- 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
ms.openlocfilehash: 3fe205223b6cf381bbf3e2872b1a84f9d81a3cb7
ms.sourcegitcommit: 2da5c42928739ca8cd683a9002598f28d8ec5f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70060066"
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>Postupy: Použití událostí sestavení v projektech MSBuild

Událost sestavení je příkaz, který MSBuild provádí v konkrétní fázi procesu sestavení. Událost *před sestavením* probíhá před spuštěním sestavení; událost před *propojením* proběhne před zahájením kroku propojení; a událost *po sestavení* nastane po úspěšném dokončení sestavení. Událost sestavení nastane pouze v případě, že dojde k přidruženému kroku sestavení. Událost před propojením například nenastane, pokud se krok propojení nespustí.

Jednotlivé tři události sestavení jsou reprezentovány ve skupině definice položky pomocí příkazu (`<Command>`), který je proveden a elementu zprávy (`<Message>`), který se zobrazí, když nástroj **MSBuild** provede událost sestavení. Každý prvek je nepovinný a pokud zadáte stejný prvek několikrát, má přednost poslední výskyt.

Volitelný element *use-in-Build* (`<`*sestavení-Event*`UseInBuild>`) lze zadat ve skupině vlastností, aby označoval, zda je událost sestavení provedena. Hodnota obsahu prvku pro *použití v sestavení* je **true** nebo **false**. Ve výchozím nastavení je událost sestavení provedena, pokud není odpovídající element *use-in-Build* nastaven na `false`hodnotu.

V následující tabulce jsou uvedeny jednotlivé prvky XML události sestavení:

|XML – element|Popis|
|-----------------|-----------------|
|`PreBuildEvent`|Tato událost se spustí před zahájením sestavování.|
|`PreLinkEvent`|Tato událost se spustí před zahájením kroku propojení.|
|`PostBuildEvent`|Tato událost se spustí po dokončení sestavení.|

V následující tabulce jsou uvedeny jednotlivé prvky pro *použití v sestavení* :

|XML – element|Popis|
|-----------------|-----------------|
|`PreBuildEventUseInBuild`|Určuje, zda se má spustit událost *před sestavením* .|
|`PreLinkEventUseInBuild`|Určuje, zda se má spustit událost *před propojením* .|
|`PostBuildEventUseInBuild`|Určuje, zda se má spustit událost *po sestavení* .|

## <a name="example"></a>Příklad

Následující příklad lze přidat do prvku projektu souboru MyProject. vcxproj vytvořeného v [návodu: pomocí nástroje MSBuild vytvořte projekt C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md). Událost *před sestavením* vytváří kopii Main. cpp; událost *před propojením* vytváří kopii hlavního objektu. obj;. a událost *po sestavení* vytvoří kopii souboru MyProject. exe. Pokud je projekt sestaven pomocí konfigurace vydané verze, spustí se události sestavení. Pokud je projekt sestaven pomocí konfigurace ladění, události sestavení nejsou provedeny.

``` xml
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

[MSBuild na příkazovém řádku – C++](msbuild-visual-cpp.md)<br/>
[Návod: vytvoření projektu jazyka C++ pomocí nástroje MSBuild](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)
