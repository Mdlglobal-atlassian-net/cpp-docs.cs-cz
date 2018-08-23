---
title: 'Návod: Vytvoření projektu jazyka Visual C++ pomocí nástroje MSBuild | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.walkthrough.createproject
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), walkthrough: create a project'
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8bb957f0ab1dd2ea7d05151257aee0e15561e8a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609696"
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>Návod: Vytvoření projektu jazyka Visual C++ pomocí nástroje MSBuild

Tento návod ukazuje způsob použití nástroje MSBuild k sestavení projektu Visual C++ v příkazovém řádku. Se dozvíte, jak vytvořit zdrojové soubory C++ a soubor projektu založený na formátu XML pro konzolovou aplikaci Visual C++. Po vytvoření projektu, se dozvíte, jak přizpůsobit proces sestavení.

Tento návod znázorňuje následující úlohy:

- Vytváření zdrojových souborů C++ pro váš projekt.

- Vytvoření souboru projektu XML MSBuild.

- Použití nástroje MSBuild k sestavení projektu.

- Použití nástroje MSBuild k přizpůsobení projektu.

## <a name="prerequisites"></a>Požadavky

Budete potřebovat k dokončení tohoto návodu:

- Kopie sady Visual Studio s **vývoj desktopových aplikací pomocí C++** nainstalovaná úloha.

- Obecné principy systému MSBuild.

> [!NOTE]
> Tento postup nepoužívejte, pokud máte v úmyslu později upravit soubor projektu s použitím rozhraní IDE sady Visual Studio. Pokud jste ručně vytvořili soubor .vcxproj, zejména v případě, že projekt používá zástupné znaky v položkách projektu nemusí být schopni upravit nebo načtení, integrovaném vývojovém prostředí sady Visual Studio.

> [!NOTE]
> Většina nízké úrovně sestavení pokyny jsou součástí **.targets** a **.props** soubory, které jsou definovány v adresáři VCTargets uložená ve vlastnosti `$(VCTargetsPath)`. Výchozí cesta pro tyto soubory v aplikaci Visual Studio 2017 Enterprise Edition je C:\\Program Files (x86)\\sady Microsoft Visual Studio\\2017\\Enterprise\\Common7\\integrovanéhovývojovéhoprostředí\\ VC\\VCTargets\\.

## <a name="creating-the-c-source-files"></a>Vytváření zdrojových souborů C++

V tomto návodu vytvoříte projekt, který obsahuje zdrojový soubor a soubor hlaviček. Zdrojový soubor main.cpp obsahuje hlavní funkci pro konzolové aplikace. Main.h v souboru záhlaví obsahuje kód přikazující zahrnutí souboru záhlaví iostream. Tyto soubory C++ můžete vytvořit pomocí sady Visual Studio nebo textový editor, třeba Visual Studio Code.

### <a name="to-create-the-c-source-files-for-your-project"></a>Vytvoření zdrojových souborů C++ pro váš projekt

1. Vytvořte adresář pro váš projekt.

2. Vytvořte soubor s názvem main.cpp a do tohoto souboru přidejte následující kód:

    ```cpp
    // main.cpp : the application source code.
    #include <iostream>
    #include "main.h"
    int main()
    {
       std::cout << "Hello, from MSBuild!\n";
       return 0;
    }
    ```

3. Vytvořte soubor s názvem main.h a do tohoto souboru přidejte následující kód:

    ```cpp
    // main.h: the application header code.
    /* Additional source code to include. */
    ```

## <a name="creating-the-xml-msbuild-project-file"></a>Vytváření XML souboru projektu nástroje MSBuild

Soubor projektu MSBuild je soubor XML, který obsahuje kořenový prvek projektu (\<Projekt >). V následujícím příkladu projektu \<Project > sedm podřízených elementů obsahuje element:

- Tři značky skupiny položek (\<ItemGroup >), které určují konfiguraci projektu a platforem, název zdrojového souboru a název souboru hlaviček.

- Tři tagy pro import (\<Import >), které určují umístění nastavení Microsoft Visual C++.

- Značka skupiny vlastností (\<PropertyGroup >), která určuje nastavení projektu.

### <a name="to-create-the-msbuild-project-file"></a>K vytvoření souboru projektu MSBuild

