---
title: Použijte sadu nástrojů MSVC z příkazového řádku – Visual Studio
description: Pomocí nástrojů Microsoft C++ kompilátor (MSVC) z příkazového řádku mimo rozhraní IDE sady Visual Studio.
ms.custom: conceptual
ms.date: 12/10/2018
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: 21d1c9063a1d6dd154de8d2caca913ea3fd0ce37
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342155"
---
# <a name="use-the-msvc-toolset-from-the-command-line"></a>Použití nástrojů MSVC z příkazového řádku

Pomocí nástrojů, které jsou zahrnuty v sadě Visual Studio můžete vytvářet aplikace jazyka C a C++ v příkazovém řádku. Sada nástrojů kompilátoru si můžete stáhnout také jako samostatného balíčku z [Build Tools pro Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=875721).

## <a name="how-to-use-the-command-line-tools"></a>Jak používat nástroje příkazového řádku

Když vyberete některou C++ zátěží v instalačním programu sady Visual Studio, nainstaluje Visual Studio *sada nástrojů platformy*. Sada nástrojů platformy má nástroje pro konkrétní verze sady Visual Studio, včetně kompilátory jazyka C/C++, linkers, montážní společnosti a dalších nástrojů sestavování, jakož i odpovídající knihovny vytváření C a C++. Můžete použít všechny tyto nástroje příkazového řádku a používají se také interně v integrovaném vývojovém prostředí sady Visual Studio. Existují samostatné hostované x86 a x64 hostované kompilátory a nástroje pro vytváření kódu pro x86, x 64, ARM a ARM64 cíle. Každá sada nástrojů pro konkrétní architekturu hostitele a cílovém sestavení je uložen do vlastního adresáře.

Sady nástrojů kompilátoru, které jsou nainstalovány, závisí na procesoru počítače a možnosti, které vybrali při instalaci. Minimálně jsou nainstalovány 32bitové hostované x86 nástroje, které sestavení 32-bit x86 nativního kódu a různé nástroje, které sestavení 64-bit x64 nativní kód. Pokud máte Windows 64-bit, nainstaluje se také 64bitové hostované x64 nástroje, které sestavení nativního kódu 64bitovým kompilátorem a různé nástroje, které sestavení 32bitového nativního kódu. Pokud budete chtít nainstalovat nástroje pro univerzální platformu Windows C++ volitelné, pak 32bitové a 64bitové nativní nástroje, které sestavení kódu ARM jsou také nainstalované. Jiné úlohy může nainstalovat další nástroje.

## <a name="environment-variables-and-developer-command-prompts"></a>Proměnné prostředí a příkazového řádku pro vývojáře

Pracovala správně, nástroje vyžadují několik proměnných prostředí konkrétní nastavení. Ty se používají, je přidat do cesty a nastavit zahrnout soubor, soubor knihovny a umístění sad SDK. Abyste usnadnili snadnou k nastavení těchto proměnných prostředí, instalační program vytvoří přizpůsobené *soubory příkazů*, nebo dávkové soubory, během instalace. Spusťte jeden z těchto souborů příkazů v okně příkazového řádku k nastavení konkrétního hostitele a Cílová architektura sestavení, verzi sady Windows SDK, cílové platformy a sady nástrojů platformy. Pro usnadnění práce Instalační program také vytvoří zástupce v nabídce Start, která spustit příkazový řádek pro vývojáře systému windows s použitím těchto souborů příkaz tak, aby byly všechny požadované prostředí proměnné nastavené a připravené k použití.

