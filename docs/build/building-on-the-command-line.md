---
title: Použití služby Microsoft C++ sady nástrojů z příkazového řádku
description: Pomocí nástrojů Microsoft C++ kompilátor (MSVC) z příkazového řádku mimo rozhraní IDE sady Visual Studio.
ms.custom: conceptual
ms.date: 06/06/2019
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: b5e9bf266d79ee86cae84535641a52c7c52be391
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821136"
---
# <a name="use-the-microsoft-c-toolset-from-the-command-line"></a>Použití služby Microsoft C++ sady nástrojů z příkazového řádku

Pomocí nástrojů, které jsou zahrnuty v sadě Visual Studio můžete vytvářet aplikace jazyka C a C++ v příkazovém řádku. Microsoft C++ sada nástrojů kompilátoru (MSVC) je také jako samostatný balíček ke stažení [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads/) stránky. To je součástí **Build Tools pro Visual Studio** balíčku. Můžete také stáhnout jenom nástroje, které potřebujete pro C++ vývoje.

## <a name="how-to-use-the-command-line-tools"></a>Jak používat nástroje příkazového řádku

Když vyberete některou C++ zátěží v instalačním programu sady Visual Studio, nainstaluje Visual Studio *sada nástrojů platformy*. Sada nástrojů platformy má všechny C a C++ nástroje pro konkrétní verze sady Visual Studio. Mezi tyto nástroje patří jazyka C /C++ kompilátory, linkers, montážní společnosti a další sestavení odpovídající knihoven a nástrojů. Všechny tyto nástroje můžete na příkazovém řádku. Budete také používají interně v integrovaném vývojovém prostředí sady Visual Studio. Existují samostatné hostované x86 a x64 hostované kompilátory a nástroje pro vytváření kódu pro x86, x 64, ARM a ARM64 cíle. Každá sada nástrojů pro konkrétní architekturu hostitele a cílovém sestavení je uložen do vlastního adresáře.

Pracovala správně, nástroje vyžadují několik proměnných prostředí konkrétní nastavení. Tyto proměnné se používají k přidání nástrojů do cesty a nastavit obsahovat soubor, soubor knihovny a umístění sad SDK. Abyste usnadnili snadnou k nastavení těchto proměnných prostředí, instalační program vytvoří přizpůsobené *soubory příkazů*, nebo dávkové soubory, během instalace. Můžete spustit některý z těchto souborů příkaz k nastavení konkrétního hostitele a Cílová architektura sestavení, verzi sady Windows SDK a sady nástrojů platformy. Pro usnadnění práce Instalační program také vytvoří zástupce v nabídce Start. Klávesové zkratky spustit příkazový řádek pro vývojáře systému windows s použitím tyto příkazové soubory pro konkrétní kombinací hostitelů a cíl. Tyto klávesové zkratky Ujistěte se, že jsou všechny proměnné požadované prostředí nastavené a připravené k použití.

Požadované proměnné jsou specifické pro vaši instalaci a sestavení architektury, které zvolíte. Jsou také může změnit aktualizací produktu nebo upgradu. Proto doporučujeme použít nainstalovaných příkazový řádek příkazu nebo místní soubor, místo nastavení proměnných prostředí. Další informace najdete v tématu [nastavit cesty a proměnných prostředí pro sestavení příkazového řádku](setting-the-path-and-environment-variables-for-command-line-builds.md).

Sady nástrojů, souborů příkazů a zkratky nainstalované závisí na procesor počítače a možností, které jste vybrali při instalaci. Nástroje hostované v x86 a různé nástroje, které sestavení x86 a x64 kódu se vždy instalují. Pokud máte Windows 64-bit, jsou nainstalovány také nástroje x64 hostované a různé nástroje, které sestavení x86 a x64 kódu. Pokud se rozhodnete nepovinný C++ nástroje pro univerzální platformu Windows a pak x86 a x64 nástroje, které sestavení kódu ARM a ARM64 také se nainstalují. Jiné úlohy může nainstalovat další nástroje.

