---
title: Použití sady nástrojů C++ Microsoft z příkazového řádku
description: Použijte Microsoft C++ Compiler sada nástrojů (MSVC) z příkazového řádku mimo integrované vývojové prostředí (IDE) sady Visual Studio.
ms.custom: conceptual
ms.date: 11/12/2019
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: ec30cba8e119f96efc5bca156fa565db77904520
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051484"
---
# <a name="use-the-microsoft-c-toolset-from-the-command-line"></a>Použití sady nástrojů C++ Microsoft z příkazového řádku

Můžete sestavit C a C++ aplikace na příkazovém řádku pomocí nástrojů, které jsou součástí sady Visual Studio. Sada nástrojů C++ kompilátoru Microsoft (MSVC) je také ke stažení jako samostatný balíček, který neobsahuje integrované vývojové prostředí (IDE) sady Visual Studio.

## <a name="download-and-install-the-tools"></a>Stažení a instalace nástrojů

Pokud jste nainstalovali aplikaci Visual Studio a C++ úlohu, máte k dispozici všechny nástroje příkazového řádku. Informace o tom, jak nainstalovat C++ a Visual Studio, najdete v tématu [instalace C++ podpory v aplikaci Visual Studio](vscpp-step-0-installation.md). Pokud chcete pouze sadu nástrojů příkazového řádku, Stáhněte si [nástroje Build Tools for Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019). Když spustíte stažený spustitelný soubor, aktualizuje a spustí Instalační program pro Visual Studio. Chcete-li nainstalovat pouze nástroje, které C++ potřebujete pro vývoj, vyberte úlohu  **C++ nástroje sestavení** . Můžete vybrat volitelné knihovny a sady nástrojů, které chcete zahrnout do **podrobností o instalaci**. Chcete-li vytvořit kód pomocí nástrojů sady Visual Studio 2015 nebo 2017, vyberte volitelné nástroje buildu MSVC v140 nebo MSVC v141. Až budete s vybranými možnostmi spokojeni, vyberte **nainstalovat**.

## <a name="how-to-use-the-command-line-tools"></a>Jak používat nástroje příkazového řádku

Když vyberete jednu z C++ úloh v instalační program pro Visual Studio, nainstaluje *sadu nástrojů platformy*sady Visual Studio. Sada nástrojů platformy obsahuje všechny nástroje C a C++ pro konkrétní verzi sady Visual Studio. Mezi tyto nástroje patří kompilátoryC++ C/kompilátory, propojování, assemblery a další nástroje sestavení a vyhovující knihovny. Všechny tyto nástroje můžete použít na příkazovém řádku. Používají se také interně v integrovaném vývojovém prostředí sady Visual Studio. Pro vytváření kódu pro cíle x86, x64, ARM a ARM64 jsou k dispozici samostatné kompilátory hostované pro x86 a x64 a nástroje. Každá sada nástrojů pro konkrétní hostitele a cílovou architekturu sestavení je uložena ve vlastním adresáři.

Pro správné fungování nástroje vyžadují, aby byly nastaveny několik specifických proměnných prostředí. Tyto proměnné slouží k přidání nástrojů do cesty a k nastavení souboru include, souboru knihovny a umístění sady SDK. Pro usnadnění nastavení těchto proměnných prostředí instalační program vytvoří během instalace přizpůsobené *soubory příkazů*nebo dávkové soubory. Můžete spustit jeden z těchto souborů příkazů pro nastavení konkrétního hostitele a cílové architektury sestavení, Windows SDK verze a sady nástrojů platformy. Pro usnadnění práce instalační program také vytvoří zástupce v nabídce Start. Zástupci spouštějí vývojáře příkazového řádku pro konkrétní kombinace hostitelů a cílů pomocí těchto souborů příkazů. Tyto klávesové zkratky zajišťují, aby byly všechny požadované proměnné prostředí nastaveny a připravené k použití.

Požadované proměnné prostředí jsou specifické pro vaši instalaci a architekturu sestavení, kterou zvolíte. Mohou být také změněny aktualizacemi nebo upgrady produktu. To je důvod, proč doporučujeme použít nainstalovaný zástupce příkazového řádku nebo soubor příkazů místo nastavení proměnných prostředí sami. Další informace naleznete v tématu [Nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](setting-the-path-and-environment-variables-for-command-line-builds.md).

