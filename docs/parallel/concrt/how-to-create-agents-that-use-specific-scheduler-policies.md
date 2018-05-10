---
title: 'Postupy: vytváření agentů využívajících specifické zásady plánovače | Microsoft Docs'
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
ms.openlocfilehash: 9efa40d24ed4eaee5b9fd3995a4cf9ed696eb39a
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-create-agents-that-use-specific-scheduler-policies"></a>Postupy: Vytváření agentů využívajících specifické zásady plánovače
Agenta je komponentu aplikace, která asynchronně spolupracuje s ostatními součástmi vyřešit větší výpočetní úlohy. Agenta obvykle má nastavené životní cyklus a Udržovat stav.  
  
 Každý agent může mít aplikace jedinečné požadavky. Agenta, který umožňuje interakci s uživatelem (načítání vstup nebo výstup zobrazení) může například vyžadovat vyšší prioritu přístupu k výpočetních prostředků. Zásady plánovače umožňuje řídit strategie používající Plánovač při správě úloh. Toto téma ukazuje, jak vytváření agentů využívajících specifické zásady plánovače.  
  
 Základní příklad, který používá zásady vlastní plánovače společně s asynchronní bloky zpráv najdete v tématu [postup: Zadejte specifické zásady plánovače](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).  
  
 Toto téma používá funkce z asynchronní knihovna agentů, jako jsou agenti, bloky zpráv a funkce předávání zpráv pro práci. Další informace o knihovně asynchronních agentů najdete v tématu [knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje dvě třídy, které jsou odvozeny od [concurrency::agent](../../parallel/concrt/reference/agent-class.md): `permutor` a `printer`. `permutor` Třída vypočítá všechny permutací daný vstupní řetězec. `printer` Třída vytiskne hlášení průběhu ke konzole. `permutor` Třída provádí operaci výpočetně náročných, který může použít všechny dostupné výpočetní prostředky. Chcete-li být užitečné, `printer` třída musí tisku každou zprávu průběh včas.  
  
 K poskytování `printer` třída úloha dostatečný přístup k výpočetních prostředků, tento příklad používá kroky, které jsou popsané v [postupy: Správa Instance plánovače](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) k vytvoření instance plánovače, který má vlastní zásady. Vlastní zásady určuje prioritu vlákno jako s nejvyšší prioritou.  
  
 Tento příklad pro ilustraci výhody použití plánovače, který má vlastní zásady, provede úlohu celkový dvakrát. V příkladu nejprve používá výchozí plánovač k naplánování obě úlohy. V příkladu použije výchozí plánovač naplánovat `permutor` objekt a Plánovač, který má vlastní zásady při plánování `printer` objektu.  
  
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
  
 I když obě sady úlohy vytvořila stejný výsledek, verzi, která používá vlastní zásadu umožňuje `printer` objekt, který chcete spouštět se zvýšenými oprávněními důležitostí tak, aby se chová více responsively.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `permute-strings.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **permute /EHsc cl.exe-strings.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Zásady plánovače](../../parallel/concrt/scheduler-policies.md)   
 [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)   
 

