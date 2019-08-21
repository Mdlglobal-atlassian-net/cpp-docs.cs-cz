---
title: 'Návod: Vytvoření aplikace založené na agentovi'
ms.date: 04/25/2019
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
ms.openlocfilehash: 4a2fabd9ab4f358d40b17e662fb64ab70d01c58e
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631651"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>Návod: Vytvoření aplikace založené na agentovi

Toto téma popisuje, jak vytvořit základní aplikaci založenou na agentech. V tomto návodu můžete vytvořit agenta, který načte data z textového souboru asynchronně. Aplikace používá algoritmus Checksum Adler-32 k výpočtu kontrolního součtu obsahu daného souboru.

## <a name="prerequisites"></a>Požadavky

Chcete-li dokončit tento návod, je nutné pochopit následující témata:

- [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)

- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)

- [Synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md)

##  <a name="top"></a>Řezů

Tento návod ukazuje, jak provádět následující úlohy:

- [Vytvoření konzolové aplikace](#createapplication)

- [Vytvoření třídy file_reader](#createagentclass)

- [Použití třídy file_reader v aplikaci](#useagentclass)

##  <a name="createapplication"></a>Vytvoření konzolové aplikace

V této části se dozvíte, C++ jak vytvořit konzolovou aplikaci, která odkazuje na soubory hlaviček, které bude program používat. Počáteční postupy se liší v závislosti na verzi sady Visual Studio, kterou používáte. Přesvědčte se, zda je selektor verzí nastaven správně v levém horním rohu této stránky.

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-application-in-visual-studio-2019"></a>Vytvoření C++ konzolové aplikace v aplikaci Visual Studio 2019

1. V hlavní nabídce vyberte **soubor** > **Nový** > **projekt** a otevřete tak dialogové okno **vytvořit nový projekt** .

1. V horní části dialogového okna nastavte **jazyk** na **C++** , nastavte **platformu** na **Windows**a jako **typ projektu** nastavte **Console**. 

1. Z filtrovaného seznamu typů projektů zvolte Konzolová **aplikace** a pak zvolte **Další**. Na další stránce zadejte `BasicAgent` název projektu a v případě potřeby zadejte umístění projektu.

1. Kliknutím na tlačítko **vytvořit** vytvořte projekt.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **vlastnosti**. V **části vlastnosti** > konfigurace > **C/C++** **předkompilované**hlavičky Předkompilovaná hlavička vyberte vytvořit. > 

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

##  <a name="createagentclass"></a>Vytvoření třídy file_reader

V `file_reader` této části se dozvíte, jak vytvořit třídu. Modul runtime naplánuje, aby každý Agent prováděl práci ve vlastním kontextu. Proto můžete vytvořit agenta, který provádí synchronní práci, ale spolupracuje s ostatními komponentami asynchronně. `file_reader` Třída čte data z daného vstupního souboru a odesílá data z daného souboru do dané cílové součásti.

#### <a name="to-create-the-file_reader-class"></a>Vytvoření třídy file_reader

1. Přidejte do projektu C++ nový soubor hlaviček. Provedete to tak, že kliknete pravým tlačítkem na uzel **soubory hlaviček** v **Průzkumník řešení**, kliknete na **Přidat**a potom kliknete na **Nová položka**. V podokně **šablony** Vyberte hlavičkový **soubor (. h)** . V dialogovém okně **Přidat novou položku** zadejte `file_reader.h` do pole **název** a klikněte na tlačítko **Přidat**.

1. V file_reader. h přidejte následující kód.

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. V file_reader. h vytvořte třídu s názvem `file_reader` , která je odvozena z. `agent`

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. Do `private` části vaší třídy přidejte následující datové členy.

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

   `_file_name` Člen je název souboru, ze kterého Agent čte. Člen je objekt [Concurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md) , který agent zapisuje obsah souboru do. `_target` `_error` Člen obsahuje chybu, ke které dojde během životnosti agenta.

1. `file_reader` Do oddílu třídy`file_reader` přidejte následující kód pro konstruktory `public` .

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

   Každé přetížení konstruktoru nastaví `file_reader` datové členy. Druhé a třetí konstruktor přetížení umožňují vaší aplikaci používat konkrétní Plánovač s vaším agentem. První přetížení používá výchozí Plánovač s vaším agentem.

1. Přidejte metodu do veřejné části `file_reader` třídy. `get_error`

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

   `get_error` Metoda načte všechny chyby, ke kterým dojde během životnosti agenta.

1. Implementujte metodu [Concurrency:: Agent:: Run](reference/agent-class.md#run) v `protected` části vaší třídy.

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

`run` Metoda otevře soubor a načte z něj data. `run` Metoda používá zpracování výjimek k zachycení všech chyb, ke kterým dojde během zpracování souboru.

   Pokaždé, když tato metoda načte data ze souboru, zavolá funkci [Concurrency:: asend](reference/concurrency-namespace-functions.md#asend) , která odešle tato data do cílové vyrovnávací paměti. Pošle prázdný řetězec do cílové vyrovnávací paměti pro indikaci konce zpracování.

Následující příklad ukazuje úplný obsah file_reader. h.

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

[[Nahoře](#top)]

##  <a name="useagentclass"></a>Použití třídy file_reader v aplikaci

V této části se dozvíte, `file_reader` jak použít třídu ke čtení obsahu textového souboru. Také ukazuje, jak vytvořit objekt [Concurrency:: Call](../../parallel/concrt/reference/call-class.md) , který obdrží tato data souborů a vypočítá kontrolní součet Adler-32.

#### <a name="to-use-the-file_reader-class-in-your-application"></a>Použití třídy file_reader v aplikaci

1. V BasicAgent. cpp přidejte následující `#include` příkaz.

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. V BasicAgent. cpp přidejte následující `using` direktivy.

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. Ve funkci vytvořte objekt [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) , který signalizuje konec zpracování. `_tmain`

[!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]

1. `call` Vytvoří objekt, který aktualizuje kontrolní součet při přijímání dat.

[!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]

   Tento `call` objekt také `event` nastaví objekt, když obdrží prázdný řetězec pro signál ke konci zpracování.

1. Vytvořte objekt, který načte z souboru Test. txt a zapíše obsah tohoto souboru `call` do objektu. `file_reader`

[!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]

1. Spusťte agenta a počkejte na jeho dokončení.

[!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]

1. Počkejte, až objekt dostanou všechna data a dokončí. `call`

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

Chcete-li zabránit souběžnému přístupu k datovým členům, doporučujeme přidat metody, které provádějí práci `protected` do `private` oddílu nebo vaší třídy. Do `public` části vaší třídy přidejte pouze metody, které odesílají nebo přijímají zprávy do nebo z agenta.

Vždy zavolejte metodu [Concurrency:: Agent::d jednu](reference/agent-class.md#done) metodu pro přesunutí agenta do dokončeného stavu. Tuto metodu obvykle vyvoláte předtím, než se `run` vrátíte z metody.

## <a name="next-steps"></a>Další kroky

Další příklad aplikace založené na agentovi naleznete v tématu [Návod: Zabránit zablokování](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)pomocí spojení.

## <a name="see-also"></a>Viz také:

[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)<br/>
[Synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Návod: Použití metody join k zabránění vzájemnému zablokování](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)
