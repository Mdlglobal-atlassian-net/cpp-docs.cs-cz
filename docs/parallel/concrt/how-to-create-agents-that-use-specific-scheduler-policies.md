---
title: 'Postupy: vytváření agentů využívajících specifické zásady plánovače | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scheduler policies, agents [Concurrency Runtime]
- creating agents that use specific policies [Concurrency Runtime]
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5205f46a6be872a1065dfafc38ae8cbefec7b49b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444889"
---
# <a name="how-to-create-agents-that-use-specific-scheduler-policies"></a>Postupy: Vytváření agentů využívajících specifické zásady plánovače

Agent je součástí aplikace, která funguje asynchronně s jinými součástmi řešení větší výpočetní úlohy. Agent obvykle má nastavení životního cyklu a udržuje svůj stav.

Každý agent může mít jedinečné požadavky. Agenta, který umožňuje interakci uživatele (Načítání vstupu nebo zobrazení výstupu) může například vyžadovat vyšší prioritní přístup k výpočetní prostředky. Zásady plánovače umožňují ovládat strategie, Plánovač používá při správě úloh. Toto téma ukazuje, jak vytváření agentů využívajících specifické zásady plánovače.

Základní příklad, který používá vlastní plánovač zásady spolu s asynchronní bloky zpráv, najdete v části [postupy: určení specifické zásady plánovače](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).

Toto téma používá funkci z asynchronní knihovnou agentů, například agenti, blokům zpráv a funkce předávání zpráv a provádí práci. Další informace o asynchronní knihovnou agentů najdete v tématu [asynchronní knihovnou agentů](../../parallel/concrt/asynchronous-agents-library.md).

## <a name="example"></a>Příklad

Následující příklad definuje dvě třídy, které jsou odvozeny z [concurrency::agent](../../parallel/concrt/reference/agent-class.md): `permutor` a `printer`. `permutor` Třídy vypočítá všechny permutací daný vstupní řetězec. `printer` Třídy vytiskne zprávy o průběhu do konzoly. `permutor` Třída provádí výpočetně náročné operace, kterou může použít všechny dostupné výpočetní prostředky. Užitečnost `printer` třídy musí každá zpráva o průběhu tisk včas.

K poskytování `printer` třídy spravedlivého přístupu k výpočetním prostředkům, v tomto příkladu kroky, které jsou popsány v [postupy: Správa Instance plánovače](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) k vytvoření instance plánovače, která má vlastní zásady. Vlastní zásada určuje priorita vlákna bude s nejvyšší prioritou.

Pro ilustraci výhody použití, který má vlastní zásadu plánovače, provede v tomto příkladu celkové úlohu dvakrát. V prvním příkladu výchozím plánovačem naplánování úlohy i. Příklad poté použije výchozí scheduler k plánování `permutor` objektu a Plánovač, který má vlastní zásady pro naplánování `printer` objektu.

[!code-cpp[concrt-permute-strings#1](../../parallel/concrt/codesnippet/cpp/how-to-create-agents-that-use-specific-scheduler-policies_1.cpp)]

Tento příklad vytvoří následující výstup.

```Output
With default scheduler:
Computing all permutations of 'Grapefruit'...
100% complete...

With higher context priority:
Computing all permutations of 'Grapefruit'...
100% complete...
```

I když obě sady úkolů přinesou stejný výsledek, verzi, která používá vlastní zásady umožňuje `printer` objektu, který chcete spustit se zvýšenými oprávněními důležitostí tak, aby se chová více responzivně.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `permute-strings.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**permute – / EHsc cl.exe-strings.cpp**

## <a name="see-also"></a>Viz také

[Zásady plánovače](../../parallel/concrt/scheduler-policies.md)<br/>
[Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)