Sady nástrojů, soubory příkazů a klávesové zkratky závisí na procesoru počítače a možnostech, které jste vybrali během instalace. Nástroje hostované pro platformu x86 a různé nástroje, které sestavují kód x86 a x64, jsou vždy nainstalovány. Pokud máte 64 Windows, nainstalují se i nástroje hostované pro platformu x64 a mezi nástroji, které sestavují kód x86 a x64. Pokud zvolíte volitelné C++ Univerzální platforma Windows nástroje, nainstaluje se také nástroj x86 a x64, který sestaví kód ARM a ARM64. Jiné úlohy můžou nainstalovat další nástroje.

## <a name="developer_command_prompt_shortcuts"></a>Zástupci příkazového řádku pro vývojáře

Zástupce příkazového řádku jsou nainstalovány ve složce sady Visual Studio specifické pro danou verzi v nabídce Start. Tady je seznam základních klávesových zkratek příkazového řádku a architektury sestavení, které podporují:

- **Developer Command Prompt** – nastaví prostředí tak, aby používalo 32 – nativní nástroje x86 pro sestavování 32 kódu nativního pro x86.
- **x86 Native Tools Command Prompt** – nastaví prostředí tak, aby používalo 32 – nativní nástroje x86 pro sestavování 32 kódu nativního pro x86.
- **x64 Native Tools Command Prompt** – nastaví prostředí tak, aby používalo 64 – 32bitové nástroje x64 pro sestavování kódu 64-bit, x64-Native.
- **x86_x64 cross Tools Command Prompt** – nastaví prostředí tak, aby používalo 32 – nativní nástroje x86 pro sestavování kódu 64-bit, x64 – Native.
- **x64_x86 cross Tools Command Prompt** – nastaví prostředí tak, aby používalo 64 – 32bitové nástroje x64 pro sestavování 32 kódu nativního pro x86.

::: moniker range=">= vs-2019"

Složka nabídky Start a názvy zástupců se liší v závislosti na nainstalované verzi sady Visual Studio. Pokud jste ho nastavili, závisí taky na **přezdívkě**instalace. Předpokládejme například, že jste nainstalovali sadu Visual Studio 2019 a zadali jste přezdívku *nejnovější*. Zástupce příkazového řádku pro vývojáře má název **Developer Command Prompt pro VS 2019 (nejnovější)** ve složce s názvem **Visual Studio 2019**.

::: moniker-end
::: moniker range="= vs-2017"

Složka nabídky Start a názvy zástupců se liší v závislosti na nainstalované verzi sady Visual Studio. Pokud jste ho nastavili, závisí taky na **přezdívkě**instalace. Předpokládejme například, že jste nainstalovali sadu Visual Studio 2017 a zadali jste přezdívku *nejnovější*. Zástupce příkazového řádku pro vývojáře má název **Developer Command Prompt pro VS 2017 (nejnovější)** ve složce s názvem **Visual Studio 2017**.

::: moniker-end
::: moniker range="< vs-2017"

Složka nabídky Start a názvy zástupců se liší v závislosti na nainstalované verzi sady Visual Studio. Předpokládejme například, že jste nainstalovali Visual Studio 2015. Zástupce příkazového řádku pro vývojáře má název **Developer Command Prompt pro VS 2015**.

::: moniker-end

### <a name="developer_command_prompt"></a>Otevření okna příkazového řádku pro vývojáře

1. Na ploše otevřete nabídku **Start** systému Windows a potom posuňte zobrazení a otevřete složku pro vaši verzi sady Visual Studio, například **Visual Studio 2019**.

1. Ve složce vyberte **Developer Command Prompt** pro vaši verzi sady Visual Studio. Tato klávesová zkratka spustí okno příkazového řádku pro vývojáře, které používá výchozí architekturu sestavení rozhraní 32 x86, nativní nástroje pro sestavování 32 kódu nativního pro x86. Pokud dáváte přednost jiné než výchozí architektuře sestavení, zvolte jeden z příkazů pro nativní nebo mezinástrojní příkazy k určení architektury hostitele a cíle.

