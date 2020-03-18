---
title: 'Návod: Vytvoření projektu jazyka Visual C++ pomocí nástroje MSBuild'
ms.date: 05/16/2019
helpviewer_keywords:
- 'msbuild (c++), walkthrough: create a project'
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
ms.openlocfilehash: c93867f3be3b17f703c549aa5c05f3d327934c26
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417185"
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>Návod: Vytvoření projektu jazyka Visual C++ pomocí nástroje MSBuild

Tento návod ukazuje, jak použít MSBuild k sestavení projektu sady Visual C++ Studio na příkazovém řádku. Naučíte se, jak vytvořit C++ zdrojové soubory a soubor projektu založený na jazyce XML pro konzolovou aplikaci C++ Visual Console. Po sestavení projektu se dozvíte, jak přizpůsobit proces sestavení.

Tento návod znázorňuje následující úlohy:

- Vytváření C++ zdrojových souborů pro projekt.

- Vytváření souboru projektu XML MSBuild.

- Použití nástroje MSBuild k sestavení projektu.

- Použití nástroje MSBuild k přizpůsobení projektu.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu potřebujete následující:

- Kopie sady Visual Studio s nainstalovanou úlohou **vývoj C++ pro desktopy**

- Obecné porozumění systému MSBuild.

> [!NOTE]
> Nepoužívejte tento přístup, pokud máte v úmyslu později upravit soubor projektu pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio. Vytvoříte-li soubor. vcxproj ručně, rozhraní IDE sady Visual Studio nemusí být schopno ho upravit ani načíst, zejména v případě, že projekt používá zástupné znaky v položkách projektu.

> [!NOTE]
> Většina pokynů pro sestavení na nízké úrovni je obsažena v souborech **. targets** a **. props** , které jsou definovány v adresáři VCTargets, uložené ve vlastnosti `$(VCTargetsPath)`. Výchozí cesta pro tyto soubory v aplikaci Visual Studio 2019 Enterprise Edition je C:\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\MSBuild\Microsoft\VC\v160\Microsoft.Cpp.Common.props.

## <a name="creating-the-c-source-files"></a>Vytváření C++ zdrojových souborů

V tomto návodu vytvoříte projekt, který má zdrojový soubor a hlavičkový soubor. Zdrojový soubor Main. cpp obsahuje hlavní funkci pro konzolovou aplikaci. Hlavičkový soubor Main. h obsahuje kód pro zahrnutí hlavičkového souboru iostream –. Tyto C++ soubory můžete vytvořit pomocí sady Visual Studio nebo textového editoru, jako je například Visual Studio Code.

### <a name="to-create-the-c-source-files-for-your-project"></a>Vytvoření C++ zdrojových souborů pro váš projekt

1. Vytvořte adresář pro váš projekt.

1. Vytvořte soubor s názvem Main. cpp a do tohoto souboru přidejte následující kód:

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

1. Vytvořte soubor s názvem Main. h a do tohoto souboru přidejte následující kód:

    ```cpp
    // main.h: the application header code.
    /* Additional source code to include. */
    ```

## <a name="creating-the-xml-msbuild-project-file"></a>Vytváření souboru projektu XML MSBuild

Soubor projektu MSBuild je soubor XML, který obsahuje kořenový prvek projektu (`<Project>`). V následujícím ukázkovém projektu `<Project>` element obsahuje sedm podřízených elementů:

- Tři značky skupin položek (`<ItemGroup>`), které určují konfiguraci a platformu projektu, název zdrojového souboru a název souboru hlaviček.

- Tři značky importu (`<Import>`), které určují umístění nastavení Microsoft Visual C++ .

- Značka skupiny vlastností (`<PropertyGroup>`), která určuje nastavení projektu.

### <a name="to-create-the-msbuild-project-file"></a>Vytvoření souboru projektu MSBuild

