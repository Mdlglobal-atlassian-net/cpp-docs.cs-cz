---
title: Vytvoření kódu C/C++ v příkazovém řádku | Microsoft Docs
ms.custom: ''
ms.date: 03/29/2018
ms.technology:
- cpp-tools
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fc4ec1034d4d77542df4a4241ad3ba5c087602ae
ms.sourcegitcommit: 78e5e5cdbafd29e2a6ccf68d4cce215136952907
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2018
---
# <a name="build-cc-code-on-the-command-line"></a>Vytvoření kódu C/C++ v příkazovém řádku

Pomocí nástrojů, které jsou zahrnuté v sadě Visual Studio můžete vytvořit aplikace C a C++ v příkazovém řádku.

## <a name="how-to-get-the-command-line-tools"></a>Jak získat nástroje příkazového řádku

Když vyberete některou úloh C++ v instalačním programu Visual Studio, nainstaluje sady Visual Studio *sada nástrojů platformy*. Sada nástrojů platformy má nástroje C a C++ pro konkrétní verzi sady Visual Studio, včetně kompilátory jazyka C/C++, linkers, kompletující a další nástroje pro sestavení, jakož i odpovídající knihovny. Všechny tyto nástroje můžete použít na příkazovém řádku a také používají se interně v prostředí Visual Studio IDE. Existují samostatné x86 hostovaná a je hostovaná x64 kompilátory a nástroje potřebné k vytváření kódu pro ARM x86 x 64 a ARM64 cíle. Každá sada nástrojů pro konkrétní architekturu sestavení hostitele a cíle je uložen v jeho vlastní adresáře.

Fungovala správně, vyžadují nástroje řady proměnných prostředí konkrétní nastavení. Ty se používají k je přidejte do cesty a k nastavení zahrnují souboru, soubor knihovny a umístění SDK. Můžete snadno nastavit těchto proměnných prostředí, instalační program vytvoří vlastní *soubory příkazů*, nebo dávkové soubory, během instalace. Můžete spustit jeden z těchto souborů příkazu v okně příkazového řádku k nastavení konkrétního hostitele a architektura cíl sestavení, verze sady Windows SDK, cílové platformy a sada nástrojů platformy. Pro usnadnění práce, instalační program vytvoří také zástupce v nabídce Start (nebo úvodní stránku v systému Windows 8.x), spusťte příkazový řádek vývojáře systému windows pomocí tyto soubory příkaz tak, aby byly všechny požadované prostředí proměnné nastavené a připravené k použití.

Požadované prostředí proměnné jsou specifické pro instalaci a architektura sestavení vyberte a může být změněna produktu aktualizace nebo upgrady. Proto důrazně doporučujeme použít jednu zástupce nainstalované příkazového řádku nebo soubory příkazů místo nastavení proměnných prostředí ve Windows sami. Další informace najdete v tématu [nastavit cesty a proměnných prostředí pro sestavení příkazového řádku](../build/setting-the-path-and-environment-variables-for-command-line-builds.md).

Modulové příkazového řádku, soubory příkazů a zástupce příkazového řádku, které jsou nainstalovány závisí na procesor počítače a možnosti výběru během instalace. Minimálně jsou nainstalovány 32bitové hostované x86 nástroje, které sestavení 32bitového x86 nativního kódu a různé nástroje, které sestavení 64-bit x64 nativního kódu. Pokud máte 64bitová verze Windows, jsou nainstalovány také 64bitové hostované x64 nástroje, které sestavení nativní 64bitový kód a různé nástroje, které sestavení 32-bit nativního kódu. Pokud si zvolíte instalaci volitelných nástrojů C++ Universal Windows Platform, pak 32bitové a 64bitové verze nativní nástroje, které sestavení ARM kódu jsou také nainstalované. Další úlohy, může nainstalovat další nástroje.

## <a name="developer-command-prompt-shortcuts"></a>Zástupce příkazového řádku vývojáře

Zástupce příkazového řádku jsou nainstalovány ve složce specifické pro verzi Visual Studio v nabídce Start. Tady je seznam zástupců základní příkazového řádku a architektury sestavení, které podporují:

- **Příkazový řádek vývojáře** -nastaví prostředí tak, aby používat 32-bit, x86 nativních nástrojů pro vytváření 32-bit, x86 nativního kódu.
- **x86 nativní nástroje příkazového řádku** -nastaví prostředí tak, aby používat 32-bit, x86 nativních nástrojů pro vytváření 32-bit, x86 nativního kódu.
- **x64 nativní nástroje příkazového řádku** -nastaví prostředí pomocí 64-bit, x64 nativních nástrojů pro sestavení 64-bit, x64 nativního kódu.
- **x86_x64 různé nástroje pro příkazový řádek** -nastaví prostředí pomocí 32-bit, x86 nativních nástrojů pro sestavení 64-bit, x64 nativního kódu.
- **x64_x86 různé nástroje pro příkazový řádek** -nastaví prostředí tak, aby používat 64-bit, x64 nativních nástrojů pro vytváření 32-bit, x86 nativního kódu.

Skutečné počáteční složky a místní názvy nabídek lišit v závislosti na verzi Visual Studia, instalaci a instalaci přezdívka, pokud jste nastavili jednu. Pro příklad, pokud máte Visual Studio 2017 nainstalován a vy jste danou ho instalace Přezdívka z *Preview*, má název zástupce příkazového řádku vývojáře **příkazový řádek vývojáře pro VS 2017 (Preview)**, ve složce s názvem **Visual Studio 2017**.

Pokud jste nainstalovali [nástroje sestavení pro Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=840931) (který také obsahuje sady nástrojů kompilátoru Visual Studio 2015 Update 3), jenom na konkrétní architektury nativní nebo mezi nástroje příkazového řádku vývojáře možnosti jsou nainstalovány. a ne obecný **příkazový řádek vývojáře** zástupce.

<a name="developer_command_prompt"></a>
### <a name="to-open-a-developer-command-prompt-window"></a>Chcete-li otevřít okno příkazového řádku vývojáře

1. Na ploše otevřete Windows **spustit** nabídce a potom přejděte k vyhledání a otevřete složku pro vaši verzi sady Visual Studio, například **Visual Studio 2017**. V některých starších verzí sady Visual Studio zástupce jsou v podsložce s názvem **nástroje sady Visual Studio**.

1. Ve složce, vyberte **příkazový řádek vývojáře** pro vaši verzi sady Visual Studio. Tento zástupce spustí okno příkazového řádku vývojáře využívající architekturu sestavení výchozí 32-bit, x86 nativních nástrojů k sestavení 32-bit, x86 nativního kódu. Pokud dáváte přednost architektura sestavení jiné než výchozí, vyberte jednu z nativního nebo mezi nástroje okna příkazového řádku k určení architektura hostitele a cíle.

Otevřete okno příkazového řádku vývojáře ještě rychleji je zadání *příkazový řádek vývojáře* plochy vyhledávacího pole, pak vyberte požadovaný výsledek.

## <a name="developer-command-files-and-locations"></a>Soubory příkazů Developer a umístění

Pokud dáváte přednost nastavení prostředí architektura sestavení v existujícího okna příkazového řádku, můžete jeden ze souborů příkazu (dávkové soubory) vytvořený instalačním programem nastavit požadované prostředí. Pouze doporučujeme to udělat v novém okně příkazového řádku a nedoporučujeme vám novější přepínače prostředí ve stejném okně příkazu. Umístění těchto souborů závisí na verzi sady Visual Studio, které jste nainstalovali a na umístění a pojmenování volby, které jste nastavili během instalace. Pro Visual Studio 2017 umístěním typické instalace na 64bitovém počítači je \Program soubory (x86) \Microsoft Visual Studio\2017\\*edition*, kde *edice* může být komunity Professional, Enterprise, BuildTools nebo jiný název, který jste zadali. Pro Visual Studio 2015 umístěním typické instalace je \Program Files (x86) \Microsoft Visual Studio 14.0.

Primární vývojáře soubor příkazů příkazového řádku, VsDevCmd.bat, se nachází v instalačním adresáři na Common7\Tools. Pokud nejsou zadány žádné parametry, nastaví tato prostředí a hostitele a cíl sestavení architekturu pro sestavení 32-bit x86 pomocí nástrojů pro 32-bit x86 nativní kód.