Chcete-li ještě rychlejší otevření příkazového řádku pro vývojáře, zadejte do pole pro hledání na ploše *příkaz Developer Command Prompt* . Pak zvolte výsledek, který chcete.

## <a name="developer_command_file_locations"></a>Umístění souborů příkazů pro vývojáře

Pokud dáváte přednost nastavení prostředí sestavení v existujícím okně příkazového řádku, můžete použít jeden ze souborů příkazů vytvořených instalačním programem. Doporučujeme nastavit prostředí v novém okně příkazového řádku. Nedoporučujeme vám později přepnout prostředí ve stejném příkazovém okně.

::: moniker range=">= vs-2019"

Umístění souboru příkazů závisí na verzi sady Visual Studio, kterou jste nainstalovali, a na volbách, které jste provedli během instalace. V případě sady Visual Studio 2019 je typické umístění instalace v systému 64 v \\Program Files (x86)\\Microsoft Visual Studio\\2019\\*Edition*. *Edice* může být komunita, Professional, Enterprise, BuildTools nebo jiná Přezdívka, kterou jste zadali.

::: moniker-end
::: moniker range="= vs-2017"

Umístění souboru příkazů závisí na verzi sady Visual Studio, kterou jste nainstalovali, a na volbách, které jste provedli během instalace. V případě sady Visual Studio 2017 je typické umístění instalace v systému 64 v \\Program Files (x86)\\Microsoft Visual Studio\\2017\\*Edition*. *Edice* může být komunita, Professional, Enterprise, BuildTools nebo jiná Přezdívka, kterou jste zadali.

::: moniker-end
::: moniker range="< vs-2017"

Umístění souboru příkazů závisí na verzi sady Visual Studio a instalačním adresáři. V případě sady Visual Studio 2015 je obvyklé umístění instalace ve \\Program Files (x86)\\Microsoft Visual Studio 14,0.

::: moniker-end

Primární soubor příkazů příkazového řádku pro vývojáře, VsDevCmd. bat, je umístěný v podadresáři Common7\\Tools. Pokud nejsou zadány žádné parametry, nastaví prostředí pro použití nástrojů x86-Native k sestavení 32 kódu x86.

::: moniker range=">= vs-2017"

K dispozici jsou další soubory příkazů pro nastavení konkrétní architektury sestavení. Dostupné soubory příkazů závisí na úlohách sady Visual Studio a možnostech, které jste nainstalovali. V aplikaci Visual Studio 2017 a Visual Studio 2019 najdete je v VC\\pomocné adresáře\\sestavení.

::: moniker-end
::: moniker range="< vs-2017"

K dispozici jsou další soubory příkazů pro nastavení konkrétní architektury sestavení. Dostupné soubory příkazů závisí na úlohách sady Visual Studio a možnostech, které jste nainstalovali. V aplikaci Visual Studio 2015 jsou umístěny v *podadresářích* VC, VC\\bin nebo VC\\bin\\, kde *Architektura* je jednou z nativních možností nebo z možností křížového kompilátoru.

::: moniker-end

Tyto příkazové soubory nastavují výchozí parametry a volají VsDevCmd. bat pro nastavení zadaného prostředí architektury sestavení. Typická instalace může zahrnovat tyto soubory příkazů:

|Soubor příkazů|Architektury hostitelů a cílů|
|---|---|
|**Vcvars32. bat**| Pro sestavování 32 kódu x86 použijte 32 nástroje x86-Native.|
|**vcvars64. bat**| Pro sestavování 64 kódu x64 použijte rozhraní 64 x64 – nativní nástroje pro 64bitovou verzi.|
|**vcvarsx86_amd64. bat**| Pro sestavování kódu 64 x64 použijte 32 nativních různých nástrojů x86.|
|**vcvarsamd64_x86. bat**| Pro sestavování 32 kódu x86 použijte 64 nativních mezinástrojních x64 platforem.|
|**vcvarsx86_arm. bat**| K sestavení kódu ARM použijte 32 nativních různých nástrojů x86.|
|**vcvarsamd64_arm. bat**| K sestavení kódu ARM použijte 64 x64 nativních různých nástrojů.|
|**vcvarsall. bat**| Pomocí parametrů můžete zadat hostitele a cílové architektury, Windows SDK a možnosti platformy. Seznam podporovaných možností zavoláte pomocí parametru **/help** .|