## <a name="developer_command_prompt_shortcuts"></a> Zástupce příkazového řádku pro vývojáře

Zástupce příkazového řádku se instalují do složky specifické pro verzi sady Visual Studio v nabídce Start. Tady je seznam zástupců základní příkazový řádek a sestavení architektury, které podporují:

- **Developer Command Prompt** – nastaví prostředí tak, aby 32-bit, nativní x86 nástroje použít k vytváření 32-bit, x86 nativní kód.
- **x86 native Tools Command Prompt** – nastaví prostředí tak, aby 32-bit, nativní x86 nástroje použít k vytváření 32-bit, x86 nativní kód.
- **x64 native Tools Command Prompt** – nastaví prostředí tak, aby použít 64-bit, x64 cloudově nativních nástrojů k vytváření 64-bit, x64 nativní kód.
- **x86_x64 Cross Tools Command Prompt** – nastaví prostředí tak, aby použití 32-bit x86 cloudově nativních nástrojů k vytvoření 64-bit, x64 nativní kód.
- **x64_x86 Cross Tools Command Prompt** – nastaví prostředí tak, aby použít 64-bit, x64 cloudově nativních nástrojů k vytváření 32-bit, x86 nativní kód.

::: moniker range=">= vs-2019"

Názvy složky a místní nabídky Start se liší v závislosti na nainstalované verzi sady Visual Studio. Pokud nastavíte jeden, jsou také závislé na instalaci **Přezdívka**. Předpokládejme například, že jste nainstalovali Visual Studio 2019 a dáte ho přezdívku z *nejnovější*. Zástupce příkazového řádku pro vývojáře jmenuje **Developer Command Prompt for VS 2019 (nejnovější)** , do složky s názvem **Visual Studio 2019**.

::: moniker-end
::: moniker range="= vs-2017"

Názvy složky a místní nabídky Start se liší v závislosti na nainstalované verzi sady Visual Studio. Pokud nastavíte jeden, jsou také závislé na instalaci **Přezdívka**. Předpokládejme například, že jste nainstalovali Visual Studio 2017 a jste zadali, ho přezdívku z *nejnovější*. Zástupce příkazového řádku pro vývojáře jmenuje **Developer Command Prompt for VS 2017 (nejnovější)** , do složky s názvem **Visual Studio 2017**.

::: moniker-end
::: moniker range="< vs-2017"

Názvy složky a místní nabídky Start se liší v závislosti na nainstalované verzi sady Visual Studio. Předpokládejme například, že jste nainstalovali Visual Studio 2015. Zástupce příkazového řádku pro vývojáře jmenuje **Developer Command Prompt for VS 2015**.

::: moniker-end

## <a name="developer_command_prompt"></a> Chcete-li otevřít okno příkazového řádku pro vývojáře

1. Na ploše otevřete Windows **Start** nabídky a pak přejděte k vyhledání a otevření složky pro vaši verzi sady Visual Studio, například **Visual Studio 2019**.

1. Ve složce, vyberte **Developer Command Prompt** pro vaši verzi sady Visual Studio. Tento zástupce spustí okno příkazového řádku pro vývojáře, který používá výchozí architektura sestavení 32-bit, x86 cloudově nativních nástrojů k vývoji 32-bit, x86 nativní kód. Pokud dáváte přednost architektura jiné než výchozí sestavení, zvolte jednu z nativní nebo různé nástroje příkazové řádky k určení hostitele a cílové architektury.

Pro ještě rychlejší možností, jak otevřít příkazový řádek pro vývojáře, zadejte *příkazový řádek pro vývojáře* klasické pracovní plochy vyhledávacího pole. Zvolte požadovaný výsledek.

## <a name="developer_command_file_locations"></a> Umístění souborů příkaz pro vývojáře

Pokud chcete nastavit prostředí pro sestavení v existující okno příkazového řádku, můžete použít jeden příkaz soubory vytvořené pomocí Instalační služby. Doporučujeme, abyste že nastavení prostředí v novém okně příkazového řádku. Nedoporučujeme vám novější přepínače prostředí v příkazovém okně stejné.