Další příkaz soubory jsou k dispozici nastavit konkrétní sestavení architektury, v závislosti na architektuře procesoru a úloh v sadě Visual Studio a možnosti, které jste nainstalovali. V 2017 Visual Studio ty jsou umístěny v podadresáři VC\Auxiliary\Build instalační adresář nástroje Visual Studio. V sadě Visual Studio 2015, jsou umístěny v VC, VC\bin nebo VC\bin\\*architektury* podadresáře instalační adresář, kde *architektury* je jedním z nativního nebo možnosti kompilátoru mezi. Tyto soubory příkazu nastavte výchozí parametry a volání VsDevCmd.bat nastavení prostředí architektura zadané sestavení. Typické instalace může zahrnovat tyto soubory příkazů:

|Soubor příkazů|Hostitele a cílové architektury|
|---|---|
|**vcvars32.bat**| Pomocí nástrojů pro nativní x86 32bitová verze sestavení 32-bit x86 kódu.|
|**vcvars64.bat**| Použít k vytvoření 64-bit x64 nástroje x64 nativní 64bitový kód.|
|**vcvarsx86_amd64.bat**| Pomocí nástrojů křížové x86 nativní 32bitová verze sestavení 64-bit x64 kódu.|
|**vcvarsamd64_x86.bat**| Pomocí nástrojů pro křížové x64 nativní 64bitové verze sestavení x86 32-bit kódu.|
|**vcvarsx86_arm.bat**| Pomocí nástrojů křížové x86 nativní 32bitová verze sestavení kódu ARM.|
|**vcvarsamd64_arm.bat**| Pomocí nástrojů křížové x64 nativní 64bitová verze sestavení kódu ARM.|
|**vcvarsall.bat**| Pomocí parametrů můžete určit na hostiteli a cílové architektury, a také možnosti sady SDK a platformy. Seznam podporovaných možností pro volání **/help** parametr.|

> [!CAUTION]
> Soubor vcvarsall.bat a další soubory příkazů sady Visual Studio se může lišit počítačů. Nepřepisovat existující soubor nebo je poškozena vcvarsall.bat pomocí souboru z jiného počítače. Znovu spusťte instalační program sady Visual Studio k nahrazení chybějícího souboru.
>
> Soubor vcvarsall.bat se také liší v závislosti na verzi. Pokud je aktuální verze sady Visual Studio nainstalovaná na počítači, který má také starší verze sady Visual Studio, nespouštějte vcvarsall.bat nebo jiný soubor příkazů sady Visual Studio z různých verzí ve stejném okně příkazového řádku.

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>Použití nástrojů pro vývojáře v existující příkazové okno

Nejjednodušší způsob, jak určit konkrétní sestavení architektura v existující příkazové okno je chcete použít soubor vcvarsall.bat. Vcvarsall.bat můžete použít k nastavení proměnných prostředí ke konfiguraci příkazového řádku pro nativní kompilace 32bitové nebo 64bitové, nebo mezi kompilace x86, x64 nebo procesory ARM; cíl Microsoft Store, univerzální platformu Windows nebo platformy Windows Desktop; Chcete-li určit Windows SDK, které se použije. a zadejte verzi sady nástrojů platformy. Pokud jsou k dispozici žádné argumenty, vcvarsall.bat nakonfiguruje proměnných prostředí pro používání aktuální 32-bit nativního kompilátoru pro x86 Windows Desktop cíle. Ale můžete použít ke konfiguraci libovolné nativního nebo křížové nástrojů kompilátoru. Pokud zadáte konfigurace kompilátoru, která není nainstalována nebo není k dispozici v vaší sestavení počítače architektury, se zobrazí chybová zpráva.

### <a name="vcvarsall-syntax"></a>Syntaxe vcvarsall

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [**-vcvars_ver=**_vcversion_]

*architecture*<br/>
Tento volitelný argument určuje architektuře hostitele a cíle použít. Pokud *architektura* není zadán, se používá výchozí prostředí sestavení. Podporují se tyto argumenty:

|*architecture*|Kompilátoru|Architektura počítače hostitele|Sestavení architektura výstup (cíl)|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|x86 nativní 32-bit|x86, x64|x86|
|**x86\_amd64** nebo **x86\_x64**|mezi x64 na x86|x86, x64|x64|
|**x86_arm**|ARM na x86 mezi|x86, x64|ARM|
|**x86_arm64**|ARM64 na x86 mezi|x86, x64|ARM64|
|**AMD64** nebo **x64**|x64 nativní 64bitová verze|x64|x64|
|**AMD64\_x86** nebo **x64\_x86**|mezi x86 na x64|x64|x86|
|**AMD64\_arm** nebo **x64\_arm**|ARM na x64 mezi|x64|ARM|
|**AMD64\_arm64** nebo **x64\_arm64**|ARM64 na x64 mezi|x64|ARM64|

*platform_type*<br/>
Tento volitelný argument umožňuje určit **ukládání** nebo **uwp** jako typu platformy. Ve výchozím nastavení prostředí nastavena můžete vytvářet aplikace, plocha nebo konzoly.

*winsdk_version*<br/>
Volitelně určuje verzi sady Windows SDK používat. Ve výchozím nastavení se používá nejnovější nainstalované Windows SDK. K určení verze sady Windows SDK, můžete použít úplnou číslo Windows 10 SDK, jako **10.0.10240.0**, nebo zadejte **8.1** k využívání sady SDK pro Windows 8.1.

*vcversion*<br/>
Volitelně můžete určit sady nástrojů kompilátoru Visual Studio, používat. Ve výchozím nastavení prostředí nastavena používat aktuální sady nástrojů kompilátoru Visual Studio 2017. Použití **-vcvars_ver = 14.0** k určení sady nástrojů kompilátoru Visual Studio 2015.

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>Nastavení prostředí sestavení v existujícím okně příkazového řádku

1. Na příkazovém řádku přejděte do adresáře instalace sady Visual Studio pomocí příkazu disku CD. Potom pomocí disku CD-ROM znovu změnit na podadresáře, který obsahuje soubory konfigurace konkrétní příkaz. Pro Visual Studio 2017 jde podadresáři VC\Auxiliary\Build. Pro Visual Studio 2015 použijte podadresáři VC.

1. Zadejte příkaz pro upřednostňované vývojářského prostředí. Například k sestavení kódu ARM pro UPW na 64bitové platformě pomocí nejnovější Windows SDK a sady nástrojů kompilátoru Visual Studio 2017 RTM, použijte tento příkazový řádek:

   `vcvarsall.bat amd64_arm uwp -vcvars_ver=14.10`

## <a name="create-your-own-command-prompt-shortcut"></a>Vytvořit vlastní zástupce příkazového řádku

Pokud otevřete dialogové okno Vlastnosti pro jednu z existujících zástupce příkazového řádku vývojáře, uvidíte cíl příkazu použít. Například cíle pro **x64 nativní nástroje příkazového řádku pro VS 2017** zástupce je něco podobného jako:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

Batch architektura konkrétní soubory sady *architektura* vcvarsall.bat parametr a volání. Tyto dávkové soubory lze předat stejné další možnosti, jako by předat vcvarsall.bat nebo vcvarsall.bat právě volat přímo. K určení parametrů příkazu zkratku, přidáte na konec příkazu v uvozovky. Například nastavit zástupce stavět ARM kód pro UPW na 64bitové platformě pomocí nejnovější Windows SDK a sady nástrojů kompilátoru Visual Studio 2017 RTM, použijte něco jako tento cíl příkazu ve vaší místní:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.10"`

Je nutné upravit cesta tak, aby odrážela adresáře instalace sady Visual Studio.

## <a name="command-line-tools"></a>Nástroje příkazového řádku

Pro vytvoření projektu jazyka C nebo C++ v příkazovém řádku, Visual Studio poskytuje tyto nástroje příkazového řádku:

[CL](../build/reference/compiling-a-c-cpp-program.md)<br/>
Pro zkompilování a spojení soubory zdrojového kódu do aplikace, knihovny a knihovny DLL pomocí kompilátoru (cl.exe).

