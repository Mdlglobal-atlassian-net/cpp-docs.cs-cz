---
title: Dědičnost vlastností v projektech sady Visual Studio – C++
description: Jak funguje dědičnost vlastností v nativních projektech Visual Studio C++(I. MSBuild).
ms.date: 02/21/2020
helpviewer_keywords:
- C++ projects, property inheritance
ms.openlocfilehash: 4740c479c6cc7c877fd72b7828a8e4811826de6c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328478"
---
# <a name="property-inheritance-in-visual-studio-projects"></a>Dědičnost vlastností v projektech sady Visual Studio

Nativní projektový systém sady Visual Studio je založen na msbuildu. MSBuild definuje formáty souborů a pravidla pro vytváření projektů jakéhokoli druhu. Spravuje většinu složitosti vytváření pro více konfigurací a platforem. Zjistíte, že je užitečné pochopit, jak to funguje. To je obzvláště důležité, pokud chcete definovat vlastní konfigurace. Nebo chcete-li vytvořit opakovaně použitelné sady vlastností, které můžete sdílet a importovat do více projektů.

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>Soubor .vcxproj, soubory .props a .targets

Vlastnosti projektu jsou uloženy buď*`.vcxproj`* přímo v *`.targets`* *`.props`* souboru projektu ( ) nebo v jiných nebo souborech, které soubor projektu importuje a které poskytují výchozí hodnoty. Pro Visual Studio 2015 tyto *`\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140`* soubory jsou umístěny v . Pro Visual Studio 2017 tyto *`\Program Files (x86)\Microsoft Visual Studio\2017\<edition>\Common7\IDE\VC\VCTargets`* soubory *`<edition>`* jsou umístěny v , kde je nainstalována edice Visual Studio. V sadě Visual Studio 2019 *`\Program Files (x86)\Microsoft Visual Studio\2019\<edition>\MSBuild\Microsoft\VC\v160`* jsou tyto soubory umístěny v aplikaci . Vlastnosti jsou také *`.props`* uloženy ve všech vlastních souborech, které můžete přidat do vlastního projektu. Důrazně doporučujeme, abyste tyto soubory neupravovali ručně. Místo toho použijte stránky vlastností v rozhraní IDE k úpravě všech vlastností, zejména těch, které se účastní dědičnosti, pokud nemáte hluboké pochopení MSBuild.

Jak je uvedeno výše, stejné vlastnosti pro stejnou konfiguraci může být přiřazena jiná hodnota v těchto různých souborů. Při vytváření projektu modul MSBuild vyhodnotí soubor projektu a všechny importované soubory v dobře definovaném pořadí (popsané níže). Při vyhodnocuje se, že všechny hodnoty vlastností definované v tomto souboru přepíší existující hodnoty. Všechny hodnoty, které nejsou zadány, jsou zděděny ze souborů, které byly vyhodnoceny dříve. Když nastavíte vlastnost se stránkami vlastností, je také důležité věnovat pozornost tomu, kde ji nastavíte. Pokud nastavíte vlastnost "X" *`.props`* v souboru, ale vlastnost je nastavena na "Y" v souboru projektu, pak projekt bude stavět s vlastností nastavenou na "Y". Pokud je stejná vlastnost nastavena na "Z" *`.cpp`* na položku projektu, jako je například soubor, pak modul MSBuild použije hodnotu "Z".

Zde uvádíme základní strom dědičnosti:

1. Výchozí nastavení ze sady nástrojů CPP sestavení MSBuild (.. \Program Files\MSBuild\Microsoft.Cpp\v4.0\Microsoft.Cpp.Default.props, který je *`.vcxproj`* importován souborem.)

1. Seznamy vlastností

1. *`.vcxproj`* Soubor. (Může přepsat výchozí nastavení a nastavení seznamu vlastností.)

1. Metadata položek

