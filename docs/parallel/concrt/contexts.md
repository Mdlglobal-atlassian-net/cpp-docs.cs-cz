---
title: Kontexty
ms.date: 11/04/2016
helpviewer_keywords:
- contexts [Concurrency Runtime]
ms.assetid: 10c1d861-8fbb-4ba0-b2ec-61876b11176e
ms.openlocfilehash: 9eaf21a3d65ae891a48657de9d3e7aff78ce12b9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142193"
---
# <a name="contexts"></a>Kontexty

Tento dokument popisuje role kontextů v Concurrency Runtime. Vlákno, které je připojeno ke Scheduleru, je známé jako *kontext spuštění*nebo pouze *kontext*. Funkce [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait) a třída concurrency::[Context](../../parallel/concrt/reference/context-class.md) vám umožní řídit chování kontextů. K pozastavení aktuálního kontextu v zadaném čase použijte funkci `wait`. Třídu `Context` použijte v případě, že potřebujete větší kontrolu nad tím, kdy kontexty blok, odblokování a vracení nebo když chcete přehlásit odběr aktuálního kontextu.

> [!TIP]
> Concurrency Runtime poskytuje výchozí Plánovač, a proto není nutné ho v aplikaci vytvořit. Vzhledem k tomu, že Plánovač úloh pomáhá doladit výkon aplikací, doporučujeme začít s knihovnou [paralelních vzorů (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) nebo s [knihovnou asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) , pokud s Concurrency Runtime začínáte.

## <a name="the-wait-function"></a>Funkce Wait

Funkce [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait) spolupracuje s provedením aktuálního kontextu po zadaný počet milisekund. Modul runtime používá dobu zpracování k provádění dalších úkolů. Po uplynutí určeného času modul runtime znovu naplánuje kontext pro provedení. Proto funkce `wait` může pozastavit aktuální kontext déle než hodnota zadaná pro parametr `milliseconds`.

Předání hodnoty 0 (nula) pro parametr `milliseconds` způsobí, že modul runtime zastaví aktuální kontext, dokud nebudou všem ostatním aktivním kontextům přidělena příležitost k provedení práce. To vám umožní získat úkol pro všechny ostatní aktivní úlohy.

### <a name="example"></a>Příklad

Příklad, který používá funkci `wait` k získání aktuálního kontextu, a umožňuje tak spuštění jiných kontextů, naleznete v tématu [How to: use Schedule Groups to ovlivnit pořadí provádění](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

## <a name="the-context-class"></a>Třída kontextu

Třída concurrency::[Context](../../parallel/concrt/reference/context-class.md) poskytuje abstrakci programování pro kontext spuštění a nabízí dvě důležité funkce: schopnost spojit blokovat, odblokovat a získat aktuální kontext a možnost přerušit odběr aktuálního kontextu.

### <a name="cooperative-blocking"></a>Kooperativní blokování

Třída `Context` umožňuje blokovat nebo vracet aktuální kontext spuštění. Blokování nebo vracení je užitečné v případě, že aktuální kontext nemůže pokračovat, protože prostředek není k dispozici.

Metoda [Concurrency:: Context:: Block](reference/context-class.md#block) blokuje aktuální kontext. Blok, který je blokován, poskytuje své prostředky zpracování, aby modul runtime mohl provádět jiné úlohy. Metoda [Concurrency:: Context:: odblokování](reference/context-class.md#unblock) odblokuje blokovaný kontext. Metoda `Context::Unblock` musí být volána z jiného kontextu, než je ta, která se nazývá `Context::Block`. Modul runtime vyvolá [Concurrency:: context_self_unblock](../../parallel/concrt/reference/context-self-unblock-class.md) , pokud se kontext pokusí odblokovat sám sebe.

Pro kooperativní blokování a odblokování kontextu se obvykle volá [Concurrency:: Context:: CurrentContext](reference/context-class.md#currentcontext) , aby se načetl ukazatel na objekt `Context`, který je přidružený k aktuálnímu vláknu, a výsledek se uloží. Pak zavoláte metodu `Context::Block` pro blokování aktuálního kontextu. Později zavolejte `Context::Unblock` od samostatného kontextu pro odblokování blokovaného kontextu.

Je nutné, abyste poshodovali s každým párem volání `Context::Block` a `Context::Unblock`. Modul runtime vyvolá [Concurrency:: context_unblock_unbalanced](../../parallel/concrt/reference/context-unblock-unbalanced-class.md) při následném volání metody `Context::Block` nebo `Context::Unblock` bez odpovídajícího volání jiné metody. Nemusíte však volat `Context::Block` před voláním `Context::Unblock`. Například pokud jeden kontext volá `Context::Unblock` před tím, než jiný kontext volá `Context::Block` pro stejný kontext, zůstane tento kontext odblokován.

Metoda [Concurrency:: Context:: yield](reference/context-class.md#yield) vypočítá provádění, aby modul runtime mohl provádět jiné úlohy a následně přeplánovat kontext pro provedení. Když zavoláte metodu `Context::Block`, modul runtime neprovede přeplánování kontextu.

#### <a name="example"></a>Příklad

Příklad, který používá metody `Context::Block`, `Context::Unblock`a `Context::Yield` k implementaci třídy semaforu pro spolupráci, naleznete v tématu [How to: Use a Context a implementujte semafor družstva](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).

##### <a name="oversubscription"></a>Kompenzace

Výchozí Plánovač vytvoří stejný počet vláken, protože jsou k dispozici hardwarová vlákna. Pomocí předaného *předplatného* můžete vytvořit další vlákna pro dané hardwarové vlákno.

U výpočetně náročných operací se nadvýšení obvykle neškáluje, protože přináší další režii. U úloh, které mají vysokou latenci, například čtení dat z disku nebo ze síťového připojení, může nadvýšení služby zlepšit celkovou efektivitu některých aplikací.

> [!NOTE]
> Možnost předaného předplatného Povolte jenom z vlákna, které vytvořila Concurrency Runtime. Při volání z vlákna, které nebylo vytvořeno modulem runtime (včetně hlavního vlákna), nemá předplatné žádný vliv.

Chcete-li v aktuálním kontextu povolit přeměnu, zavolejte metodu [Concurrency:: Context::](reference/context-class.md#oversubscribe) resubscription s parametrem `_BeginOversubscription` nastaveným na **hodnotu true**. Pokud povolíte přeregistraci na vlákně, které bylo vytvořeno Concurrency Runtime, způsobí to, že modul runtime vytvoří jedno další vlákno. Po všech úkolech, které vyžadují dokončení přeplacení, zavolejte `Context::Oversubscribe` s parametrem `_BeginOversubscription` nastaveným na **hodnotu false**.

V aktuálním kontextu můžete více než jeden odběr povolit několikrát, ale je nutné ho zakázat stejným počtem, kolikrát ho povolíte. Předané předplatné může být také vnořené. To znamená, že úkol, který je vytvořen jinou úlohou, která používá předané předplatné, může také přeodebírat svůj kontext. Nicméně pokud vnořená úloha i její nadřazená položka patří do stejného kontextu, pouze vnější volání `Context::Oversubscribe` způsobí vytvoření dalšího vlákna.

> [!NOTE]
> Modul runtime vyvolá [Concurrency:: invalid_oversubscribe_operation](../../parallel/concrt/reference/invalid-oversubscribe-operation-class.md) , pokud je před povolením zakázané předplatné.

###### <a name="example"></a>Příklad

Příklad, který používá přebírání dat k posunu latence, která je způsobená čtením dat ze síťového připojení, najdete v tématu [How to: use resubscriptions to a offset](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

## <a name="see-also"></a>Viz také

[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Postupy: Použití skupin plánů k ovlivnění pořadí provádění](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)<br/>
[Postupy: Použití třídy kontextu pro implementaci semaforu pro spolupráci](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[Postupy: Kompenzace latence vytvořením nadbytečného počtu vláken](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)
