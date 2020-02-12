---
title: 'Návod: Vytvoření aplikace založené na agentovi'
ms.date: 04/25/2019
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
ms.openlocfilehash: 3ece04811a75fba22db447875dc6ed08c22987b5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142042"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>Návod: Vytvoření aplikace založené na agentovi

Toto téma popisuje, jak vytvořit základní aplikaci založenou na agentech. V tomto návodu můžete vytvořit agenta, který načte data z textového souboru asynchronně. Aplikace používá algoritmus Checksum Adler-32 k výpočtu kontrolního součtu obsahu daného souboru.

## <a name="prerequisites"></a>Předpoklady

Chcete-li dokončit tento návod, je nutné pochopit následující témata:

- [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)

- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)

- [Synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md)

## <a name="top"></a>Řezů

Tento návod ukazuje, jak provádět následující úlohy:

- [Vytvoření konzolové aplikace](#createapplication)

- [Vytváření file_reader třídy](#createagentclass)

- [Použití třídy file_reader v aplikaci](#useagentclass)

## <a name="createapplication"></a>Vytvoření konzolové aplikace

V této části se dozvíte, C++ jak vytvořit konzolovou aplikaci, která odkazuje na soubory hlaviček, které bude program používat. Počáteční postupy se liší v závislosti na verzi sady Visual Studio, kterou používáte. Přesvědčte se, zda je selektor verzí nastaven správně v levém horním rohu této stránky.

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-application-in-visual-studio-2019"></a>Vytvoření C++ konzolové aplikace v aplikaci Visual Studio 2019

1. V hlavní nabídce vyberte možnost **soubor** > **Nový** > **projekt** . otevře se dialogové okno **vytvořit nový projekt** .

1. V horní části dialogového okna nastavte **jazyk** na **C++** , nastavte **platformu** na **Windows**a jako **typ projektu** nastavte **Console**. 

1. Z filtrovaného seznamu typů projektů zvolte **Konzolová aplikace** a pak zvolte **Další**. Na další stránce zadejte jako název projektu `BasicAgent` a v případě potřeby zadejte umístění projektu.

1. Kliknutím na tlačítko **vytvořit** vytvořte projekt.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **vlastnosti**. V části **Vlastnosti konfigurace** > **předkompilovaných hlaviček** **C/C++**  >  > **Předkompilovaná hlavička** vyberte **vytvořit**.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-c-console-application-in-visual-studio-2017-and-earlier"></a>Vytvoření C++ konzolové aplikace v aplikaci Visual Studio 2017 a starší

1. V nabídce **soubor** klikněte na příkaz **Nový**a potom klikněte na **projekt** . zobrazí se dialogové okno **Nový projekt** .

1. V dialogovém okně **Nový projekt** vyberte v podokně **typy projektů** uzel  **C++ vizuálů** a v podokně **šablony** vyberte položku **Konzolová aplikace Win32** . Zadejte název projektu, například `BasicAgent`, a pak kliknutím na tlačítko **OK** zobrazte **Průvodce konzolovou aplikací Win32**.

1. V dialogovém okně **Průvodce konzolovou aplikací Win32** klikněte na tlačítko **Dokončit**.

::: moniker-end

1. V souboru *PCH. h* (*stdafx. h* v aplikaci Visual Studio 2017 a starší) přidejte následující kód:

[!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]

   Soubor hlaviček Agents. h obsahuje funkce třídy [Concurrency:: Agent](../../parallel/concrt/reference/agent-class.md) .

1. Vytvořením a spuštěním aplikace ověřte, zda byla aplikace vytvořena úspěšně. Chcete-li sestavit aplikaci, klikněte v nabídce **sestavení** na příkaz **Sestavit řešení**. Pokud se aplikace úspěšně sestaví, spusťte aplikaci kliknutím na příkaz **Spustit ladění** v nabídce **ladění** .

[[Nahoře](#top)]

## <a name="createagentclass"></a>Vytváření file_reader třídy

V této části se dozvíte, jak vytvořit třídu `file_reader`. Modul runtime naplánuje, aby každý Agent prováděl práci ve vlastním kontextu. Proto můžete vytvořit agenta, který provádí synchronní práci, ale spolupracuje s ostatními komponentami asynchronně. Třída `file_reader` čte data z daného vstupního souboru a odesílá data z daného souboru do dané cílové součásti.

#### <a name="to-create-the-file_reader-class"></a>Vytvoření třídy file_reader

1. Přidejte do projektu C++ nový soubor hlaviček. Provedete to tak, že kliknete pravým tlačítkem na uzel **soubory hlaviček** v **Průzkumník řešení**, kliknete na **Přidat**a potom kliknete na **Nová položka**. V podokně **šablony** vyberte **hlavičkový soubor (. h)** . V dialogovém okně **Přidat novou položku** zadejte do pole **název** text `file_reader.h` a pak klikněte na tlačítko **Přidat**.

1. V file_reader. h přidejte následující kód.

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. V file_reader. h vytvořte třídu s názvem `file_reader`, která je odvozena z `agent`.

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. Do oddílu `private` vaší třídy přidejte následující datové členy.

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

   Člen `_file_name` je název souboru, ze kterého Agent čte. `_target` člen je objekt [Concurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md) , který agent zapisuje obsah souboru do. Člen `_error` obsahuje chybu, ke které dojde během životního cyklu agenta.

1. Přidejte následující kód pro konstruktory `file_reader` do oddílu `public` třídy `file_reader`.

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

   Každé přetížení konstruktoru nastaví `file_reader` datových členů. Druhé a třetí konstruktor přetížení umožňují vaší aplikaci používat konkrétní Plánovač s vaším agentem. První přetížení používá výchozí Plánovač s vaším agentem.

1. Přidejte metodu `get_error` do veřejné části `file_reader` třídy.

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

   Metoda `get_error` načítá všechny chyby, ke kterým dojde během životnosti agenta.

1. Implementujte metodu [Concurrency:: Agent:: Run](reference/agent-class.md#run) v oddílu `protected` vaší třídy.

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

Metoda `run` otevře soubor a přečte z něj data. Metoda `run` používá zpracování výjimek k zachycení všech chyb, ke kterým dojde během zpracování souboru.

   Pokaždé, když tato metoda načte data ze souboru, zavolá funkci [Concurrency:: asend](reference/concurrency-namespace-functions.md#asend) , která odešle tato data do cílové vyrovnávací paměti. Pošle prázdný řetězec do cílové vyrovnávací paměti pro indikaci konce zpracování.

Následující příklad ukazuje úplný obsah file_reader. h.

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

[[Nahoře](#top)]

## <a name="useagentclass"></a>Použití třídy file_reader v aplikaci

V této části se dozvíte, jak použít třídu `file_reader` ke čtení obsahu textového souboru. Také ukazuje, jak vytvořit objekt [Concurrency:: Call](../../parallel/concrt/reference/call-class.md) , který obdrží tato data souborů a vypočítá kontrolní součet Adler-32.

#### <a name="to-use-the-file_reader-class-in-your-application"></a>Použití třídy file_reader v aplikaci

1. V BasicAgent. cpp přidejte následující příkaz `#include`.

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. V BasicAgent. cpp přidejte následující direktivy `using`.

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. Ve funkci `_tmain` vytvořte objekt [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) , který signalizuje konec zpracování.

[!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]

1. Vytvoří objekt `call`, který aktualizuje kontrolní součet při přijímání dat.

[!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]

   Tento objekt `call` také nastaví `event` objekt, když obdrží prázdný řetězec pro signál ke konci zpracování.

1. Vytvořte objekt `file_reader`, který čte ze souboru Test. txt a zapíše obsah tohoto souboru do objektu `call`.

[!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]

1. Spusťte agenta a počkejte na jeho dokončení.

[!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]

1. Počkejte, až objekt `call` obdrží všechna data a dokončete.

[!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]

1. Vyhledejte chyby ve čtečce souborů. Pokud nedošlo k žádné chybě, vypočítejte Konečný součet Adler-32 a vytiskněte součet do konzoly.

[!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]

Následující příklad ukazuje úplný soubor BasicAgent. cpp.

[!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]

[[Nahoře](#top)]

## <a name="sample-input"></a>Ukázkový vstup

Toto je ukázkový obsah vstupního souboru text. txt:

```Output
The quick brown fox
jumps
over the lazy dog
```

## <a name="sample-output"></a>Vzorový výstup

Při použití s ukázkovým vstupem tento program generuje následující výstup:

```Output
Adler-32 sum is fefb0d75
```

## <a name="robust-programming"></a>Robustní programování

Chcete-li zabránit souběžnému přístupu k datovým členům, doporučujeme přidat metody, které provádějí práci s oddílem `protected` nebo `private` vaší třídy. Přidejte pouze metody, které odesílají nebo přijímají zprávy do nebo z agenta do oddílu `public` vaší třídy.

Vždy zavolejte metodu [Concurrency:: Agent::d jednu](reference/agent-class.md#done) metodu pro přesunutí agenta do dokončeného stavu. Tuto metodu obvykle vyvoláte předtím, než se vrátíte z metody `run`.

## <a name="next-steps"></a>Další kroky

Další příklad aplikace založené na agentech najdete v tématu [Návod: použití spojení k zabránění zablokování](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).

## <a name="see-also"></a>Viz také

[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)<br/>
[Synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Návod: Použití metody join k zabránění vzájemnému zablokování](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)
