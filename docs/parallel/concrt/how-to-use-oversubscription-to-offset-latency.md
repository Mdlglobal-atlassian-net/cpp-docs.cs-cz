---
title: 'Postupy: Kompenzace latence vytvořením nadbytečného počtu vláken'
ms.date: 11/04/2016
helpviewer_keywords:
- oversubscription, using [Concurrency Runtime]
- using oversubscription [Concurrency Runtime]
ms.assetid: a1011329-2f0a-4afb-b599-dd4043009a10
ms.openlocfilehash: 02c72e7b7f0e3ec9727504d62341d945dcd0d957
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141942"
---
# <a name="how-to-use-oversubscription-to-offset-latency"></a>Postupy: Kompenzace latence vytvořením nadbytečného počtu vláken

Přeplacené předplatné může zlepšit celkovou efektivitu některých aplikací, které obsahují úkoly s vysokým množstvím latence. V tomto tématu se naučíte, jak pomocí přepočtu použít předplatné kompenzovat latenci, která je způsobená čtením dat ze síťového připojení.

## <a name="example"></a>Příklad

V tomto příkladu se pomocí [knihovny asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) stahují soubory ze serverů HTTP. Třída `http_reader` je odvozena z [: concurrency:: Agent](../../parallel/concrt/reference/agent-class.md) a používá předávání zpráv pro asynchronní čtení těch názvů adres URL, které se mají stáhnout.

Třída `http_reader` používá třídu [Concurrency:: task_group](reference/task-group-class.md) pro souběžné čtení jednotlivých souborů. Každý úkol volá metodu [Concurrency:: Context::](reference/context-class.md#oversubscribe) resubscription s parametrem `_BeginOversubscription` nastaveným na **hodnotu true** , aby bylo možné v aktuálním kontextu povolit přeměnu. Každý úkol následně používá třídy Microsoft Foundation Classes (MFC) [CInternetSession](../../mfc/reference/cinternetsession-class.md) a [CHttpFile](../../mfc/reference/chttpfile-class.md) ke stažení souboru. Nakonec každý úkol volá `Context::Oversubscribe` s parametrem `_BeginOversubscription` nastaveným na **hodnotu false** , aby se přepnulo předané předplatné.

Pokud je povoleno předané předplatné, modul runtime vytvoří jedno další vlákno, ve kterém budou spouštěny úlohy. Každé z těchto vláken může také přeodebírat aktuální kontext, a vytvořit tak další vlákna. Třída `http_reader` používá objekt [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) k omezení počtu vláken, která aplikace používá. Agent inicializuje vyrovnávací paměť s pevným počtem hodnot tokenu. Pro každou operaci stahování načte agent hodnotu tokenu z vyrovnávací paměti před spuštěním operace a po dokončení operace zapíše tuto hodnotu zpět do vyrovnávací paměti. Pokud je vyrovnávací paměť prázdná, agent počká na jednu z operací stahování, aby zapsala hodnotu zpět do vyrovnávací paměti.

Následující příklad omezuje počet souběžných úloh na dva, kolikrát je počet dostupných hardwarových vláken. Tato hodnota je dobrým výchozím bodem, který se použije při experimentování s předaným předplatným. Můžete použít hodnotu, která odpovídá konkrétnímu prostředí zpracování, nebo dynamicky měnit tuto hodnotu, aby odpovídala skutečnému zatížení.

[!code-cpp[concrt-download-oversubscription#1](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_1.cpp)]

Tento příklad vytvoří následující výstup na počítači, který má čtyři procesory:

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

Příklad může běžet rychleji, pokud je povoleno přepínání, protože se spouštějí další úlohy, zatímco jiné úlohy čekají na dokončení latentní operace.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `download-oversubscription.cpp` a potom v okně **příkazového řádku sady Visual Studio** spusťte jeden z následujících příkazů.

```cmd
cl.exe /EHsc /MD /D "_AFXDLL" download-oversubscription.cpp
cl.exe /EHsc /MT download-oversubscription.cpp
```

## <a name="robust-programming"></a>Robustní programování

Pokud už nebudete vyžadovat předplatné, vždycky ho zakažte. Vezměte v úvahu funkci, která nezpracovává výjimku, která je vyvolána jinou funkcí. Pokud nezakážete přepočet před vrácením funkce, budou všechny další paralelní práce také předávat k odběru aktuálního kontextu.

Pokud chcete omezit předplatné na daný obor, můžete použít vzor pro *získání prostředků* (RAII). V rámci vzoru RAII se datová struktura přiděluje v zásobníku. Tato struktura dat inicializuje nebo získá prostředek při jeho vytvoření a zničí nebo uvolní tento prostředek při zničení struktury dat. Vzor RAII zaručuje, že je destruktor volán před ukončením ohraničujícího oboru. Proto je prostředek správně spravován, pokud je vyvolána výjimka nebo když funkce obsahuje více příkazů `return`.

Následující příklad definuje strukturu s názvem `scoped_blocking_signal`. Konstruktor `scoped_blocking_signal` struktury umožňuje přeupisování a destruktor zakáže přepočet.

[!code-cpp[concrt-download-oversubscription#2](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_2.cpp)]

Následující příklad upravuje tělo metody `download` pro použití RAII k tomu, aby bylo zajištěno, že před vrácením funkce dojde k deaktivaci předplatného. Tento postup zajišťuje, že metoda `download` je bezpečná pro výjimky.

[!code-cpp[concrt-download-oversubscription#3](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_3.cpp)]

## <a name="see-also"></a>Viz také

[Kontexty](../../parallel/concrt/contexts.md)<br/>
[Context:: replacení – metoda](reference/context-class.md#oversubscribe)
