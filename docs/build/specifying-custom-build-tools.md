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
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823441"
---
# <a name="specify-custom-build-tools"></a>Určení vlastních sestavovacích nástrojů

A *vlastní nástroj sestavení* sestavovací systém poskytuje informace potřebné k sestavení konkrétní vstupní soubory. Pro vlastní nástroj sestavení určuje příkaz pro spuštění, seznam vstupních souborů, seznam výstupních souborů, které jsou generovány pomocí příkazu a volitelný popis tohoto nástroje.

Obecné informace o vlastních sestavovacích nástrojů a vlastní kroky sestavení, naleznete v tématu [Principy vlastní kroky sestavení a události sestavení](understanding-custom-build-steps-and-build-events.md).

### <a name="to-specify-a-custom-build-tool"></a>K určení vlastních sestavovacích nástrojů

1. Otevřete v projektu **stránky vlastností** dialogové okno. Další informace najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](working-with-project-properties.md).

1. Zvolte **vlastnosti konfigurace** povolit **konfigurace** pole. V **konfigurace** pole, vyberte položku konfigurace, pro kterou chcete určit pro vlastní nástroj sestavení.

1. V **Průzkumníka řešení**, výběr vstupního souboru pro vlastní nástroj sestavení.

   Pokud **nástroj Custom Build** složka nezobrazí, je přidružena k nástroji výchozí příponu souboru, který jste vybrali. Kompilátor je například výchozí nástroj pro soubory .c a .cpp. Chcete přepsat nástroj ve výchozím nastavení v **vlastnosti konfigurace** uzlu v **Obecné** složky v **typ položky** vlastnost, zvolte **vlastního sestavení Nástroj**. Zvolte **použít** a **nástroj Custom Build** uzel se zobrazí.

1. V **vlastní nástroj sestavení** uzlu v **Obecné** složce, zadejte vlastnosti přidružené k vlastní nástroj sestavení:

   - V **Další závislosti**, zadejte jakékoli další soubory kromě pro který je definován vlastní nástroj sestavení (soubor přidružený k vlastní nástroj sestavení implicitně považuje vstup do nástroje). S dalšími vstupními soubory není vyžadována pro pro vlastní nástroj sestavení. Pokud máte více než jeden další vstup, oddělte je středníkem.

      Pokud **Další závislosti** datum souboru je novější než vstupní soubor a potom spusťte vlastní nástroj sestavení. Pokud všechny aplikace **Další závislosti** soubory jsou starší než vstupní soubor a vstupní soubor je starší než **výstupy** vlastnosti souboru a pak vlastní nástroj sestavení se nespouští.

      Předpokládejme například, že máte pro vlastní nástroj sestavení, která přijímá jako vstup MyInput.x a generuje MyInput.cpp a že MyInput.x obsahuje soubor hlaviček, MyHeader.h. Můžete zadat MyHeader.h jako vstupní závislost na MyInput.x a systém sestavení sestaví MyInput.cpp, když je zastaralé s ohledem na MyInput.x nebo MyHeader.h.

      Vstupní závislosti můžete také zajistit, že v pořadí, ve kterém je budete potřebovat ke spuštění vlastních sestavovacích nástrojů. V předchozím příkladu předpokládejme, že MyHeader.h je ve skutečnosti výstup pro vlastní nástroj sestavení. Protože MyHeader.h, představuje závislost MyInput.x, systém sestavení sestaví před spuštěním vlastního nástroje sestavení na MyInput.x nejprve Myheader.h

   - V **příkazového řádku**, jako kdyby byly jeho zadáním na příkazovém řádku zadejte příkaz. Zadejte platný příkaz nebo dávkový soubor a všechny povinné vstupní nebo výstupní soubory. Zadejte **volání** dávkového příkazu před název dávkového souboru zaručí, že jsou provedeny všechny následné příkazy.

      Více vstupních a výstupních souborů lze symbolicky s makry MSBuild. Informace o tom, jak zadat umístění souborů nebo názvy sad souborů najdete v tématu [sestavení běžná makra pro příkazy a vlastnosti](reference/common-macros-for-build-commands-and-properties.md).

      Protože znak '%' je vyhrazený nástroj MSBuild, pokud zadáte proměnnou prostředí nahraďte každé **%** řídicí znak s **% 25** šestnáctková řídicí sekvence. Nahraďte třeba **% WINDIR %** s **25WINDIR % 25**. Nástroj MSBuild nahradí každou **% 25** pořadí se **%** dříve, než přistupuje k proměnné prostředí.

   - V **popis**, zadejte popisný zprávu o tomto nástroji vlastního sestavení. Zprávy zobrazeny **výstup** okna, je-li tento nástroj zpracuje systém sestavení.

   - V **výstupy**, zadejte název výstupního souboru. To je požadovaná položka; bez hodnoty pro tuto vlastnost nebude spustit vlastní nástroj sestavení. Pokud pro vlastní nástroj sestavení má více než jeden výstup, názvech souborů oddělujte středníkem.

      Název výstupního souboru by měla být stejná jako je uveden v **příkazového řádku** vlastnost. Systém sestavení projektu vyhledejte soubor a zkontrolujte jeho data. Pokud výstupní soubor je starší než vstupní soubor nebo výstupního souboru nebyl nalezen, je spustit vlastní nástroj sestavení. Pokud všechny sady **Další závislosti** soubory jsou starší než vstupní soubor a vstupní soubor je starší než zadaný v souboru **výstupy** vlastnosti vlastního nástroje sestavení se nespouští.

Pokud chcete, aby systém sestavení provozovat na výstupní soubor generované vlastním nástrojem sestavení, je třeba ručně přidat do projektu. Vlastní nástroj sestavení aktualizuje soubor během sestavení.

## <a name="example"></a>Příklad

Předpokládejme, že chcete zahrnout do souboru s názvem parser.l ve vašem projektu. Máte na lexikální analyzátor **lexer.exe**, na vaše cesta ke spustitelnému souboru. Chcete použít ke zpracování parser.l a vytvořit soubor .c, který má stejný základní název (parser.c).

Nejprve přidejte parser.l a parser.c do projektu. Pokud soubor ještě neexistuje, přidejte odkaz na soubory. Vytvoření vlastního sestavení nástroj pro parser.l a zadejte následující v **příkazy** vlastnost:

> **lexeru %(FullPath). \%.C (název souboru)**

Tento příkaz spustí lexikální analyzátor parser.l a vypíše parser.c k adresáři projektu.

V **výstupy** vlastnost, zadejte následující:

> **.\%(Filename).c**

Při sestavování projektu se porovnává sestavovací systém časová razítka parser.l a parser.c. Pokud je novější parser.l nebo parser.c neexistuje, systém sestavení spustí hodnotu **příkazového řádku** vlastnost parser.c byl aktuální. Protože parser.c se taky přidala do projektu, systém sestavení parser.c pak zkompiluje.

## <a name="see-also"></a>Viz také:

[Běžná makra pro příkazy a vlastnosti sestavení](reference/common-macros-for-build-commands-and-properties.md)<br>
[Řešení potíží s přizpůsobením sestavení](troubleshooting-build-customizations.md)
