---
title: 'Postupy: Určení specifických zásad plánovače'
ms.date: 11/04/2016
helpviewer_keywords:
- specifying scheduler policies [Concurrency Runtime]
- scheduler policies, specifying [Concurrency Runtime]
ms.assetid: 9c5149f9-ac34-4ff3-9e79-0bad103e4e6b
ms.openlocfilehash: bd5edfbdf6b0fda9c7e327dab9538bbf6b5e4b12
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142453"
---
# <a name="how-to-specify-specific-scheduler-policies"></a>Postupy: Určení specifických zásad plánovače

Zásady plánovače umožňují řídit strategii, kterou Plánovač používá při správě úkolů. V tomto tématu se dozvíte, jak použít zásadu plánovače ke zvýšení priority vlákna úlohy, která tiskne indikátor průběhu na konzolu.

Příklad, který používá vlastní zásady plánovače spolu s asynchronními agenty, najdete v tématu [Postupy: vytváření agentů využívajících specifické zásady plánovače](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).

## <a name="example"></a>Příklad

Následující příklad provádí paralelní zpracování dvou úloh. První úkol vypočítá n-<sup>tý</sup> Fibonacci číslo. Druhý úkol vytiskne indikátor průběhu do konzoly.

První úkol používá k výpočtu Fibonacci čísla rekurzivní rozklad. To znamená, že každý úkol rekurzivně vytvoří dílčí úkoly k výpočtu celkového výsledku. Úloha, která používá rekurzivní rozkládání, může využívat všechny dostupné prostředky, a tím omezují další úlohy. V tomto příkladu úloha, která tiskne ukazatel průběhu, nemusí získat včas přístup k výpočetním prostředkům.

Tento příklad používá kroky popsané v tématu [Postupy: Správa instance plánovače](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) k vytvoření instance Scheduleru, která má vlastní zásady, a poskytnout tak úkol, který vytiskne zprávu o průběhu. Vlastní zásady určují, že priorita vlákna bude mít nejvyšší prioritní třídu.

Tento příklad používá třídy [Concurrency:: Call](../../parallel/concrt/reference/call-class.md) a [Concurrency:: Timer](../../parallel/concrt/reference/timer-class.md) k vytištění indikátoru průběhu. Tyto třídy mají verze svých konstruktorů, které přijímají odkaz na objekt [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) , který je plánuje. V příkladu se používá výchozí Plánovač k naplánování úlohy, která vypočítá Fibonacci číslo a instanci plánovače k naplánování úlohy, která vytiskne ukazatel průběhu.

K ilustraci výhod používání Scheduleru, který má vlastní zásady, tento příklad provede celou úlohu dvakrát. První příklad používá výchozí Plánovač k naplánování obou úloh. V příkladu se pak použije výchozí Plánovač k naplánování prvního úkolu a Scheduler, který má vlastní zásadu pro naplánování druhého úkolu.

[!code-cpp[concrt-scheduler-policy#1](../../parallel/concrt/codesnippet/cpp/how-to-specify-specific-scheduler-policies_1.cpp)]

Tento příklad vytvoří následující výstup.

```Output
Default scheduler:
...........................................................................done
Scheduler that has a custom policy:
...........................................................................done
```

I když obě sady úloh vytváří stejný výsledek, verze, která používá vlastní zásady, umožňuje úlohu, která tiskne indikátor průběhu, aby běžela se zvýšenou prioritou, takže se chová rychleji.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `scheduler-policy.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc Scheduler-Policy. cpp**

## <a name="see-also"></a>Viz také

[Zásady plánovače](../../parallel/concrt/scheduler-policies.md)<br/>
[Postupy: Správa instance plánovače](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[Postupy: Vytváření agentů využívajících specifické zásady plánovače](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
