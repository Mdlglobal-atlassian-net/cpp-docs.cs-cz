---
title: 'Postupy: Kompenzace latence vytvořením nadbytečného počtu vláken'
ms.date: 11/04/2016
helpviewer_keywords:
- oversubscription, using [Concurrency Runtime]
- using oversubscription [Concurrency Runtime]
ms.assetid: a1011329-2f0a-4afb-b599-dd4043009a10
ms.openlocfilehash: fc16fa5cfeddf82b9fcb0164796fb7f4c90aef15
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653073"
---
# <a name="how-to-use-oversubscription-to-offset-latency"></a>Postupy: Kompenzace latence vytvořením nadbytečného počtu vláken

Překryvný odběr můžete zlepšit celkové efektivity některé aplikace, které obsahují úloh, které mají vysoké množství latence. Toto téma ukazuje, jak nadbytečného latenci, které je způsobeno tím, že čtení dat z připojení k síti.

## <a name="example"></a>Příklad

V tomto příkladu [asynchronní knihovnou agentů](../../parallel/concrt/asynchronous-agents-library.md) ke stažení souborů ze serverů HTTP. `http_reader` Třída odvozena z [concurrency::agent](../../parallel/concrt/reference/agent-class.md) a používá zprávu předávání k asynchronnímu čtení názvy adresu URL ke stažení.

`http_reader` Třídy používá [concurrency::task_group](reference/task-group-class.md) třídy souběžně číst každý soubor. Každý úkol volá [concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe) metodu `_BeginOversubscription` parametr nastaven na **true** chcete povolit překročení stanovených v aktuálním kontextu. Každý úkol, použije Microsoft Foundation Classes (MFC) [cinternetsession –](../../mfc/reference/cinternetsession-class.md) a [chttpfile –](../../mfc/reference/chttpfile-class.md) třídy ke stažení souboru. Nakonec se volá každý úkol `Context::Oversubscribe` s `_BeginOversubscription` parametr nastaven na **false** zakázat překryvného odběru.

Pokud je povoleno více úloh než, modul runtime vytvoří jeden další vlákno, ve kterém chcete spouštět úlohy. Každá z tato vlákna můžete také přidělit nadměrnému počtu procesů aktuálního kontextu a tím vytvořit další vlákna. `http_reader` Třídy používá [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objektu, který chcete omezit počet vláken, které aplikace používá. Agent inicializuje vyrovnávací paměti s pevným počtem hodnoty tokenu. Pro každou operaci stahování agent načte hodnota tokenu z vyrovnávací paměti předtím, než spustí operace a pak zapíše tuto hodnotu do vyrovnávací paměti po dokončení operace. Pokud vyrovnávací paměť je prázdná, agent čeká na jednu operací stažení, která hodnotu zapíše zpět do vyrovnávací paměti.

Následující příklad omezí počet souběžných úloh dvakrát počet podprocesů hardwaru k dispozici. Tato hodnota je dobrým výchozím bodem pro použití při experimentovat s překryvného odběru. Můžete použít hodnotu, která odpovídá konkrétní zpracování prostředí nebo dynamicky měnit tuto hodnotu na skutečné pracovní vytížení.

[!code-cpp[concrt-download-oversubscription#1](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_1.cpp)]

Tento příklad vytvoří následující výstup v počítači, který má čtyři procesory:

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

V příkladu může pracovat rychleji, pokud více úloh než je povolena, protože spustit další úkoly při další úlohy počkat na dokončení latentní operace.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `download-oversubscription.cpp` a pak spusťte jeden z následujících příkazů v **příkazový řádek sady Visual Studio** okna.

**cl.exe/EHsc/MD /D "_AFXDLL" download-oversubscription.cpp**

**cl.exe/EHsc/MT download-oversubscription.cpp**

## <a name="robust-programming"></a>Robustní programování

Vždy zakážete překryvného odběru po již nejsou potřebná. Vezměte v úvahu funkci, která zpracovává výjimku, která je vyvolána jinou funkci. Pokud se předtím, než funkce vrátí nezakazujte překryvného odběru, další paralelní práce se také přidělit nadměrnému počtu procesů aktuálního kontextu.

Můžete použít *získání prostředků je inicializace* vzor (RAII) k omezení Překryvný odběr k daném oboru. Podle vzoru RAII je datová struktura přidělené v zásobníku. Struktury dat inicializuje nebo získá prostředek, když se vytvoří a odstraní nebo vydání prostředku při zničení datová struktura. Vzorek RAII, aby zaručuje, že destruktoru je volána před ukončení nadřazeného oboru. Proto prostředku se správně spravuje při vyvolání výjimky, nebo když funkce obsahuje více `return` příkazy.

V následujícím příkladu definuje strukturu, která má název `scoped_blocking_signal`. Konstruktor třídy `scoped_blocking_signal` struktura umožňuje překryvného odběru a destruktor zakáže překryvného odběru.

[!code-cpp[concrt-download-oversubscription#2](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_2.cpp)]

Následující příklad upravuje text `download` metoda použijte vzor RAII zajistit, že překryvného odběru je zakázaná, než funkce vrátí. Tento postup zajišťuje, `download` metoda je bezpečnost výjimek.

[!code-cpp[concrt-download-oversubscription#3](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_3.cpp)]

## <a name="see-also"></a>Viz také

[Kontexty](../../parallel/concrt/contexts.md)<br/>
[Context::oversubscribe – metoda](reference/context-class.md#oversubscribe)

