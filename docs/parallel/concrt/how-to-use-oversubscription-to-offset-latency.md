---
title: 'Postupy: kompenzace latence vytvořením nadbytečného | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- oversubscription, using [Concurrency Runtime]
- using oversubscription [Concurrency Runtime]
ms.assetid: a1011329-2f0a-4afb-b599-dd4043009a10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c27864d040d0b6ce7b36087cff85ed750aa7ed2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689256"
---
# <a name="how-to-use-oversubscription-to-offset-latency"></a>Postupy: Kompenzace latence vytvořením nadbytečného počtu vláken
Překryvný odběr může zvýšit celkový efektivitu některé aplikace, které obsahují úlohy, které mají vysokou úrovní latence. Toto téma ukazuje, jak nadbytečného kompenzace latence, která je způsobena čtení dat z připojení k síti.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá [knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) se stahování souborů z servery HTTP. `http_reader` Třída odvozená z [concurrency::agent](../../parallel/concrt/reference/agent-class.md) a používá zprávu předávání asynchronně číst které názvy adresy URL ke stažení.  
  
 `http_reader` Třídy používá [concurrency::task_group](reference/task-group-class.md) třída souběžně přečíst každý soubor. Každý úkol volá [concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe) metoda s `_BeginOversubscription` parametr nastaven na `true` povolit Překryvný odběr v aktuálním kontextu. Každý úkol, použije Microsoft Foundation třídy (MFC) [CInternetSession](../../mfc/reference/cinternetsession-class.md) a [CHttpFile](../../mfc/reference/chttpfile-class.md) třídy ke stažení souboru. Nakonec každý úkol volá `Context::Oversubscribe` s `_BeginOversubscription` parametr nastaven na `false` zakázat Překryvný odběr.  
  
 Pokud je povoleno Překryvný odběr, modul runtime vytvoří jeden další vlákno, ve kterém se má spouštět úlohy. Každý z těchto vláken můžete také přidělit nadměrnému počtu procesů aktuální kontext a tím vytvořit další vlákna. `http_reader` Třídy používá [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objekt, který chcete omezit počet vláken, které aplikace používá. Agent inicializuje vyrovnávací paměti s pevný počet hodnoty tokenu. Pro každou operaci stažení agenta přečte hodnota tokenu z vyrovnávací paměti předtím, než spustí operace a pak zapíše danou hodnotu zpět do vyrovnávací paměti po dokončení operace. Pokud vyrovnávací paměť je prázdná, agent čeká jednu operací stažení ke zpětnému zápisu hodnotu do vyrovnávací paměti.  
  
 Následující příklad omezuje počet souběžných úloh, které se dvakrát počet vláken, dostupného hardwaru. Tato hodnota je to dobrý výchozí bod pro použití při experimentovat s Překryvný odběr. Můžete použít hodnotu, která nejlépe odpovídá konkrétní zpracování prostředí nebo dynamicky měnit tato hodnota reagovat na skutečné pracovní vytížení.  
  
 [!code-cpp[concrt-download-oversubscription#1](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_1.cpp)]  
  
 Tento příklad vytvoří na počítači, který má čtyři procesory následující výstup:  
  
```Output  
Downloading http://www.adatum.com/...  
Downloading http://www.adventure-works.com/...  
Downloading http://www.alpineskihouse.com/...  
Downloading http://www.cpandl.com/...  
Downloading http://www.cohovineyard.com/...  
Downloading http://www.cohowinery.com/...  
Downloading http://www.cohovineyardandwinery.com/...  
Downloading http://www.contoso.com/...  
Downloading http://www.consolidatedmessenger.com/...  
Downloading http://www.fabrikam.com/...  
Downloading http://www.fourthcoffee.com/...  
Downloading http://www.graphicdesigninstitute.com/...  
Downloading http://www.humongousinsurance.com/...  
Downloading http://www.litwareinc.com/...  
Downloading http://www.lucernepublishing.com/...  
Downloading http://www.margiestravel.com/...  
Downloading http://www.northwindtraders.com/...  
Downloading http://www.proseware.com/...  
Downloading http://www.fineartschool.net...  
Downloading http://www.tailspintoys.com/...  
Downloaded 1801040 bytes in 3276 ms.  
```  
  
 V příkladu může pracovat rychleji, pokud Překryvný odběr je povolena, protože další úlohy spustit, zatímco jiné úlohy počkejte na dokončení latentní operace.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `download-oversubscription.cpp` a pak spusťte jeden z následujících příkazů v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc /MD /D "_AFXDLL" stažení oversubscription.cpp**  
  
 **cl.exe /EHsc/MT stažení oversubscription.cpp**  
  
## <a name="robust-programming"></a>Robustní programování  
 Překryvný odběr vždy vypnout. po už nebudou potřebovat. Vezměte v úvahu funkci, která zpracovává výjimku, která je vyvolána jinou funkcí. Pokud nezakážete Překryvný odběr před funkce vrátí hodnotu, bude jakékoli další paralelní práce také oversubscribe aktuálního kontextu.  
  
 Můžete použít *prostředků pořízení je inicializace* (RAII) vzor omezit Překryvný odběr do daného oboru. V části vzoru RAII je datová struktura přidělena v zásobníku. Aby datová struktura inicializuje nebo získá prostředek, pokud je vytvořen a ničí nebo uvolní prostředku, když je datová struktura zničen. Vzor RAII zaručuje, že destruktoru je volána před ukončí vymezeném oboru. Proto prostředek správně spravované když je vyvolána výjimka, nebo když funkce obsahuje více `return` příkazy.  
  
 V následujícím příkladu definuje strukturu, která je s názvem `scoped_blocking_signal`. Konstruktoru `scoped_blocking_signal` struktura umožňuje Překryvný odběr a destruktoru zakáže Překryvný odběr.  
  
 [!code-cpp[concrt-download-oversubscription#2](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_2.cpp)]  
  
 Následující příklad změní text `download` metodu použít RAII zajistit, že Překryvný odběr je zakázána, než funkce vrátí hodnotu. Tento postup zajišťuje, že `download` metoda je bezpečný pro výjimky.  
  
 [!code-cpp[concrt-download-oversubscription#3](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_3.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Kontexty](../../parallel/concrt/contexts.md)   
 [Context::oversubscribe – metoda](reference/context-class.md#oversubscribe)