Požadované prostředí proměnné jsou specifické pro vaši instalaci a sestavení architektury, vyberte a může být změněn aktualizace produktu nebo upgrady. Proto důrazně doporučujeme použít klávesové zkratky nainstalovaných příkazový řádek nebo soubory příkazů místo nastavení proměnných prostředí ve Windows sami. Další informace najdete v tématu [nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="developer_command_prompt_shortcuts"></a> Zástupce příkazového řádku pro vývojáře

Zástupce příkazového řádku se instalují do složky specifické pro verzi sady Visual Studio v nabídce Start. Tady je seznam zástupců základní příkazový řádek a sestavení architektury, které podporují:

- **Developer Command Prompt** – nastaví prostředí tak, aby 32-bit, nativní x86 nástroje použít k vytváření 32-bit, x86 nativní kód.
- **x86 native Tools Command Prompt** – nastaví prostředí tak, aby 32-bit, nativní x86 nástroje použít k vytváření 32-bit, x86 nativní kód.
- **x64 native Tools Command Prompt** – nastaví prostředí tak, aby použít 64-bit, x64 cloudově nativních nástrojů k vytváření 64-bit, x64 nativní kód.
- **x86_x64 Cross Tools Command Prompt** – nastaví prostředí tak, aby použití 32-bit x86 cloudově nativních nástrojů k vytvoření 64-bit, x64 nativní kód.
- **x64_x86 Cross Tools Command Prompt** – nastaví prostředí tak, aby použít 64-bit, x64 cloudově nativních nástrojů k vytváření 32-bit, x86 nativní kód.

Úvodní nabídky složky a místní názvy lišit v závislosti na verzi sady Visual Studio, které jste si nainstalovali a Přezdívka instalace, pokud nastavíte jednu. Například, pokud máte nainstalovanou sadu Visual Studio 2017 a jste jste vzhledem k jeho instalaci Přezdívka z *ve verzi Preview*, má název zástupce příkazového řádku pro vývojáře **Developer Command Prompt for VS 2017 (verze Preview)**, do složky s názvem **Visual Studio 2017**.

Pokud jste nainstalovali [Build Tools pro Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=875721) (které také obsahují sada nástrojů kompilátoru Visual Studio 2015 Update 3), pouze nativní specifické pro architekturu nebo různé nástroje příkazového řádku pro vývojáře, které jsou nainstalovány možnosti a není generálního **Developer Command Prompt** zástupce.

## <a name="developer_command_prompt"></a> Chcete-li otevřít okno příkazového řádku pro vývojáře

1. Na ploše otevřete Windows **Start** nabídky a pak přejděte k vyhledání a otevření složky pro vaši verzi sady Visual Studio, například **Visual Studio 2017**. V některých starších verzích sady Visual Studio jsou klávesové zkratky v podsložce s názvem **Visual Studio Tools**.

1. Ve složce, vyberte **Developer Command Prompt** pro vaši verzi sady Visual Studio. Tento zástupce spustí okno příkazového řádku pro vývojáře, který používá výchozí architektura sestavení 32-bit, x86 cloudově nativních nástrojů k vývoji 32-bit, x86 nativní kód. Pokud dáváte přednost architektura jiné než výchozí sestavení, zvolte jednu z nativní nebo různé nástroje příkazové řádky k určení hostitele a cílové architektury.

Otevřete okno příkazového řádku pro vývojáře ještě rychleji je zaujmout *příkazový řádek pro vývojáře* klasické pracovní plochy vyhledávacího pole, klikněte na tlačítko požadovaný výsledek.

## <a name="developer_command_file_locations"></a> Umístění souborů příkaz pro vývojáře

Pokud chcete nastavit prostředí pro sestavení architektury ve stávajícím okně příkazového řádku, můžete použít jeden z soubory příkazů (dávkové soubory) vytvořené pomocí Instalační služby nastavte požadované prostředí. Pouze doporučujeme to provést v novém okně příkazového řádku a nedoporučujeme je novější přepínače prostředí v příkazovém okně stejné. Umístění těchto souborů závisí na verzi sady Visual Studio, které jste nainstalovali a na umístění a pojmenování volby provedené během instalace. Pro Visual Studio 2017, je umístění typické instalace na 64bitovém počítači v \Microsoft Visual Studio\2017 soubory (x86) \Program\\*edition*, kde *edition* může být komunity, Professional, Enterprise, BuildTools nebo jiný název, který jste zadali. Pro sadu Visual Studio 2015 je umístění typické instalace v \Program Files (x86) \Microsoft Visual Studio 14.0.

Soubor příkazů hlavního vývojáře příkazového řádku, VsDevCmd.bat, se nachází v instalačním adresáři na Common7\Tools. Při nejsou zadány žádné parametry, tím se nastaví prostředí a hostitele a cílovém sestavení Architektura nástroje x86 nativní 32bitový použít k vytváření x86 32bitová verze kódu.

Další příkaz soubory jsou k dispozici k nastavení konkrétního sestavení architektury, v závislosti na architektuře procesoru a úlohy sady Visual Studio a možnosti, které jste nainstalovali. V sadě Visual Studio 2017 ty jsou umístěny v podadresáři VC\Auxiliary\Build z adresáře instalace sady Visual Studio. V sadě Visual Studio 2015, ty jsou umístěny v VC, VC\bin nebo VC\bin\\*architektury* podadresáře instalační adresář, ve kterém *architektury* je nativní nebo Možnosti křížový kompilátor. Tyto soubory příkaz nastavit výchozí parametry a volání VsDevCmd.bat k nastavení prostředí architektury zadané sestavení. Typické instalace může zahrnovat tyto soubory příkazů:

|Soubor příkazů|Hostitel a cílové architektury|
|---|---|
|**vcvars32.bat**| Nástroje x86 nativní 32bitový použít k vytváření x86 32bitová verze kódu.|
|**vcvars64.bat**| Nástroje x64 nativní 64bitové použít k vytváření 64-bit x64 kódu.|
|**vcvarsx86_amd64.bat**| Pomocí nástrojů mezi 32-bit x86 nativní k vytvoření 64-bit x64 kódu.|
|**vcvarsamd64_x86.bat**| 64-bit x64 nativní křížové nástroje použít k vytváření x86 32bitová verze kódu.|
|**vcvarsx86_arm.bat**| Pomocí nástrojů mezi 32-bit x86 nativní sestavení kódu ARM.|
|**vcvarsamd64_arm.bat**| Pomocí křížové nástroje x64 nativní 64bitové sestavení kódu ARM.|
|**vcvarsall.bat**| Pomocí parametrů můžete určit hostitele a cílové architektury, jakož i možnosti sady SDK a platformu. Seznam podporované možnosti, volání pomocí **/help** parametru.|

> [!CAUTION]
> Soubor vcvarsall.bat a další soubory příkazů sady Visual Studio se může lišit od počítače na počítač. Nepřepisovat existující soubor vcvarsall.bat nebo je poškozena pomocí souboru z jiného počítače. Znovu spusťte instalační program sady Visual Studio k nahrazení souboru chybí.
>
> Soubor vcvarsall.bat se také liší mezi verzemi. Pokud na počítači, který také používá starší verzi sady Visual Studio je nainstalovaná aktuální verze sady Visual Studio, nespouštějte vcvarsall.bat nebo jiného souboru příkazů sady Visual Studio z různých verzí ve stejném okně příkazového řádku.

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>Pomocí vývojářských nástrojů v existujících příkazové okno

Použít soubor vcvarsall.bat je nejjednodušší způsob, jak určit konkrétní sestavení architektury v existující příkazové okno. Můžete nastavit proměnné prostředí příkazového řádku pro nativní kompilace 32bitové nebo 64bitové, nebo pro křížové kompilace x86, x64 nebo procesory ARM; konfigurace vcvarsall.bat Chcete-li cílit na Microsoft Store, Windows Desktop platformy; nebo univerzální platformu Windows Chcete-li určit, které Windows SDK se použije. a určit verzi sady nástrojů platformy. Pokud nejsou zadány žádné argumenty, vcvarsall.bat nastaví proměnné prostředí pro používání aktuální 32bitového nativního kompilátoru pro x86 cílů Windows Desktop. Ale můžete použít ke konfiguraci libovolné nativní nebo kompilátoru nástrojů pro různé. Pokud chcete zadat nastavení kompilátoru, který není nainstalován nebo není k dispozici na architektuře počítače sestavení, zobrazí se chybová zpráva.

### <a name="vcvarsall-syntax"></a>Syntaxe vcvarsall

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [**-vcvars_ver=**_vcversion_]

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
Volitelně určuje sada nástrojů kompilátoru Visual Studio používat. Ve výchozím nastavení je prostředí nastaveno použití aktuální sady nástrojů kompilátoru Visual Studio 2017. Použití **-vcvars_ver = 14.0** k určení sady nástrojů kompilátoru Visual Studio 2015.

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>K nastavení prostředí pro sestavení v existující okno příkazového řádku

1. Na příkazovém řádku pomocí příkazu CD přejděte do adresáře instalace sady Visual Studio. Potom použijte CD znovu změnit na podadresář, který obsahuje soubory příkazů určených pro konfigurace. Pro Visual Studio 2017 jde VC\Auxiliary\Build podadresáře. Pro Visual Studio 2015 použijte podadresáři VC.

1. Zadejte příkaz pro upřednostňovaných vývojářského prostředí. Například k sestavení kódu ARM pro UPW na 64bitové platformě pomocí nejnovější sadu Windows SDK a sady nástrojů kompilátoru Visual Studio 2017 RTM, použijte tento příkazový řádek:

   `vcvarsall.bat amd64_arm uwp -vcvars_ver=14.10`

## <a name="create-your-own-command-prompt-shortcut"></a>Vytvoření vlastního zástupce příkazového řádku

Pokud otevřete dialogové okno Vlastnosti pro jeden z existujícího klávesové zkratky příkazového řádku pro vývojáře, zobrazí se cíl příkazu použít. Například cíl **x64 Native Tools Command Prompt pro VS 2017** zástupce je podobný:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

Specifické pro architekturu dávkové soubory sady *architektura* vcvarsall.bat parametr a volání. K těmto souborům služby batch můžete předat stejné další možnosti, jak by předat vcvarsall.bat nebo vcvarsall.bat lze volat pouze přímo. Zadat parametry pro příkaz zástupce, přidejte je na konec příkazu v uvozovkách. Například pokud chcete nainstalovat zástupce pro sestavení kódu ARM pro UPW na 64bitové platformě pomocí nejnovější sadu Windows SDK a sady nástrojů kompilátoru Visual Studio 2017 RTM, pomocí něčeho jako tento cíl příkazu ve vaší místní:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.10"`

Je nutné upravit cestu tak, aby odrážely adresáře instalace sady Visual Studio.

## <a name="command-line-tools"></a>Nástroje příkazového řádku

K vytvoření projektu jazyka C/C++ v příkazovém řádku sady Visual Studio poskytuje nástroje příkazového řádku:

[CL](reference/compiling-a-c-cpp-program.md)<br/>
Zkompilujte a propojte soubory zdrojového kódu do aplikací, knihoven a knihovny DLL pomocí kompilátoru (cl.exe).

[Odkaz](reference/linking.md)<br/>
Pokud chcete připojit zkompilované soubory objektů a knihovny do aplikací a knihoven DLL použijte linker (link.exe).

[MSBuild](msbuild-visual-cpp.md)<br/>
Slouží ke konfiguraci sestavení a nepřímo volat sada nástrojů MSBuild (msbuild.exe) a soubor projektu (.vcxproj). Jedná se o ekvivalent spuštění **sestavení** projektu nebo **sestavit řešení** příkazu v integrovaném vývojovém prostředí sady Visual Studio. Spuštění nástroje MSBuild z příkazového řádku je pokročilý scénář a obecně není doporučeno.

[NÁSTROJE DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
Použití nástroje DEVENV (devenv.exe) v kombinaci s přepínačem příkazového řádku – například **/Build** nebo **/Clean**– k provedení určité příkazy sestavení bez zobrazení integrovaném vývojovém prostředí sady Visual Studio. To je obecně upřednostňované za použití nástroje MSBuild přímo, protože můžete umožnit, aby Visual Studio zpracovávat složité MSBuild.

[NMAKE](reference/nmake-reference.md)<br/>
Pomocí NMAKE (nmake.exe) ve Windows můžete vytvářet projekty C++ založené na tradiční souboru pravidel.

Při sestavování v příkazovém řádku příkaz F1 není k dispozici pro rychlou nápovědu. Místo toho vyhledávacího webu můžete použít k získání informací o upozornění, chyby a zprávy, nebo můžete použít soubory offline Nápověda. Hledání v [docs.microsoft.com](https://docs.microsoft.com/cpp/), zadejte hledaný řetězec do vyhledávacího pole v horní části stránky.

## <a name="in-this-section"></a>V tomto oddílu

Články v této části dokumentace ukazují, jak vytvářet aplikace v příkazovém řádku, které popisují, jak přizpůsobit prostředí sestavení z příkazového řádku použít 64-bit sady nástrojů a cíl x86, x64 a ARM platformy a ukazují, jak použít příkazový řádek sestavení nástroje MSBuild a příkaz NMAKE.

[Návod: Kompilace nativního programu C++ na příkazovém řádku](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
Poskytuje příklad, který ukazuje, jak vytvořit a zkompilujte jednoduchý program jazyka C++ v příkazovém řádku.

[Návod: Kompilace programu C na příkazovém řádku](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
Popisuje, jak kompilovat program napsaný v programovacím jazyce C.

[Návod: Kompilace programu C++/CLI na příkazovém řádku](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
Popisuje, jak vytvořit a zkompilujte C++vyhodnocovací program, který používá rozhraní .NET Framework.

[Návod: Kompilace programu C++/CX na příkazovém řádku](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
Popisuje, jak vytvořit a zkompilujte C++/CX program, který používá prostředí Windows Runtime.

[Nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
Popisuje, jak spustit okno příkazového řádku, který má požadované proměnné nastavit pro sestavení příkazového řádku, které cílí x86, x64 a ARM platformy s využitím 32bitová nebo 64bitová verze nástrojů.

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