1. Pomocí textového editoru vytvořte soubor projektu s názvem `myproject.vcxproj`a poté přidejte následující kořenový prvek `<Project>`. Vložte prvky do následujících kroků procedury mezi kořenovými `<Project>` značkami. (Použijte ToolsVersion = "15.0", pokud používáte Visual Studio 2017 nebo ToolsVersion = "16.0", pokud používáte Visual Studio 2019.)

    ```xml
    <Project DefaultTargets="Build" ToolsVersion="16.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

1. Do `<ItemGroup>` elementu přidejte následující dva `<ProjectConfiguration>` podřízené prvky. Podřízený element určuje konfiguraci ladění a vydání pro 32 operační systém Windows:

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

1. Přidejte následující prvek `<Import>`, který určuje cestu k výchozímu C++ nastavení pro tento projekt:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
    ```

1. Přidejte následující prvek skupiny vlastností (`<PropertyGroup>`), který určuje dvě vlastnosti projektu. (Použijte v141, pokud používáte Visual Studio 2017 nebo V142, pokud používáte Visual Studio 2019.)

    ```xml
    <PropertyGroup>
      <ConfigurationType>Application</ConfigurationType>
      <PlatformToolset>v142</PlatformToolset>
    </PropertyGroup>
    ```

1. Přidejte následující prvek `<Import>`, který určuje cestu k aktuálnímu C++ nastavení pro tento projekt:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
    ```

1. Do `<ItemGroup>` elementu přidejte následující `<ClCompile>` podřízený element. Podřízený prvek určuje názevC++ zdrojového souboru jazyka C, který má být zkompilován:

    ```xml
    <ItemGroup>
      <ClCompile Include="main.cpp" />
    </ItemGroup>
    ```

   > [!NOTE]
   > `<ClCompile>` je *cíl sestavení* a je definován v adresáři **VCTargets** .

1. Do `<ItemGroup>` elementu přidejte následující `<ClInclude>` podřízený element. Podřízený prvek určuje název hlavičkového souboru pro C/C++ zdrojový soubor:

    ```xml
    <ItemGroup>
      <ClInclude Include="main.h" />
    </ItemGroup>
    ```

1. Přidejte následující prvek `<Import>`, který určuje cestu k souboru, který definuje cíl pro tento projekt:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
    ```

### <a name="complete-project-file"></a>Dokončit soubor projektu

Následující kód ukazuje kompletní soubor projektu, který jste vytvořili v předchozím postupu. (Použijte ToolsVersion = "15.0" pro Visual Studio 2017.)

