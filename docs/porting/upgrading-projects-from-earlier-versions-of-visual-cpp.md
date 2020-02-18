---
title: Upgradovat C++ projekty z dřívějších verzí sady Visual Studio
description: Postup upgradu projektů společnosti C++ Microsoft ze starších verzí sady Visual Studio.
ms.date: 01/21/2020
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: bc9fb5628c1a628b91f306c346f2bbb1dea13de8
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416113"
---
# <a name="upgrade-c-projects-from-earlier-versions-of-visual-studio"></a>Upgradovat C++ projekty z dřívějších verzí sady Visual Studio

Chcete-li upgradovat projekt vytvořený ve starší verzi sady Visual Studio, stačí otevřít projekt v nejnovější verzi sady Visual Studio. Visual Studio nabízí upgrade projektu na aktuální schéma.

Pokud zvolíte **ne**, projekt se neupgraduje. Pro projekty vytvořené v aplikaci Visual Studio 2010 a novější můžete i nadále používat projekt v novější verzi sady Visual Studio. Chcete-li pokračovat v cílení na starší sadu nástrojů, stačí nastavit vlastnosti projektu. Pokud ponecháte starší verzi sady Visual Studio na počítači, je její sada nástrojů k dispozici v novějších verzích. Například pokud váš projekt musí i nadále běžet v systému Windows XP, můžete upgradovat na Visual Studio 2019. Pak zadáte sadu nástrojů jako v141_xp nebo dříve ve vlastnostech projektu. Další informace naleznete v tématu [použití nativního cílení na více platforem v aplikaci Visual Studio k sestavení starých projektů](use-native-multi-targeting.md).

Pokud zvolíte **Ano**, projekt se upgraduje na místo. Nedá se převést zpátky na předchozí verzi. Ve scénářích upgradu je to proto, že je vhodné vytvořit záložní kopii stávajících souborů projektu a řešení.

## <a name="upgrade-reports"></a>Sestavy upgradu

Při upgradu projektu obdržíte zprávu o upgradu. Sestava je také uložena ve složce projektu jako UpgradeLog. htm. Zpráva o upgradu zobrazuje souhrn toho, jaké problémy byly během převodu zjištěny. Obsahuje seznam některých informací o provedených změnách, včetně:

- Vlastnosti projektu.

- Soubory k zahrnutí

- Kód, který již není zkompilován čistě z důvodu vylepšení shody kompilátoru nebo změn ve standardu.

- Kód, který závisí na funkcích sady Visual Studio nebo Windows, které již nejsou k dispozici. Nebo soubory hlaviček, které buď nejsou zahrnuty ve výchozí instalaci aplikace Visual Studio, nebo byly z produktu odebrány.

- Kód, který již není zkompilován z důvodu změn v rozhraních API, jako jsou přejmenovaná rozhraní API, změněné signatury funkcí nebo zastaralé funkce.

- Kód, který již není zkompilován z důvodu změn v diagnostice, jako například upozornění se stane chybou

- Chyby linkeru, protože došlo ke změně knihoven, zejména při použití/NODEFAULTLIB.

- Chyby za běhu nebo neočekávané výsledky kvůli změnám chování.

- Chyby, které byly představeny v nástrojích. Pokud narazíte na problém, ohlaste ho C++ týmu pomocí normálních kanálů podpory nebo pomocí stránky komunity pro vývojáře v rámci sady [Visual Studio C++ ](https://developercommunity.visualstudio.com/spaces/62/index.html) .

Některé upgradované projekty a řešení lze úspěšně sestavit bez úprav. Nicméně většina projektů bude pravděpodobně vyžadovat změny nastavení projektu i zdrojového kódu. Není k dispozici žádný jediný způsob, jak si vyřešit tyto problémy, ale doporučujeme použít postup s fázemi. Než začnete, přečtěte si téma [Přehled potenciálních problémů s upgradem](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) , kde najdete další informace o mnoha různých běžných chybách.

1. Nastavte sadu nástrojů platformy, C++ jazyk Standard a verzi Windows SDK (Pokud je k dispozici) na upřednostňovanou verzi. ( **Vlastnosti** > **projektu** > **Vlastnosti konfigurace** > **Obecné**)

1. Pokud máte spoustu chyb, můžete při jejich opravě dočasně vypnout některé možnosti. Chcete-li vypnout možnost [/Permissive-](../build/reference/permissive-standards-conformance.md) , použijte **vlastnosti** **projektu** >  > **Vlastnosti konfigurace** > **jazyk** **CC++ /**  > . Chcete-li vypnout možnost [analýzy kódu](/cpp/code-quality/code-analysis-for-c-cpp-overview) , použijte **vlastnosti** **projektu** >  > **Vlastnosti konfigurace** > **analýze kódu**.

1. Zajistěte, aby byly přítomny všechny závislosti a zda jsou cesty zahrnutí nebo umístění knihoven správné. ( **Vlastnosti** > **projektu** > **Vlastnosti konfigurace** > **adresáře VC + +** )

1. Identifikujte a opravte chyby způsobené odkazy na rozhraní API, která už neexistují.

1. Opravte všechny zbývající chyby, které brání kompilaci. V tématu [Přehled potenciálních problémů s upgradem](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) najdete opravy běžných chyb.

1. Zapněte **/Permissive-** a opravte všechny nové chyby způsobené nevyhovujícím kódem, který se dřív ZKOMPILUJE v MSVC.

1. Zapněte analýzu kódu a Identifikujte potenciální problémy nebo zastaralé vzory kódování, které se již nepovažují za přijatelné. Pokud analýza kódu označí mnoho chyb, můžete některá upozornění vypnout a soustředit se na nejdůležitější. Integrované vývojové prostředí (IDE) může v některých typech problémů pomáhat s rychlými opravami.

1. Zvažte další příležitosti pro modernizacií kódu. Například nahraďte vlastní struktury dat a algoritmy pomocí těch ze C++ standardní knihovny, nebo zvyšte Open Source knihovnu. Pomocí standardních funkcí usnadňuje ostatním uživatelům údržbu kódu. Můžete si být jistí, že tento kód byl dobře testován a přezkoumán mnoha odborníky na výboru standardů a v širší C++ komunitě.

V případě, že chcete opravit chyby, zkuste hledat nebo vystavit dotaz na Stack Overflow nebo [ C++ komunitě vývojářů](https://developercommunity.visualstudio.com/spaces/62/index.html).

## <a name="in-this-section"></a>V tomto oddílu

[Přehled potenciálních problémů s upgradem](overview-of-potential-upgrade-issues-visual-cpp.md)\
[Upgrade kódu na Universal CRT](upgrade-your-code-to-the-universal-crt.md)\
[Aktualizace winver a _WIN32_WINNT](modifying-winver-and-win32-winnt.md)\
[Opravte závislosti na interních knihovnách](fix-your-dependencies-on-library-internals.md)\
[Problémy s migrací s plovoucí](floating-point-migration-issues.md) desetinnou čárkou\
[funkce zastaralé v aplikaci Visual Studio 2019\ C++ ](features-deprecated-in-visual-studio.md)
[Vcbuild a\ MSBuild](build-system-changes.md)
[Portování knihoven třetích stran](porting-third-party-libraries.md)

## <a name="see-also"></a>Viz také

[Novinky pro vizuál C++ v aplikaci Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)\
[Historie C++ vizuálních změn 2003 – 2015](../porting/visual-cpp-change-history-2003-2015.md)\
[Nestandardní\ chování](../cpp/nonstandard-behavior.md)
[Datové aplikace portu](../data/data-access-programming-mfc-atl.md)
