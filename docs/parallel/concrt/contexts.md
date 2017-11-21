---
title: Kontexty | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: contexts [Concurrency Runtime]
ms.assetid: 10c1d861-8fbb-4ba0-b2ec-61876b11176e
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e77ee30c284797f0e16f5a28787c065faa9e9e29
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="contexts"></a>Kontexty

Tento dokument popisuje roli kontextů v Concurrency Runtime. Podproces, který je připojen k plánovače se označuje jako *kontext spuštění*, nebo jenom *kontextu*. [Concurrency::wait](reference/concurrency-namespace-functions.md#wait) funkce a souběžnost::[třída kontextu](../../parallel/concrt/reference/context-class.md) vám umožňují řídit chování kontexty. Použití `wait` funkce pozastavit aktuální kontext po určitou dobu. Použití `Context` třídy, pokud potřebujete větší kontrolu nad při kontexty blokovat, odblokovat a poskytne nebo když chcete přidělit nadměrnému počtu procesů aktuální kontext.  
  
> [!TIP]
>  Concurrency Runtime poskytuje výchozí plánovač, a proto není nutné vytvořit ve vaší aplikaci. Protože Plánovač úloh umožňuje optimalizovat výkon aplikací, doporučujeme začínat [paralelní vzory knihovna PPL ()](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo [knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) Pokud jste nové do Concurrency Runtime.  
  
## <a name="the-wait-function"></a>Počkejte – funkce  

 [Concurrency::wait](reference/concurrency-namespace-functions.md#wait) funkce vypočítá spolupráce při provádění aktuální kontext pro zadaný počet milisekund. Modul runtime používá čas yield provést další úlohy. Po uplynutí zadané doby, modul runtime přeplánuje kontext pro spuštění. Proto `wait` funkce může pozastavit delší než hodnota zadaná pro aktuální kontext `milliseconds` parametr.  
  
 Probíhá předání 0 (nula) `milliseconds` parametr způsobí, že modulu runtime pozastavit aktuální kontext, dokud všechny aktivní kontexty zadána možnost pro práci. Díky tomu můžete yield úloh pro všechny ostatní aktivní úlohy.  
  
### <a name="example"></a>Příklad  
 Pro příklad, který používá `wait` funkci, aby se yield aktuálního kontextu a proto umožňují jiných kontextech spustit, najdete v článku [postupy: použití skupin plánů vliv pořadí spouštění](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).  
  
## <a name="the-context-class"></a>Context – třída  
 Souběžnost::[třída kontextu](../../parallel/concrt/reference/context-class.md) poskytuje programovací abstrakci pro kontextu provádění a nabízí dvě důležité funkce: možnost spolupráce při blokování, odblokovat, a poskytne aktuální kontext a schopnost oversubscribe aktuálního kontextu.  
  
### <a name="cooperative-blocking"></a>Spolupráci blokování  
 `Context` Třída umožňuje blokovat nebo yield aktuálním kontextu spuštění. Blokování nebo je je užitečné, když aktuální kontext nemůže pokračovat, protože prostředek není k dispozici.  
  

 [Concurrency::Context::Block](reference/context-class.md#block) metoda blokuje aktuálního kontextu. Kontext, který je blokovaný předá její zpracování prostředky tak, aby modul runtime můžete provádět další úlohy. [Concurrency::Context::Unblock](reference/context-class.md#unblock) metoda odblokuje blokované kontextu. `Context::Unblock` Musí být volána metoda z kontextu jiný než ten, který volá `Context::Block`. Modul runtime vyvolá [concurrency::context_self_unblock](../../parallel/concrt/reference/context-self-unblock-class.md) Pokud kontextu pokusí odblokovat sám sebe.  
  
 Spolupráce při blokovat a odblokovat kontextu, obvykle zavoláte [concurrency::Context::CurrentContext](reference/context-class.md#currentcontext) načíst ukazatel `Context` objekt, který je spojen s aktuálním vláknem a uložit výsledek. Potom zavolejte `Context::Block` metoda blokování aktuálního kontextu. Později, volání `Context::Unblock` ze samostatné kontextu odblokovat kontext blokované.  
  
 Každý pár volání musí odpovídat `Context::Block` a `Context::Unblock`. Modul runtime vyvolá [concurrency::context_unblock_unbalanced](../../parallel/concrt/reference/context-unblock-unbalanced-class.md) při `Context::Block` nebo `Context::Unblock` metoda je volána po sobě bez odpovídající volání jiné metody. Však není nutné volat `Context::Block` před voláním `Context::Unblock`. Například, pokud jeden kontext volání `Context::Unblock` před jiné volání kontextu `Context::Block` u stejného kontextu, zůstává odblokuje tohoto kontextu.  
  
 [Concurrency::Context::Yield](reference/context-class.md#yield) metoda předá provádění, aby mohli provést další úlohy a následně přeplánovat kontext pro spuštění modulu runtime. Při volání `Context::Block` metoda, modul runtime není změnit plán kontextu.  

  
#### <a name="example"></a>Příklad  
 Pro příklad, který používá `Context::Block`, `Context::Unblock`, a `Context::Yield` metody k implementaci třídy semaforu pro spolupráci, najdete v části [postupy: použití třídy kontextu pro implementaci semaforu spolupráce](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).  
  
##### <a name="oversubscription"></a>Překryvný odběr  
 Výchozí plánovač vytváří stejný počet vláken, jsou k dispozici hardwaru vláken. Můžete použít *Překryvný odběr* vytvořit další vlákna vlákna daného hardwaru.  
  
 Pro výpočetně náročné operace Překryvný odběr obvykle není škálovat, protože zavádí další režii. Ale pro úlohy, které mají vysokou velikost latence, například čtení dat z disku nebo ze síťového připojení, Překryvný odběr může zvýšit celkový efektivitu některých aplikací.  
  
> [!NOTE]
>  Povolte Překryvný odběr pouze z vlákna, který byl vytvořen Concurrency Runtime. Překryvný odběr nemá žádný vliv, pokud je volána z vlákna, jež nebyla vytvořena modulem runtime (včetně hlavní vlákno).  
  
 Chcete-li povolit Překryvný odběr v aktuálním kontextu, volejte [concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe) metoda s `_BeginOversubscription` parametr nastaven na `true`. Pokud povolíte Překryvný odběr na vlákno, které bylo vytvořeno pomocí Concurrency Runtime, budou modulu runtime vytvořit jeden další vlákno. Po všechny úlohy, které vyžadují dokončit Překryvný odběr, volání `Context::Oversubscribe` s `_BeginOversubscription` parametr nastaven na `false`.  

  
 Můžete povolit Překryvný odběr vícekrát z aktuálního kontextu, ale je nutné jej vypnout stejný počet pokusů, které je v režimu. Překryvný odběr mohou být také vnořené; úloha, která je vytvořen jinou úlohou, který používá Překryvný odběr tedy můžete oversubscribe jeho kontextu. Ale pokud vnořené úlohy a její nadřazený patří do stejného kontextu pouze nejkrajnější volání `Context::Oversubscribe` způsobí, že vytvoření další vlákno.  
  
> [!NOTE]
>  Modul runtime vyvolá [concurrency::invalid_oversubscribe_operation](../../parallel/concrt/reference/invalid-oversubscribe-operation-class.md) Pokud Překryvný odběr je zakázána, než je povolený.  
  
###### <a name="example"></a>Příklad  
 Příklad, který používá Překryvný odběr kompenzace latence, která je způsobena čtení dat z připojení k síti, naleznete v části [postupy: použití Překryvný odběr pro posun latence](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).  
  
## <a name="see-also"></a>Viz také  
 [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Postupy: použití skupin plánů k ovlivnění pořadí provádění](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)   
 [Postupy: použití třídy kontextu pro implementaci semaforu pro spolupráci](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)   
 [Postupy: kompenzace latence vytvořením nadbytečného](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)

