---
title: Vcxproj.filtruje soubory
ms.date: 09/25/2019
description: Definování vlastních logických složek pro soubory v Průzkumníkovi řešení pomocí souborů filtrů v projektech sady Visual Studio C++
helpviewer_keywords:
- vcxproj.filters
- filters file [C++]
ms.openlocfilehash: 57735246b543680243994b99b8c05c9ad1211f38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335937"
---
# <a name="vcxprojfilters-files"></a>vcxproj.filtruje soubory

Soubor *filters* \*( .vcxproj.filters) je soubor XML ve formátu MSBuild, který je umístěn v kořenové složce projektu. Určuje, které typy souborů přejdou do které logické složky v **Průzkumníku řešení**. Na následujícím obrázku jsou soubory *CPP* pod uzlemi **Zdrojové soubory.** Soubory *H* jsou pod uzly **Soubory hlaviček** a soubory *.ico* a *RC* jsou v části **Soubory prostředků**. Toto umístění je řízeno souborem filtrů.

![Logické složky v Průzkumníku řešení](media/solution-explorer-filters.png)

## <a name="creating-a-custom-filters-file"></a>Vytvoření vlastního souboru filtrů

Visual Studio vytvoří tento soubor automaticky. U aplikací klasické pracovní plochy jsou předdefinovanými logickými složkami (filtry): **Zdrojové soubory**, **Soubory hlaviček** a **Soubory prostředků**. Jiné typy projektů, například UPW, mohou mít jinou sadu výchozích složek. Visual Studio automaticky přiřadí známé typy souborů každé složce. Chcete-li vytvořit filtr s vlastním názvem nebo filtrem, který obsahuje vlastní typy souborů, můžete vytvořit vlastní soubor filtrů v kořenové složce projektu nebo pod existujícím filtrem. (**Odkazy** a **externí závislosti** jsou zvláštní složky, které se neúčastní filtrování.)

## <a name="example"></a>Příklad

Následující příklad ukazuje soubor filtrů pro ukázkový pořad dříve. Má plochou hierarchii; jinými slovy, neexistují žádné vnořené logické složky. Uzel `UniqueIdentifier` je volitelný. Umožňuje rozhraní automatizace sady Visual Studio najít filtr. `Extensions`je také volitelná. Když je do projektu přidán nový soubor, je přidán do nejvyššího filtru s odpovídající příponou souboru. Chcete-li přidat soubor do určitého filtru, klepněte pravým tlačítkem myši na filtr a zvolte **Přidat novou položku**.

Který `ItemGroup` obsahuje `ClInclude` uzly je vytvořen při prvním spuštění projektu. Pokud generujete vlastní soubory vcxproj, ujistěte se, že všechny položky projektu mají také položku v souboru filtrů. Hodnoty v `ClInclude` uzlu přepíší výchozí filtrování na základě přípon souborů. Při použití sady Visual Studio přidat novou položku do projektu, ide přidá jednotlivé položky souboru v souboru filtrů. Pokud změníte příponu souboru, nebude filtr automaticky znovu přiřazen.

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

Chcete-li vytvořit vnořené logické `ItemGroup` složky, deklarujte všechny uzly ve filtrech, jak je znázorněno níže. Každý podřízený uzel musí deklarovat úplnou logickou cestu k nejvyššímu nadřazenému objektu. V následujícím příkladu `ParentFilter` musí být deklarováno prázdné, protože je odkazováno v pozdějších uzlech.

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
