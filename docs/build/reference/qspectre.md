---
title: / Qspectre | Microsoft Docs
ms.custom: 
ms.date: 1/23/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
f1_keywords:
- /Qspectre
helpviewer_keywords:
- /Qspectre
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b114239ad57b484c9290fbe1cc2f0ae18cb565ec
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2018
---
# <a name="qspectre"></a>/Qspectre

Určuje kompilátoru generování pokyny ke zmírnění chyby zabezpečení určité spektrum variant 1.

## <a name="syntax"></a>Syntaxe

> **/Qspectre**

## <a name="remarks"></a>Poznámky

**/Qspectre** možnost způsobí, že kompilátor vložte pokyny pro zmírnění některých [ohrožení zabezpečení spektrum](https://spectreattack.com/spectre.pdf). Tyto chyby zabezpečení, nazývá *spekulativní provádění straně kanál útoky*, ovlivnit řada operačních systémů a moderní procesorů, včetně procesory z Intel, AMD a ARM.

**/Qspectre** možnost je ve výchozím nastavení vypnuta.

V původní verze **/Qspectre** možnost funguje jenom na optimalizovaný kód. Ujistěte se, kompilace kódu s žádným z možnosti optimalizace (například [/O2 nebo /O1](o1-o2-minimize-size-maximize-speed.md) ale ne [/Od](od-disable-debug.md)) a ujistěte se, je použita zmírnění dopadů. Podobně, zkontrolujte kód, který používá [optimalizovat #pragma ("stg", vypnutí)](../../preprocessor/optimize.md).

### <a name="applicability"></a>Použitelnosti

Pokud váš kód pracuje s daty, přes hranici vztahu důvěryhodnosti, pak doporučujeme použít **/Qspectre** umožňuje znovu sestavili a nasadili kódu ke zmírnění tohoto problému co nejdříve. Příklady kódu, který funguje na data, která protne hranice vztahu důvěryhodnosti kód, který načte nedůvěryhodné vstup, který může ovlivnit provádění, například kód, který umožňuje vzdálené procedury volá, analyzuje nedůvěryhodné vstup nebo soubory nebo používá jiný proces, mezi místní komunikace (IPC) rozhraní. Standardní sandboxing techniky nemusí být dostatečná. Než rozhodnete, že váš kód nekříží hranice vztahu důvěryhodnosti byste měli pečlivě prozkoumat vaše izolovaných prostorů.

### <a name="availability"></a>Dostupnost

**/Qspectre** možnost je dostupná ve verzi Visual Studio 2017 15.5.5 a všechny aktualizace pro Microsoft Visual C++ kompilátory (MSVC) udělali 23 leden 2018.

Všechny verze sady Visual Studio 2017 verze 15,5 a všechny verze Preview ze sady Visual Studio verze 15,6 operací již zahrnují nedokumentovanými možnost, **/d2guardspecload**, který je ekvivalentní počáteční chování **/Qspectre**. Můžete použít **/d2guardspecload** použít stejné způsoby zmírnění kódu v těchto verzích kompilátoru. Aktualizujte prosím vaše sestavení **/Qspectre** v kompilátory, které podporují možnost; **/Qspectre** možnost mohou podporovat nové způsoby zmírnění v novějších verzích kompilátoru.

### <a name="effect"></a>Efekt

**/Qspectre** možnost výstupy kódu ke zmírnění Specter variant 1, zkontrolujte nepoužívat hranice [CVE. 2017 5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753). Funguje díky vkládání pokyny, které se chovají jako bariéry provádění spekulativní kódu. Konkrétní pokyny používají ke zmírnění spekulativní procesoru závisí na procesor a jeho micro architektura a může v budoucích verzích kompilátor změnit.

Když **/Qspectre** je povolena možnost, kompilátor se pokusí identifikovat instance, kde spekulativní provádění mohou obejít rozsah kontroly a vloží bariéry pokynů. Je důležité si uvědomit, že jsou limity pro analýzy, která může provádět kompilátor k identifikaci instance typu variant 1. Jako takový není zaručeno, že všechny možné instance typu variant 1 jsou vybaveny pod **/Qspectre**.

### <a name="performance-impact"></a>Vliv na výkon

Dopad na výkonu **/Qspectre** ukázala zanedbatelný v několika velmi rozsáhlých základů kódu, ale nejsou žádné záruky, že výkon kódu v části **/Qspectre** zůstává neovlivní. Měli otestovat kód pro ověření účinnosti možnost na výkon. Pokud víte, že není vyžadován zmírnění v kritické výkonu bloku nebo smyčku, můžete zmírnění pomocí selektivně zakázána [__declspec(spectre(nomitigation))](../../cpp/spectre.md) – direktiva. Tato direktiva není k dispozici v kompilátory, které podporují pouze **/d2guardspecload** možnost.

### <a name="additional-information"></a>Další informace

Další podrobnosti naleznete v oficiální [ADV180002 informační zpravodaj zabezpečení společnosti Microsoft, pokyny ke zmírnění ohrožení zabezpečení kanálu straně spekulativní provádění](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002). Jsou také k dispozici z Intel, pokyny [spekulativní provádění straně kanál jejich zmírnění](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf)a ARM, [mezipaměti spekulativní straně kanály](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf). Přehled spektrum a Meltdown jejich zmírnění specifické pro systém Windows, najdete v tématu [pochopení dopad na výkon z jejich zmírnění spektrum a Meltdown v systémech Windows](https://cloudblogs.microsoft.com/microsoftsecure/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/) na blogu Microsoft Secure. Přehled spektrum chyba omezením MSVC najdete v tématu [jejich zmírnění spektrum v MSVC](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc./) na blogu týmu Visual C++.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Zadejte **/Qspectre** – možnost kompilátoru v **další možnosti** pole. Zvolte **OK** na použití změny.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[/Q – možnosti (operace nízké úrovně)](../../build/reference/q-options-low-level-operations.md)  
[Možnosti kompilátoru](../../build/reference/compiler-options.md)  
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)  
