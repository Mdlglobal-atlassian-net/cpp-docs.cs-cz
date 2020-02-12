---
title: 'Postupy: Vytváření agentů využívajících specifické zásady plánovače'
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies, agents [Concurrency Runtime]
- creating agents that use specific policies [Concurrency Runtime]
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
ms.openlocfilehash: ece6b113e3fe10c2c3179517f73137df281acf87
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141738"
---
# <a name="how-to-create-agents-that-use-specific-scheduler-policies"></a>Postupy: Vytváření agentů využívajících specifické zásady plánovače

Agent je součást aplikace, která asynchronně spolupracuje s ostatními komponentami k řešení větších výpočetních úloh. Agent má obvykle nastavený životní cyklus a udržuje stav.

Každý agent může mít jedinečné požadavky na aplikaci. Například agent, který umožňuje interakci uživatele (načtení vstupu nebo zobrazení výstupu), může vyžadovat vyšší prioritu přístupu k výpočetním prostředkům. Zásady plánovače umožňují řídit strategii, kterou Plánovač používá při správě úkolů. Toto téma ukazuje, jak vytvořit agenty, které používají konkrétní zásady plánovače.

Základní příklad, který používá vlastní zásady plánovače spolu s asynchronními bloky zpráv, najdete v tématu [How to: zadat konkrétní zásady plánovače](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).

Toto téma používá funkce z knihovny asynchronních agentů, jako jsou agenti, bloky zpráv a funkce předávající zprávy, k provedení práce. Další informace o knihovně asynchronních agentů najdete v tématu [Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md).

## <a name="example"></a>Příklad

Následující příklad definuje dvě třídy, které jsou odvozeny z [: concurrency:: Agent](../../parallel/concrt/reference/agent-class.md): `permutor` a `printer`. Třída `permutor` vypočítá všechny permutace daného vstupního řetězce. Třída `printer` vytiskne zprávy o průběhu do konzoly. Třída `permutor` provádí výpočetní náročnou operaci, která může využívat všechny dostupné výpočetní prostředky. Aby bylo možné použít třídu `printer` musí včas tisknout každou zprávu o průběhu.

V tomto příkladu se pro zajištění spravedlivého přístupu `printer` třídy k výpočetním prostředkům používá postup, který je popsán v tématu [Postupy: Správa instance Scheduleru](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) pro vytvoření instance Scheduleru, která má vlastní zásadu. Vlastní zásady určují, že priorita vlákna bude mít nejvyšší prioritní třídu.

K ilustraci výhod používání Scheduleru, který má vlastní zásady, tento příklad provede celou úlohu dvakrát. První příklad používá výchozí Plánovač k naplánování obou úloh. Příklad pak pomocí výchozího plánovače naplánuje objekt `permutor` a Scheduler, který má vlastní zásadu pro naplánování objektu `printer`.

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

I když obě sady úloh tvoří stejný výsledek, verze, která používá vlastní zásady, umožňuje, aby se objekt `printer` spouštěl se zvýšenou prioritou, takže se chová rychleji.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `permute-strings.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc permute-Strings. cpp**

## <a name="see-also"></a>Viz také

[Zásady plánovače](../../parallel/concrt/scheduler-policies.md)<br/>
[Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)