::: moniker range=">= vs-2019"

Umístění souboru příkazu závisí na verzi sady Visual Studio, které jste nainstalovali a na možnosti, které jste provedli během instalace. Pro Visual Studio 2019 umístění typické instalace na 64bitovém systému je v \\Program Files (x86)\\sady Microsoft Visual Studio\\2019\\*edition*. *Edice* může být Community, Professional, Enterprise, BuildTools nebo jiné pojmenování, které jste zadali.

::: moniker-end
::: moniker range="= vs-2017"

Umístění souboru příkazu závisí na verzi sady Visual Studio, které jste nainstalovali a na možnosti, které jste provedli během instalace. Pro Visual Studio 2017, umístění typické instalace na 64bitovém systému je v \\Program Files (x86)\\sady Microsoft Visual Studio\\2017\\*edition*. *Edice* může být Community, Professional, Enterprise, BuildTools nebo jiné pojmenování, které jste zadali.

::: moniker-end
::: moniker range="< vs-2017"

Umístění souboru příkaz závisí na verzi sady Visual Studio a v instalačním adresáři. Pro Visual Studio 2015, umístění typické instalace probíhá \\Program Files (x86)\\Microsoft Visual Studio 14.0.

::: moniker-end

Soubor příkazů hlavního vývojáře příkazového řádku, VsDevCmd.bat, je umístěn ve Common7\\podadresáři Tools. Pokud nejsou zadány žádné parametry, nastaví prostředí tak, aby x86 nativní nástroje použít k vytváření x86 32bitová verze kódu.

::: moniker range=">= vs-2017"

Další příkaz soubory jsou k dispozici k nastavení konkrétního sestavení architektury. Soubory příkazů, který je k dispozici, závisí na úlohách sady Visual Studio a možnostech, které jste nainstalovali. V sadě Visual Studio 2017 a Visual Studio 2019, najdete je v VC\\pomocné\\sestavení podadresář.

::: moniker-end
::: moniker range="< vs-2017"

Další příkaz soubory jsou k dispozici k nastavení konkrétního sestavení architektury. Soubory příkazů, který je k dispozici, závisí na úlohách sady Visual Studio a možnostech, které jste nainstalovali. V sadě Visual Studio 2015, nacházejí v VC VC\\bin nebo VC\\bin\\*architektura* podadresářů, kde *architektura* je nativní nebo Možnosti křížový kompilátor.

::: moniker-end

Tyto soubory příkaz nastavit výchozí parametry a volání VsDevCmd.bat k nastavení prostředí architektury zadané sestavení. Typické instalace může zahrnovat tyto soubory příkazů:

|Soubor příkazů|Hostitel a cílové architektury|
|---|---|
|**vcvars32.bat**| Nástroje x86 nativní 32bitový použít k vytváření x86 32bitová verze kódu.|
|**vcvars64.bat**| Nástroje x64 nativní 64bitové použít k vytváření 64-bit x64 kódu.|
|**vcvarsx86_amd64.bat**| Pomocí nástrojů mezi 32-bit x86 nativní k vytvoření 64-bit x64 kódu.|
|**vcvarsamd64_x86.bat**| 64-bit x64 nativní křížové nástroje použít k vytváření x86 32bitová verze kódu.|
|**vcvarsx86_arm.bat**| Pomocí nástrojů mezi 32-bit x86 nativní sestavení kódu ARM.|
|**vcvarsamd64_arm.bat**| Pomocí křížové nástroje x64 nativní 64bitové sestavení kódu ARM.|
|**vcvarsall.bat**| Pomocí parametrů můžete určit hostitele a cílové architektury, sady Windows SDK a možností platformy. Seznam podporované možnosti, volání pomocí **/help** parametru.|

