---
title: "Návod: Implementace tříd Future | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- implementing futures [Concurrency Runtime]
- futures, implementing [Concurrency Runtime]
ms.assetid: 82ea75cc-aaec-4452-b10d-8abce0a87e5b
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 86d4eeaadd8c2afcd5b223e7431614436ab8a786
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-implementing-futures"></a>Návod: Implementace tříd future
Toto téma ukazuje, jak implementace tříd Future ve vaší aplikaci. Téma ukazuje, jak kombinovat stávajících funkcí v Concurrency Runtime na něco jiného, který nemá informace.  
  
> [!IMPORTANT]
>  Toto téma ukazuje koncept futures pro demonstrační účely. Doporučujeme vám, že používáte [std::future](../../standard-library/future-class.md) nebo [concurrency::task](../../parallel/concrt/reference/task-class.md) když, aby asynchronní úlohu, která vypočítá hodnotu pro pozdější použití.  
  
 A *úloh* je výpočtu, který lze rozložit na další, podrobnějšího, výpočty. A *budoucí* je asynchronní úloha, která vypočítá hodnotu pro pozdější použití.  
  
 Implementace tříd Future, definuje toto téma `async_future` třídy. `async_future` Třída používá tyto součásti Concurrency Runtime: [concurrency::task_group](reference/task-group-class.md) třídy a [concurrency::single_assignment](../../parallel/concrt/reference/single-assignment-class.md) třídy. `async_future` Třídy používá `task_group` třída k výpočtu hodnoty asynchronně a `single_assignment` třídu pro ukládání výsledek výpočet. Konstruktoru `async_future` třída trvá pracovní funkci, která vypočítá výsledek a `get` metoda načte výsledek.  
  
### <a name="to-implement-the-asyncfuture-class"></a>Implementace třídy async_future  
  
1.  Deklarace třídy šablony s názvem `async_future` , je pro typ výpočtu výsledné parametry. Přidat `public` a `private` oddíly pro tuto třídu.  
  
 [!code-cpp[concrt-futures#2](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_1.cpp)]  
  
2.  V `private` části `async_future` třídy, deklarovat `task_group` a `single_assignment` – datový člen.  
  
 [!code-cpp[concrt-futures#3](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_2.cpp)]  
  

3.  V `public` části `async_future` třídy, implementovat konstruktoru. Konstruktor je šablonu, která je v pracovní funkce, která vypočítá výsledek parametry. Asynchronně provede pracovní funkce v konstruktoru `task_group` – datový člen a používá [concurrency::send](reference/concurrency-namespace-functions.md#send) funkce zápis výsledek, který má `single_assignment` – datový člen.  
  
 [!code-cpp[concrt-futures#4](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_3.cpp)]  
  
4.  V `public` části `async_future` třídy, implementovat destruktoru. Destruktoru čeká na dokončení úlohy.  
  
 [!code-cpp[concrt-futures#5](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_4.cpp)]  
  

5.  V `public` části `async_future` třídy, implementovat `get` metoda. Tato metoda používá [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkce načíst výsledky pracovní funkce.  

  
 [!code-cpp[concrt-futures#6](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_5.cpp)]  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ukazuje kompletní `async_future` třídy a příklad jeho použití. `wmain` Funkce vytvoří std::[vektoru](../../standard-library/vector-class.md) objekt, který obsahuje 10 000 náhodných celočíselné hodnoty. Poté použije `async_future` objekty, které chcete najít nejnižší a nejvyšší hodnoty, které jsou součástí `vector` objektu.  
  
### <a name="code"></a>Kód  
 [!code-cpp[concrt-futures#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_6.cpp)]  
  
### <a name="comments"></a>Komentáře  
 Tento příklad vytvoří následující výstup:  
  
```Output  
smallest: 0  
largest:  9999  
average:  4981  
```  
  
 V příkladu se používá `async_future::get` metoda načíst výsledky výpočet. `async_future::get` Metoda čeká výpočet ukončíte Pokud výpočet je stále aktivní.  
  
## <a name="robust-programming"></a>Robustní programování  


 Rozšíření `async_future` třída pro zpracování výjimek, které jsou vyvolány pracovní funkce, je třeba změnit `async_future::get` metoda k volání [concurrency::task_group::wait](reference/task-group-class.md#wait) metoda. `task_group::wait` Jakékoli výjimky, které byly vygenerovány pracovní funkce vyvolá metoda.  


  
 Následující příklad ukazuje upravenou verzi `async_future` třídy. `wmain` Využívá `try` - `catch` bloku tisknout výsledek `async_future` objekt nebo tisknout hodnotu výjimku, která je generován pracovní funkce.  
  
 [!code-cpp[concrt-futures-with-eh#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_7.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
caught exception: error  
```  
  
 Další informace o modelu zpracování výjimek v Concurrency Runtime najdete v tématu [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `futures.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc futures.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Návody k Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [task_group – třída](reference/task-group-class.md)   
 [Třída single_assignment](../../parallel/concrt/reference/single-assignment-class.md)
