---
title: "Vytvoření kódu C/C++ v příkazovém řádku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f613c20e0cab45a8eaa802c4c7ba0c6ac391357
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="build-cc-code-on-the-command-line"></a>Vytvoření kódu C/C++ v příkazovém řádku

Můžete vytvořit aplikace C a C++ v příkazovém řádku pomocí nástrojů, které jsou součástí [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].

Pokud vyberete jednu z úloh C++ v [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] instalační program, nainstaluje sada nástrojů, která zahrnuje kompilátory jazyka C/C++, linkers, a další nástroje sestavení. Tyto nástroje jsou používány [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE a můžete také použít na příkazovém řádku. Existují samostatné x86 hostovaná a je hostovaná x64 kompilátory a nástroje pro sestavení kód pro x86, x64 a ARM cíle. Každá sada nástrojů pro konkrétní architekturu sestavení hostitele a cíle je uložen v jeho vlastní adresáře. Fungovala správně, vyžadují tyto nástroje několik určité proměnné prostředí je přidejte do cesty a k nastavení zahrnují souboru, soubor knihovny a umístění SDK. Instalační program vytvoří snadno nastavit těchto proměnných prostředí, soubory přizpůsobené příkazů, také známé jako dávkové soubory, během instalace. Můžete spustit jeden z těchto souborů příkazu v okně příkazového řádku nastavit architektura konkrétní sestavení. Pro usnadnění práce, instalační program vytvoří také zástupce v nabídce Start (nebo úvodní stránku v systému Windows 8.x), spusťte příkazový řádek vývojáře systému windows pomocí tyto soubory příkaz tak, aby byly všechny požadované prostředí proměnné nastavené a připravené k použití. 

Požadované prostředí proměnné jsou specifické pro instalaci a architektura sestavení vyberte a může být změněna produktu aktualizace nebo upgrady. Proto důrazně doporučujeme použít jednu zástupce nainstalované příkazového řádku nebo soubory příkazů místo nastavení proměnných prostředí ve Windows sami. Další informace najdete v tématu [nastavit cesty a proměnných prostředí pro sestavení příkazového řádku](../build/setting-the-path-and-environment-variables-for-command-line-builds.md).  

Modulové příkazového řádku, soubory příkazů a zástupce příkazového řádku, které jsou nainstalovány závisí na procesor počítače a možnosti výběru během instalace. Minimálně jsou nainstalovány 32bitové hostované x86 nástroje, které sestavení 32bitového x86 nativního kódu a různé nástroje, které sestavení 64-bit x64 nativního kódu. Pokud máte 64bitová verze Windows, jsou nainstalovány také 64bitové hostované x64 nástroje, které sestavení nativní 64bitový kód a různé nástroje, které sestavení 32-bit nativního kódu. Pokud si zvolíte instalaci volitelných nástrojů C++ Universal Windows Platform, pak 32bitové a 64bitové verze nativní nástroje, které sestavení ARM kódu jsou také nainstalované. Další úlohy, může nainstalovat další nástroje.

<a name="developer_command_prompt_shortcuts"></a>
## <a name="developer-command-prompt-shortcuts"></a>Zástupce příkazového řádku vývojáře

Zástupce příkazového řádku jsou nainstalovány ve specifické verze [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] složku v nabídce Start. Tady je seznam zástupců základní příkazového řádku a architektury sestavení, které podporují:

- **Příkazový řádek vývojáře** nastaví prostředí tak, aby používat 32-bit, x86 nativních nástrojů pro vytváření 32-bit, x86 nativního kódu.  
- **x86 nativní nástroje příkazového řádku** nastaví prostředí tak, aby používat 32-bit, x86 nativních nástrojů pro vytváření 32-bit, x86 nativního kódu.  
- **x64 nativní nástroje příkazového řádku** nastaví prostředí pomocí 64-bit, x64 nativních nástrojů pro sestavení 64-bit, x64 nativního kódu.  
- **x86_x64 různé nástroje pro příkazový řádek** nastaví prostředí pomocí 32-bit, x86 nativních nástrojů pro sestavení 64-bit, x64 nativního kódu.  
- **x64_x86 různé nástroje pro příkazový řádek** nastaví prostředí tak, aby používat 64-bit, x64 nativních nástrojů pro vytváření 32-bit, x86 nativního kódu.  

Skutečné počáteční složky a místní názvy nabídek lišit v závislosti na verzi [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] jste nainstalovali a instalaci Přezdívka Pokud nastavíte jeden. Například, pokud máte Visual Studio 2017 nainstalovaná a je jste dali instalaci Přezdívka 15.3, na zástupce příkazového řádku vývojáře se jmenuje **příkazový řádek vývojáře pro VS 2017 (15.3)**, ve složce s názvem  **Visual Studio 2017**. 

Pokud jste nainstalovali [nástroje sestavení pro Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=840931) nebo [nástroje Visual C++ 2015 sestavení](http://landinghub.visualstudio.com/visual-cpp-build-tools) edition, může existovat pouze konkrétní nativní nebo mezi nástroje Možnosti příkazového řádku pro vývojáře. 

<a name="developer_command_prompt"></a>
## <a name="to-open-a-developer-command-prompt-window"></a>Chcete-li otevřít okno příkazového řádku vývojáře  
  
1.  Na ploše otevřete Windows **spustit** nabídce a potom přejděte k vyhledání a otevřete složku pro vaši verzi sady Visual Studio, například **Visual Studio 2017**. V některých starších verzí sady Visual Studio zástupce jsou v podsložce s názvem **nástroje sady Visual Studio**.  
  
2.  Ve složce, vyberte **příkazový řádek vývojáře** pro vaši verzi sady Visual Studio. Tento zástupce spustí okno příkazového řádku vývojáře využívající architekturu sestavení výchozí 32-bit, x86 nativních nástrojů k sestavení 32-bit, x86 nativního kódu. Pokud dáváte přednost architektura sestavení jiné než výchozí, vyberte jednu z nativního nebo mezi nástroje okna příkazového řádku k určení architektura hostitele a cíle. 

Otevřete okno příkazového řádku vývojáře ještě rychleji je zadání *příkazový řádek vývojáře* plochy vyhledávacího pole, pak vyberte požadovaný výsledek.

<a name="developer_command_files"></a>
## <a name="developer-command-files-and-locations"></a>Soubory příkazů Developer a umístění

Pokud dáváte přednost nastavení prostředí architektura sestavení v existujícího okna příkazového řádku, můžete použít jeden ze souborů příkaz vytvořené instalační služby. Umístění těchto souborů závisí na verzi [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] jste nainstalovali, a na umístění a pojmenování volby můžete provedeny během instalace. Pro Visual Studio 2017 umístěním typické instalace na 64bitovém počítači je \Program soubory (x86) \Microsoft Visual Studio\2017\\*edition*, kde *edice* může být komunity Professional, Enterprise, BuildTools nebo jiný název, který jste zadali. Pro Visual Studio 2015 umístěním typické instalace je \Program Files (x86) \Microsoft Visual Studio 14.0. 

Primární vývojáře soubor příkazů příkazového řádku, VsDevCmd.bat, se nachází v instalačním adresáři na Common7\Tools. Pokud nejsou zadány žádné parametry, nastaví tato architektura prostředí a sestavení při použití nástroje pro nativní x86 32-bit k sestavení 32-bit x86 kódu.

Další příkaz soubory jsou k dispozici nastavit konkrétní sestavení architektury, v závislosti na architektuře procesoru a [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] úlohy a možnosti, které jste nainstalovali. V aplikaci Visual Studio 2017, jsou umístěny v podadresáři VC\Auxiliary\Build [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] instalační adresář. V sadě Visual Studio 2015, jsou umístěny v VC, VC\bin nebo VC\bin\\*architektury* podadresáře instalační adresář, kde *architektury* je jedním z nativního nebo křížové možnosti kompilátoru. Tyto soubory příkaz Nastavit parametry a volání VsDevCmd.bat nastavení prostředí architektura zadané sestavení. Typické instalace může zahrnovat tyto soubory příkazů:

- **vcvars32.bat –** sestavení 32-bit x86 pomocí nástrojů pro 32-bit x86 nativní kód.  
- **vcvars64.bat** použít k vytvoření 64-bit x64 nástroje x64 nativní 64bitový kód.  
- **vcvarsx86_amd64.bat** pomocí nástrojů křížové x86 nativní 32bitová verze sestavení 64-bit x64 kódu.  
- **vcvarsamd64_x86.bat** použít k vytvoření x86 32bitová verze nástroje křížové x64 nativní 64bitové verze kódu.  
- **vcvarsx86_arm.bat** pomocí nástrojů křížové x86 nativní 32bitová verze sestavení kódu ARM.  
- **vcvarsamd64_arm.bat** pomocí nástrojů pro křížové x64 nativní 64bitové verze sestavení kódu ARM.  
- **vcvarsall.bat** použijte parametry k určení na hostiteli a cílové architektury, a také možnosti sady SDK a platformy. Pro volání `/help` parametr pro seznam možností.  

> [!CAUTION]
>  Soubor vcvarsall.bat a další soubory příkazu se může lišit počítačů. Nepřepisovat existující soubor nebo je poškozena vcvarsall.bat pomocí souboru z jiného počítače. Znovu spustit [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] instalačního programu za účelem nahrazení chybějícího souboru.  
>   
> Soubor vcvarsall.bat se také liší v závislosti na verzi. Pokud je aktuální verze Visual C++ nainstalovaná na počítači, který má také dřívější verzi Visual C++, nespouštějte vcvarsall.bat nebo jiný příkaz soubor z různých verzí ve stejném okně příkazového řádku.  
 
Nejjednodušší způsob, jak určit konkrétní sestavení architektura v existující příkazové okno je chcete použít soubor vcvarsall.bat. Vcvarsall.bat můžete použít k nastavení proměnných prostředí ke konfiguraci příkazového řádku pro nativní kompilace 32bitové nebo 64bitové, nebo mezi kompilace x86, x64 nebo procesory ARM; cíl Microsoft Store, univerzální platformu Windows nebo platformy Windows Desktop; Chcete-li určit Windows SDK, které se použije. a zadejte verzi sady nástrojů platformy. Pokud jsou k dispozici žádné argumenty, vcvarsall.bat nakonfiguruje proměnných prostředí pro používání aktuální 32-bit nativního kompilátoru pro x86 Windows Desktop cíle. Ale můžete použít ke konfiguraci libovolné nativního nebo křížové nástrojů kompilátoru. Pokud zadáte konfigurace kompilátoru, která není nainstalována nebo není k dispozici v vaší sestavení počítače architektury, se zobrazí chybová zpráva. Tato tabulka ukazuje podporovaná architektura argumenty:  
  
|Argument vcvarsall.bat architektura|Kompilátoru|Architektura počítače hostitele|Vytvoření výstupní architektura|  
|----------------------------|--------------|----------------------------------|-------------------------------|  
|x86|x86 nativní 32-bit|x86, x64|x86|  
|x86\_amd64 nebo x86\_x64|mezi x64 na x86|x86, x64|x64|  
|x86_arm|ARM na x86 mezi|x86, x64|ARM|  
|amd64 nebo x64|x64 nativní 64bitová verze|x64|x64|  
|AMD64\_x86 nebo x64\_x86|mezi x86 na x64|x64|x86|  
|AMD64\_arm nebo x64\_arm|ARM na x64 mezi|x64|ARM|  
  
Můžete použít **ukládání** nebo **uwp** možností pro zadání typu platformy, nebo ani jeden z nich k zadání aplikace na ploše. K určení verze sady Windows SDK, můžete použít úplnou Windows 10 SDK číslo například 10.0.10240.0 nebo zadejte 8.1 se používat sadu SDK Windows 8.1. Použijte 14.0 k určení sady nástrojů kompilátoru Visual Studio 2015; ve výchozím nastavení je hodnotu prostředí pomocí sady nástrojů kompilátoru Visual Studio 2017.

<a name="vcvarsall"></a>
## <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>Nastavení prostředí sestavení v existujícím okně příkazového řádku  
  
1.  Na příkazovém řádku přejděte do adresáře instalace sady Visual Studio pomocí příkazu disku CD. Potom pomocí disku CD-ROM znovu změnit na podadresáře, který obsahuje soubory konfigurace konkrétní příkaz. Pro Visual Studio 2017 jde podadresáři VC\Auxiliary\Build. Pro Visual Studio 2015 použijte podadresáři VC.  
  
1.  Ke konfiguraci toto okno příkazového řádku pomocí 32bitová verze nástrojů pro sestavení kód pro x86 platformy, na příkazovém řádku zadejte:  
  
     `vcvarsall`  

1.  Ke konfiguraci toto okno příkazového řádku pomocí 32bitová verze nástrojů pro sestavení kód pro x64 platformy, na příkazovém řádku zadejte:  
  
     `vcvarsall x86_amd64`  
  
1.  Pokud chcete konfigurovat toto okno příkazového řádku pomocí 32bitová verze nástrojů pro sestavení kódu pro ARM platformy, na příkazovém řádku zadejte:  
  
     `vcvarsall x86_arm`  
  
1.  Ke konfiguraci toto okno příkazového řádku pomocí 64bitová verze nástrojů pro sestavení kód pro x64 platformy, na příkazovém řádku zadejte:  
  
     `vcvarsall amd64`  
  
1.  Ke konfiguraci toto okno příkazového řádku pomocí 64bitová verze nástrojů pro sestavení kód pro x86 platformy, na příkazovém řádku zadejte:  
  
     `vcvarsall amd64_x86`  
  
1.  Pokud chcete konfigurovat toto okno příkazového řádku pomocí 64bitová verze nástrojů pro sestavení kódu pro ARM platformy, na příkazovém řádku zadejte:  
  
     `vcvarsall amd64_arm`  

Soubor příkazů nastaví proměnné požadované prostředí pro cesty sestavovací nástroje, knihovny a hlavičky. Nyní můžete toto okno příkazového řádku spouštět kompilátoru příkazového řádku a nástroje.  
  
Pokud používáte [DEVENV](/visualstudio/ide/reference/devenv-command-line-switches) pro sestavení příkazového řádku, nastavte vcvarsall.bat nebo jiné soubory příkazů prostředí nemá vliv na vaše sestavení pokud zároveň určíte **/useenv** možnost.  

## <a name="command-line-tools"></a>Nástroje příkazového řádku
  
Pro vytvoření projektu jazyka C nebo C++ v příkazovém řádku, můžete použít tyto nástroje příkazového řádku Visual C++:  
  
[CL](../build/reference/compiling-a-c-cpp-program.md)  
Pro zkompilování a spojení soubory zdrojového kódu do aplikace, knihovny a knihovny DLL pomocí kompilátoru (cl.exe).  
  
[Link](../build/reference/linking.md)  
Použijte linker (link.exe) pro propojení zkompilovaný objekt soubory a knihovny do aplikace a knihovny DLL.  
  
[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)  
Pomocí nástroje MSBuild (msbuild.exe) můžete vytvářet projekty Visual C++ a [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] řešení. Jde o ekvivalent spuštění **sestavení** projektu nebo **sestavit řešení** v příkazu [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE.  
  
[NÁSTROJE DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)  
Použití nástroje DEVENV (devenv.exe) v kombinaci s přepínačem příkazového řádku – například **/Build** nebo **/Clean**– k provedení určité příkazy bez zobrazení sestavení [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE.  
  
[NMAKE](../build/nmake-reference.md)  
Použijte k automatizaci úloh, které sestavení projektů Visual C++ pomocí tradičních souboru pravidel NMAKE (nmake.exe).  
  
Když vytvoříte na příkazovém řádku, můžete získat informace o upozornění, chyby a zprávy. Spustit [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] a potom na panelu nabídek vyberte **pomoci**, **vyhledávání**.  
  
## <a name="in-this-section"></a>V tomto oddílu  

Články v této části dokumentace ukazují, jak vytvářet aplikace, na příkazovém řádku, které popisují, jak přizpůsobit sestavení příkazového řádku prostředí použít 64-bit modulové a cíl x86, x64 a ARM platformy a ukazují, jak používat sestavení příkazového řádku nástroje MSBuild a příkaz NMAKE.  
  
[Návod: Kompilace nativního programu C++ v příkazovém řádku](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)  
Poskytuje příklad, který ukazuje, jak vytvořit a kompilaci jednoduché programu C++ v příkazovém řádku.  
  
[Návod: Kompilace programu v jazyce C na příkazovém řádku](../build/walkthrough-compile-a-c-program-on-the-command-line.md)  
Popisuje způsob kompilace programu v jazyce programovacího jazyka C.  
  
[Návod: Kompilace programu C++/CLI v příkazovém řádku](../build/walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)  
Popisuje, jak vytvořit a kompilaci C + +/ CLI program, který používá rozhraní .NET Framework.  
  
[Návod: Kompilace programu C++/CX v příkazovém řádku](../build/walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)  
Popisuje, jak vytvořit a kompilaci C + +/ CX program, který používá prostředí Windows Runtime.  
  
[Nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)  
Popisuje, jak spustit okno příkazového řádku, který má proměnné požadované prostředí pro sestavení příkazového řádku nastavit cílených x86, x64 a ARM platforem pomocí nástrojů 32bitové nebo 64bitové verze.  
  
[NMAKE – referenční zdroje](../build/nmake-reference.md)  
Obsahuje odkazy na články, které popisují Program údržby nástroj Microsoft (NMAKE. SOUBOR EXE).  
  
[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)  
Obsahuje odkazy na články, které vysvětluje použití MSBuild.EXE.  
  
## <a name="related-sections"></a>Související oddíly  

[/MD, /MT, /LD (použití knihovny run-time)](../build/reference/md-mt-ld-use-run-time-library.md)  
Popisuje, jak pomocí těchto možností kompilátoru pro použití běhové knihovny ladění nebo verze.  
  
[Možnosti kompilátoru C/C++](../build/reference/compiler-options.md)  
Obsahuje odkazy na články, které popisují možnosti kompilátoru C a C++ a CL.exe.  
  
[Možnosti linkeru](../build/reference/linker-options.md)  
Obsahuje odkazy na články, které popisují možnosti linkeru a LINK.exe.  
  
[Nástroje sestavení C/C++](../build/reference/c-cpp-build-tools.md)  
Poskytuje nástroje, které jsou součástí sestavení odkazy pro C/C++ [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Viz také  

[Sestavování programů v jazyce C/C++](../build/building-c-cpp-programs.md)