1. Pomocí textového editoru vytvořte soubor projektu s názvem `myproject.vcxproj`a potom přidejte následující kořen \<Projekt > element. Vložte prvky do následujících kroků postupu mezi kořenové \<Projekt > značky:

    ```xml
    <Project DefaultTargets="Build" ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. Přidejte následující dva \<ProjectConfiguration > podřízené elementy v \<ItemGroup > element. Podřízený prvek určuje ladění a konfigurace pro operační systém Windows 32-bit verze:

    ```xml
    <ItemGroup>
      <ProjectConfiguration Include="Debug|Win32">
        <Configuration>Debug</Configuration>
        <Platform>Win32</Platform>
      </ProjectConfiguration>
      <ProjectConfiguration Include="Release|Win32">
        <Configuration>Release</Configuration>
        <Platform>Win32</Platform>
      </ProjectConfiguration>
    </ItemGroup>
    ```

3. Přidejte následující \<Import / > prvku, který určuje cestu k výchozímu nastavení C++ pro tento projekt:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
    ```

4. Přidejte následující element skupiny vlastností (\<PropertyGroup >), který určuje dvě vlastnosti projektu:

    ```xml
    <PropertyGroup>
      <ConfigurationType>Application</ConfigurationType>
      <PlatformToolset>v141</PlatformToolset>
    </PropertyGroup>
    ```

5. Přidejte následující \<Import / > prvku, který určuje cestu k aktuálnímu nastavení C++ pro tento projekt:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
    ```

6. Přidejte následující \<ClCompile > podřízený element v \<ItemGroup > element. Podřízený prvek určuje název pro kompilaci zdrojového souboru jazyka C/C++:

    ```xml
    <ItemGroup>
      <ClCompile Include="main.cpp" />
    </ItemGroup>
    ```

   > [!NOTE]
   > \<ClCompile > je *cíl sestavení* a je definován v **VCTargets** adresáře.

7. Přidejte následující \<ClInclude > podřízený element v \<ItemGroup > element. Podřízený prvek určuje název hlavičkového souboru pro zdrojový soubor jazyka C/C++:

    ```xml
    <ItemGroup>
      <ClInclude Include="main.h" />
    </ItemGroup>
    ```

8. Přidejte následující \<Import > prvek, který určuje cestu k souboru, který definuje cíl pro tento projekt:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
    ```

### <a name="complete-project-file"></a>Dokončit soubor projektu

Následující kód ukazuje celý soubor projektu, který jste vytvořili v předchozím postupu.

```xml
<Project DefaultTargets="Build" ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <ProjectConfiguration Include="Debug|Win32">
      <Configuration>Debug</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
    <ProjectConfiguration Include="Release|Win32">
      <Configuration>Release</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
  </ItemGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
  <PropertyGroup>
    <ConfigurationType>Application</ConfigurationType>
    <PlatformToolset>v141</PlatformToolset>
  </PropertyGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
  <ItemGroup>
    <ClCompile Include="main.cpp" />
  </ItemGroup>
  <ItemGroup>
    <ClInclude Include="main.h" />
  </ItemGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
</Project>
```

## <a name="using-msbuild-to-build-your-project"></a>Použití nástroje MSBuild k sestavení projektu

Zadejte následující příkaz na příkazovém řádku k vytvoření konzolové aplikace:

`msbuild myproject.vcxproj /p:configuration=debug`

Nástroj MSBuild vytvoří adresář pro výstupní soubory a potom zkompiluje a propojí vaše projekty ke generování programu Myproject.exe. Po dokončení procesu sestavení, použijte následující příkaz ke spuštění aplikace:

`myproject`

Aplikace by měla zobrazit "Hello, MSBuild!" v okně konzoly.

## <a name="customizing-your-project"></a>Přizpůsobení vašeho projektu

Nástroj MSBuild umožňuje spustit předdefinované cíle sestavení, použít uživatelem definované vlastnosti a použít vlastní nástroje, události a kroky sestavení. Tato část ilustruje následující úkoly:

- Použití nástroje MSBuild s cíli sestavení.

- Použití nástroje MSBuild s vlastnostmi sestavení.

- Použití nástroje MSBuild s 64bitovým kompilátorem a nástroji.

- Použití nástroje MSBuild s různými sadami nástrojů.

- Přidání vlastního nastavení MSBuild.

