---
title: "Návod: Vytvoření projektu Visual C++ pomocí nástroje MSBuild | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: msbuild.cpp.walkthrough.createproject
dev_langs: C++
helpviewer_keywords: 'msbuild (c++), walkthrough: create a project'
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 92b954f334517adc22ca17f8324ec1a78819d9f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>Návod: Vytvoření projektu jazyka Visual C++ pomocí nástroje MSBuild
Tento návod ukazuje, jak používat [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] pro vytvoření projektu Visual C++ v příkazovém řádku. Se dozvíte, jak vytvořit zdrojové soubory C++ a soubor projektu na základě XML pro konzolovou aplikaci Visual C++. Po vytvoření projektu, se dozvíte, jak k přizpůsobení procesu sestavení.  
  
 Tento návod znázorňuje následující úlohy:  
  
-   Vytváření C++ zdrojové soubory pro váš projekt.  
  
-   Vytváření XML [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] souboru projektu.  
  
-   Pomocí [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] k sestavení projektu.  
  
-   Pomocí [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] k přizpůsobení projektu.  
  
## <a name="prerequisites"></a>Požadavky  
 Budete potřebovat k dokončení tohoto názorného postupu:  
  
-   [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)]  
  
-   Obecné znalosti o [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] systému.  
  
## <a name="creating-the-c-source-files"></a>Vytváření C++ zdrojové soubory  
 V tomto návodu vytvoříte projekt, který obsahuje zdrojový soubor a soubor hlaviček. Main.cpp souboru zdroj obsahuje hlavní funkce konzolové aplikace. Main.h soubor záhlaví obsahuje kód pro zahrnout soubor hlaviček, iostream. Můžete vytvořit tyto soubory C++ pomocí [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] nebo textovém editoru.  
  
#### <a name="to-create-the-c-source-files-for-your-project"></a>Chcete-li vytvořit C++ zdrojové soubory pro svůj projekt  
  
1.  Vytvořte adresář pro váš projekt.  
  
2.  Vytvoření souboru, který je pojmenován main.cpp a přidejte následující kód k tomuto souboru:  
  
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
  
3.  Vytvoření souboru, který je pojmenován main.h a přidejte následující kód k tomuto souboru:  
  
    ```hlsl  
    // main.h: the application header code.  
    /* Additional source code to include. */  
    ```  
  
## <a name="creating-the-xml-msbuild-project-file"></a>Vytvoření projektu nástroje MSBuild souboru XML  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] Projektový soubor je soubor XML, který obsahuje kořenový element projektu (\<Projekt >). V následujícím příkladu projektu \<Projekt > element obsahuje sedm podřízených elementů:  
  
-   Tři položky skupiny značky (\<ItemGroup >), zadejte konfigurací projektu a platformy, název zdrojového souboru a název souboru záhlaví.  
  
-   Tři importovat značky (\<Import >), zadejte umístění nastavení Microsoft Visual C++.  
  
-   Vlastnost skupiny značky (\<PropertyGroup >), který určuje nastavení projektu.  
  
#### <a name="to-create-the-msbuild-project-file"></a>Chcete-li vytvořit soubor projektu nástroje MSBuild  
  
1.  Pomocí textového editoru vytvořte soubor projektu s názvem `myproject.vcxproj`a poté přidejte následující kořenové \<Projekt > elementu. Vložit elementy v následujících krocích postupu mezi kořenu \<Projekt > značky:  
  
    ```xml  
    <Project DefaultTargets="Build" ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    </Project>  
    ```  
  
2.  Přidejte následující dva \<ProjectConfiguration > podřízených elementů v \<ItemGroup > elementu. Podřízený element určuje ladění a konfigurace pro operační systém Windows 32bitová verze:  
  
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
  
3.  Přidejte následující \<importu / > elementu, který určuje cestu k výchozí nastavení C++ pro tento projekt:  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />  
  
    ```  
  
4.  Přidejte následující element skupiny vlastnost (\<PropertyGroup >) určující, že dvě vlastnosti projektu:  
  
    ```xml  
    <PropertyGroup>  
      <ConfigurationType>Application</ConfigurationType>  
      <PlatformToolset>v120</PlatformToolset>  
    </PropertyGroup>  
    ```  
  
5.  Přidejte následující \<importu / > elementu, který určuje cestu aktuální nastavení C++ pro tento projekt:  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />  
    ```  
  
6.  Přidejte následující \<ClCompile > podřízený element v \<ItemGroup > elementu. Podřízený element určuje název zdrojového souboru C/C++ kompilace:  
  
    ```xml  
    <ItemGroup>  
      <ClCompile Include="main.cpp" />  
    </ItemGroup>  
    ```  
  
7.  Přidejte následující \<ClInclude > podřízený element v \<ItemGroup > elementu. Podřízený element určuje název hlavičky souboru pro C/C++ zdrojového souboru:  
  
    ```xml  
    <ItemGroup>  
      <ClInclude Include="main.h" />  
    </ItemGroup>  
    ```  
  
8.  Přidejte následující \<Import > elementu, který určuje cestu k souboru, který definuje cíle pro tento projekt:  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />  
  
    ```  
  
### <a name="complete-project-file"></a>Dokončení souboru projektu  
 Následující kód ukazuje soubor dokončený projekt, který jste vytvořili v předchozím postupu.  
  
```xml  
<Project DefaultTargets="Build" ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
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
    <PlatformToolset>v120</PlatformToolset>  
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
 Zadejte následující příkaz na příkazovém řádku k vytvoření konzolové aplikace:  
  
