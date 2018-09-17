---
title: / Qspectre | Dokumentace Microsoftu
ms.custom: ''
ms.date: 1/23/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- /Qspectre
helpviewer_keywords:
- /Qspectre
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5dde5d8bb2e7b973b505b467165a710546f2a6a0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716024"
---
# <a name="qspectre"></a>/ Qspectre

Určuje kompilátoru generování pokynů ke zmírnění chyby zabezpečení určité chyby zabezpečení Spectre variant 1.

## <a name="syntax"></a>Syntaxe

> **/Qspectre**

## <a name="remarks"></a>Poznámky

**/Qspectre** možnost je k dispozici v sadě Visual Studio 2017 verze 15.7 nebo novější. To způsobí, že kompilátor vložit pokyny pro zmírnění některých [chyby zabezpečení Spectre](https://spectreattack.com/spectre.pdf). Tyto chyby zabezpečení, volá *útoky na straně kanálu spekulativního spouštění*, ovlivnit řada operačních systémů a moderní procesory, včetně procesory od Intelu, AMD a ARM.

**/Qspectre** možnost je vypnuto ve výchozím nastavení.

V úvodním vydání **/qspectre** možnost funguje pouze v optimalizovaném kódu. Měli byste zajistit Kompilujte kód pomocí některé z možností optimalizace (například [/O2 nebo/O1](o1-o2-minimize-size-maximize-speed.md) , ale ne [/Od](od-disable-debug.md)) k Ujistěte se, že použijí omezení rizik. Podobně, kontrolovat veškerý kód, který používá [#pragma optimize ("stg", vypnuto)](../../preprocessor/optimize.md).

### <a name="applicability"></a>Použitelnost.

Pokud váš kód pracuje s daty, která překročí hranice vztahu důvěryhodnosti, doporučujeme použít **/qspectre** znovu sestavit nebo znovu nasazovat kód co nejdříve problém zmírnit. Příklady kódu, který pracuje s daty, která překročí hranice vztahů důvěryhodnosti obsahovat kód, který načte nedůvěryhodný vstup může mít vliv na spuštění, například kód, který umožňuje vzdálenou proceduru volá, analyzuje nedůvěryhodný vstup nebo soubory nebo používá jiný místní proces mezi komunikace (IPC) rozhraní. Standardní sandboxing techniky nemusí být dostatečné. Vaše sandboxy byste měli prozkoumat pečlivě než se rozhodnete, že váš kód není napříč hranicí vztahu důvěryhodnosti.

### <a name="availability"></a>Dostupnost

**/Qspectre** možnost je dostupná v sadě Visual Studio 2017 verze 15.5.5 a všechny aktualizace kompilátory Microsoft Visual C++ (MSVC) provedené po 23. ledna 2018. Aktualizovat kompilátor a k instalaci knihoven zmírnit hrozby Spectre jako jednotlivé komponenty, použijte instalační program sady Visual Studio. **/Qspectre** možnost je také k dispozici v sadě Visual Studio 2015 Update 3 prostřednictvím opravy. Další informace najdete v tématu [KB 4338871](https://support.microsoft.com/help/4338871).

Všechny verze sady Visual Studio 2017 verze 15.5 a všechny verze Preview sady Visual Studio verze 15.6 již obsahuje nezdokumentovaný možnost **/d2guardspecload**, tedy ekvivalent počáteční chování   **/qspectre**. Můžete použít **/d2guardspecload** použít stejné způsoby zmírnění rizik pro váš kód v těchto verzích kompilátoru. Aktualizujte prosím vaše sestavení, **/qspectre** v kompilátorech, které podporují parametr; **/qspectre** možnost můžou podporovat i nové způsoby zmírnění rizik v novějších verzích kompilátoru.

### <a name="effect"></a>Efekt

**/Qspectre** možnost výstupy kód ke zmírnění Specter variant 1, zkontrolujte obejít hranice [CVE-2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753). Funguje díky vložení instrukcí, které se chovají jako spuštění bariéra spekulativního kódu. Konkrétní pokyny zmírnit spekulační procesoru závisí na procesoru a její mikroarchitekturu a může změnit v budoucích verzí kompilátoru.

Když **/qspectre** je povolená možnost, kompilátor se pokusí identifikovat instance, kde spekulativního spouštění kontroly omezení mohou obejít a vloží barrier pokyny. Je důležité si uvědomit, že existují omezení pro analýzy, které provádí kompilátor k identifikaci instance typu variant 1. V důsledku toho neexistuje žádná záruka, že jsou podporovány všechny možné instance typu variant 1 v části **/qspectre**.

### <a name="performance-impact"></a>Dopad na výkon

Dopad výkon **/qspectre** ukázala být nepatrné v několika velmi rozsáhlých základů kódu, ale neexistují žádné záruky, že výkon kódu v rámci **/qspectre** to neovlivní. By měl testu výkonnosti kódu účinnosti možnost na výkon. Pokud víte, že řešení není nutné v kritickém pro výkon bloku nebo smyčku, omezení rizik lze jednotlivě zakázat použití [__declspec(spectre(nomitigation))](../../cpp/spectre.md) směrnice. Tato direktiva není k dispozici v kompilátorech, které podporují pouze **/d2guardspecload** možnost.

### <a name="required-libraries"></a>Požadované knihovny

**/Qspectre** – možnost kompilátoru generuje kód, který se odkazuje implicitně verzí knihoven runtime, která byla vytvořená pro poskytování zmírnění hrozby Spectre. Tyto knihovny jsou volitelné součásti, které je třeba nainstalovat pomocí instalačního programu sady Visual Studio:

- VC ++ 2017 verze *version_number* knihovny pro Spectre (x86 a x64)
- Visual C++ ATL (x86/x64) se zmírněními hrozeb Spectre
- Visual C++ MFC pro x86/x64 se zmírněními hrozeb Spectre

Při vytváření kódu s použitím **/qspectre** a tyto knihovny nejsou nainstalované, zprávy systému sestavení **upozornění MSB8038: zmírnění hrozby Spectre je zapnutá, ale nebyly nalezeny zmírnit hrozby Spectre knihovny**. Pokud se nepovede kódu knihovny MFC nebo ATL k sestavení a propojovací program hlásí chybu, jako **závažná chyba LNK1104: Nelze otevřít soubor oldnames.lib**, tyto chybějící knihovny může být příčinou.

### <a name="additional-information"></a>Další informace

Další informace najdete v tématu official je přínosné pro [Microsoft Security Advisory ADV180002, pokyny ke zmírnění chyby zabezpečení na straně kanálu spekulativního spouštění](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002). Pokyny jsou také k dispozici od Intelu, [spekulativního spouštění na straně kanálu způsoby zmírnění rizik](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf)a ARM, [Spekulační mezipaměti na straně kanálů](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf). Přehled zmírnění hrozby Spectre a Meltdown specifické pro Windows, naleznete v tématu [pochopení vlivu na výkon zmírnění hrozby Spectre a Meltdown v systémech Windows](https://cloudblogs.microsoft.com/microsoftsecure/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/) na blogu Microsoft Secure. Přehled chyby zabezpečení Spectre řešit omezením MSVC, naleznete v tématu [zmírnění hrozby Spectre v MSVC](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc./) na blogu týmu Visual C++.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Zadejte **/qspectre** – možnost kompilátoru v **další možnosti** pole. Zvolte **OK** na použití změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[/Q – možnosti (operace nízké úrovně)](../../build/reference/q-options-low-level-operations.md)
[– možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
