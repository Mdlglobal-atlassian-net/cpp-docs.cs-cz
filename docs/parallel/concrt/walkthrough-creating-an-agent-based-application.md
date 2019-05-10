---
title: 'Návod: Vytvoření aplikace založené na agentovi'
ms.date: 04/25/2019
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
ms.openlocfilehash: c249bc8138a3617cce3eae836751575b2626f4aa
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857316"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>Návod: Vytvoření aplikace založené na agentovi

Toto téma popisuje, jak vytvořit základní aplikaci založené na agentovi. V tomto podrobném návodu můžete vytvořit agenta, který asynchronně čte data z textového souboru. Aplikace používá algoritmus Adler 32 kontrolní součet vypočítat kontrolní součet obsah tohoto souboru.

## <a name="prerequisites"></a>Požadavky

V následujících tématech k dokončení tohoto názorného postupu musíte znát:

- [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)

- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)

- [Synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md)

##  <a name="top"></a> Oddíly

Tento návod ukazuje, jak provádět následující úlohy:

- [Vytvoření konzolové aplikace](#createapplication)

- [Vytvoření třídy file_reader](#createagentclass)

- [Používání třídy file_reader v aplikaci](#useagentclass)

##  <a name="createapplication"></a> Vytvoření konzolové aplikace

Tato část ukazuje, jak vytvořit C++ konzolovou aplikaci, která odkazuje na soubory hlaviček, které budou používat program. Počáteční kroky se liší v závislosti na tom, kterou verzi sady Visual Studio, kterou používáte. Ujistěte se, že volič verze je správně nastavena v levém horním rohu této stránky.

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-application-in-visual-studio-2019"></a>Chcete-li vytvořit C++ konzolovou aplikaci v aplikaci Visual Studio 2019

1. V hlavní nabídce zvolte **souboru** > **nový** > **projektu** otevřít **vytvořte nový projekt** dialogového okna pole.

1. V horní části dialogového okna, nastavte **jazyk** k **C++**, nastavte **platformy** k **Windows**a nastavte **typprojektu** k **konzoly**. 

1. Filtrované seznamu typů projektů zvolte **konzolovou aplikaci** klikněte na tlačítko **Další**. Na další stránce zadejte `BasicAgent` jako název projektu a zadejte umístění projektu, v případě potřeby.

1. Zvolte **vytvořit** tlačítko pro vytvoření projektu.

1. Klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení**a zvolte **vlastnosti**. V části **vlastnosti konfigurace** > **C /C++** > **předkompilované hlavičky** > **předkompilované hlavička** zvolte **vytvořit**.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-c-console-application-in-visual-studio-2017-and-earlier"></a>Chcete-li vytvořit C++ konzolovou aplikaci v sadě Visual Studio 2017 a starší

1. Na **souboru** nabídky, klikněte na tlačítko **nový**a potom klikněte na tlačítko **projektu** zobrazíte **nový projekt** dialogové okno.

1. V **nový projekt** dialogovém okně **Visual C++** uzlu **typy projektů** podokně a pak vyberte **Konzolová aplikace Win32** v **šablony** podokně. Zadejte název projektu, například `BasicAgent`a potom klikněte na tlačítko **OK** zobrazíte **Průvodce konzolovou aplikací Win32**.

1. V **Průvodce konzolovou aplikací Win32** dialogové okno, klikněte na tlačítko **Dokončit**.

::: moniker-end

1. V souboru stdafx.h (nebo soubor pch.h v závislosti na vaší verzi sady Visual Studio) přidejte následující kód.

[!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]

   Agents.h souboru záhlaví obsahuje funkce [concurrency::agent](../../parallel/concrt/reference/agent-class.md) třídy.

1. Ověřte, že aplikace úspěšně vytvořil sestavováním a spouštěním ho. Jak vytvořit aplikaci, na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**. Je-li aplikace sestavena úspěšně, spusťte aplikaci kliknutím **spustit ladění** na **ladění** nabídky.

[[Horní](#top)]

##  <a name="createagentclass"></a> Vytvoření třídy file_reader

Tato část ukazuje, jak vytvořit `file_reader` třídy. Modul runtime naplánuje každého agenta a provádí práci ve vlastním kontextu. Proto můžete vytvořit agenta, který provádí práci synchronně, ale spolupracuje s ostatními součástmi asynchronně. `file_reader` Třída čte data z daného vstupního souboru a odesílá data z tohoto souboru pro danou cílovou komponenty.

#### <a name="to-create-the-filereader-class"></a>Vytvoření třídy file_reader

1. Přidejte do projektu nový soubor hlaviček jazyka C++. Uděláte to tak, klikněte pravým tlačítkem na **hlavičkové soubory** uzel v **Průzkumníku řešení**, klikněte na tlačítko **přidat**a potom klikněte na tlačítko **nová položka**. V **šablony** vyberte **soubor hlaviček (.h)**. V **přidat novou položku** dialogovém okně `file_reader.h` v **název** pole a potom klikněte na tlačítko **přidat**.

1. V file_reader.h přidejte následující kód.

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. V file_reader.h, vytvořte třídu s názvem `file_reader` , která je odvozena z `agent`.

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. Přidejte následující datové členy do `private` část vaší třídy.

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

   `_file_name` Člen je název souboru, která agent načítá z. `_target` Člen je [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) , že agent zapíše obsah souboru do objektu. `_error` Člena obsahuje všechny chyby, ke které dojde během existence agenta.

1. Přidejte následující kód pro `file_reader` konstruktory mají být `public` část `file_reader` třídy.

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

   Nastaví jednotlivá přetížení konstruktoru `file_reader` datové členy. Druhý a třetí konstruktor přetížení umožňuje vaší aplikaci pro použití určitého plánovače s agenta. První přetížení se svým zástupcem používá výchozím plánovačem.

1. Přidat `get_error` metodu pro veřejnou část `file_reader` třídy.

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

   `get_error` Metoda načte všechny chyby, ke které dojde během existence agenta.

1. Implementace [concurrency::agent::run](reference/agent-class.md#run) metodu `protected` část vaší třídy.

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

`run` Metoda otevře soubor a čte data z něj. `run` Metoda zachytit všechny chyby, k nimž došlo při zpracování souboru pomocí zpracování výjimek.

   Pokaždé, když tato metoda načte data ze souboru, zavolá [concurrency::asend](reference/concurrency-namespace-functions.md#asend) funkce k odesílání dat do cílové vyrovnávací paměti. Prázdný řetězec odešle do její cílové vyrovnávací paměti pro označení konce zpracování.

Následující příklad ukazuje kompletní obsah file_reader.h.

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

[[Horní](#top)]

##  <a name="useagentclass"></a> Používání třídy file_reader v aplikaci

Tato část ukazuje způsob použití `file_reader` třídy k načtení obsahu textového souboru. Také ukazuje, jak vytvořit [concurrency::call](../../parallel/concrt/reference/call-class.md) objekt, který obdrží tato data souborů a vypočítá jeho kontrolní součet Adler-32.

#### <a name="to-use-the-filereader-class-in-your-application"></a>Použití třídy file_reader v aplikaci

1. V souboru BasicAgent.cpp, přidejte následující `#include` příkazu.

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. V souboru BasicAgent.cpp, přidejte následující `using` direktivy.

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. V `_tmain` funkce, vytváření [concurrency::event](../../parallel/concrt/reference/event-class.md) objekt, který označuje konec zpracování.

[!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]

1. Vytvoření `call` objekt, který aktualizuje kontrolního součtu, když přijme data.

[!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]

   To `call` objekt také nastaví `event` objektu, když přijme prázdný řetězec, který signalizuje, že na konec zpracování.

1. Vytvoření `file_reader` objekt, který čte ze souboru test.txt a zapíše obsah tohoto souboru do `call` objektu.

[!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]

1. Spustit agenta a počkejte na dokončení.

[!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]

1. Počkejte `call` objektu, který chcete zobrazit všechna data a dokončení.

[!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]

1. Zkontrolujte soubor čtecí zařízení pro chyby. Pokud nedošlo k žádné chybě, vypočítat součet konečné Adler-32 a Tisk součtu do konzoly.

[!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]

Následující příklad ukazuje kompletní soubor BasicAgent.cpp.

[!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]

[[Horní](#top)]

## <a name="sample-input"></a>Ukázkový vstup

Toto je ukázkový obsah vstupního souboru text.txt:

```Output
The quick brown fox
jumps
over the lazy dog
```

## <a name="sample-output"></a>Vzorový výstup

Při použití s ukázkový vstup, tento program vytvoří následující výstup:

```Output
Adler-32 sum is fefb0d75
```

## <a name="robust-programming"></a>Robustní programování

Aby se zabránilo souběžný přístup k datové členy, doporučujeme přidat metody, které provádějí práci na `protected` nebo `private` část vaší třídy. Pouze přidat metody, které odesílání nebo příjmu zpráv do nebo z agenta tak, aby `public` část vaší třídy.

Vždy volat [concurrency::agent:: provádí](reference/agent-class.md#done) metody pro přesun do dokončeného stavu agenta. Obvykle tuto metodu lze volat před vrácením z `run` metody.

## <a name="next-steps"></a>Další kroky

Další příklad aplikace založené na agentovi, naleznete v tématu [názorný postup: Použití metody join k zabránění vzájemnému zablokování](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).

## <a name="see-also"></a>Viz také:

[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)<br/>
[Synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Návod: Použití metody join k zabránění vzájemnému zablokování](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)