```  
msbuild myproject.vcxproj /p:configuration=debug  
```  
  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]Vytvoří adresář pro výstupní soubory a zkompiluje a odkazů projektu pro generování Myproject.exe program. Po dokončení procesu sestavení, použijte následující příkaz ke spuštění aplikace:  
  
```  
myproject  
```  
  
 Aplikace by se měla zobrazovat "Hello, z nástroje MSBuild!" v okně konzoly.  
  
## <a name="customizing-your-project"></a>Přizpůsobení projektu  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]Umožňuje provést předdefinované sestavení cílů, použije uživatelem definované vlastnosti a použijte vlastní nástroje, události a kroky sestavení. Tato část ukazuje následující úlohy:  
  
-   Pomocí [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] s sestavení cílů.  
  
-   Pomocí [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] s vlastnostmi sestavení.  
  
-   Pomocí [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] s 64bitový kompilátor a nástroje.  
  
-   Pomocí [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] s jinou modulové.  
  
-   Přidání [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] přizpůsobení.  
  
### <a name="using-msbuild-with-build-targets"></a>Pomocí nástroje MSBuild sestavení cílů  
 A *sestavení cíl* pojmenovanou sadu předdefinovaných nebo uživatelsky definovaných příkazy, které mohou být provedeny během sestavení. Použít možnost příkazového řádku cíl (**/t**) k určení cíl sestavení. U `myproject` příklad projektu, předdefinovanou **čisté** cíle odstraní všechny soubory ve složce ladění a vytvoří nový soubor protokolu.  
  
 Na příkazovém řádku zadejte následující příkaz pro čištění `myproject`.  
  
 `msbuild myproject.vcxproj /t:clean`  
  
### <a name="using-msbuild-with-build-properties"></a>Pomocí nástroje MSBuild vlastnosti sestavení  
 Vlastnost příkazového řádku (**/p**) můžete přepsat vlastnost v souboru sestavení projektu. V `myproject` konfigurace sestavení projektu, vydání nebo ladění příkladu je zadána `Configuration` vlastnost. A je zadána operačního systému, který slouží ke spuštění aplikace vytvořené `Platform` vlastnost.  
  
 Na příkazovém řádku zadejte následující příkaz k vytvoření nové sestavení ladicí `myproject` aplikace, která je určená ke spuštění na 32bitový systém Windows.  
  
 `msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`  
  
 Předpokládáme, že `myproject` příklad projektu také definuje konfiguraci pro 64bitový systém Windows a další konfigurace pro vlastního operačního systému s názvem `myplatform`.  
  
 Na příkazovém řádku zadejte následující příkaz pro vytvoření verze sestavení, která běží na 64bitovém systému Windows.  
  
 `msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`  
  
 Na příkazovém řádku zadejte následující příkaz k vytvoření sestavení pro vydání pro `myplatform`.  
  
 `msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`  
  
### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>Pomocí 64bitový kompilátor a nástroje MSBuild  
 Pokud jste nainstalovali Visual C++ v 64bitovém systému Windows, ve výchozím nastavení, nenainstalují se 64-bit x64 nativní a multiplatformní nástroje. Můžete nakonfigurovat [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] pomocí nástrojů pro 64bitový kompilátor a sestavit aplikaci nastavením `PreferredToolArchitecture` vlastnost. Tato vlastnost nemá vliv na konfiguraci nebo platformu vlastností projektu. Ve výchozím nastavení se používá 32bitovou verzi nástroje. Zadat 64bitovou verzi kompilátoru a nástroje, přidejte následující element skupiny vlastnost k souboru projektu Myproject.vcxproj po `Microsoft.Cpp.default.props` \<importu / > element:  
  
```xml  
<PropertyGroup>  
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>  
</PropertyGroup>  
```  
  
 Na příkazovém řádku zadejte následující příkaz k sestavení aplikace pomocí nástrojů pro 64bitové verze.  
  
 `msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`  
  
### <a name="using-msbuild-with-a-different-toolset"></a>Pomocí různých nástrojů MSBuild  
 Pokud máte modulové a knihovny pro jiné verze aplikace Visual C++ nainstalovaná, [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] mohou vytvářet aplikace pro buď aktuální verze Visual C++, nebo pro druhý nainstalované verze. Například pokud jste nainstalovali [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)], k určení sady nástrojů Visual C++ 11.0 pro systém Windows XP, přidejte následující element skupiny vlastnost k souboru projektu Myproject.vcxproj po Microsoft.Cpp.props `<Import />` element:  
  
```xml  
<PropertyGroup>  
    <PlatformToolset>v110_xp</PlatformToolset>  
</PropertyGroup>  
```  
  
 Chcete-li znovu sestavte projekt pomocí sady nástrojů Visual C++ 11.0 Windows XP, zadejte jeden z následujících příkazů:  
  
 `msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`  
  
 `msbuild myproject.vcxproj /t:rebuild`  
  
### <a name="adding-msbuild-customizations"></a>Přidání přizpůsobení nástroje MSBuild  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]poskytuje různé způsoby, jak přizpůsobit proces sestavení. Následující témata ukazují, jak přidat vlastní kroky sestavení, nástroje a události na váš [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] projektu:  
  
-   [Postupy: Přidání vlastního kroku sestavení do projektů MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)  
  
-   [Postupy: Přidání vlastních nástrojů sestavení do projektů MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)  
  
-   [Postupy: Použití událostí sestavení v projektech MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)