> [!TIP]
> Na stránce vlastností je vlastnost **tučně** definována v aktuálním kontextu. Vlastnost uvedená normálním písmem je zděděná.

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>Zobrazení rozšířeného souboru projektu se všemi importovanými hodnotami

Někdy je užitečné zobrazit rozbalený soubor, ve kterém zjistíte, jak je hodnota dané vlastnosti zděděna. Rozbalenou verzi zobrazíte zadáním následujícího příkazu na příkazovém řádku Visual Studio. (Podle potřeby zaměňte zástupné symboly názvy souborů, které chcete použít.)

> **msbuild /pp:**_temp_**.txt** _myapp_**.vcxproj**

Rozšířené soubory projektu může být velké a obtížné pochopit, pokud jste obeznámeni s MSBuild. Zde uvádíme základní strukturu souboru projektu:

1. Základní vlastnosti projektu, které nejsou vystaveny v rozhraní IDE.

1. Import *`Microsoft.cpp.default.props`* aplikace , která definuje některé základní vlastnosti nezávislé na sadě nástrojů.

1. Vlastnosti globální konfigurace (vystavené jako **výchozí vlastnosti PlatformToolset** a **Project** na stránce **Obecné konfigurace.** Tyto vlastnosti určují, do které sady nástrojů a *`Microsoft.cpp.props`* vnitřních seznamů vlastností se importují v dalším kroku.

1. Import *`Microsoft.cpp.props`* aplikace , který nastaví většinu výchozích hodnot projektu.

1. Import všech seznamů *`.user`* vlastností včetně souborů. Tyto seznamy vlastností můžete přepsat vše kromě **PlatformToolset** a **Project** výchozí vlastnosti.

1. Zbývající vlastnosti konfigurace projektu. Tyto hodnoty mohou přepsat nastavení provedená v seznamu vlastností.

1. Položky (soubory) spolu s příslušnými metadaty. Tyto položky jsou vždy poslední slovo v pravidlech vyhodnocení MSBuild, i v případě, že k nim dojde před jinými vlastnostmi a importy.

Další informace naleznete v tématu [MSBuild Properties](/visualstudio/msbuild/msbuild-properties).

## <a name="build-configurations"></a>Konfigurace sestavení

Konfigurace je pouze libovolná skupina vlastností, které jsou uvedeny název. Visual Studio poskytuje ladění a vydání konfigurace. Každý nastaví různé vlastnosti vhodně pro sestavení ladění nebo vydání sestavení. Pomocí nástroje **Configuration Manager** můžete definovat vlastní konfigurace. Jsou to pohodlný způsob, jak seskupit vlastnosti pro konkrétní chuť sestavení.

Chcete-li získat lepší představu o konfiguracích sestavení, otevřete **Správce vlastností**. V závislosti na nastavení jej můžete otevřít tak, že zvolíte **Zobrazit správce vlastností >** nebo Zobrazit > jiný správce **vlastností windows >**. **Správce vlastností** má uzly pro každou konfiguraci a dvojici platformy v projektu. Pod každým z těchto uzlů jsou uzly pro seznamy vlastností (soubory),*`.props`* které nastavují některé specifické vlastnosti pro tuto konfiguraci.

![Správce vlastností](media/property-manager.png "Správce vlastností")

Můžete například přejít do podokna Obecné na stránkách vlastností. Změňte vlastnost Znaková sada na "Nenastavit" místo "Použít Unicode" a klepněte na tlačítko **OK**. Správce vlastností nyní nezobrazuje žádný seznam vlastností **podpory Unicode.** Je odebrán pro aktuální konfiguraci, ale je stále k dispozici pro jiné konfigurace.

Další informace o Správci vlastností a seznamech vlastností naleznete v [tématu Sdílení nebo opakované použití nastavení projektu sady Visual Studio C++](create-reusable-property-configurations.md).

> [!TIP]
> Soubor *`.user`* je starší funkce. Doporučujeme jej odstranit, aby vlastnosti správně seskupeny podle konfigurace a platformy.
