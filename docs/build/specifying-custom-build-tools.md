---
title: Určení vlastních sestavovacích nástrojů
ms.date: 06/05/2018
f1_keywords:
- VC.Project.VCCustomBuildTool.CustomBuildToolBeforeTargets
- VC.Project.VCCustomBuildTool.Outputs
- VC.Project.VCCustomBuildTool.Command
- VC.Project.VCCustomBuildTool.CommandLine
- VC.Project.VCCustomBuildTool.AdditionalDependencies
- VC.Project.VCCustomBuildTool.Message
- VC.Project.VCCustomBuildTool.CustomBuildToolAfterTargets
- VC.Project.VCCustomBuildTool.Description
- VC.Project.VCCustomBuildTool.AdditionalInputs
helpviewer_keywords:
- build tools (C++), specifying
- custom build tools (C++), specifying
- builds (C++), custom build tools
ms.openlocfilehash: dbce226b34503a9e8e70b6f19d9aa0c68ef487f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314751"
---
# <a name="specify-custom-build-tools"></a>Určení nástrojů vlastního sestavení

*Vlastní nástroj sestavení* poskytuje systém sestavení s informacemi, které potřebuje k sestavení specifických vstupních souborů. Vlastní nástroj sestavení Určuje příkaz, který se má spustit, seznam vstupních souborů, seznam výstupních souborů generovaných příkazem a nepovinný popis nástroje.

Obecné informace o vlastních nástrojích sestavení a vlastních krocích sestavení naleznete v tématu [Principy vlastních kroků sestavení a událostí sestavení](understanding-custom-build-steps-and-build-events.md).

### <a name="to-specify-a-custom-build-tool"></a>Určení vlastního nástroje sestavení

1. Otevřete dialogové okno **stránky vlastností** projektu. Další informace najdete v tématu [nastavení kompilátoru C++ a vlastností sestavení v sadě Visual Studio](working-with-project-properties.md).

1. Chcete-li povolit pole **Konfigurace** , vyberte možnost **Vlastnosti konfigurace** . V poli **Konfigurace** vyberte konfiguraci, pro kterou chcete zadat vlastní nástroj sestavení.

1. V **Průzkumník řešení**vyberte vstupní soubor pro vlastní nástroj sestavení.

   Pokud se složka **vlastních nástrojů sestavení** nezobrazí, Přípona souboru, kterou jste vybrali, je přidružená k výchozímu nástroji. Například výchozí nástroj pro soubory. c a. cpp je kompilátor. Chcete-li přepsat výchozí nastavení nástroje, v uzlu **Vlastnosti konfigurace** , ve složce **Obecné** , ve vlastnosti **typ položky** vyberte možnost Nástroj pro **vlastní sestavení**. Klikněte na tlačítko **použít** a zobrazí se uzel **Nástroje pro vlastní sestavení** .

