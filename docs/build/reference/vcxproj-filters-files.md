---
title: vcxproj. filters – soubory
ms.date: 09/25/2019
description: Použijte filtry souborů v projektech sady C++ Visual Studio k definování vlastních logických složek pro soubory v Průzkumník řešení
helpviewer_keywords:
- vcxproj.filters
- filters file [C++]
ms.openlocfilehash: ee44bf3d1cbe06d6c007ed8976ec384a456efca5
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686857"
---
# <a name="vcxprojfilters-files"></a>vcxproj. filters – soubory

Soubor *filtrů* (\*. vcxproj. filters) je soubor XML ve formátu MSBuild, který je umístěn v kořenové složce projektu. Určuje typy souborů, do kterých se v **Průzkumník řešení**logická složka. Na následujícím obrázku jsou soubory *. cpp* pod uzlem **zdrojové soubory** . soubory *. h* jsou pod uzlem **soubory hlaviček** a soubory *. ico* a *. RC* jsou v **souborech prostředků**. Toto umístění je řízeno souborem filtrů.

![Logické složky v Průzkumník řešení](media/solution-explorer-filters.png)

## <a name="creating-a-custom-filters-file"></a>Vytvoření vlastního souboru filtrů

Visual Studio automaticky vytvoří tento soubor. V případě aplikací klasické pracovní plochy jsou předdefinované logické složky (filtry): **zdrojové soubory**, **soubory hlaviček** a **soubory prostředků**. Jiné typy projektů, jako je UWP, můžou mít jinou sadu výchozích složek. Visual Studio automaticky přiřadí známé typy souborů do každé složky. Pokud chcete vytvořit filtr s vlastním názvem nebo filtrem, který obsahuje vlastní typy souborů, můžete vytvořit vlastní soubor filtrů v kořenové složce projektu nebo pod existujícím filtrem. (**Odkazy** a **externí závislosti** jsou speciální složky, které se nepodílejí na filtrování.)

## <a name="example"></a>Příklad

Následující příklad ukazuje soubor filtrů pro příklad zobrazený výše. Má plochou hierarchii; Jinými slovy nejsou žádné vnořené logické složky. Uzel `UniqueIdentifier` je nepovinný. Umožňuje rozhraní automatizace sady Visual Studio najít filtr. `Extensions` je také volitelné. Když se do projektu přidá nový soubor, přidá se do nejvyššího filtru se stejnou příponou souboru. Chcete-li přidat soubor do konkrétního filtru, klikněte pravým tlačítkem na filtr a vyberte možnost **Přidat novou položku**.

`ItemGroup`, který obsahuje uzly `ClInclude`, se vytvoří při prvním spuštění projektu. Pokud generujete vlastní soubory vcxproj, ujistěte se, že všechny položky projektu mají také záznam v souboru filters. Hodnoty v uzlu `ClInclude` přepisují výchozí filtrování na základě přípon souborů. Při použití sady Visual Studio k přidání nové položky do projektu přidá rozhraní IDE jednotlivé položky souboru do souboru filtrů. Když změníte příponu souboru, filtr se automaticky znovu nepřiřazuje. 

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Filter Include="Source Files">
      <UniqueIdentifier>{4FC737F1-C7A5-4376-A066-2A32D752A2FF}</UniqueIdentifier>
      <Extensions>cpp;c;cc;cxx;def;odl;idl;hpj;bat;asm;asmx</Extensions>
    </Filter>
    <Filter Include="Header Files">
      <UniqueIdentifier>{93995380-89BD-4b04-88EB-625FBE52EBFB}</UniqueIdentifier>
      <Extensions>h;hh;hpp;hxx;hm;inl;inc;ipp;xsd</Extensions>
    </Filter>
    <Filter Include="Resource Files">
      <UniqueIdentifier>{67DA6AB6-F800-4c08-8B7A-83BB121AAD01}</UniqueIdentifier>
      <Extensions>rc;ico;cur;bmp;dlg;rc2;rct;bin;rgs;gif;jpg;jpeg;jpe;resx;tiff;tif;png;wav;mfcribbon-ms</Extensions>
    </Filter>
  </ItemGroup>
  <ItemGroup>
    <ClInclude Include="MFCApplication1.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="MFCApplication1Dlg.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="stdafx.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="targetver.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="Resource.h">
      <Filter>Header Files</Filter>
    </ClInclude>
  </ItemGroup>
  <ItemGroup>
    <ClCompile Include="MFCApplication1.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
    <ClCompile Include="MFCApplication1Dlg.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
    <ClCompile Include="stdafx.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
  </ItemGroup>
  <ItemGroup>
    <ResourceCompile Include="MFCApplication1.rc">
      <Filter>Resource Files</Filter>
    </ResourceCompile>
  </ItemGroup>
  <ItemGroup>
    <None Include="res\MFCApplication1.rc2">
      <Filter>Resource Files</Filter>
    </None>
  </ItemGroup>
  <ItemGroup>
    <Image Include="res\MFCApplication1.ico">
      <Filter>Resource Files</Filter>
    </Image>
  </ItemGroup>
</Project>
```

Chcete-li vytvořit vnořené logické složky, deklarujte všechny uzly ve filtrech `ItemGroup`, jak je znázorněno níže. Každý podřízený uzel musí deklarovat úplnou logickou cestu k nejvyšší nadřazené položce. V následujícím příkladu musí být deklarován prázdný `ParentFilter`, protože se na něj odkazuje v pozdějších uzlech.

```xml
  <ItemGroup>
    <Filter Include="ParentFilter">
    </Filter>
    <Filter Include="ParentFilter\Source Files"> <!-- Full path to topmost parent.-->  
      <UniqueIdentifier>{4FC737F1-C7A5-4376-A066-2A32D752A2FF}</UniqueIdentifier> <!--  Optional-->
      <Extensions>cpp;c;cc;cxx;def;odl;idl;hpj;bat;asm;asmx</Extensions> <!-- Optional -->
    </Filter>
    <Filter Include="Header Files">
      <UniqueIdentifier>{93995380-89BD-4b04-88EB-625FBE52EBFB}</UniqueIdentifier>
      <Extensions>h;hh;hpp;hxx;hm;inl;inc;ipp;xsd</Extensions>
    </Filter>
  </ItemGroup>
```