> [!CAUTION]
> Soubor vcvarsall. bat a další soubory příkazů sady Visual Studio se mohou v počítači lišit. Neměňte chybějící nebo poškozený soubor vcvarsall. bat pomocí souboru z jiného počítače. Opětovným spuštěním instalačního programu sady Visual Studio nahraďte chybějící soubor.
>
> Soubor vcvarsall. bat se také liší od verze k verzi. Pokud je aktuální verze sady Visual Studio nainstalována na počítači, který má také starší verzi sady Visual Studio, nespouštějte vcvarsall. bat ani jiný soubor příkazů sady Visual Studio z různých verzí ve stejném okně příkazového řádku.

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>Použití vývojářských nástrojů v existujícím příkazovém okně

Nejjednodušší způsob, jak zadat konkrétní architekturu sestavení v existujícím příkazovém okně, je použití souboru vcvarsall. bat. Pomocí vcvarsall. bat nastavte proměnné prostředí pro konfiguraci příkazového řádku pro nativní 32 nebo 64 bitovou kompilaci. Argumenty umožňují určit více kompilací procesorů x86, x64, ARM nebo ARM64. Můžete cílit na platformy Microsoft Store, Univerzální platforma Windows nebo Windows Desktop. Můžete dokonce určit, které Windows SDK se mají použít, a vybrat verzi sady nástrojů platformy.

Při použití bez argumentů nakonfiguruje vcvarsall. bat proměnné prostředí tak, aby používaly aktuální kompilátor x86-Native pro 32 cíle pro stolní počítače s Windows. Můžete přidat argumenty a nakonfigurovat prostředí tak, aby používalo některé z nativních nebo přesných nástrojů pro více kompilátorů. vcvarsall. bat zobrazí chybovou zprávu, pokud zadáte konfiguraci, která není v počítači nainstalovaná nebo dostupná.

### <a name="vcvarsall-syntax"></a>syntaxe vcvarsall

> **vcvarsall. bat** [*architektura*] [*platform_type*] [*winsdk_version*] [ **-vcvars_ver =** _vcversion_]

*Architektura*<br/>
Tento nepovinný argument určuje hostitelskou a cílovou architekturu, která se má použít. Pokud *Architektura* není zadaná, použije se výchozí prostředí sestavení. Jsou podporovány tyto argumenty:

|*Architektura*|Přepínač|Architektura hostitelského počítače|Sestavit výstupní (cílovou) architekturu|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**architektur**|x86 32-bit Native|x86, x64|x86|
|**x86\_amd64** nebo **x86\_x64**|x64 na platformě x86|x86, x64|x64|
|**x86_arm**|ARM na platformě x86|x86, x64|ARM|
|**x86_arm64**|ARM64 v x86 – křížení|x86, x64|ARM64|
|**amd64** nebo **x64**|x64 64-bit Native|x64|x64|
|**amd64\_x86** nebo **x64\_x86**|x86 na platformě x64|x64|x86|
|**amd64\_ARM** nebo **x64\_ARM**|ARM na platformě x64|x64|ARM|
|**amd64\_arm64** nebo **x64\_arm64**|ARM64 na platformě x64|x64|ARM64|

*platform_type*<br/>
Tento volitelný argument umožňuje zadat **úložiště** nebo **UWP** jako typ platformy. Ve výchozím nastavení je prostředí nastavené na sestavování desktopových nebo konzolových aplikací.

*winsdk_version*<br/>
Volitelně určuje verzi Windows SDK, která se má použít. Ve výchozím nastavení se používá nejnovější nainstalovaná Windows SDK. K určení verze Windows SDK můžete použít celé číslo sady Windows 10 SDK, například **10.0.10240.0**, nebo zadat **8,1** pro použití sady Windows 8.1 SDK.

*vcversion*<br/>
Volitelně určuje sadu nástrojů kompilátoru sady Visual Studio, která se má použít. Ve výchozím nastavení je prostředí nastaveno na použití aktuální sady nástrojů kompilátoru sady Visual Studio.

::: moniker range=">= vs-2019"

Použijte **-vcvars_ver = 14.2 x. yyyyy** k určení konkrétní verze sady nástrojů kompilátoru sady Visual Studio 2019.