### <a name="using-msbuild-with-build-targets"></a>Použití nástroje MSBuild s cíli sestavení

A *cíl sestavení* je pojmenovaná sada předdefinovaných nebo uživatelem definované příkazů, které mohou být provedeny během sestavení. Použít možnost příkazového řádku target (**/t**) Chcete-li určit cíle sestavení. V případě třídy `myproject` příklad projektu, předdefinované **čisté** cíle odstraní všechny soubory ve složce ladění a vytvoří nový soubor protokolu.

Na příkazovém řádku zadejte následující příkaz k čištění `myproject`.

`msbuild myproject.vcxproj /t:clean`

### <a name="using-msbuild-with-build-properties"></a>Použití nástroje MSBuild s vlastnostmi sestavení

Možnost příkazového řádku vlastností (**/p**) umožňuje přepsat vlastnost v souboru sestavení projektu. V `myproject` příklad projektu, vydání nebo ladícího sestavení konfigurace je určena `Configuration` vlastnost. A je určený operační systém, který se má spustit sestavenou aplikaci `Platform` vlastnost.

Na příkazovém řádku zadejte následující příkaz k vytvoření nového sestavení ladění aplikace `myproject` aplikaci, která je určena pro spuštění na 32bitová verze Windows.

`msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`

Předpokládejme, že `myproject` příklad projektu také definuje konfiguraci pro Windows 64-bit a jinou konfiguraci pro vlastní operační systém s názvem `myplatform`.

Na příkazovém řádku zadejte následující příkaz k vytvoření verze sestavení, která běží na Windows 64-bit.

`msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`

Na příkazovém řádku zadejte následující příkaz k vytvoření sestavení pro vydání pro `myplatform`.

`msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`

### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>Použití nástroje MSBuild s 64bitovým kompilátorem a nástroji

Pokud jste nainstalovali Visual C++ v 64bitová verze Windows ve výchozím nastavení, nainstaluje se x64 64bitové nativní a křížové nástroje. Můžete nakonfigurovat nástroj MSBuild pro použití 64bitového kompilátoru a nástrojů k sestavení aplikace nastavením `PreferredToolArchitecture` vlastnost. Tato vlastnost nemá vliv na vlastnosti projektu konfiguraci nebo platformu. Ve výchozím nastavení se používá 32bitovou verzi nástroje. Chcete-li určit 64bitovou verzi kompilátoru a nástrojů, přidejte následující element skupiny vlastností do souboru projektu Myproject.vcxproj po `Microsoft.Cpp.default.props` \<Import / > prvku:

```xml
<PropertyGroup>
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>
</PropertyGroup>
```

Na příkazovém řádku zadejte následující příkaz k použití 64bitových nástrojů k sestavení aplikace.

`msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="using-msbuild-with-a-different-toolset"></a>Použití nástroje MSBuild s různými sadami nástrojů

Pokud máte sady nástrojů a knihovny pro jiné verze jazyka Visual C++ nainstalovaná, nástroj MSBuild můžete vytvářet aplikace pro aktuální verzi jazyka Visual C++, nebo pro ostatní nainstalované verze. Například pokud jste nainstalovali sadu Visual Studio 2012, chcete-li určit sadu nástrojů Visual C++ 11.0 pro systém Windows XP, přidejte následující element skupiny vlastností do souboru projektu Myproject.vcxproj po elementu Microsoft.Cpp.props `<Import />` element:

```xml
<PropertyGroup>
    <PlatformToolset>v110_xp</PlatformToolset>
</PropertyGroup>
```

Chcete-li znovu sestavit projekt pomocí sady nástrojů Visual C++ 11.0 Windows XP, zadejte některý z následujících příkazů:

`msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`

`msbuild myproject.vcxproj /t:rebuild`

### <a name="adding-msbuild-customizations"></a>Přidání vlastního nastavení MSBuild

Nástroj MSBuild poskytuje různé způsoby přizpůsobení procesu sestavení. Následující témata ukazují, jak přidat vlastní kroky sestavení, nástroje a události do vašeho projektu nástroje MSBuild:

- [Postupy: Přidání vlastního kroku sestavení do projektů MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)

- [Postupy: Přidání vlastních nástrojů sestavení do projektů MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)

- [Postupy: Použití událostí sestavení v projektech MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)
