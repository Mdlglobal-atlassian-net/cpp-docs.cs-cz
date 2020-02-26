---
title: Dědičnost vlastností v projektech sady Visual Studio –C++
description: Jak dědičnost vlastností funguje v nativních projektech (MSBuild) C++ Visual Studio.
ms.date: 02/21/2020
helpviewer_keywords:
- C++ projects, property inheritance
ms.openlocfilehash: 2032ab63c7d278a080742dba8d8d0c6c3ed7a094
ms.sourcegitcommit: 9a63e9b36d5e7fb13eab15c2c35bedad4fb03ade
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77600030"
---
# <a name="property-inheritance-in-visual-studio-projects"></a>Dědičnost vlastností v projektech sady Visual Studio

Systém nativního projektu sady Visual Studio je založen na nástroji MSBuild. MSBuild definuje formáty souborů a pravidla pro vytváření projektů libovolného druhu. Spravuje většinu složitosti sestavení pro více konfigurací a platforem. Zjistíte, že je užitečné pochopit, jak to funguje. To je obzvláště důležité, pokud chcete definovat vlastní konfigurace. Nebo můžete vytvořit opakovaně použitelné sady vlastností, které můžete sdílet a importovat do více projektů.

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>Soubor. vcxproj,. props a soubory. targets

Vlastnosti projektu jsou uloženy buď přímo v souboru projektu ( *`.vcxproj`* ), nebo v jiných *`.targets`* nebo *`.props`* souborech, které soubor projektu importuje a které dodávají výchozí hodnoty. Pro Visual Studio 2015 se tyto soubory nacházejí v *`\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140`* . V případě sady Visual Studio 2017 jsou tyto soubory umístěny v *`\Program Files (x86)\Microsoft Visual Studio\2017\<edition>\Common7\IDE\VC\VCTargets`* , kde *`<edition>`* je nainstalovaná edice sady Visual Studio. V aplikaci Visual Studio 2019 se tyto soubory nacházejí v *`\Program Files (x86)\Microsoft Visual Studio\2019\<edition>\MSBuild\Microsoft\VC\v160`* . Vlastnosti jsou také uloženy v jakémkoli vlastním *`.props`* soubory, které můžete přidat do svého projektu. Důrazně doporučujeme, abyste tyto soubory neupravili ručně. Místo toho použijte stránky vlastností v integrovaném vývojovém prostředí k úpravě všech vlastností, zejména těch, které se podílejí na dědění, pokud nemáte hlubokou porozumět nástroji MSBuild.

Jak je uvedeno výše, může být stejná vlastnost pro stejnou konfiguraci přiřazena jinou hodnotou v těchto různých souborech. Při sestavování projektu modul MSBuild vyhodnotí soubor projektu a všechny importované soubory v přesně definovaném pořadí (popsané níže). Při vyhodnocování každého souboru všechny hodnoty vlastností definované v tomto souboru přepíšou existující hodnoty. Všechny hodnoty, které nejsou zadány, jsou zděděny ze souborů, které byly vyhodnoceny dříve. Když nastavíte vlastnost se stránkami vlastností, je také důležité věnovat pozornost tomu, kde jste ji nastavili. Pokud nastavíte vlastnost na "X" v souboru *`.props`* , ale vlastnost je v souboru projektu nastavena na "Y", projekt se sestaví s vlastností nastavenou na "y". Pokud je stejná vlastnost nastavena na "Z" na položce projektu, jako je například *`.cpp`* soubor, pak modul MSBuild použije hodnotu "z".

Zde uvádíme základní strom dědičnosti:

1. Výchozí nastavení ze sady nástrojů MSBuild CPP (.. \Program Files\MSBuild\Microsoft.Cpp\v4.0\Microsoft.Cpp.Default.props, který je importován souborem *`.vcxproj`* .)

1. Seznamy vlastností

1. soubor *`.vcxproj`* . (Může přepsat výchozí nastavení a nastavení seznamu vlastností.)

1. Metadata položek

