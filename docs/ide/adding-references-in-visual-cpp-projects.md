---
title: "Přidání odkazů v projektech Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.References
dev_langs:
- C++
helpviewer_keywords:
- Add References Dialog Box (C++)
- .NET Framework (C++), Add References Dialog Box
ms.assetid: 12b8f571-0f21-40b3-9404-5318a57e9cb5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7bacb5663d8e06ee5a10629c547de6f96219697e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="adding-references-in-visual-c-projects"></a>Přidání odkazů v projektech v jazyce Visual C++
Je velmi běžné programy provést volání do rozhraní API v jiné binární soubory, například knihovny DLL, komponent prostředí Windows Runtime, rozšíření sady SDK, komponenty modelu COM a sestavení .NET. Tak, aby váš program vyhledá tyto další binární soubory závisí typu projektu a typ binárního souboru.  
  
 V nativním projektu jazyka C++ Pokud spotřebovávají nativní knihovny DLL nebo klasické komponenty COM, není vytvářen jiný projekt ve vašem řešení pomocí LoadLibrary nebo CoCreateInstance zadejte cestu k binárního souboru, jinak umožní systému, vyhledejte je podle konkrétní – Úvod definované l umístění.  
  
 V jiné typy projektů, jako jsou projekty UWP nebo C + +/ CLI projekty, nebo při binárního souboru je produkovaný jiného projektu ve vašem řešení, můžete přidat *odkaz* sestavení, komponenty nebo projektu.   Odkaz je v podstatě sada dat, která umožňuje váš program pro vyhledání a komunikaci s binárního souboru.       Když přidáte odkaz, Visual Studio zpracovává dolní úrovně podrobností. Lze nastavit odkazy z projektu jazyka C++ do .NET Frameworkassemblies (C + +/ CLI pouze), klikněte pravým tlačítkem na komponenty modelu COM, další projekty ve vašem řešení včetně sdílených projektů nebo připojení služby, **odkazy** uzlu v **Průzkumníku řešení** se zprovoznit **správce odkazů**. Co se zobrazí v správce odkazů se liší v závislosti na typu vašeho projektu.  
  
 V nativním projektu jazyka C++ (ATL) koncept z *odkazy* se vztahuje pouze na jiné projekty v řešení, včetně sdílených projektů tak, aby se všechny můžete vidět v **správce odkazů**:  
  
 ![Visual C & č. 43; & č. 43; Správce odkazů &#40; Projekty knihovny ATL &#41; ] (../ide/media/visual-c---reference-manager--atl-projects-.png "Správce odkazů visual C++ (projekty knihovny ATL)")  
  
 V jazyce C + +/ CLI nebo univerzální platformu Windows projektu koncept odkazy se vztahuje na více druhů binárních souborů kromě jiných projekty v řešení.  Tyto jsou všechny přístupné **správce odkazů**.
  
## <a name="reference-properties"></a>Referenční dokumentace vlastnosti  
 Jednotlivé typy odkaz má vlastnosti. Vlastnosti můžete zobrazit výběrem odkaz v Průzkumníku řešení a stisknutím klávesy **Alt + Enter**, nebo klikněte pravým tlačítkem na a výběrem možnosti **vlastnosti**. Některé vlastnosti jsou jen pro čtení a nelze jej změnit některé. Však obvykle nemusíte ručně úpravou těchto vlastností.  
  
### <a name="activex-reference-properties"></a>Vlastnosti odkazu ActiveX  
 Vlastnosti odkazu ActiveX jsou k dispozici pouze pro odkazy na COM – součásti. Tyto vlastnosti se zobrazí jenom v případě, že je vybraný komponenty modelu COM v **odkazy** podokně. Vlastnosti nemůže být upraven.  
  
 **Úplná cesta ovládacích prvků**  
 Zobrazuje cestu k adresáři odkazovaný ovládací prvek.  
  
 **Ovládací prvek GUID**  
 Zobrazuje identifikátor GUID pro ovládací prvek ActiveX.  
  
 **Verze ovládacího prvku**  
 Zobrazí verzi odkazovaného ovládacího prvku ActiveX.  
  
 **Název knihovny typů**  
 Zobrazuje název odkazovaného typu knihovny.  
  
 **Nástroj obálky**  
 Zobrazí nástroj, který slouží k vytvoření sestavení vzájemné spolupráce z odkazovaného knihovny COM nebo ovládací prvek ActiveX.  
  
### <a name="assembly-reference-properties"></a>Referenční dokumentace vlastnosti sestavení  
 Sestavení referenční dokumentace vlastnosti jsou k dispozici pouze pro odkazy na rozhraní .NET Frameworkassemblies v jazyce C + +/ CLI projekty. Tyto vlastnosti se zobrazí jenom v případě, že je vybraný .NET Frameworkassembly v **odkazy** podokně. Vlastnosti nemůže být upraven.  
  
 **Relativní cesta**  
 Zobrazuje relativní cestu z adresáře projektu na odkazované sestavení.  
  
### <a name="build-properties"></a>Vlastnosti sestavení  
 Následující vlastnosti jsou k dispozici na různé druhy odkazy. Ty umožňují určit způsob sestavení s odkazy.  
  
 **Zkopírujte místní**  
 Určuje, jestli se má automaticky kopírovat odkazované sestavení do cílového umístění během sestavení.  
  
 **Zkopírujte místní satelitní sestavení**  
 Určuje, jestli se má automaticky kopírovat satelitní sestavení odkazovaného sestavení do cílového umístění během sestavení. Použít jen v případě **místní kopie** je `true`.  
  
 **Odkaz na sestavení výstupu**  
 Určuje, že je toto sestavení používá v procesu sestavení. Pokud `true`, sestavení se používá v příkazovém řádku kompilátoru během sestavení.  
  
### <a name="project-to-project-reference-properties"></a>Odkaz na projekt na projekt vlastnosti  
 Zadejte následující vlastnosti *odkaz na projekt na projekt* z projektu, který je vybraný v **odkazy** podokně do jiného projektu ve stejném řešení. Další informace najdete v tématu [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project).  
  
 **Propojení závislosti knihoven**  
 Pokud je tato vlastnost **True**, odkazy systému projektu do projektu závislé soubory .lib, které vytváří nezávislé projektu. Obvykle zadáte **True**.  
  
 **Identifikátor projektu**  
 Jednoznačně identifikuje nezávislé projektu. Hodnota vlastnosti je interní systém identifikátor GUID, který nelze změnit.  
  
 **Použití vstupů závislosti knihovny**  
 Pokud je tato vlastnost **False**, systém projektu nepropojí do projektu závislé soubory .obj vyprodukované nezávislé projektu knihovny. Tato hodnota v důsledku toho zakáže přírůstkové propojování. Obvykle zadáte **False** vzhledem k tomu, že vytváření aplikace může trvat dlouhou dobu, pokud existují mnoha nezávislé projektů.  
  
### <a name="reference-properties"></a>Referenční dokumentace vlastnosti  
 Následující vlastnosti se nacházejí na odkazy na sestavení modelu COM a .NET a nemůže být upraven.  
  
 **Název sestavení**  
 Zobrazí název sestavení pro odkazované sestavení.  
  
 **Jazyková verze**  
 Zobrazí jazykovou verzi vybraný odkaz.  
  
 **Popis**  
 Zobrazí popis vybraný odkaz.  
  
 **Úplná cesta**  
 Zobrazuje cestu k adresáři odkazované sestavení.  
  
 **Identita**  
 Pro rozhraní .NET Frameworkassemblies zobrazí úplnou cestu. Pro komponenty modelu COM zobrazuje identifikátor GUID.  
  
 **Popisek**  
 Zobrazí popisek odkazu.  
  
 **Jméno**  
 Zobrazí název odkazu.  
  
 **Token veřejného klíče**  
 Zobrazí token veřejného klíče, který se používá k identifikaci odkazované sestavení.  
  
 **Silné jméno**  
 `true`Pokud odkazované sestavení se silným názvem. Silně pojmenované sestavení je jednoznačně verzí.  
  
 **Verze**  
 Zobrazí verzi odkazované sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Stránky vlastností](../ide/property-pages-visual-cpp.md)   
 [Práce s vlastnostmi projektu](../ide/working-with-project-properties.md)