> [!CAUTION]
> Soubor vcvarsall.bat a další soubory příkazů sady Visual Studio se může lišit od počítače na počítač. Nepřepisovat existující soubor vcvarsall.bat nebo je poškozena pomocí souboru z jiného počítače. Znovu spusťte instalační program sady Visual Studio k nahrazení souboru chybí.
>
> Soubor vcvarsall.bat se také liší mezi verzemi. Pokud na počítači, který také používá starší verzi sady Visual Studio je nainstalovaná aktuální verze sady Visual Studio, nespouštějte vcvarsall.bat nebo jiného souboru příkazů sady Visual Studio z různých verzí ve stejném okně příkazového řádku.

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>Pomocí vývojářských nástrojů v existujících příkazové okno

Použít soubor vcvarsall.bat je nejjednodušší způsob, jak určit konkrétní sestavení architektury v existující příkazové okno. Pomocí vcvarsall.bat můžete nastavit proměnné prostředí pro příkazový řádek pro nativní kompilace 32bitová nebo 64bitová verze konfigurace. Argumenty umožňují zadat křížové kompilace x86, x 64, ARM, nebo procesory ARM64. Můžete cílit platformy Microsoft Store, univerzální platformu Windows a Windows Desktop. Dokonce je možné určit, které Windows SDK používat a vyberte verzi sady nástrojů platformy.

Při použití bez argumentů, vcvarsall.bat nastaví proměnné prostředí použít aktuální x86 nativního kompilátoru pro cíle 32bitová verze Windows Desktop. Můžete přidat nakonfigurovat prostředí tak, aby používat žádné nativní nebo kompilátoru nástrojů pro různé argumenty. vcvarsall.bat zobrazí chybovou zprávu, pokud zadáte konfiguraci, která není nainstalována nebo je dostupný na vašem počítači.

### <a name="vcvarsall-syntax"></a>Syntaxe vcvarsall

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [ **-vcvars_ver=** _vcversion_]

*architecture*<br/>
Tento volitelný argument určuje architekturu hostitele a cílovém používat. Pokud *architektura* není zadán, výchozí prostředí pro sestavení se používá. Podporují se tyto argumenty:

|*architecture*|Kompilátor|Architektura počítače hostitele|Architektura výstupu (cíl) sestavení|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|x86 32bitová nativní|x86, x64|x86|
|**x86\_amd64** nebo **x86\_x64**|různé x64 na x86|x86, x64|x64|
|**x86_arm**|ARM na křížové x86|x86, x64|ARM|
|**x86_arm64**|ARM64 na x86 křížové|x86, x64|ARM64|
|**AMD64** nebo **x64**|x64 64bitové nativní|x64|x64|
|**AMD64\_x86** nebo **x64\_x86**|x86 na x64 cross|x64|x86|
|**AMD64\_arm** nebo **x64\_arm**|ARM na křížové x64|x64|ARM|
|**AMD64\_arm64** nebo **x64\_arm64**|ARM64 na x64 křížové|x64|ARM64|

*platform_type*<br/>
Tento volitelný argument můžete zadat **ukládání** nebo **UPW** jako typ platformy. Ve výchozím nastavení je nastavit prostředí k vytváření aplikací konzoly nebo stolního počítače.

*winsdk_version*<br/>
Volitelně určuje verzi sady Windows SDK používat. Ve výchozím nastavení se používá nejnovější nainstalovaný Windows SDK. Chcete-li určit verzi sady Windows SDK, můžete použít úplné číslo Windows 10 SDK, jako **10.0.10240.0**, nebo zadejte **8.1** použití sady SDK pro Windows 8.1.

*vcversion*<br/>
Volitelně určuje sada nástrojů kompilátoru Visual Studio používat. Ve výchozím nastavení je prostředí nastaveno použití aktuální sady nástrojů kompilátoru Visual Studio.

::: moniker range=">= vs-2019"

Použití **-vcvars_ver = 14.2 x .yyyyy** určit konkrétní verzi sady nástrojů kompilátoru Visual Studio 2019.

Použití **-vcvars_ver = 14.16** určíme nejnovější verzi sady nástrojů kompilátoru Visual Studio 2017.

::: moniker-end
::: moniker range="= vs-2017"