1. V uzlu **nástroje vlastního sestavení** ve složce **Obecné** zadejte vlastnosti přidružené k nástroji pro vlastní sestavení:

   - V části **Další závislosti**zadejte další soubory nad rámec toho, pro který je definován vlastní nástroj sestavení (soubor přidružený k nástroji vlastní sestavení je implicitně považován za vstup do nástroje). Další vstupní soubory nejsou požadavkem pro vlastní nástroj sestavení. Pokud máte více než jeden další vstup, oddělte je středníkem.

      Pokud je datum **dalšího souboru závislostí** pozdější než vstupní soubor, spustí se vlastní nástroj sestavení. Pokud jsou všechny **Další soubory závislosti** starší než vstupní soubor a vstupní soubor je starší než **soubor vlastností** Outputs, vlastní sestavení nástroje není spuštěno.

      Předpokládejme například, že máte vlastní nástroj sestavení, který jako vstup přijímá MyInput. x a generuje MyInput. cpp a který MyInput. x obsahuje hlavičkový soubor MyHeader. h. MyHeader. h můžete zadat jako závislost vstupu na MyInput. x a systém sestavení bude sestavovat MyInput. cpp, pokud je zastaralý s ohledem na MyInput. x nebo MyHeader. h.

      Vstupní závislosti můžou také zajistit, aby vaše vlastní nástroje pro sestavení běžely v pořadí, ve kterém je budete potřebovat. V předchozím příkladu Předpokládejme, že MyHeader. h je ve skutečnosti výstup vlastního nástroje sestavení. Vzhledem k tomu, že MyHeader. h je závislost MyInput. x, systém sestavení nejprve sestaví MyHeader. h před spuštěním vlastního nástroje sestavení v MyInput. x.

   - V **příkazovém řádku**zadejte příkaz, jako kdybyste ho zadali v příkazovém řádku. Zadejte platný příkaz nebo dávkový soubor a všechny požadované vstupní nebo výstupní soubory. Před názvem dávkového souboru zajistěte, aby se zajistilo, že se budou spouštět všechny následné příkazy, zadáním příkazu Batch pro **volání** .

      Více vstupních a výstupních souborů lze zadat symbolické pomocí maker nástroje MSBuild. Informace o tom, jak určit umístění souborů nebo názvy sad souborů, naleznete v tématu [společná makra pro příkazy a vlastnosti sestavení](reference/common-macros-for-build-commands-and-properties.md).

      Vzhledem k tomu, že je znak% rezervován nástrojem MSBuild, pokud zadáte proměnnou prostředí, nahraďte každý **%** řídicí znak znakem **%25** v šestnáctkové řídicí sekvenci. Například nahraďte **% windir%** za **% 25WINDIR %25**. Nástroj **%** MSBuild nahradí každé **%25** sekvence znakem před tím, než přistupuje k proměnné prostředí.

   - V **popisu**zadejte popisnou zprávu o tomto nástroji pro vlastní sestavení. Zpráva je vytištěna do okna **výstup** , když systém sestavení zpracovává tento nástroj.

   - Do pole **výstupy**zadejte název výstupního souboru. Tato položka je povinná. bez hodnoty této vlastnosti se vlastní nástroj sestavení nespustí. Pokud má vlastní nástroj sestavení více než jeden výstup, oddělte názvy souborů středníkem.

      Název výstupního souboru by měl být stejný, jako byl zadán ve vlastnosti **příkazového řádku** . Systém sestavení projektu bude hledat soubor a zkontrolovat jeho datum. Je-li výstupní soubor starší než vstupní soubor nebo pokud nebyl nalezen výstupní soubor, spustí se vlastní nástroj sestavení. Pokud jsou všechny **Další soubory závislostí** starší než vstupní soubor a vstupní soubor je starší než soubor určený **ve vlastnosti** Outputs, vlastní sestavení nástroje není spuštěno.

Chcete-li, aby systém sestavení pracoval na výstupním souboru vygenerovaném nástrojem pro vlastní sestavení, je nutné jej ručně přidat do projektu. Nástroj pro vlastní sestavení aktualizuje soubor během sestavení.

## <a name="example"></a>Příklad

Předpokládejme, že chcete do projektu zahrnout soubor s názvem parser. l. Máte lexikální analyzátor, **lexer. exe**, na cestě ke spustitelnému souboru. Chcete jej použít ke zpracování souboru. c, který má stejný základní název (parser. c).

Nejprve do projektu přidejte parser. l a parser. c. Pokud soubory ještě neexistují, přidejte odkaz na soubory. Vytvořte vlastní nástroj sestavení pro parser. l a do vlastnosti **Commands (příkazy** ) zadejte následující:

> **lexer% (FullPath). \%(Název souboru). c**

Tento příkaz spustí lexikální analyzátor analyzátoru. l a provede výstup analyzátoru. c do adresáře projektu.

Do vlastnosti Outputs ( **výstupy** ) zadejte následující:

> **. \%(Název souboru). c**

Při sestavování projektu systém sestavení porovná časová razítka analyzátoru. l a parser. c. Pokud je analyzátor. l novější nebo pokud analyzátor. c neexistuje, spustí systém sestavení hodnotu vlastnosti **příkazového řádku** , aby mohl přenést parser. c v aktuálním stavu. Vzhledem k tomu, že analyzátor. c byl také přidán do projektu, systém sestavení potom zkompiluje parser. c.

## <a name="see-also"></a>Viz také

[Společná makra pro příkazy a vlastnosti sestavení](reference/common-macros-for-build-commands-and-properties.md)<br>
[Řešení potíží s přizpůsobením sestavení](troubleshooting-build-customizations.md)