```xml
<Project DefaultTargets="Build" ToolsVersion="16.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
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
    <PlatformToolset>v142</PlatformToolset>
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

## <a name="using-msbuild-to-build-your-project"></a>Sestavení projektu pomocí nástroje MSBuild

Na příkazovém řádku zadejte následující příkaz pro sestavení konzolové aplikace:

`msbuild myproject.vcxproj /p:configuration=debug`

Nástroj MSBuild vytvoří adresář pro výstupní soubory a poté zkompiluje a propojí váš projekt, aby vygeneroval program MyProject. exe. Po dokončení procesu sestavení pomocí následujícího příkazu spusťte aplikaci ze složky pro ladění:

`myproject`

Aplikace by měla v MSBuildu zobrazovat text "Hello". v okně konzoly.

## <a name="customizing-your-project"></a>Přizpůsobení projektu

Nástroj MSBuild umožňuje spustit předdefinované cíle sestavení, použít uživatelsky definované vlastnosti a použít vlastní nástroje, události a kroky sestavení. Tato část ilustruje následující úlohy:

- Použití nástroje MSBuild s cíli sestavení.

- Použití nástroje MSBuild s vlastnostmi buildu.

- Použití nástroje MSBuild s 64m kompilátorem a nástroji.

- Použití nástroje MSBuild s různými sadami nástrojů.

- Přidávání přizpůsobení nástroje MSBuild.

### <a name="using-msbuild-with-build-targets"></a>Použití nástroje MSBuild s cíli sestavení

*Cíl sestavení* je pojmenovaná sada předdefinovaných nebo uživatelsky definovaných příkazů, které lze spustit během sestavení. K určení cíle sestavení použijte možnost příkazového řádku cíle (`/t`). V případě projektu `myproject` příkladu předdefinovaný **čistý** cíl odstraní všechny soubory ve složce Debug a vytvoří nový soubor protokolu.

Na příkazovém řádku zadejte následující příkaz pro vyčištění `myproject`.

`msbuild myproject.vcxproj /t:clean`

### <a name="using-msbuild-with-build-properties"></a>Použití nástroje MSBuild s vlastnostmi sestavení

Možnost příkazového řádku vlastnosti (`/p`) umožňuje přepsat vlastnost v souboru sestavení projektu. V projektu `myproject` příkladu je konfigurace verze nebo sestavení ladění určena vlastností `Configuration`. A operační systém, který je určen ke spuštění sestavené aplikace, je určen vlastností `Platform`.

Na příkazovém řádku zadejte následující příkaz pro vytvoření ladicího sestavení aplikace `myproject`, které je určeno ke spuštění v 32 bitových oknech.

`msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`

Předpokládejme, že `myproject` ukázkový projekt také definuje konfiguraci pro 64 Windows a další konfiguraci pro vlastní operační systém s názvem `myplatform`.

Na příkazovém řádku zadejte následující příkaz, který vytvoří sestavení pro vydání, které běží v 64-bitových oknech.

`msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`

Na příkazovém řádku zadejte následující příkaz, který vytvoří sestavení pro vydání pro `myplatform`.

`msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`

### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>Použití nástroje MSBuild s 64 kompilátorem a nástroji

Pokud jste nainstalovali Visual Studio na 64 Windows, nainstalují se standardně 64 nativní a křížové nástroje x64. Nástroj MSBuild můžete nakonfigurovat tak, aby používal 64 kompilátor a nástroje pro sestavení aplikace nastavením vlastnosti `PreferredToolArchitecture`. Tato vlastnost nemá vliv na vlastnosti konfigurace projektu nebo platformy. Ve výchozím nastavení se používá 32 verze nástrojů. Chcete-li určit 64 verzi kompilátoru a nástrojů, přidejte následující prvek skupiny vlastností do souboru projektu MyProject. vcxproj `Microsoft.Cpp.default.props` za \<elementu Import/>:

```xml
<PropertyGroup>
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>
</PropertyGroup>
```

Na příkazovém řádku zadejte následující příkaz pro použití 64 bitových nástrojů k sestavení aplikace.

`msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="using-msbuild-with-a-different-toolset"></a>Použití nástroje MSBuild s jinou sadou nástrojů

Máte-li sady nástrojů a knihovny pro jiné verze aplikace Visual C++ , nástroj MSBuild může sestavovat aplikace buď pro aktuální verzi C++ vizuálu, nebo pro ostatní nainstalované verze. Pokud jste například nainstalovali sadu Visual Studio 2012, chcete-li zadat sadu nástrojů C++ Visual 11,0 pro systém Windows XP, přidejte následující element skupiny vlastností do souboru projektu MyProject. vcxproj `Microsoft.Cpp.props` za \<elementu Import/>:

```xml
<PropertyGroup>
    <PlatformToolset>v110_xp</PlatformToolset>
</PropertyGroup>
```

Chcete-li projekt znovu sestavit pomocí sady C++ nástrojů Visual 11,0 Windows XP, zadejte následující příkazy:

`msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`

### <a name="adding-msbuild-customizations"></a>Přidávání přizpůsobení nástroje MSBuild

Nástroj MSBuild poskytuje různé způsoby přizpůsobení procesu sestavení. Následující témata ukazují, jak přidat vlastní kroky sestavení, nástroje a události do projektu nástroje MSBuild:

- [Postupy: Přidání vlastního kroku sestavení do projektů MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md)

- [Postupy: Přidání vlastních nástrojů sestavení do projektů MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md)

- [Postupy: Použití událostí sestavení v projektech MSBuild](how-to-use-build-events-in-msbuild-projects.md)
