---
title: 'Návod: Vytvoření aplikace založené na agentovi'
ms.date: 04/25/2019
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
ms.openlocfilehash: 20197786e3d3c2d34d29af748c1cc073902cf70d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377447"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>Návod: Vytvoření aplikace založené na agentovi

Toto téma popisuje, jak vytvořit základní aplikaci založenou na agentovi. V tomto návodu můžete vytvořit agenta, který čte data z textového souboru asynchronně. Aplikace používá algoritmus kontrolního součtu Adler-32 k výpočtu kontrolního součtu obsahu tohoto souboru.

## <a name="prerequisites"></a>Požadavky

Chcete-li tento návod dokončit, musíte porozumět následujícím tématům:

- [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)

- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkce předávání zpráv](../../parallel/concrt/message-passing-functions.md)

- [Datové struktury synchronizace](../../parallel/concrt/synchronization-data-structures.md)

## <a name="sections"></a><a name="top"></a>Oddíly

Tento návod ukazuje, jak provádět následující úkoly:

- [Vytvoření konzolové aplikace](#createapplication)

- [Vytvoření file_reader třídy](#createagentclass)

- [Použití třídy file_reader v aplikaci](#useagentclass)

## <a name="creating-the-console-application"></a><a name="createapplication"></a>Vytvoření konzolové aplikace

Tato část ukazuje, jak vytvořit konzolovou aplikaci jazyka C++, která odkazuje na soubory hlaviček, které bude program používat. Počáteční kroky se liší v závislosti na verzi sady Visual Studio, kterou používáte. Chcete-li zobrazit dokumentaci k upřednostňované verzi sady Visual Studio, použijte ovládací prvek pro výběr **verze.** Nachází se v horní části obsahu na této stránce.

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-application-in-visual-studio-2019"></a>Vytvoření aplikace konzoly C++ ve Visual Studiu 2019

1. V hlavní nabídce zvolte **Soubor** > **nového** > **projektu** a otevřete dialogové okno Vytvořit **nový projekt.**

1. V horní části dialogového okna nastavte **jazyk** na **C++**, nastavte **platformu** na **Systém Windows**a **typ projektu** na **Console**.

1. Z filtrovaného seznamu typů projektů zvolte **Konzolová aplikace** a pak zvolte **Další**. Na další stránce `BasicAgent` zadejte jako název projektu a v případě potřeby zadejte umístění projektu.

1. Chcete-li vytvořit projekt, zvolte tlačítko **Vytvořit.**

1. Klepněte pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení**a zvolte **Vlastnosti**. V části **Vlastnosti** > konfigurace**C/C++** > **Předkompilované hlavičky** > **Předkompilované hlavičky** zvolte **Vytvořit**.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-c-console-application-in-visual-studio-2017-and-earlier"></a>Vytvoření konzolové aplikace C++ ve Visual Studiu 2017 a starších

1. V nabídce **Soubor** klikněte na **Nový**a potom kliknutím na **Projekt** zobrazte dialogové okno **Nový projekt.**

1. V dialogovém okně **Nový projekt** vyberte uzel **Visual C++** v podokně **Typy projektu** a v podokně **Šablony** vyberte **Konzolovou aplikaci Win32.** Zadejte například `BasicAgent`název projektu a klepnutím na tlačítko **OK** zobrazte **Průvodce konzolou Win32**.

1. V dialogovém okně **Průvodce konzolou Win32** klepněte na tlačítko **Dokončit**.

::: moniker-end

1. V *pch.h* (*stdafx.h* v Visual Studiu 2017 a starší) přidejte následující kód:

[!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]

   Hlavička souboru agents.h obsahuje funkce [třídy concurrency::agent.](../../parallel/concrt/reference/agent-class.md)

1. Ověřte, zda byla aplikace úspěšně vytvořena sestavením a spuštěním. Chcete-li vytvořit aplikaci, klikněte v nabídce **Sestavení** na **tlačítko Sestavit řešení**. Pokud se aplikace úspěšně vytvoří, spusťte aplikaci klepnutím na tlačítko **Spustit ladění v** nabídce **Ladění.**

[[Nahoře]](#top)

## <a name="creating-the-file_reader-class"></a><a name="createagentclass"></a>Vytvoření file_reader třídy

Tato část ukazuje, `file_reader` jak vytvořit třídu. Za běhu naplánuje každý agent provádět práci ve vlastním kontextu. Proto můžete vytvořit agenta, který provádí práci synchronně, ale spolupracuje s jinými součástmi asynchronně. Třída `file_reader` čte data z daného vstupního souboru a odesílá data z tohoto souboru do dané cílové součásti.

#### <a name="to-create-the-file_reader-class"></a>Vytvoření třídy file_reader

1. Přidejte do projektu nový soubor záhlaví jazyka C++. Chcete-li tak učinit, klepněte pravým tlačítkem myši na uzel **Soubory hlaviček** v **Průzkumníku řešení**, klepněte na tlačítko **Přidat**a potom klepněte na příkaz **Nová položka**. V podokně **Šablony** vyberte **Soubor záhlaví (.h).** V dialogovém okně Přidat `file_reader.h` novou **položku** zadejte do pole **Název** a klepněte na tlačítko **Přidat**.

1. V file_reader.h přidejte následující kód.

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. V file_reader.h vytvořte třídu `file_reader` s názvem, která je odvozena od `agent`.

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. Přidejte následující datové `private` členy do části třídy.

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

   Člen `_file_name` je název souboru, ze kterého agent čte. Člen `_target` je [souběžnost::ITarget](../../parallel/concrt/reference/itarget-class.md) objekt, který agent zapíše obsah souboru. Člen `_error` obsahuje všechny chyby, ke kterému dochází během životnosti agenta.

1. Přidejte následující kód `file_reader` pro konstruktory `public` do `file_reader` části třídy.

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

   Každý konstruktor přetížení `file_reader` nastaví datové členy. Druhé a třetí přetížení konstruktoru umožňuje aplikaci používat konkrétní plánovač s agentem. První přetížení používá výchozí plánovač s agentem.

1. Přidejte `get_error` metodu do veřejné `file_reader` části třídy.

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

   Metoda `get_error` načte všechny chyby, ke kterému dochází během životnosti agenta.

1. Implementujte [souběžnost::agent::run](reference/agent-class.md#run) metodu `protected` v části vaší třídy.

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

Metoda `run` otevře soubor a přečte data z něj. Metoda `run` používá zpracování výjimek k zachycení všech chyb, ke kterým dojde během zpracování souborů.

   Pokaždé, když tato metoda čte data ze souboru, volá [funkci concurrency::asend](reference/concurrency-namespace-functions.md#asend) k odeslání těchto dat do cílové vyrovnávací paměti. Odešle prázdný řetězec do cílové vyrovnávací paměti k označení ukončení zpracování.

Následující příklad ukazuje úplný obsah file_reader.h.

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

[[Nahoře]](#top)

## <a name="using-the-file_reader-class-in-the-application"></a><a name="useagentclass"></a>Použití třídy file_reader v aplikaci

Tato část ukazuje, `file_reader` jak použít třídu ke čtení obsahu textového souboru. Také ukazuje, jak vytvořit [souběžnost::call](../../parallel/concrt/reference/call-class.md) objekt, který přijímá tato data souboru a vypočítá jeho Adler-32 kontrolní součet.

#### <a name="to-use-the-file_reader-class-in-your-application"></a>Použití třídy file_reader v aplikaci

1. V souboru BasicAgent.cpp `#include` přidejte následující příkaz.

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. V souboru BasicAgent.cpp `using` přidejte následující direktivy.

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. Ve `_tmain` funkci vytvořte [objekt souběžnosti::event,](../../parallel/concrt/reference/event-class.md) který signalizuje ukončení zpracování.

[!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]

1. Vytvořte `call` objekt, který aktualizuje kontrolní součet při příjmu dat.

[!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]

   Tento `call` objekt také `event` nastaví objekt, když obdrží prázdný řetězec signalizovat konec zpracování.

1. Vytvořte `file_reader` objekt, který čte ze souboru test.txt a `call` zapíše obsah tohoto souboru do objektu.

[!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]

1. Spusťte agenta a počkejte, až skončí.

[!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]

1. Počkejte `call` na objekt přijímat všechna data a dokončit.

[!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]

1. Zkontrolujte, zda čtečka souborů neobsahuje chyby. Pokud nedošlo k žádné chybě, vypočítejte konečný součet Adler-32 a vytiskněte součet do konzoly.

[!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]

Následující příklad ukazuje kompletní soubor BasicAgent.cpp.

[!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]

[[Nahoře]](#top)

## <a name="sample-input"></a>Ukázkový vstup

Toto je ukázkový obsah souboru text.txt vstupního souboru:

```Output
The quick brown fox
jumps
over the lazy dog
```

## <a name="sample-output"></a>Vzorový výstup

Při použití se vstupem vzorku tento program vytvoří následující výstup:

```Output
Adler-32 sum is fefb0d75
```

## <a name="robust-programming"></a>Robustní programování

Chcete-li zabránit souběžný přístup k datovým členům, `protected` doporučujeme přidat metody, které provádějí práci do nebo `private` části vaší třídy. Do `public` části třídy přidávejte pouze metody, které odesílají nebo přijímají zprávy agentovi nebo z něj.

Vždy volat [souběžnost::agent::djedna](reference/agent-class.md#done) metoda přesunout agenta do dokončeného stavu. Obvykle voláte tuto metodu před `run` návratem z metody.

## <a name="next-steps"></a>Další kroky

Další příklad aplikace založené na agentovi najdete [v tématu Návod: Použití spojení k zabránění zablokování](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).

## <a name="see-also"></a>Viz také

[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkce předávání zpráv](../../parallel/concrt/message-passing-functions.md)<br/>
[Datové struktury synchronizace](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Návod: Použití metody join k zabránění vzájemnému zablokování](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)
