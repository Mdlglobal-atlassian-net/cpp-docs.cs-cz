---
title: "Návod: Vytvoření aplikace založené na agentovi | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 245952bd8dfb9acc8fc8550955232a30b9dbfe9f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-creating-an-agent-based-application"></a>Návod: Vytvoření aplikace založené na agentovi
Toto téma popisuje, jak vytvořit základní aplikaci založené na agentovi. V tomto návodu vytvoříte agenta, který asynchronně čte data z textového souboru. Aplikace používá algoritmus kontrolního součtu Adler-32 vypočítat kontrolní součet obsah tohoto souboru.  
  
## <a name="prerequisites"></a>Požadavky  
 V následujících tématech k dokončení tohoto postupu je potřeba pochopit:  
  
- [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)  
  
- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)  
  
- [Funkce usnadnění](../../parallel/concrt/message-passing-functions.md)  
  
- [Synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md)  
  
##  <a name="top"></a>Oddíly  
 Tento návod ukazuje, jak provádět následující úlohy:  
  
- [Vytvoření konzolové aplikace](#createapplication)  
  
- [Vytváření file_reader – třída](#createagentclass)  
  
- [V aplikaci pomocí file_reader – třída](#useagentclass)  
  
##  <a name="createapplication"></a>Vytvoření konzolové aplikace  
 V této části ukazuje, jak k vytvoření konzolové aplikace Visual C++, který odkazuje na soubory hlaviček, které bude program používat.  
  
#### <a name="to-create-a-visual-c-application-by-using-the-win32-console-application-wizard"></a>Vytvoření aplikace Visual C++ pomocí Průvodce konzolovou aplikací Win32  
  
1.  Na **soubor** nabídky, klikněte na tlačítko **nový**a potom klikněte na **projektu** zobrazíte **nový projekt** dialogové okno.  
  
2.  V **nový projekt** dialogové okno, vyberte **Visual C++** uzel v **typy projektů** podokně a potom vyberte **Konzolová aplikace Win32** v **šablony** podokně. Zadejte název projektu, například `BasicAgent`a potom klikněte na **OK** zobrazíte **konzoly Win32 – Průvodce aplikací**.  
  
3.  V **konzoly Win32 – Průvodce aplikací** dialogové okno, klikněte na tlačítko **Dokončit**.  
  
4.  V stdafx.h přidejte následující kód.  
  
 [!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]  
  
     Agents.h soubor záhlaví obsahuje funkce [concurrency::agent](../../parallel/concrt/reference/agent-class.md) třídy.  
  
5.  Ověřte, že aplikace byl úspěšně vytvořen vytváření a jeho spuštěním. Vytvořit aplikaci, na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**. Pokud aplikace sestavení úspěšně, spusťte aplikaci kliknutím **spustit ladění** na **ladění** nabídky.  
  
 [[Horní](#top)]  
  
##  <a name="createagentclass"></a>Vytváření file_reader – třída  
 V této části ukazuje, jak vytvořit `file_reader` třídy. Modul runtime naplánuje každého agenta pro práci v jeho vlastní kontextu. Proto můžete vytvořit agenta, který provede práci synchronně, ale komunikuje s jinými součástmi asynchronně. `file_reader` Třída čte data z daného vstupního souboru a odesílá data z tohoto souboru pro danou cílovou součásti.  
  
#### <a name="to-create-the-filereader-class"></a>Vytvoření třídy file_reader  
  
1.  Přidáte nový soubor záhlaví C++ do projektu. Chcete-li to provést, klikněte pravým tlačítkem **soubory hlaviček** uzlu v **Průzkumníku řešení**, klikněte na tlačítko **přidat**a potom klikněte na **novou položku**. V **šablony** podokně, vyberte **soubor (hlaviček)**. V **přidat novou položku** dialogové okno, typ `file_reader.h` v **název** pole a pak klikněte na **přidat**.  
  
2.  V file_reader.h přidejte následující kód.  
  
 [!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]  
  
3.  V file_reader.h, vytvořte třídu, která je s názvem `file_reader` která je odvozena od `agent`.  
  
 [!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]  
  
4.  Přidejte následující členy dat tak, aby `private` část vaší třídy.  
  
 [!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]  
  
     `_file_name` Člen je název souboru, který čte agenta z. `_target` Člen [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) objektu, že agent zapíše obsah souboru. `_error` Člen obsahuje chyby, ke kterému dochází po dobu trvání agenta.  
  
5.  Přidejte následující kód pro `file_reader` pro konstruktory `public` části `file_reader` třídy.  
  
 [!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]  
  
     Každý přetížení konstruktoru nastaví `file_reader` datových členů. Druhý a třetí konstruktor přetížení umožňuje vaší aplikaci používat konkrétní scheduler s agenta. První přetížení používá výchozí plánovač s agenta.  
  
6.  Přidat `get_error` metoda do části veřejné `file_reader` třídy.  
  
 [!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]  
  
     `get_error` Metoda načte všechny chyby, ke kterému dochází po dobu trvání agenta.  
  

7.  Implementace [concurrency::agent::run](reference/agent-class.md#run) metoda v `protected` část vaší třídy.  

  
 [!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]  
  
`run` Metoda soubor otevře a přečte data z něj. `run` Metoda používá výjimek pro zachycení všechny chyby, ke kterým došlo během zpracování souboru.  
  
   Pokaždé, když tato metoda čte data ze souboru, zavolá [concurrency::asend](reference/concurrency-namespace-functions.md#asend) funkce k odesílání dat do cílové vyrovnávací paměti. Jeho cílové vyrovnávací paměti jako upozornění na ukončení zpracování odešle prázdný řetězec.  

  
 Následující příklad ukazuje úplný obsahu file_reader.h.  
  
 [!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]  
  
 [[Horní](#top)]  
  
##  <a name="useagentclass"></a>V aplikaci pomocí file_reader – třída  
 Tato část ukazuje způsob použití `file_reader` třídy ke čtení obsahu textového souboru. Také ukazuje, jak vytvořit [concurrency::call](../../parallel/concrt/reference/call-class.md) objekt, který obdrží tato data souborů a vypočítá jeho kontrolní součet Adler-32.  
  
#### <a name="to-use-the-filereader-class-in-your-application"></a>Použití třídy file_reader v aplikaci  
  
1.  V BasicAgent.cpp, přidejte následující `#include` příkaz.  
  
 [!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]  
  
2.  V BasicAgent.cpp, přidejte následující `using` direktivy.  
  
 [!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]  
  
3.  V `_tmain` fungovat, vytvořte [concurrency::event](../../parallel/concrt/reference/event-class.md) objekt, který označuje konec zpracování.  
  
 [!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]  
  
4.  Vytvoření `call` objekt, který aktualizuje kontrolního součtu, když obdrží data.  
  
 [!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]  
  
     To `call` také nastaví objekt `event` objektu, pokud obdrží prázdný řetězec signál konec zpracování.  
  
5.  Vytvoření `file_reader` objekt, který čte z test.txt soubor a zapíše obsah tohoto souboru do `call` objektu.  
  
 [!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]  
  
6.  Spuštění agenta a počkejte na její dokončení.  
  
 [!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]  
  
7.  Počkejte `call` objekt, který chcete zobrazit všechna data a dokončit.  
  
 [!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]  
  
8.  Zkontrolujte soubor čtečky chyby. Pokud nedošlo k žádné chybě, vypočítat daný konečným souhrnem Adler-32 a tisk do konzoly.  
  
 [!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]  
  
 Následující příklad ukazuje dokončení BasicAgent.cpp soubor.  
  
 [!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]  
  
 [[Horní](#top)]  
  
## <a name="sample-input"></a>Ukázkový vstup  
 Toto je ukázkový obsah text.txt vstupní soubor:  
  
```Output  
The quick brown fox  
jumps  
over the lazy dog  
```  
  
## <a name="sample-output"></a>Vzorový výstup  
 Při použití s ukázka vstupu, tento program vytvoří následující výstup:  
  
```Output  
Adler-32 sum is fefb0d75  
```  
  
## <a name="robust-programming"></a>Robustní programování  
 Pokud chcete zabránit souběžný přístup do datové členy, doporučujeme, abyste přidali metody, které provádějí práci `protected` nebo `private` část vaší třídy. Přidat pouze metody, které odesílat nebo přijímat zprávy do nebo z agenta tak, aby `public` část vaší třídy.  
  

 Vždy volat [concurrency::agent:: provádí](reference/agent-class.md#done) metody pro přesun agenta do stavu dokončení. Obvykle tuto metodu lze volat před vrácením z `run` metoda.  

  
## <a name="next-steps"></a>Další kroky  
 Dalším příkladem aplikace založené na agentovi, najdete v části [návod: použití metody join k zabránění vzájemnému zablokování](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).  
  
## <a name="see-also"></a>Viz také  
 [Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)   
 [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funkce usnadnění](../../parallel/concrt/message-passing-functions.md)   
 [Synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md)   
 [Návod: Použití metody join k zabránění vzájemnému zablokování](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)

