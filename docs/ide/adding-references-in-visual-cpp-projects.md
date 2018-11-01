---
title: Přidání odkazů v projektech v jazyce Visual C++
ms.date: 11/04/2016
f1_keywords:
- VC.Project.References
helpviewer_keywords:
- Add References Dialog Box (C++)
- .NET Framework (C++), Add References Dialog Box
ms.assetid: 12b8f571-0f21-40b3-9404-5318a57e9cb5
ms.openlocfilehash: c50a726b0e5b6e175bd7256ab5a5d93d6b172601
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583793"
---
# <a name="adding-references-in-visual-c-projects"></a>Přidání odkazů v projektech v jazyce Visual C++

Je velmi běžné, že aplikace provést volání do rozhraní API v jiných binárních souborů, jako je například knihovny DLL, součástí prostředí Windows Runtime, sady SDK rozšíření, komponenty modelu COM a sestavení .NET. Způsob, jakým váš program vyhledá tyto další binární soubory závisí na typu projektu a typ binárního souboru.

V nativních projektů C++ Pokud jsou využívání nativní knihovnu DLL nebo klasické komponenty COM, který není generovaná systémem jiného projektu ve vašem řešení pomocí LoadLibrary nebo funkce CoCreateInstance pro zadejte cestu k binárním souboru, jinak nechejte systém najít hledáním v konkrétní – Úvod umístění definice l.

V ostatních typů projektů, jako jsou projekty UPW nebo C + +/ projekty rozhraní příkazového řádku, nebo když binární soubor vytvořil jiný projekt ve vašem řešení, přidejte *odkaz* k sestavení, komponenta nebo projektu.   Odkaz je v podstatě sadu dat, která umožňuje program k vyhledání a komunikaci s binárního souboru.       Když přidáte odkaz, Visual Studio zpracovává podrobnosti nízké úrovně. Nastavit odkazy z projektu C++ do .NET Frameworkassemblies (C + +/ CLI pouze), klikněte pravým tlačítkem na model COM, jiné projekty v vašeho řešení, včetně sdílených projektů nebo připojené služby, **odkazy** uzel v **Průzkumníka řešení** zobrazíte **správce odkazů**. Co se zobrazí v okně Správce odkazů se liší v závislosti na typu vašeho projektu.

Nativní projekt C++ (ATL) koncept z *odkazy* platí jenom do jiných projektů v řešení, včetně sdílených projektů, takže to je všechno se zobrazí v **správce odkazů**:

![Visual C&#43; &#43; správce odkazů &#40;projektů knihovny ATL&#41;](../ide/media/visual-c---reference-manager--atl-projects-.png "správce odkazů Visual C++ (ATL – projekty)")

V jazyce C + +/ projekt rozhraní příkazového řádku nebo univerzální platformu Windows, koncept odkazů se vztahuje na víc druhů binárních souborů kromě jiných projektů v řešení.  Tyto jsou všechny přístupné **správce odkazů**.

## <a name="reference-properties"></a>Vlastnosti odkazu

Každý druh odkazu má vlastnosti. Vlastnosti můžete zobrazit výběrem odkazu v Průzkumníku řešení a stisknutím klávesy **Alt + Enter**, nebo pravým tlačítkem myši a zvolíte možnost **vlastnosti**. Některé vlastnosti jsou jen pro čtení a některé je možné upravit. Však obvykle není nutné ručně upravit tyto vlastnosti.

### <a name="activex-reference-properties"></a>Vlastnosti odkazu ActiveX

Vlastnosti odkazu ActiveX jsou dostupné pouze pro odkazy na komponenty modelu COM. Tyto vlastnosti se zobrazí, jenom když vyberete komponenty modelu COM v **odkazy** podokně. Vlastnosti nelze změnit.

- **Úplná cesta ovládacího prvku**

   Zobrazuje cestu k adresáři odkazovaného ovládacího prvku.

- **GUID ovládacího prvku**

   Zobrazuje identifikátor GUID pro ovládací prvek ActiveX.

- **Verze ovládacího prvku**

   Zobrazuje verze odkazovaného ovládacího prvku ActiveX.

- **Název knihovny typů**

   Zobrazí název odkazované knihovny typů.

- **Nástroj obálky**

   Zobrazí nástroj, který se používá k vytvoření sestavení interop z odkazované knihovny COM nebo ovládacího prvku ActiveX.

### <a name="assembly-reference-properties"></a>Vlastnosti odkazu na sestavení

Vlastnosti odkazu na sestavení jsou k dispozici pouze pro odkazy na Frameworkassemblies .NET v jazyce C + +/ CLI projekty. Tyto vlastnosti se zobrazí, jenom když vyberete .NET Frameworkassembly v **odkazy** podokně. Vlastnosti nelze změnit.

- **Relativní cesta**

   Zobrazuje relativní cesta z adresáře projektu k odkazovanému sestavení.

### <a name="build-properties"></a>Vlastnosti sestavení

Následující vlastnosti jsou k dispozici na různé typy odkazů. Umožňují určit, jak sestavení s odkazy.

- **Kopírovat místní**

   Určuje, jestli se mají automaticky kopírovat odkazované sestavení do cílového umístění během sestavení.

- **Zkopírovat místní satelitní sestavení**

   Určuje, jestli se mají automaticky kopírovat satelitní sestavení odkazovaného sestavení do cílového umístění během sestavení. Použít jenom v případě **Kopírovat místně** je **true**.

- **Výstup referenčního sestavení**

   Určuje, že toto sestavení se používá v procesu sestavení. Pokud **true**, sestavení se používá na příkazový řádek kompilátoru během sestavení.

### <a name="project-to-project-reference-properties"></a>Vlastnosti odkazu typu projekt projekt

Definujte následující vlastnosti *odkaz typu projekt projekt* z projektu, který je vybraný v **odkazy** podokno do jiného projektu ve stejném řešení. Další informace najdete v tématu [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project).

- **Propojit závislé položky knihoven**

   Pokud je tato vlastnost **True**, systém projektu propojeny do závislý projekt lib souborů, které jsou vytvářeny nezávislé projektem. Obvykle můžete zadat **True**.

- **Identifikátor projektu**

   Jednoznačně identifikuje nezávislé projektu. Hodnota vlastnosti je interní systém identifikátor GUID, který nemůže být upraven.

- **Použít vstupy závislých položek knihoven**

   Pokud je tato vlastnost **False**, systém projektu nebude propojení do závislého projektu soubory .obj pro knihovnu vytvářených nezávislé projektu. V důsledku toho tato hodnota zakáže přírůstkové propojení. Obvykle můžete zadat **False** protože vytváření aplikace může trvat dlouhou dobu, pokud existují mnoho nezávislé projektů.

### <a name="reference-properties"></a>Vlastnosti odkazu

Následující vlastnosti se nacházejí na odkazy na sestavení modelu COM a .NET a nejde změnit.

- **Název sestavení**

   Zobrazí název sestavení pro odkazované sestavení.

- **Jazyková verze**

   Zobrazí jazyková verze vybraného odkazu.

- **Popis**

   Zobrazí popis vybraného odkazu.

- **Úplná cesta**

   Zobrazuje cestu k adresáři odkazovaných sestavení.

- **Identita**

   .NET Frameworkassemblies zobrazí úplnou cestu. Pro komponenty modelu COM zobrazuje identifikátor GUID.

- **Popisek**

   Zobrazí popisek odkazu.

- **Jméno**

   Zobrazí název odkazu.

- **Token veřejného klíče**

   Zobrazí token veřejného klíče, který se používá k identifikaci odkazovaného sestavení.

- **Silným názvem**

   `true` Pokud má odkazované sestavení silný název. Silně pojmenované sestavení mají je jedinečné verze.

- **Verze**

   Verze odkazovaného sestavení zobrazí.

## <a name="see-also"></a>Viz také

[Stránky vlastností](../ide/property-pages-visual-cpp.md)<br>
[Práce s vlastnostmi projektu](../ide/working-with-project-properties.md)