[Link](../build/reference/linking.md)<br/>
Použijte linker (link.exe) pro propojení zkompilovaný objekt soubory a knihovny do aplikace a knihovny DLL.

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)<br/>
Pomocí nástroje MSBuild (msbuild.exe) vytvářet projekty Visual C++ a řešení sady Visual Studio. Jde o ekvivalent spuštění **sestavení** projektu nebo **sestavit řešení** příkazu v prostředí Visual Studio IDE.

[NÁSTROJE DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
Použití nástroje DEVENV (devenv.exe) v kombinaci s přepínačem příkazového řádku – například **/Build** nebo **/Clean**– k provedení určité příkazy sestavení bez zobrazení Visual Studio IDE.

[NMAKE](../build/nmake-reference.md)<br/>
Použijte k automatizaci úloh, které sestavení projektů Visual C++ pomocí tradičních souboru pravidel NMAKE (nmake.exe).

Při sestavování na příkazovém řádku příkaz F1 není k dispozici pro rychlou pomoc. Místo toho vyhledávacího webu můžete získat informace o upozornění, chyby a zprávy, nebo můžete použít soubory offline nápovědy. Používání funkce Hledat v [docs.microsoft.com](https://docs.microsoft.com/cpp/), zadejte hledaný řetězec do vyhledávacího pole v horní části stránky.

## <a name="in-this-section"></a>V tomto oddílu

Články v této části dokumentace ukazují, jak vytvářet aplikace, na příkazovém řádku, které popisují, jak přizpůsobit sestavení příkazového řádku prostředí použít 64-bit modulové a cíl x86, x64 a ARM platformy a ukazují, jak používat sestavení příkazového řádku nástroje MSBuild a příkaz NMAKE.

[Návod: Kompilace nativního programu C++ v příkazovém řádku](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
Poskytuje příklad, který ukazuje, jak vytvořit a kompilaci jednoduché programu C++ v příkazovém řádku.

[Návod: Kompilace programu v jazyce C na příkazovém řádku](../build/walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
Popisuje způsob kompilace programu v jazyce programovacího jazyka C.

[Návod: Kompilace programu C++/CLI v příkazovém řádku](../build/walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
Popisuje, jak vytvořit a kompilaci C + +/ CLI program, který používá rozhraní .NET Framework.

[Návod: Kompilace programu C++/CX v příkazovém řádku](../build/walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
Popisuje, jak vytvořit a kompilaci C + +/ CX program, který používá prostředí Windows Runtime.

[Nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
Popisuje, jak spustit okno příkazového řádku, který má proměnné požadované prostředí pro sestavení příkazového řádku nastavit cílených x86, x64 a ARM platforem pomocí nástrojů 32bitové nebo 64bitové verze.

[NMAKE – referenční zdroje](../build/nmake-reference.md)<br/>
Obsahuje odkazy na články, které popisují Program údržby nástroj Microsoft (NMAKE. SOUBOR EXE).

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)<br/>
Obsahuje odkazy na články, které vysvětluje použití MSBuild.EXE.

## <a name="related-sections"></a>Související oddíly

[/MD, /MT, /LD (použití knihovny run-time)](../build/reference/md-mt-ld-use-run-time-library.md)<br/>
Popisuje, jak pomocí těchto možností kompilátoru pro použití běhové knihovny ladění nebo verze.

[Možnosti kompilátoru C/C++](../build/reference/compiler-options.md)<br/>
Obsahuje odkazy na články, které popisují možnosti kompilátoru C a C++ a CL.exe.

[Možnosti linkeru](../build/reference/linker-options.md)<br/>
Obsahuje odkazy na články, které popisují možnosti linkeru a LINK.exe.

[Nástroje sestavení C/C++](../build/reference/c-cpp-build-tools.md)<br/>
Poskytuje nástroje, které jsou zahrnuté v sadě Visual Studio pro vytváření odkazy pro C/C++.

## <a name="see-also"></a>Viz také

[Sestavování programů v jazyce C/C++](../build/building-c-cpp-programs.md)