Použijte **-vcvars_ver = 14.16** k určení nejnovější verze sady nástrojů kompilátoru sady Visual Studio 2017.

::: moniker-end
::: moniker range="= vs-2017"

Použijte **-vcvars_ver = 14.16** k určení nejnovější verze sady nástrojů kompilátoru sady Visual Studio 2017.

Použijte **-vcvars_ver = 14,1 x. rrrr** k určení konkrétní verze sady nástrojů kompilátoru sady Visual Studio 2017.

::: moniker-end

Pomocí **-vcvars_ver = 14.0** určete sadu nástrojů kompilátoru sady Visual Studio 2015.

#### <a name="vcvarsall"></a>Nastavení prostředí sestavení v existujícím okně příkazového řádku

1. Na příkazovém řádku pomocí příkazu CD přejděte do instalačního adresáře sady Visual Studio. Pak znovu použijte disk CD pro změnu v podadresáři, který obsahuje soubory příkazů specifické pro konfiguraci. V případě sady Visual Studio 2019 a sady Visual Studio 2017 použijte *\\\\sestavení* podadresáře VC. V případě sady Visual Studio 2015 použijte podadresář *VC* .

1. Zadejte příkaz pro preferované vývojové prostředí. Například pro sestavení kódu ARM pro UWP na 64 platformě použijte nejnovější Windows SDK a sadu nástrojů kompilátoru sady Visual Studio, použijte tento příkazový řádek:

   `vcvarsall.bat amd64_arm uwp`

## <a name="create-your-own-command-prompt-shortcut"></a>Vytvoření vlastního zástupce příkazového řádku

::: moniker range=">= vs-2019"

Otevřete dialogové okno Vlastnosti pro zástupce příkazového řádku pro vývojáře a podívejte se na použitý cíl příkazu. Například cíl pro **x64 Native Tools Command Prompt zástupce VS 2019** je podobný následujícímu:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="= vs-2017"

Otevřete dialogové okno Vlastnosti pro zástupce příkazového řádku pro vývojáře a podívejte se na použitý cíl příkazu. Například cíl pro **x64 Native Tools Command Prompt zástupce VS 2017** je podobný následujícímu:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="< vs-2017"

Otevřete dialogové okno Vlastnosti pro zástupce příkazového řádku pro vývojáře a podívejte se na použitý cíl příkazu. Například cíl pro zástupce **VS2015 x64 Native Tools Command Prompt** vypadá podobně jako:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" amd64`

::: moniker-end

Dávkové soubory specifické pro danou architekturu nastaví parametr *architektury* a zavolají vcvarsall. bat. Do těchto dávkových souborů můžete předat stejné možnosti jako při předání do vcvarsall. bat, nebo můžete přímo volat vcvarsall. bat. Chcete-li zadat parametry vlastního zástupce příkazu, přidejte je na konec příkazu v uvozovkách. Tady je například zástupce k sestavení kódu ARM pro UWP na 64 platformě pomocí nejnovější Windows SDK. Chcete-li použít starší sadu nástrojů kompilátoru, zadejte číslo verze. Ve svém zástupci použijte něco jako tento cíl příkazu:

::: moniker range=">= vs-2019"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat" amd64_arm uwp -vcvars_ver=14.16`

::: moniker-end
::: moniker range="= vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat" amd64_arm uwp -vcvars_ver=14.0`

::: moniker-end
::: moniker range="< vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" amd64 -vcvars_ver=12.0`

::: moniker-end

Upravte cestu tak, aby odrážela instalační adresář sady Visual Studio. Soubor vcvarsall. bat obsahuje další informace o konkrétních číslech verzí.

## <a name="command-line-tools"></a>Nástroje příkazového řádku

Pro sestavení C/C++ projekt na příkazovém řádku poskytuje Visual Studio tyto nástroje příkazového řádku:

[CL](reference/compiling-a-c-cpp-program.md)<br/>
Použijte kompilátor (CL. exe) pro zkompilování a propojení souborů se zdrojovým kódem do aplikací, knihoven a knihoven DLL.

[Propojit](reference/linking.md)<br/>
Pomocí linkeru (Link. exe) můžete propojit zkompilované soubory objektů a knihovny s aplikacemi a knihovnami DLL.

