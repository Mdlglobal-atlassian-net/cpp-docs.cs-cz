---
title: Upgradovat C++ projekty z dřívějších verzí sady Visual Studio
description: Postup upgradu projektů společnosti C++ Microsoft ze starších verzí sady Visual Studio.
ms.date: 10/29/2019
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: b317271a9cd0873e60a6dd9acd1b73a766aaea19
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627169"
---
# <a name="upgrade-c-projects-from-earlier-versions-of-visual-studio"></a>Upgradovat C++ projekty z dřívějších verzí sady Visual Studio

Chcete-li upgradovat projekt vytvořený v aplikaci Visual Studio 2008 nebo starší, je nutné nejprve použít Visual Studio 2010 k převedení projektu z formátu VCBuild (. vcproj) do formátu MSBuild (. vcxproj). Další informace najdete v tématu [pokyny pro Visual Studio 2008](use-native-multi-targeting.md#instructions-for-visual-studio-2008).

Chcete-li upgradovat projekt vytvořený v aplikaci Visual Studio 2010 nebo novější, stačí otevřít projekt v nejnovější verzi sady Visual Studio. Visual Studio nabízí upgrade projektu na aktuální schéma. Pokud zvolíte možnost **ne**a máte v počítači starší verzi sady Visual Studio, můžete v projektu pracovat v novější verzi sady Visual Studio a nadále cílit na starší sadu nástrojů. Například pokud váš projekt musí i nadále běžet v systému Windows XP, můžete jej upgradovat na Visual Studio 2019, ale je nutné zadat sadu nástrojů jako v141 nebo starší. Další informace naleznete v tématu [použití nativního cílení na více platforem v aplikaci Visual Studio k sestavení starých projektů](use-native-multi-targeting.md). Pokud zvolíte **Ano**, projekt bude převeden a nebude možné ho převést zpět na předchozí verzi. Proto je ve scénářích upgradu dobrým zvykem vytvořit kopii existujícího projektu a souborů řešení.

## <a name="upgrade-reports"></a>Sestavy upgradu

Při upgradu projektu obdržíte zprávu o upgradu, která je také uložena ve složce projektu jako UpgradeLog. htm. Zpráva o upgradu zobrazuje souhrn toho, jaké problémy byly zjištěny, a některé informace o provedených změnách, včetně:

1. Vlastnosti projektu

2. Zahrnuté soubory

3. Kód, který již není zkompilován čistě z důvodu vylepšení shody s kompilátorem nebo změn ve standardu

4. Kód, který spoléhá na funkce sady Visual Studio nebo Windows, které již nejsou k dispozici, nebo soubory hlaviček, které buď nejsou zahrnuty ve výchozí instalaci sady Visual Studio, nebo byly z produktu odebrány

5. Kód, který se už nekompiluje kvůli změnám v rozhraních API, jako je přejmenovaná rozhraní API, změněné signatury funkcí nebo zastaralé funkce

6. Kód, který již není zkompilován z důvodu změn v diagnostice, jako například upozornění se stane chybou

7. Chyby linkeru kvůli změně knihoven, zejména při použití/NODEFAULTLIB.

8. Chyby za běhu nebo neočekávané výsledky z důvodu změn chování

9. Chyby, které byly představeny v nástrojích. Pokud narazíte na problém, nahlaste ho C++ týmu pomocí běžných kanálů podpory nebo pomocí stránky [komunity vývojářů pro C++ Visual Studio](https://developercommunity.visualstudio.com/spaces/62/index.html) .

Některé upgradované projekty a řešení lze úspěšně sestavit bez úprav. Nicméně většina projektů bude pravděpodobně vyžadovat změny nastavení projektu i zdrojového kódu. Neexistuje žádný jednoduchý způsob, jak jít o opravu, ale doporučuje se nějaký druh postupu dvoufázové. Než začnete, přečtěte si téma [Přehled potenciálních problémů s upgradem](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) , kde najdete další informace o mnoha různých běžných chybách.

 1. Nastavte sadu nástrojů platformy, C++ jazyk Standard a verzi Windows SDK (Pokud je k dispozici) na požadované verze. ( **Vlastnosti** > **projektu** > **Vlastnosti konfigurace** > **Obecné**)
 1. Pokud máte velké množství chyb, vypněte možnost [povolující](../build/reference/permissive-standards-conformance.md) možnosti ( > **vlastnosti** **projektu** > **Vlastnosti konfigurace** > **jazyk** **C++ C/**  > ) a [analýzu kódu ](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)( **Vlastnosti** **projektu** >  > možnosti **Konfigurace** > **Analýza kódu**) dočasně, aby se snížil počet chyb.
 1. Zajistěte, aby byly přítomny všechny závislosti a zda jsou cesty zahrnutí nebo umístění knihoven správné. ( **Vlastnosti** > **projektu** > **Vlastnosti konfigurace** > **adresáře VC + +** )
 1. Identifikujte a opravte chyby kvůli odkazům na rozhraní API, která už neexistují.
 1. Opravte všechny zbývající chyby, které brání kompilaci. V tématu [Přehled potenciálních problémů s upgradem](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) najdete opravy běžných chyb.
 1. Zapněte **znovu navrácení a** opravte všechny nové chyby, které se zobrazí v důsledku nevyhovujícího kódu, který byl dříve KOMPILOVÁN v MSVC.
 1. Zapněte analýzu kódu a Identifikujte potenciální problémy nebo zastaralé vzory kódování, které se již nepovažují za přijatelné. Pokud analýza kódu označí mnoho chyb, můžete některá upozornění vypnout a soustředit se na nejdůležitější. Integrované vývojové prostředí (IDE) může v některých typech problémů pomáhat s rychlými opravami.
 1. Zvažte další příležitosti pro modernizaci kódu, například nahrazením vlastních datových struktur a algoritmů pomocí těch z knihovny C++ Standard nebo knihovny open source Library. Pomocí standardních funkcí usnadňuje ostatním uživatelům udržování kódu a také velkou jistotu, že kód byl dobře testován a přezkoumán mnoha odborníky na výboru standardů a širší C++ komunitě.

V případě, že chcete opravit chyby, zkuste hledat nebo vystavit dotaz na Stack Overflow nebo [ C++ komunitě vývojářů](https://developercommunity.visualstudio.com/spaces/62/index.html).

## <a name="in-this-section"></a>V tomto oddílu

[Přehled potenciálních problémů s upgradem](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Upgrade kódu na Universal CRT](upgrade-your-code-to-the-universal-crt.md)<br/>
[Aktualizace WINVER a _WIN32_WINNT](modifying-winver-and-win32-winnt.md)<br/>
[Oprava závislostí u interních informací o knihovně](fix-your-dependencies-on-library-internals.md)<br/>
[Problémy migrace s plovoucí desetinnou čárkou](floating-point-migration-issues.md)<br/>
[C++Funkce zastaralé v aplikaci Visual Studio 2019](features-deprecated-in-visual-studio.md)<br/>
[VCBuild a MSBuild](build-system-changes.md)<br/>
[Portování knihoven třetích stran](porting-third-party-libraries.md)<br/>

## <a name="see-also"></a>Viz také:

[Novinky pro vizuál C++ v aplikaci Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Historie změn Visual C++ 2003–2015](../porting/visual-cpp-change-history-2003-2015.md)<br/>
[Nestandardní chování](../cpp/nonstandard-behavior.md)<br/>
[Datové aplikace portu](../data/data-access-programming-mfc-atl.md)<br/>