Použití **-vcvars_ver = 14.16** určíme nejnovější verzi sady nástrojů kompilátoru Visual Studio 2017.

Použití **-vcvars_ver = 14.1 x .yyyyy** určit konkrétní verzi sady nástrojů kompilátoru Visual Studio 2017.

::: moniker-end

Použití **-vcvars_ver = 14.0** k určení sady nástrojů kompilátoru Visual Studio 2015.

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>K nastavení prostředí pro sestavení v existující okno příkazového řádku

1. Na příkazovém řádku pomocí příkazu CD přejděte do adresáře instalace sady Visual Studio. Potom použijte CD znovu změnit na podadresář, který obsahuje soubory příkazů určených pro konfigurace. Visual Studio 2019 a Visual Studio 2017 *VC\\pomocné\\sestavení* podadresáře. Pro Visual Studio 2015, použijte *VC* podadresáře.

1. Zadejte příkaz pro upřednostňovaných vývojářského prostředí. Například k sestavení kódu ARM pro UPW na 64bitové platformě pomocí nejnovější sadu Windows SDK a sady Visual Studio sadu nástrojů kompilátoru, použijte tento příkazový řádek:

   `vcvarsall.bat amd64_arm uwp`

## <a name="create-your-own-command-prompt-shortcut"></a>Vytvoření vlastního zástupce příkazového řádku

::: moniker range=">= vs-2019"

Otevřete dialogové okno Vlastnosti pro zástupce příkazového řádku pro vývojáře najdete v tématu příkazu cíle použít. Například cíl **x64 Native Tools Command Prompt pro VS 2019** zástupce je podobný:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="= vs-2017"

Otevřete dialogové okno Vlastnosti pro zástupce příkazového řádku pro vývojáře najdete v tématu příkazu cíle použít. Například cíl **x64 Native Tools Command Prompt pro VS 2017** zástupce je podobný:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="< vs-2017"

Otevřete dialogové okno Vlastnosti pro zástupce příkazového řádku pro vývojáře najdete v tématu příkazu cíle použít. Například cíl **VS2015 x64 Native Tools Command Prompt** zástupce je podobný:

`%comspec% /k ""C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat"" amd64`

::: moniker-end

Specifické pro architekturu dávkové soubory sady *architektura* vcvarsall.bat parametr a volání. K těmto souborům služby batch můžete předat stejné možnosti, jak by předat vcvarsall.bat nebo vcvarsall.bat lze volat pouze přímo. Zadat parametry pro příkaz zástupce, přidejte je na konec příkazu v uvozovkách. Například tady je místní a začít vytvářet kód ARM pro UPW pro 64bitové platformy, pomocí nejnovější sadu Windows SDK. Pokud chcete používat starší sada nástrojů kompilátoru, zadejte číslo verze. Ve vaší místní pomocí něčeho jako cíl tohoto příkazu:

::: moniker range=">= vs-2019"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.16"`

