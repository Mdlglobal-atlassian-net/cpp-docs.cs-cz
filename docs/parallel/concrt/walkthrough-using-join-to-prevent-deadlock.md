---
title: 'Návod: Použití metody join k zabránění vzájemnému zablokování | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- preventing deadlock with joins [Concurrency Runtime]
- deadlock, preventing [Concurrency Runtime]
- non-greedy joins, example
- join class, example
ms.assetid: d791f697-bb93-463e-84bd-5df1651b7446
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5deb501cc05c2a771b6e14d5091b1baa95f2f622
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="walkthrough-using-join-to-prevent-deadlock"></a>Návod: Použití metody join k zabránění vzájemnému zablokování
Toto téma používá nabízet filosofů problém pro ilustraci použití [concurrency::join](../../parallel/concrt/reference/join-class.md) třídy, aby zablokování v aplikaci. V aplikaci softwaru *zablokování* nastane, když minimálně dva procesy každý uložení prostředku a vzájemně čekat na jiný proces k uvolnění jiný prostředek.  
  
 Nabízet filosofů problém je konkrétní příklad sadu obecné problémy, které mohou nastat při sadu prostředků je sdílen více souběžných procesů.  
  
## <a name="prerequisites"></a>Požadavky  
 Před spuštěním tohoto průvodce, přečtěte si následující témata:  
  
- [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)  
  
- [Návod: Vytvoření aplikace založené na agentovi](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)  
  
- [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)  
  
- [Funkce pro předávání zpráv](../../parallel/concrt/message-passing-functions.md)  
  
- [Synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md)  
  
##  <a name="top"></a> Oddíly  
 Tento názorný postup obsahuje následující části:  
  
