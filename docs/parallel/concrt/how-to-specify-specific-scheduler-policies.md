---
title: 'Postupy: Určení specifických zásad plánovače'
ms.date: 11/04/2016
helpviewer_keywords:
- specifying scheduler policies [Concurrency Runtime]
- scheduler policies, specifying [Concurrency Runtime]
ms.assetid: 9c5149f9-ac34-4ff3-9e79-0bad103e4e6b
ms.openlocfilehash: 3c03ef6661ebefe0bfe9fab62938ce9987a4bca1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410029"
---
# <a name="how-to-specify-specific-scheduler-policies"></a>Postupy: Určení specifických zásad plánovače

Zásady plánovače umožňují ovládat strategie, Plánovač používá při správě úloh. Toto téma ukazuje, jak můžete zvýšit prioritu vlákna úkolu, který se zobrazí indikátor průběhu ke konzole zásadu plánovače.

Příklad, který používá vlastní plánovač zásady spolu s asynchronních agentů, naleznete v tématu [jak: Vytváření agentů využívajících specifické zásady plánovače](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).

## <a name="example"></a>Příklad

Následující příklad provede dvě úlohy paralelně. Vypočítá první úkol n<sup>th</sup> Fibonacciho číslo. Druhá úloha zobrazí indikátor průběhu do konzoly.

První úkol používá k výpočtu Fibonacciho číslo rozložené rekurzivní. To znamená rekurzivně Každá úloha vytvoří dílčí úkoly k výpočtu celkový výsledek. Úkol, který používá rekurzivní rozložené může použít všechny dostupné prostředky a tím omezit jiné úlohy. V tomto příkladu nemusí dostat úloha, která se zobrazí indikátor průběhu včasný přístup k výpočetní prostředky.

K poskytování úloha, která vytiskne průběh zprávy spravedlivé přístup k výpočetní prostředky, v tomto příkladu kroky, které jsou popsány v [jak: Správa Instance plánovače](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) k vytvoření instance plánovače, která má vlastní zásady. Vlastní zásada určuje priorita vlákna bude s nejvyšší prioritou.

V tomto příkladu [concurrency::call](../../parallel/concrt/reference/call-class.md) a [concurrency::timer](../../parallel/concrt/reference/timer-class.md) tříd pro tisk indikátor průběhu. Tyto třídy mají verze jejich konstruktory, které využít odkaz [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) objektu, která plánuje je. Příklad používá výchozí scheduler k plánování úlohy, která vypočítá počet Fibonacciho a instance scheduler k plánování úlohy, která zobrazí indikátor průběhu.

Pro ilustraci výhody použití, který má vlastní zásadu plánovače, provede v tomto příkladu celkové úlohu dvakrát. V prvním příkladu výchozím plánovačem naplánování úlohy i. Příklad poté použije výchozí plánovač prvního úkolu a Plánovač, který má vlastní zásady plánování druhý úkol.

[!code-cpp[concrt-scheduler-policy#1](../../parallel/concrt/codesnippet/cpp/how-to-specify-specific-scheduler-policies_1.cpp)]

Tento příklad vytvoří následující výstup.

```Output
Default scheduler:
...........................................................................done
Scheduler that has a custom policy:
...........................................................................done
```

I když obě sady úkolů přinesou stejný výsledek, verzi, která používá vlastní zásady umožňuje úloha, která se zobrazí indikátor průběhu spuštění se zvýšenými oprávněními důležitostí tak, aby se chová více responzivně.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `scheduler-policy.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe /EHsc scheduler-policy.cpp**

## <a name="see-also"></a>Viz také:

[Zásady plánovače](../../parallel/concrt/scheduler-policies.md)<br/>
[Postupy: Správa instance plánovače](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[Postupy: Vytváření agentů využívajících specifické zásady plánovače](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
