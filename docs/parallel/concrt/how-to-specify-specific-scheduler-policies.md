---
title: "Postupy: určení specifických zásad plánovače | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- specifying scheduler policies [Concurrency Runtime]
- scheduler policies, specifying [Concurrency Runtime]
ms.assetid: 9c5149f9-ac34-4ff3-9e79-0bad103e4e6b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: af30b38a89eb7e4b50c7d31be2d3ba6572843b1e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-specify-specific-scheduler-policies"></a>Postupy: Určení specifických zásad plánovače
Zásady plánovače umožňuje řídit strategie používající Plánovač při správě úloh. Toto téma ukazuje, jak pomocí zásad plánovače můžete zvýšit prioritu vlákno úlohu, která se zobrazí indikátor průběhu ke konzole.  
  
 Příklad, který používá zásady vlastní plánovače společně s asynchronních agentů, naleznete v části [postupy: vytváření agentů této zásady použít konkrétní plánovače](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad provádí úlohy dvou paralelně. První úlohou vypočítá z n<sup>tý</sup> Fibonacciho číslo. V druhé úloze vytiskne indikátor průběhu ke konzole.  
  
 První úlohou používá k výpočtu Fibonacciho číslo rekurzivní rozložením. To znamená že každý rekurzivně úloh vytvoří dílčí úkoly k výpočtu celkového výsledek. Úloha, která používá rekurzivní rozložením může používat všechny dostupné prostředky a tím omezují další úlohy. V tomto příkladu nemusí úloha, která se zobrazí indikátor průběhu dostat včas přístup k výpočetních prostředků.  
  
 Pokud chcete zadat úloha, která se vytiskne průběh zpráva úloha dostatečný přístup k výpočetních prostředků, tento příklad používá kroky, které jsou popsané v [postupy: Správa Instance plánovače](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) k vytvoření instance plánovače, který má vlastní zásady. Vlastní zásady určuje prioritu vlákno jako s nejvyšší prioritou.  
  
 Tento příklad používá [concurrency::call](../../parallel/concrt/reference/call-class.md) a [concurrency::timer](../../parallel/concrt/reference/timer-class.md) tříd pro tisk indikátor průběhu. Tyto třídy mají verze jejich konstruktory, které provést odkaz na [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) objekt, který je plány. Příklad používá výchozí plánovač naplánovat úlohu, která vypočítá počet Fibonacciho a instance plánovače naplánovat úlohu, která se zobrazí indikátor průběhu.  
  
 Tento příklad pro ilustraci výhody použití plánovače, který má vlastní zásady, provede úlohu celkový dvakrát. V příkladu nejprve používá výchozí plánovač k naplánování obě úlohy. V příkladu použije výchozí plánovač naplánovat úlohu první a Plánovač, který má vlastní zásady při plánování v druhé úloze.  
  
 [!code-cpp[concrt-scheduler-policy#1](../../parallel/concrt/codesnippet/cpp/how-to-specify-specific-scheduler-policies_1.cpp)]  
  
 Tento příklad vytvoří následující výstup.  
  
```Output  
Default scheduler:  
...........................................................................done  
Scheduler that has a custom policy:  
...........................................................................done  
```  
  
 I když obě sady úlohy vytvořila stejný výsledek, verzi, která používá vlastní zásadu umožňuje úloha, která se zobrazí indikátor průběhu spouštět se zvýšenými oprávněními důležitostí tak, aby se chová více responsively.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `scheduler-policy.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc scheduler-policy.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Zásady plánovače](../../parallel/concrt/scheduler-policies.md)   
 [Postupy: Správa Instance plánovače](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)   
 [Postupy: Vytváření agentů využívajících specifické zásady plánovače](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)