::: moniker-end
::: moniker range="= vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.0"`

::: moniker-end
::: moniker range="< vs-2017"

`%comspec% /k ""C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat"" amd64 -vcvars_ver=12.0`

::: moniker-end

Upravte cestu tak, aby odrážely adresáře instalace sady Visual Studio. Soubor vcvarsall.bat obsahuje další informace o číslech konkrétní verzi.

## <a name="command-line-tools"></a>Nástroje příkazového řádku

K sestavení C /C++ projekt na příkazovém řádku aplikace Visual Studio poskytuje nástroje příkazového řádku:

[CL](reference/compiling-a-c-cpp-program.md)<br/>
Zkompilujte a propojte soubory zdrojového kódu do aplikací, knihoven a knihovny DLL pomocí kompilátoru (cl.exe).

[Odkaz](reference/linking.md)<br/>
Pokud chcete připojit zkompilované soubory objektů a knihovny do aplikací a knihoven DLL použijte linker (link.exe).

[MSBuild](msbuild-visual-cpp.md)<br/>
Slouží ke konfiguraci sestavení a nepřímo volat sada nástrojů MSBuild (msbuild.exe) a soubor projektu (.vcxproj). Je ekvivalentní s běžící **sestavení** projektu nebo **sestavit řešení** příkazu v integrovaném vývojovém prostředí sady Visual Studio. Spuštění nástroje MSBuild z příkazového řádku je pokročilý scénář a doporučuje nejčastěji.

[NÁSTROJE DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
Použití nástroje DEVENV (devenv.exe) v kombinaci s přepínačem příkazového řádku, jako **/Build** nebo **/Clean** k provedení určité příkazy sestavení bez zobrazení integrovaném vývojovém prostředí sady Visual Studio. Obecně platí DEVENV je upřednostňována před použití nástroje MSBuild přímo, protože můžete umožnit, aby složitosti MSBuild sady Visual Studio.

[NMAKE](reference/nmake-reference.md)<br/>
Pomocí NMAKE (nmake.exe) ve Windows můžete vytvářet projekty C++ založené na tradiční souboru pravidel.

Při sestavování v příkazovém řádku příkaz F1 není k dispozici rychlou nápovědu. Místo toho vyhledávacího webu můžete použít k získání informací o upozornění, chyby a zprávy, nebo můžete použít soubory offline Nápověda. Hledání v [docs.microsoft.com](https://docs.microsoft.com/cpp/), použijte vyhledávací pole v horní části stránky.

## <a name="in-this-section"></a>V tomto oddílu

Tyto články ukazují, jak vytvářet aplikace v příkazovém řádku a popisují, jak přizpůsobit prostředí sestavení z příkazového řádku. Některé ukazují, jak používat 64bitové sady nástrojů a cílit na x86, x 64, ARM, ARM64 platformy a. Najdete zde také popis sestavení z příkazového řádku nástroje MSBuild a příkaz NMAKE.

[Návod: Kompilace nativního programu C++ na příkazovém řádku](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
Poskytuje příklad, který ukazuje, jak vytvořit a zkompilujte C++ program na příkazovém řádku.

[Návod: Kompilace programu C na příkazovém řádku](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
Popisuje, jak kompilovat program napsaný v programovacím jazyce C.

[Návod: Kompilace programu C++/CLI na příkazovém řádku](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
Popisuje, jak vytvořit a zkompilujte C++vyhodnocovací program, který používá rozhraní .NET Framework.

[Návod: Kompilace programu C++/CX na příkazovém řádku](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
Popisuje, jak vytvořit a zkompilujte C++/CX program, který používá prostředí Windows Runtime.

[Nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
Jak nastavit proměnné prostředí použít 32bitový nebo 64bitové sady nástrojů k cíli x86, x64, ARM, ARM64 platformy a.

[NMAKE – referenční zdroje](reference/nmake-reference.md)<br/>
Obsahuje odkazy na články, které popisují Program údržby nástroj Microsoft (NMAKE. SOUBOR EXE).

[MSBuild na příkazovém řádku - C++](msbuild-visual-cpp.md)<br/>
Obsahuje odkazy na články, které popisují postup použít msbuild.exe příkazovém řádku.

## <a name="related-sections"></a>Související oddíly

[/MD, /MT, /LD (použití knihovny run-time)](reference/md-mt-ld-use-run-time-library.md)<br/>
Popisuje, jak pomocí těchto možností kompilátoru pro použití knihovny run-time ladění nebo vydání.

[Možnosti kompilátoru C/C++](reference/compiler-options.md)<br/>
Obsahuje odkazy na články, které popisují možnosti kompilátoru C a C++ a CL.exe.

[Možnosti linkeru MSVC](reference/linker-options.md)<br/>
Obsahuje odkazy na články, které popisují možnosti linkeru a LINK.exe.

[Nástroje pro vytváření dalších MSVC](reference/c-cpp-build-tools.md)<br/>
Poskytuje nástroje, které jsou zahrnuty v sadě Visual Studio pro vytváření odkazy pro C/C++.

## <a name="see-also"></a>Viz také:

[Projekty a systémy sestavení](projects-and-build-systems-cpp.md)