[MSBuild](msbuild-visual-cpp.md)<br/>
Pomocí nástroje MSBuild (MSBuild. exe) a souboru projektu (. vcxproj) můžete konfigurovat sestavení a vyvolat sadu nástrojů nepřímo. Odpovídá spuštění příkazu **sestavit** projekt nebo **Sestavit řešení** v integrovaném vývojovém prostředí sady Visual Studio. Spuštění nástroje MSBuild z příkazového řádku je pokročilý scénář a obecně se nedoporučuje.

[NÁSTROJE devenv](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
Použijte DEVENV (devenv. exe) kombinovaný s přepínačem příkazového řádku, jako je **/Build** nebo **/clean** , a spusťte některé příkazy sestavení bez zobrazení integrovaného vývojového prostředí (IDE) sady Visual Studio. V Obecné verzi je nástroj DEVENV upřednostňován při přímém použití nástroje MSBuild, protože aplikaci Visual Studio můžete nechat zpracovat složitá prostředí MSBuild.

[NMAKE](reference/nmake-reference.md)<br/>
Použijte NMAKE (NMAKE. exe) ve Windows k sestavení C++ projektů na základě tradičního souboru pravidel.

Při sestavování na příkazovém řádku není k dispozici příkaz F1 pro rychlou nápovědu. Místo toho můžete pomocí vyhledávacího modulu získat informace o upozorněních, chybách a zprávách nebo můžete použít offline soubory nápovědy. Pokud chcete použít vyhledávání v [docs.Microsoft.com](https://docs.microsoft.com/cpp/), použijte vyhledávací pole v horní části stránky.

## <a name="in-this-section"></a>V tomto oddílu

Tyto články ukazují, jak sestavovat aplikace na příkazovém řádku a popisují, jak přizpůsobit prostředí pro sestavování z příkazového řádku. Některé ukazují, jak používat 64-bitové sady nástrojů a cílit na platformy x86, x64, ARM a ARM64. Popisují také použití nástrojů pro sestavení příkazového řádku MSBuild a NMAKE.

[Návod: kompilace nativního C++ programu na příkazovém řádku](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
Poskytuje příklad, který ukazuje, jak vytvořit a zkompilovat C++ program na příkazovém řádku.

[Návod: Kompilace programu C v příkazovém řádku](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
Popisuje, jak zkompilovat program napsaný v programovacím jazyce C.

[Návod: kompilace programu C++/CLI na příkazovém řádku](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
Popisuje, jak vytvořit a zkompilovat program C++/CLI, který používá .NET Framework.

[Návod: kompilace programu C++/CX na příkazovém řádku](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
Popisuje, jak vytvořit a zkompilovat program C++/CX, který používá prostředí Windows Runtime.

[Nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
Postup nastavení proměnných prostředí pro použití 32 nebo 64 sady nástrojů pro cílení na platformy x86, x64, ARM a ARM64

[NMAKE – referenční informace](reference/nmake-reference.md)<br/>
Obsahuje odkazy na články, které popisují Nástroj Údržba programu společnosti Microsoft (NMAKE. EXE).

[MSBuild na příkazovém řádku –C++](msbuild-visual-cpp.md)<br/>
Obsahuje odkazy na články, které popisují použití nástroje MSBuild. exe z příkazového řádku.

## <a name="related-sections"></a>Související oddíly

[/MD,/MT,/LD (Použít běhovou knihovnu)](reference/md-mt-ld-use-run-time-library.md)<br/>
Popisuje, jak používat tyto možnosti kompilátoru k použití běhové knihovny ladění nebo uvolnění.

[Možnosti jazykaC++ C/kompilátoru](reference/compiler-options.md)<br/>
Obsahuje odkazy na články, které popisují možnosti jazyka C++ C a kompilátoru a CL. exe.

[Možnosti linkeru MSVC](reference/linker-options.md)<br/>
Obsahuje odkazy na články, které popisují možnosti linkeru a LINK. exe.

[Další nástroje sestavení MSVC](reference/c-cpp-build-tools.md)<br/>
Obsahuje odkazy na nástroje C/C++ Build, které jsou součástí sady Visual Studio.

## <a name="see-also"></a>Viz také:

[Projekty a systémy sestavení](projects-and-build-systems-cpp.md)
