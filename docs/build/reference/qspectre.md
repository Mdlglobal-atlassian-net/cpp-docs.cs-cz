---
title: /Qspectre
ms.date: 09/06/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.SpectreMitigation
helpviewer_keywords:
- /Qspectre
ms.openlocfilehash: e8d03075a980a9b9c345ce351413e39a3c3444cb
ms.sourcegitcommit: 7babce70714242cf498ca811eec3695fad3abd03
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2019
ms.locfileid: "70808830"
---
# <a name="qspectre"></a>/Qspectre

Určuje generování kompilátoru s pokyny pro zmírnění některých ohrožení zabezpečení Spectre varianty 1 – 1.

## <a name="syntax"></a>Syntaxe

> **/Qspectre**

## <a name="remarks"></a>Poznámky

Možnost **/Qspectre** je k dispozici v aplikaci visual Studio 2017 verze 15.5.5 a novější a v aktualizaci visual Studio 2015 Update 3 až [KB 4338871](https://support.microsoft.com/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre). Způsobí, že kompilátor vloží pokyny pro zmírnění některých [ohrožení zabezpečení Spectre](https://spectreattack.com/spectre.pdf). Tyto chyby zabezpečení se nazývají *spekulativní útoky na straně kanálu*. Mají vliv na mnoho operačních systémů a moderních procesorů, včetně procesorů od platforem Intel, AMD a ARM.

Možnost **/Qspectre** je ve výchozím nastavení vypnutá.

V původním vydání možnost **/Qspectre** pracovala pouze na optimalizovaném kódu. V aplikaci Visual Studio 2017 verze 15,7 a novější je možnost **/Qspectre** podporovaná na všech úrovních optimalizace.

Knihovny Microsoft C++ Visual jsou dostupné také ve verzích se zmírněním Spectre. Spectre-zmírňované knihovny pro Visual Studio 2017 a novější je možné stáhnout v Instalační program pro Visual Studio. Jsou k dispozici na kartě **jednotlivé komponenty** v části **kompilátory, nástroje sestavení a moduly runtime**a mají v názvu "knihovny for Spectre". Knihovny DLL i statické běhové knihovny s povolenou zmírňování jsou k dispozici pro podmnožinu vizuálních C++ modulů runtime: Spouštěcí kód VC + +, knihovny vcruntime140, msvcp140, concrt140 a vcamp140. Knihovny DLL jsou podporovány pouze pro místní nasazení aplikace. Obsah pro Distribuovatelný běhové C++ knihovny Visual 2017 a novější nebyl změněn.

Můžete také nainstalovat Spectre-zmírňované knihovny pro MFC a ATL. Jsou k dispozici na kartě **jednotlivé komponenty** v části sady **SDK, knihovny a architektury**.

> [!NOTE]
> Pro aplikace nebo komponenty Universal Windows (UWP) neexistují žádné verze Spectre knihoven s omezením. Místní nasazení takových knihoven aplikace není možné.

### <a name="applicability"></a>Použitelnost

Pokud váš kód pracuje s daty, která překračují hranice vztahu důvěryhodnosti, doporučujeme použít možnost **/Qspectre** k opětovnému sestavení a opětovnému nasazení kódu pro zmírnění tohoto problému co nejdříve. Příkladem takového kódu je kód, který načte nedůvěryhodný vstup, který může ovlivnit provádění. Například kód, který provádí vzdálená volání procedur, analyzuje nedůvěryhodný vstup nebo soubory nebo používá jiné místní rozhraní meziprocesové komunikace (IPC). Standardní techniky izolovaného prostoru (sandbox) nemusí být dostatečné. Před tím, než se rozhodnete, že váš kód nepřekračuje hranice vztahu důvěryhodnosti, prozkoumejte pečlivě své izolované prostory.

### <a name="availability"></a>Dostupnost

Možnost **/Qspectre** je k dispozici v aplikaci Visual Studio 2017 verze 15.5.5 a ve všech aktualizacích C++ kompilátorů společnosti Microsoft (MSVC), které se provedly 23. ledna 2018. Pomocí Instalační program pro Visual Studio aktualizujte kompilátor a nainstalujte knihovny s omezením Spectre jako jednotlivé komponenty. Možnost **/Qspectre** je také k dispozici v aplikaci Visual Studio 2015 Update 3 prostřednictvím opravy. Další informace najdete v [článku KB 4338871](https://support.microsoft.com/help/4338871).

Všechny verze sady Visual Studio 2017 verze 15,5 a všechny náhledy sady Visual Studio 2017 verze 15,6. Zahrňte možnost bez dokumentu **/d2guardspecload**. Odpovídá počátečnímu chování **/Qspectre**. **/D2guardspecload** můžete použít k použití stejných rizik pro váš kód v těchto verzích kompilátoru. Doporučujeme, abyste sestavení aktualizovali tak, aby používalo **/Qspectre** v kompilátorech, které podporují možnost. Možnost **/Qspectre** může také podporovat nové zmírňování v novějších verzích kompilátoru.

### <a name="effect"></a>Efekt

Možnost **/Qspectre** vypíše kód pro zmírnění Specter variant 1, hranice kontroly se nepoužívá, [CVE-2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753). Funguje na základě vložení pokynů, které fungují jako spekulativní bariéra provádění kódu. Konkrétní pokyny pro zmírnění spekulativních procesorů závisí na procesoru a jeho mikroarchitektuře a můžou se měnit v budoucích verzích kompilátoru.

Pokud povolíte možnost **/Qspectre** , kompilátor se pokusí identifikovat instance, ve kterých spekulativní spuštění může obejít kontroly hranic. Tím se vloží pokyny k bariérě. Je důležité znát omezení pro analýzu, kterou může kompilátor provést k identifikaci instancí varianty 1. V takovém případě není nijak zaručeno, aby všechny možné instance varianty 1 byly instrumentované v rámci **/Qspectre**.

### <a name="performance-impact"></a>Dopad na výkon

Dopad **/Qspectre** na výkon se zdá být zanedbatelný v několika různých kódových základech. Neexistují však žádné záruky, že výkon vašeho kódu v rámci **/Qspectre** zůstává neovlivněný. Měli byste srovnávací testy kódu, abyste zjistili účinek možnosti výkonu. Pokud víte, že zmírnění není vyžadováno v bloku nebo smyčce kritickém pro výkon, můžete selektivně zakázat zmírnění pomocí direktivy [__declspec (Spectre (nezmírňování))](../../cpp/spectre.md) . Tato direktiva není dostupná v kompilátorech, které podporují jenom možnost **/d2guardspecload** .

### <a name="required-libraries"></a>Požadované knihovny

Možnost kompilátoru **/Qspectre** generuje kód, který implicitně odkazuje na verze běhových knihoven sestavených tak, aby poskytovala zmírnění rizik Spectre. Tyto knihovny jsou volitelné součásti, které je nutné nainstalovat pomocí Instalační program pro Visual Studio:

- MSVC verze *version_numbers* knihovny pro Spectre \[(x86 a x64) | (ARM) | (ARM64)]
- Visual C++ ATL pro \[(x86/x64) | ARM | ARM64] se Zmírněními hrozeb Spectre
- Visual C++ MFC pro \[x86/x64 | ARM | ARM64] se Zmírněními hrozeb Spectre

Pokud sestavíte kód pomocí **/Qspectre** a tyto knihovny nejsou nainstalovány, systém sestavení oznamuje **upozornění MSB8038: Je povolené zmírnění Spectre, ale nenašly**se Spectre zmírňované knihovny. Pokud se váš kód MFC nebo ATL nedaří sestavit a linker hlásí chybu, jako je například **závažná chyba linkerů LNK1104: Nelze otevřít soubor ' OLDNAMES. lib '** , tyto chybějící knihovny mohou být příčinou.

### <a name="additional-information"></a>Další informace

Další informace najdete v oficiálním [informačním zpravodaji pro zabezpečení Microsoftu ADV180002, pokyny pro zmírnění spekulativních ohrožení zabezpečení na straně stran](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002). Doprovodné materiály jsou k dispozici také od společnosti Intel, [spekulativních rizik kanálu na straně spuštění](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf)a ARM, a to díky kanálům na [straně spekulativních kanálů](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf). Přehled pro Spectre a Meltdown, který je specifický pro systém Windows, najdete v tématu [Principy dopadu na výkon Spectre a Meltdown na systémy Windows](https://www.microsoft.com/security/blog/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/). Přehled chyb zabezpečení Spectre řešených zmírněními hrozeb v MSVC najdete v tématu [Spectre zmírnění v MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc./) na blogu C++ týmu.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

::: moniker range="vs-2019"

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností **Konfigurace** > **C/C++**  > **generování kódu** .

1. Vyberte novou hodnotu pro vlastnost **zmírnění rizika Spectre** . Kliknutím na **tlačítko OK** aplikujte změnu.

::: moniker-end

::: moniker range="<=vs-2017"

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností **Konfigurace** > **C/C++**  > **příkazový řádek** .

1. Do pole **Další možnosti** zadejte možnost kompilátoru **/Qspectre** . Kliknutím na **tlačítko OK** aplikujte změnu.

::: moniker-end

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[/Q – možnosti (operace nízké úrovně)](q-options-low-level-operations.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
