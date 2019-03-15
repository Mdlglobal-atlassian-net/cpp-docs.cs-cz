---
title: Dědičnost vlastnosti v projektech Visual Studio – C++
ms.date: 12/10/2018
helpviewer_keywords:
- Visual C++ projects, property inheritance
ms.openlocfilehash: edd6d3bf82f7a13cf6687abeba3758dcceca5e84
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823176"
---
# <a name="property-inheritance-in-visual-studio-projects"></a>Dědičnost vlastnosti v projektech Visual Studio

Systém projektu sady Visual Studio je založen na MSBuild, který definuje formáty souborů a pravidla pro vytváření projektů z jakéhokoli druhu. Nástroj MSBuild spravuje řadu složitost vytváření pro více konfigurací a platforem, ale je třeba porozumět ještě něco o tom, jak funguje. To je obzvláště důležité, pokud chcete definovat vlastní konfigurace nebo vytvářet opakovaně použitelné sady vlastností, které můžete sdílet a importovat do více projektů.

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>Soubor .vcxproj, souborech .props a souborech .targets

Vlastnosti projektu jsou uloženy přímo v souboru projektu (*.vcxproj) nebo v jiných souborech .targets nebo .props importuje soubor projektu a který poskytnout výchozí hodnoty. Pro Visual Studio 2015, tyto soubory jsou umístěny v **\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140**. Pro Visual Studio 2017, tyto soubory jsou umístěny v  **\\Program Files (x86)\\sady Microsoft Visual Studio\\2017\\_edition_\\Common7\\ Integrované vývojové prostředí\\VC\\VCTargets**, kde _edition_ je nainstalované verze sady Visual Studio. Vlastnosti jsou také uloženy v jakékoli vlastní souborech, které můžete přidat na svůj projekt. Důrazně doporučujeme, že není upravíte tyto soubory ručně a místo toho použijte stránky vlastností v prostředí IDE k úpravě všech vlastností, zejména těch, které se účastní dědičnosti, pokud nemáte velmi dostatečné povědomí o MSBuild.

Jak je uvedeno výše, může být přiřazen jinou hodnotu v těchto různých souborech stejnou vlastnost pro stejnou konfiguraci. Při sestavování projektu stroji MSBuild engine vyhodnotí jako soubor projektu a všechny importované soubory v dobře definovaných pořadí (popsaných níže). Jak se vyhodnotí každého souboru, všechny hodnoty vlastností, které jsou definované v tomto souboru přepíše existující hodnoty. Všechny hodnoty, které nejsou zadané se dědí ze souborů, které byly dříve vyhodnoceny. Proto když nastavíte vlastnost s použitím stránek vlastností, je také důležité věnovat pozornost tomu, kde nastavujete. Pokud vlastnost nastavíte na "X" v souboru .props, ale vlastnost je nastavena na "Y" v souboru projektu, projekt bude sestaven s nastavenou na "Y". Pokud stejnou vlastnost nastavená na "Z" na položku projektu, jako je například soubor .cpp, stroji MSBuild engine použije hodnotu "Z". 

Zde uvádíme základní strom dědičnosti:

1. Výchozí nastavení ze sady nástrojů MSBuild CPP (..\Program Files\MSBuild\Microsoft.Cpp\v4.0\Microsoft.Cpp.Default.props, tj. soubor importovaný souborem .vcxproj.)

2. Seznamy vlastností

3. Soubor .vcxproj. (Může přepsat výchozí nastavení a nastavení seznamu vlastností.)

4. Metadata položek

> [!TIP]
> Na stránce vlastností je vlastnost v `bold` je definována v aktuálním kontextu. Vlastnost uvedená normálním písmem je zděděná.

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>Zobrazit soubor rozšířené projekt se všemi hodnotami importované

Někdy je užitečné zobrazit rozbalený soubor, ve kterém zjistíte, jak je hodnota dané vlastnosti zděděna. Rozbalenou verzi zobrazíte zadáním následujícího příkazu na příkazovém řádku Visual Studio. (Podle potřeby zaměňte zástupné symboly názvy souborů, které chcete použít.)

**Nástroj MSBuild /pp:** *temp* **.txt** *myapp* **.vcxproj**

Rozbalené soubory projektů mohou být velké a náročné na orientaci, pokud dobře neznáte nástroj MSBuild. Zde uvádíme základní strukturu souboru projektu:

1. Základní vlastnosti projektu, které nejsou vystaveny v integrovaném vývojovém prostředí

2. Import souboru Microsoft.cpp.default.props, který definuje některé základní vlastnosti nezávislé na sadách nástrojů

3. Vlastnosti globální konfigurace (vystavena jako **PlatformToolset** a **projektu** výchozí vlastnosti na **Obecná konfigurace** stránky. Tyto vlastnosti určují, která sada nástrojů a vnitřní seznamy vlastností se importují v souboru Microsoft.cpp.props v dalším kroku.

4. Import souboru Microsoft.cpp.props, který nastaví většinu výchozích hodnot projektu

5. Import všech seznamů vlastností, včetně souborů .user. Tyto seznamy vlastností mohou přepsat vše kromě **PlatformToolset** a **projektu** výchozí vlastnosti.

6. Zbývající vlastnosti konfigurace projektu Tyto hodnoty mohou přepsat nastavení provedená v seznamu vlastností.

7. Položky (soubory) spolu s příslušnými metadaty. Ty v pravidlech vyhodnocování MSBuild vždy dostanou prioritu, i když se vyskytují před dalšími vlastnostmi a importy.

Další informace najdete v tématu [vlastnosti nástroje MSBuild](/visualstudio/msbuild/msbuild-properties).

## <a name="build-configurations"></a>Konfigurace sestavení

Konfigurace je právě libovolného skupiny vlastností, které je přiřazen název. Visual Studio poskytuje konfigurace Debug a Release a každý nastaví různé vlastnosti pro sestavení pro ladění nebo sestavení pro vydání. Můžete použít **nástroje Configuration Manager** definovat vlastní konfigurace jako pohodlný způsob, jak vlastnosti skupiny pro konkrétní charakter sestavení. 

Chcete-li získat lepší představu o konfiguracích sestavení, otevřete **Správce vlastností** výběrem **zobrazení &#124; Správce vlastností** nebo **zobrazení &#124; ostatní Windows &#124; Správce vlastností**  v závislosti na nastavení. **Správce vlastností** má uzlů pro každý pár konfigurace a platformy v projektu. U každého z těchto uzlů jsou uzly pro seznamy vlastností (souborech .props), které nastavit některé specifické vlastnosti pro tuto konfiguraci.

![Property Manager](media/property-manager.png "Property Manager")

Pokud přejděte do podokna obecné na stránkách vlastností a nastavte vlastnost znaková sada na "Nenastaveno" místo "Použití Unicode" a klikněte na tlačítko **OK**, se zobrazí Správce vlastností žádné **Podpora kódování Unicode** vlastností aktuální konfiguraci, ale bude stále existovat pro další konfigurace.

Další informace o Správci vlastností a vlastností najdete v tématu [sdílené složky nebo resuse nastavení projektu Visual Studio C++](create-reusable-property-configurations.md).

> [!TIP]
> Soubor .user je starší verze funkce a doporučujeme odstranit aby bylo možné zachovat vlastnosti správně seskupeny podle konfigurace a platformy.