> [!TIP]
> Na stránce vlastností je vlastnost **tučně** definována v aktuálním kontextu. Vlastnost uvedená normálním písmem je zděděná.

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>Zobrazit rozbalený soubor projektu se všemi importovanými hodnotami

Někdy je užitečné zobrazit rozbalený soubor, ve kterém zjistíte, jak je hodnota dané vlastnosti zděděna. Rozbalenou verzi zobrazíte zadáním následujícího příkazu na příkazovém řádku Visual Studio. (Podle potřeby zaměňte zástupné symboly názvy souborů, které chcete použít.)

> **MSBuild/PP:** _TEMP_ **. txt** _Mojeapl_ **. vcxproj**

Rozšířené soubory projektu mohou být velké a obtížné pochopit, pokud nejste obeznámeni s nástrojem MSBuild. Zde uvádíme základní strukturu souboru projektu:

1. Základní vlastnosti projektu, které nejsou vystaveny v integrovaném vývojovém prostředí.

1. Import *`Microsoft.cpp.default.props`* , který definuje některé základní vlastnosti nezávislé na sadě nástrojů.

1. Vlastnosti globální konfigurace (zveřejněné jako výchozí vlastnosti **PlatformToolset** a **projekt** na stránce **Obecná konfigurace** ). Tyto vlastnosti určují, která sada nástrojů a vnitřní seznamy vlastností se importují v *`Microsoft.cpp.props`* v dalším kroku.

1. Import *`Microsoft.cpp.props`* , který nastaví většinu výchozích hodnot projektu.

1. Import všech seznamů vlastností, včetně souborů *`.user`* . Tyto seznamy vlastností mohou přepsat vše kromě výchozích vlastností **PlatformToolset** a **projektu** .

1. Zbytek vlastností konfigurace projektu. Tyto hodnoty mohou přepsat nastavení provedená v seznamu vlastností.

1. Položky (soubory) spolu s příslušnými metadaty. Tyto položky jsou vždycky poslední slovo v pravidlech vyhodnocování MSBuild, a to i v případě, že se vyskytují před dalšími vlastnostmi a importy.

Další informace najdete v tématu [Vlastnosti nástroje MSBuild](/visualstudio/msbuild/msbuild-properties).

## <a name="build-configurations"></a>Konfigurace sestavení

Konfigurace je pouze libovolná skupina vlastností, které jsou zadány jako název. Visual Studio poskytuje konfigurace ladění a vydání. Každý nastaví různé vlastnosti pro sestavení ladění nebo sestavení pro vydání. Pomocí **Configuration Manager** můžete definovat vlastní konfigurace. Představují pohodlný způsob, jak seskupit vlastnosti pro konkrétní charakter sestavení.

Chcete-li získat lepší představu o konfiguracích sestavení, otevřete **Správce vlastností**. Můžete ji otevřít výběrem možnosti **zobrazit > Správce vlastností** nebo **Zobrazit > jiných oknech > Správce vlastností**v závislosti na nastaveních. **Správce vlastností** má uzly pro každou dvojici konfigurace a platforem v projektu. V každém z těchto uzlů jsou uzly pro seznamy vlastností ( *`.props`* soubory), které pro tuto konfiguraci nastavily určité vlastnosti.

![Správce vlastností](media/property-manager.png "Správce vlastností")

Například můžete přejít na podokno obecné na stránkách vlastností. Změňte vlastnost znaková sada na nenastavenou místo na použít Unicode a pak klikněte na **OK**. Správce vlastností nyní nezobrazuje žádný seznam vlastností **podpory kódování Unicode** . Je odebraný pro aktuální konfiguraci, ale pro ostatní konfigurace je stále k dispozici.

Další informace o Správce vlastností a seznamech vlastností naleznete v tématu [sdílení nebo opětovné použití C++ nastavení projektu sady Visual Studio](create-reusable-property-configurations.md).

> [!TIP]
> Soubor *`.user`* je starší verze funkce. Doporučujeme, abyste ho odstranili, aby se vlastnosti správně seskupoval podle konfigurace a platformy.