- [Nabízet filosofů problém](#problem)  
  
- [Implementace Naïve](#deadlock)  
  
- [Použití metody join k zabránění vzájemnému zablokování](#solution)  
  
##  <a name="problem"></a> Nabízet filosofů problém  
 Nabízet problém filosofů ukazuje, jak dojde k zablokování v aplikaci. V tento problém pět filosofů nacházejí se na kulatého stolu. Každý filosofovi střídá myslím a pít. Každý filosofovi musí sdílet s sousedním na levé straně a druhý chopstick chopstick s sousedním vpravo. Následující obrázek znázorňuje tuto rozložení.  
  
 ![Problém jídlo filosofů](../../parallel/concrt/media/dining_philosophersproblem.png "dining_philosophersproblem")  
  
 Chcete-li eat, musí filosofovi podržte dvě chopsticks. Pokud každých filosofovi obsahuje pouze jednu chopstick a čeká na jiný, pak můžete eat žádné filosofovi a všechny omezují.  
  
 [[Horní](#top)]  
  
##  <a name="deadlock"></a> Implementace Naïve  
 Následující příklad ukazuje implementaci naïve nabízet filosofů problému. `philosopher` Třída, která je odvozena z [concurrency::agent](../../parallel/concrt/reference/agent-class.md), umožňuje každý filosofovi tak, aby fungoval nezávisle. Tento příklad používá sdílené pole [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) objekty, které chcete poskytnout každý `philosopher` objektu výhradní přístup k pár chopsticks.  
  
 Chcete-li se týkají implementace na obrázku, `philosopher` třída reprezentuje jeden filosofovi. `int` Každý chopstick představuje proměnnou. `critical_section` Objekty sloužit jako držitelé, na kterých chopsticks rest. `run` Metoda simuluje dobu životnosti filosofovi. `think` Metoda simuluje v rámci přemýšlení a `eat` metoda simuluje v rámci pít.  
  
 A `philosopher` objekt zamkne obě `critical_section` objekty k simulaci odebrání chopsticks z držitelé dříve, než se volá `eat` metoda. Po zavolání `eat`, `philosopher` objekt vrátí chopsticks držitelům podle nastavení `critical_section` objekty zpět do stavu odemknout.  
  
 `pickup_chopsticks` Metoda ukazuje, kde můžete k zablokování. Pokud každých `philosopher` objekt získá přístup k mezi zámky, pak ne `philosopher` objekt můžete pokračovat, protože jiné zámek je řízena pomocí jiného `philosopher` objektu.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
  
### <a name="code"></a>Kód  
 [!code-cpp[concrt-philosophers-deadlock#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_1.cpp)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `philosophers-deadlock.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc filosofů deadlock.cpp**  
  
 [[Horní](#top)]  
  
##  <a name="solution"></a> Použití metody join k zabránění vzájemnému zablokování  
 Tato část ukazuje způsob použití vyrovnávacích pamětí zpráv a funkce pro předávání zpráv omezit riziko vzájemného zablokování.  
  
 Pro tento příklad starší tomu se týkají `philosopher` třída nahrazuje každý `critical_section` objekt pomocí [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objektu a `join` objektu. `join` Objektu slouží jako arbiter poskytující chopsticks k filosofovi.  
  
 Tento příklad používá `unbounded_buffer` třídy, protože když cíl obdrží zprávu od `unbounded_buffer` objektu zpráva je odebrána z fronty zpráv. To umožňuje `unbounded_buffer` objekt, který obsahuje zprávu, která označuje, že chopstick je k dispozici. `unbounded_buffer` Objekt, který obsahuje žádná zpráva označuje, jestli se používá chopstick.  
  
 Tento příklad používá typu non-greedy `join` objekt, protože spojení typu non-greedy poskytuje každý `philosopher` objektu přístup k obou chopsticks pouze tehdy, když oba `unbounded_buffer` objekty obsahovat zprávu. Spojení typu greedy by nedošlo k zablokování, protože spojení typu greedy přijímá zprávy, jakmile budou k dispozici. Zablokování může dojít, pokud všechny typu greedy `join` objekty zobrazit jedna z zprávy však navždy počkejte dalších k dispozici.  
  
 Další informace o spojení typu greedy a typu non-greedy a rozdíly mezi různé typy vyrovnávací paměti zpráv najdete v tématu [asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md).  
  
#### <a name="to-prevent-deadlock-in-this-example"></a>Jak v tomto příkladu zabránit zablokování  
  
1.  Odeberte následující kód z příkladu.  
  
 [!code-cpp[concrt-philosophers-deadlock#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_2.cpp)]  
  
2.  Změnit typ `_left` a `_right` datových členů `philosopher` třídy k `unbounded_buffer`.  
  
 [!code-cpp[concrt-philosophers-join#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_3.cpp)]  
  
3.  Změnit `philosopher` konstruktor provést `unbounded_buffer` objekty jako jeho parametry.  
  
 [!code-cpp[concrt-philosophers-join#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_4.cpp)]  
  
4.  Změnit `pickup_chopsticks` metodu použít typu non-greedy `join` objekt pro příjem zpráv z vyrovnávací paměti zpráv pro obě chopsticks.  
  
 [!code-cpp[concrt-philosophers-join#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_5.cpp)]  
  
5.  Změnit `putdown_chopsticks` metodu pro uvolnění přístup k chopsticks odesláním zprávy do vyrovnávacích pamětí zpráv pro obě chopsticks.  
  
 [!code-cpp[concrt-philosophers-join#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_6.cpp)]  
  
6.  Změnit `run` metoda pro uložení výsledků `pickup_chopsticks` metoda a předávat tyto výsledky `putdown_chopsticks` metoda.  
  
 [!code-cpp[concrt-philosophers-join#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_7.cpp)]  
  
7.  Upravit deklaraci `chopsticks` proměnné v `wmain` funkce, která má být pole `unbounded_buffer` objekty, že každý obsahovat jednu zprávu.  
  
 [!code-cpp[concrt-philosophers-join#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_8.cpp)]  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující ukazuje dokončené příklad, který používá typu non-greedy `join` objekty omezit riziko vzájemného zablokování.  
  
### <a name="code"></a>Kód  
 [!code-cpp[concrt-philosophers-join#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_9.cpp)]  
  
### <a name="comments"></a>Komentáře  
 Tento příklad vytvoří následující výstup.  
  
```Output  
aristotle ate 50 times.  
descartes ate 50 times.  
hobbes ate 50 times.  
socrates ate 50 times.  
plato ate 50 times.  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `philosophers-join.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc filosofů join.cpp**  
  
 [[Horní](#top)]  
  
## <a name="see-also"></a>Viz také  
 [Návody k Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)   
 [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)   
 [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funkce usnadnění](../../parallel/concrt/message-passing-functions.md)   
 [Synchronizační datové struktury](../../parallel/concrt/synchronization-data-structures.md)
