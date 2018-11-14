---
title: Zrušení v knihovně PPL
ms.date: 11/04/2016
helpviewer_keywords:
- parallel algorithms, canceling [Concurrency Runtime]
- canceling parallel algorithms [Concurrency Runtime]
- parallel tasks, canceling [Concurrency Runtime]
- cancellation in the PPL
- parallel work trees [Concurrency Runtime]
- canceling parallel tasks [Concurrency Runtime]
ms.assetid: baaef417-b2f9-470e-b8bd-9ed890725b35
ms.openlocfilehash: b1a762f97cf144c39043203dbf68d927b2cbd0e4
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327418"
---
# <a name="cancellation-in-the-ppl"></a>Zrušení v knihovně PPL

Tento dokument popisuje roli zrušení v knihovna paralelních vzorů (PPL), jak zrušení paralelně prováděných úloh a jak určit, kdy zrušení paralelně prováděných úloh.

> [!NOTE]
>  Modul runtime používá k implementaci zrušení zpracování výjimek. Catch nebo zpracování těchto výjimek v kódu. Kromě toho doporučujeme psát kód bezpečnost výjimek v těla funkcí pro své úkoly. Například můžete použít *získání prostředků je inicializace* vzorek (RAII), ujistěte se, že prostředky jsou správně zpracují, když dojde k výjimce v těle úlohy. Kompletní příklad, který používá vzor RAII pro vyčištění prostředků v zrušitelný úkol, naleznete v tématu [návod: odebrání práce z uživatelského rozhraní vlákna](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md).

## <a name="key-points"></a>Klíčové body

- Zrušení je spolupráce a zahrnuje koordinaci mezi kód, který požaduje zrušení a úlohu, která bude reagovat na zrušení.

- Pokud je to možné, použijte tokeny zrušení pro zrušení pracovní. [Concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) třída definuje token zrušení.

- Při použití tokenů zrušení, použijte [concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) metoda k iniciaci zrušení a [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) funkce reagovat na zrušení. Použití [concurrency::cancellation_token::is_canceled](reference/cancellation-token-class.md#is_canceled) metodu ke kontrole, jestli jakoukoliv jinou úlohu požadoval zrušení.

- Zrušení se nevyskytuje okamžitě. I když nových neběží, pokud se zrušila, úkolu nebo skupiny úkolů, aktivních pracovních musí vyhledat a reagovat na zrušení.

- Pokračování založené na hodnotách zdědí token zrušení svého předchozího úkolu. Pokračování podle úloh nikdy zdědí token svého předchozího úkolu.

- Použití [concurrency::cancellation_token:: žádný](reference/cancellation-token-class.md#none) metody při volání konstruktoru nebo funkce, která přijímá `cancellation_token` objekt, ale nechcete, aby operace zrušit. Také pokud nelze předat token zrušení pro [concurrency::task](../../parallel/concrt/reference/task-class.md) konstruktor nebo [concurrency::create_task](reference/concurrency-namespace-functions.md#create_task) funkce, tento úkol není zrušitelný.

##  <a name="top"></a> V tomto dokumentu

- [Paralelně prováděné stromy](#trees)

- [Zrušení paralelních úloh](#tasks)

    - [Zrušení paralelně prováděných úloh pomocí tokenu zrušení](#tokens)

    - [Pomocí metody zrušení paralelně prováděných cancel](#cancel)

    - [Zrušení paralelně prováděných úloh pomocí výjimek](#exceptions)

- [Zrušení paralelních algoritmů](#algorithms)

- [Kdy nepoužívat zrušení](#when)

##  <a name="trees"></a> Paralelně prováděné stromy

PPL používá úloh a skupin úloh pro správu jemně úkoly a výpočty. Skupiny úloh do formuláře můžete vnořit *stromů* paralelní práce. Následující obrázek znázorňuje stromové struktuře paralelní práce. Na tomto obrázku `tg1` a `tg2` reprezentaci skupin úkolů; `t1`, `t2`, `t3`, `t4`, a `t5` představují práci, kterou vytvořili skupiny úloh.

![Stromové struktuře paralelní práce](../../parallel/concrt/media/parallelwork_trees.png "parallelwork_trees")

Následující příklad ukazuje kód, který je potřebný k vytvoření stromu na obrázku. V tomto příkladu `tg1` a `tg2` jsou [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objekty; `t1`, `t2`, `t3`, `t4`, a `t5` jsou [concurrency::task_handle](../../parallel/concrt/reference/task-handle-class.md) objekty.

[!code-cpp[concrt-task-tree#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_1.cpp)]

Můžete také použít [concurrency::task_group](reference/task-group-class.md) třídy za účelem vytvoření podobné pracovní stromu. [Concurrency::task](../../parallel/concrt/reference/task-class.md) třídy také podporuje pojem stromu práce. Ale `task` stromu je strom závislostí. V `task` stromu budoucí funguje dokončena po aktuální práci. Ve stromové struktuře skupiny úloh interní pracovní dokončí než vnější práce. Další informace o rozdílech mezi úloh a skupin úloh naleznete v tématu [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

[[Horní](#top)]

##  <a name="tasks"></a> Zrušení paralelních úloh

Zrušení paralelně prováděných úloh několika způsoby. Upřednostňovaným způsobem je použít token zrušení. Skupiny úloh také podporu [concurrency::task_group::cancel](reference/task-group-class.md#cancel) metoda a [Concurrency::structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) metody. Posledním způsobem je vyvolat výjimku v těle funkce pracovních úkolů. Bez ohledu na to, jakou metodu zvolíte pochopit, že zrušení nedojde okamžitě. I když nových neběží, pokud se zrušila, úkolu nebo skupiny úkolů, aktivních pracovních musí vyhledat a reagovat na zrušení.

Další příklady, které zrušení paralelních úloh, naleznete v tématu [návod: připojení pomocí úloh a žádostí XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md), [postupy: použití zrušení přerušení paralelní smyčky](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md), a [postupy: použití Zpracování výjimek pro přerušení paralelní smyčky](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

###  <a name="tokens"></a> Zrušení paralelně prováděných úloh pomocí tokenu zrušení

`task`, `task_group`, A `structured_task_group` třídy podporují zrušení prostřednictvím použití tokenů zrušení. Definuje PPL [concurrency::cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md) a [concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) třídy pro tento účel. Při použití token zrušení pro zrušení pracovní modul runtime nelze spustit novou práci, která si předplatí tento token. Můžete použít práci, která je již aktivní [is_canceled –](../../parallel/concrt/reference/cancellation-token-class.md#is_canceled) členskou funkci monitorování token zrušení a zastaví, jakmile ho může.

Abyste zahájili zrušení, zavolejte [concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) metody. Můžete tak reagovat na zrušení následujícími způsoby:

- Pro `task` objekty, použijte [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) funkce. `cancel_current_task` Zruší aktuální úloha a všechny jeho pokračování založené na hodnotách. (Nezruší zrušení *token* přidružený k úkolu nebo jeho pokračování.)

- U skupin úloh a paralelní algoritmy, použijte [concurrency::is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) funkce zjistit zrušení a vrátit co nejdříve z těla úkolu, když se tato funkce vrátí **true** . (Nevolejte `cancel_current_task` ze skupiny úkolů.)

Následující příklad ukazuje první základní vzor pro zrušení úlohy. Tělo úkolu příležitostně zkontroluje zrušení uvnitř smyčka.

[!code-cpp[concrt-task-basic-cancellation#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_2.cpp)]

`cancel_current_task` Funkce vyvolá výjimku, proto není potřeba explicitně vrátit z aktuální smyčku nebo funkce.

> [!TIP]
> Alternativně můžete volat [concurrency::interruption_point](reference/concurrency-namespace-functions.md#interruption_point) místo funkce `cancel_current_task`.

Je potřeba volat `cancel_current_task` kdy můžete reagovat na zrušení protože přechází na zrušeném stavu úlohy. Pokud jste již v rané fázi vrátíte namísto volání metody `cancel_current_task`, operace přejde do dokončeného stavu a spouštějí se všechny pokračování založené na hodnotách.

> [!CAUTION]
> Nikdy nevyvolají `task_canceled` z vašeho kódu. Volání `cancel_current_task` místo.

Pokud úkol skončí ve zrušeném stavu [Concurrency::Task:: Get](reference/task-class.md#get) vyvolá metoda výjimku [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md). (A naopak, [Concurrency::Task:: wait](reference/task-class.md#wait) vrátí [task_status::canceled](reference/concurrency-namespace-enums.md#task_group_status) a nevyvolá.) Následující příklad ukazuje toto chování pro pokračování podle úloh. Pokračování podle úloh je volána vždy, i když je předchozí úloha se zruší.

[!code-cpp[concrt-task-canceled#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_3.cpp)]

Proto, že pokračování založené na hodnotách zdědí token svého předchozího úkolu, pokud byly vytvořené pomocí explicitní tokenu, pokračování okamžitě zadejte zrušeném stavu i v případě, že je stále provádí předchozí úlohy. Proto jakékoli výjimce, která je vyvolána předchozí úlohou od zrušení předplatného se nerozšíří do pokračujících úloh. Zrušení vždy přepíše stav předchozí úlohy. Následující příklad se podobá předchozí, ale ukazuje chování pro pokračování založené na hodnotách.

[!code-cpp[concrt-task-canceled#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_4.cpp)]

> [!CAUTION]
> Pokud nelze předat token zrušení pro `task` konstruktor nebo [concurrency::create_task](reference/concurrency-namespace-functions.md#create_task) funkce, tento úkol není zrušitelný. Kromě toho je nutné předat stejný token zrušení do konstruktoru všech vnořených úloh (to znamená, úkoly, které jsou vytvořeny v těle jiný úkol) k zrušení všech úloh současně.

Můžete chtít spustit libovolný kód, když je zrušen token zrušení. Například, pokud uživatel klikne **zrušit** tlačítko v uživatelském rozhraní na tlačítko Storno, může zakázat toto tlačítko, dokud uživatel spustí jiná operace. Následující příklad ukazuje způsob použití [concurrency::cancellation_token::register_callback](reference/cancellation-token-class.md#register_callback) metody pro registraci funkce zpětného volání, která se spustí, když je zrušen token zrušení.

[!code-cpp[concrt-task-cancellation-callback#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_5.cpp)]

Dokument [paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md) vysvětluje rozdíl mezi pokračování založené na hodnotách a založený na úlohách. Pokud nezadáte `cancellation_token` objektu úkolu pokračování, pokračování token rušení, který dědí z předchozí úlohy následujícími způsoby:

- Pokračování založené na hodnotách vždy zdědí token zrušení předchozího úkolu.

- Pokračování podle úloh nikdy zdědí token zrušení předchozího úkolu. Jediným způsobem, aby bylo možné zrušit pokračování podle úloh je explicitně předat token zrušení.

Těchto projevů nejsou ovlivněny chybnou úkolu (to znamená, vyvolá výjimku). V takovém případě se zrušila, pokračování založené na hodnotách; pokračování podle úloh není zrušena.

> [!CAUTION]
> Úloha, která je vytvořena v jiném úkolu (jinými slovy, vnořené úlohy) nedědí token zrušení nadřazeného úkolu. Pouze pokračování založené na hodnotách zdědí token zrušení svého předchozího úkolu.

> [!TIP]
> Použití [concurrency::cancellation_token:: žádný](reference/cancellation-token-class.md#none) metody při volání konstruktoru nebo funkce, která přijímá `cancellation_token` objektů a nechcete, aby operace zrušit.

Můžete také zadat token zrušení pro konstruktor třídy `task_group` nebo `structured_task_group` objektu. Důležitou součástí to je, že podřízené skupiny úloh zdědí tento token zrušení. Příklad, který tento koncept demonstruje pomocí [concurrency::run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) spouštění pro volání funkce `parallel_for`, naleznete v tématu [zrušení paralelních algoritmů](#algorithms) dále v tomto dokument.

[[Horní](#top)]

#### <a name="cancellation-tokens-and-task-composition"></a>Tokeny zrušení a skládání úloh

[Concurrency::when_all](reference/concurrency-namespace-functions.md#when_all) a [concurrency::when_any](reference/concurrency-namespace-functions.md#when_all) funkcí můžete vytvořit více úkolů k implementaci běžných vzorů. Tato část popisuje, jak tyto funkce pracují s tokeny zrušení.

Když zadáte token zrušení pro buď `when_all` a `when_any` fungovala, že funkce zruší pouze v případě, že je zrušen token zrušení, nebo když jeden účastník úkoly skončí ve zrušeném stavu nebo vyvolá výjimku.

`when_all` Funkce dědí z každý úkol, který lze kombinovat celkovou operaci, pokud nezadáte token zrušení do ní token zrušení. Úloha, která je vrácena z `when_all` zruší se, když některý z těchto tokenů se zruší a alespoň jeden z účastníků úkolů ještě nezačala nebo je spuštěná. Podobného chování nastane, pokud jeden z úkolů dojde k výjimce – úloha, která je vrácena z `when_all` je okamžitě bylo zrušeno s tuto výjimku.

Modul runtime zvolí token zrušení pro úlohu, která je vrácena z `when_any` fungovat po dokončení této úlohy. Je-li žádný účastníka úlohy dokončení ve stavu dokončení a vyvolá výjimku, jeden nebo více úkolů, jednu z úloh, které vyvolala je vybrán k dokončení `when_any` a jeho token je vybrán jako token pro poslední úlohu. Pokud více než jeden úkol skončí ve dokončenou stavu, úloha, která je vrácena z `when_any` úkol skončí ve stavu dokončení. Modul runtime pokusí vyberte dokončené úlohy, jehož token není zrušena v době dokončení tak, aby úloha, která je vrácena z `when_any` není zrušena okamžitě i v případě, že ostatní spuštěné úlohy může dokončit později.

[[Horní](#top)]

###  <a name="cancel"></a> Pomocí metody zrušení paralelně prováděných cancel

[Concurrency::task_group::cancel](reference/task-group-class.md#cancel) a [Concurrency::structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) nastavit skupinu úloh pro zrušeném stavu. Po zavolání `cancel`, skupina úloh nespustí budoucí úlohy. `cancel` Metody mohou být volány více podřízených úloh. Zrušené úlohy způsobí, že [Concurrency::task_group:: wait](reference/task-group-class.md#wait) a [Concurrency::structured_task_group:: wait](reference/structured-task-group-class.md#wait) metody k vrácení [concurrency::canceled](reference/concurrency-namespace-enums.md#task_group_status).

Pokud dojde ke zrušení skupiny úloh, můžete aktivovat volání z každé podřízené úlohy do modulu runtime *bodu přerušení*, což způsobí, že modul runtime throw a catch – typ vnitřní výjimky pro zrušení aktivních úloh. Modulu Runtime souběžnosti nedefinuje konkrétní přerušení body; můžete k nim dojde v kterémkoli volání modulu runtime. Modul runtime musí zpracovat výjimky, které se vyvolá, aby bylo možné provést zrušení. Proto není zpracovat Neznámý výjimky v těle úlohy.

Pokud podřízená úloha provede časově náročná operace a nevolá do modulu runtime, musí pravidelně kontrolovat zrušení a ukončete včas. Následující příklad ukazuje jeden způsob, jak zjistit, když se zruší práce. Úloha `t4` zruší skupinu nadřazeného úkolu, když dojde k chybě. Úloha `t5` čas od času volání `structured_task_group::is_canceling` metodu ke kontrole pro zrušení. Pokud dojde ke zrušení nadřazené skupiny úloh, úkolů `t5` vytiskne zprávu a ukončí.

[!code-cpp[concrt-task-tree#6](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_6.cpp)]

Tento příklad kontroluje pro zrušení na každých 100<sup>th</sup> iteraci smyčky úloh. Frekvence, se kterým můžete zkontrolovat zrušení závisí na množství práce, kterou provádí vaše úlohy a jak rychle je potřeba pro úlohy reagovat na zrušení.

Pokud nemáte přístup k nadřazeného objektu skupiny úloh, zavolejte [concurrency::is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) funkce určit, zda je zrušena skupinu nadřazeného úkolu.

`cancel` Metoda má vliv pouze podřízených úloh. Například, pokud zrušíte skupiny úloh `tg1` obrázku stromové struktuře paralelní práce, všechny úlohy ve stromové struktuře (`t1`, `t2`, `t3`, `t4`, a `t5`) se to týká. Pokud zrušíte skupiny vnořené úlohy `tg2`, pouze úlohy `t4` a `t5` se to týká.

Při volání `cancel` metoda, všechny podřízené úlohy také zrušení skupiny. Zrušení neovlivní žádné nadřazené skupiny úloh ve stromové struktuře paralelní práce. Následující příklady ukazují to vytvořením obrázek stromu paralelní práci.

První z těchto příkladů vytvoří pracovní funkce pro úlohu `t4`, což je podřízenou skupinu úloh `tg2`. Pracovní funkce volá funkci `work` ve smyčce. Pokud některý volání `work` selže, úloha zruší její nadřazenou skupinu úloh. To způsobí, že skupina úloh `tg2` zadat zrušeném stavu, ale nezruší skupina úloh `tg1`.

[!code-cpp[concrt-task-tree#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_7.cpp)]

Tento druhý příklad vypadá podobně jako první z nich, s tím rozdílem, že úloha zruší skupina úloh `tg1`. Tato akce ovlivní všechny úlohy ve stromové struktuře (`t1`, `t2`, `t3`, `t4`, a `t5`).

[!code-cpp[concrt-task-tree#3](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_8.cpp)]

`structured_task_group` Třída není bezpečná pro vlákno. Proto podřízená úloha, která volá metodu svého nadřazeného objektu `structured_task_group` objekt vytváří neurčené chování. Výjimky z tohoto pravidla jsou `structured_task_group::cancel` a [Concurrency::structured_task_group:: is_canceling](reference/structured-task-group-class.md#is_canceling) metody. Podřízená úloha může tyto metody volat a zrušit skupinu nadřazeného úkolu a zkontrolovat zrušení.

> [!CAUTION]
>  I když používáte token zrušení pro zrušení práci, která se provádí pomocí skupiny úloh, na kterém běží jako podřízený objekt `task` objektu nelze použít `task_group::cancel` nebo `structured_task_group::cancel` metody zrušit `task` objekty, které běží ve skupině úloh.

[[Horní](#top)]

###  <a name="exceptions"></a> Zrušení paralelně prováděných úloh pomocí výjimek

Použití tokenů zrušení a `cancel` metody jsou účinnější než na zrušení paralelně prováděných úloh stromu zpracování výjimek. Tokeny zrušení a `cancel` metodu zrušení úlohy a všechny podřízené úkoly způsobem shora dolů. Naopak zpracování výjimek funguje způsobem zdola nahoru a musíte zrušit každou podřízenou skupinu úloh nezávisle na sobě jako výjimka šíří, směrem nahoru. Téma [zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md) vysvětluje, jak Concurrency Runtime používá k předání chyby výjimky. Ale ne všechny výjimky signalizují chybu. Například vyhledávací algoritmus může zrušit jeho přidružené úlohy, najde-výsledek. Jak už bylo zmíněno dříve, zpracování výjimek je však méně efektivní než při použití `cancel` metodu zrušení paralelně prováděných úloh.

> [!CAUTION]
>  Doporučujeme používat výjimky zrušení paralelně prováděných pouze v případě potřeby. Tokeny zrušení a skupiny úloh `cancel` metody jsou efektivnější a méně náchylná k chybě.

Při vyvolání výjimky v textu, který předáte pracovní funkce pro skupinu úloh, modul runtime ukládá tuto výjimku a zařadí výjimka, která má kontext, který se čeká na skupinu úloh na dokončení. Stejně jako u `cancel` metody, modul runtime zahodí všechny úkoly, které ještě nebyly spuštěny a nepřijímá nové úkoly.

Tento třetí příklad se podobá druhý, s výjimkou tento úkol `t4` vyvolá výjimku zrušení skupiny úloh `tg2`. Tento příklad používá `try` - `catch` bloku zkontrolovat zrušení při skupina úloh `tg2` čeká na dokončení podřízených úloh. Podobně jako v prvním příkladu, způsobí to, že skupina úloh `tg2` zadat zrušeném stavu, ale nezruší skupina úloh `tg1`.

[!code-cpp[concrt-task-tree#4](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_9.cpp)]

Zpracování výjimek pro zrušení stromu celý pracovní tento čtvrtý příkladu. V příkladu zachytí výjimku při úkol skupiny `tg1` čeká na dokončení místo při jeho podřízených úloh, úkolů skupiny `tg2` počká na jeho podřízené úlohy. Podobně jako v druhém příkladu to způsobí, že obě úlohy ve stromové struktuře `tg1` a `tg2`, zadat zrušeném stavu.

[!code-cpp[concrt-task-tree#5](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_10.cpp)]

Vzhledem k tomu, `task_group::wait` a `structured_task_group::wait` metody vyvolání v případě, že podřízená úloha vyvolá výjimku, neobdržíte návratovou hodnotu z nich.

[[Horní](#top)]

##  <a name="algorithms"></a> Zrušení paralelních algoritmů

Paralelní algoritmy v knihovně PPL, například `parallel_for`, vytvářet skupiny úkolů. Proto řadu stejné postupy můžete použít pro zrušení paralelních algoritmů.

Následující příklady znázorňují několik způsobů, jak zrušit paralelního algoritmu.

V následujícím příkladu `run_with_cancellation_token` funkce má být volána `parallel_for` algoritmus. `run_with_cancellation_token` Funkce přijme token jako argument zrušení a volá zadaný pracovní funkce synchronně. Protože paralelní algoritmy jsou postavené na úkoly, zdědí token zrušení nadřazeného úkolu. Proto `parallel_for` můžou reagovat na zrušení.

[!code-cpp[concrt-cancel-parallel-for#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_11.cpp)]

V následujícím příkladu [Concurrency::structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait) metoda se má volat `parallel_for` algoritmus. `structured_task_group::run_and_wait` Metoda čeká na dokončení zadané úlohy. `structured_task_group` Objektu umožňuje pracovní funkce pro zrušení úkolu.

[!code-cpp[concrt-task-tree#7](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_12.cpp)]

Tento příklad vytvoří následující výstup.

```Output
The task group status is: canceled.
```

Následující příklad používá pro zrušení zpracování výjimek `parallel_for` smyčky. Modul runtime zařazuje výjimka, která má kontext volání.

[!code-cpp[concrt-task-tree#9](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_13.cpp)]

Tento příklad vytvoří následující výstup.

```Output
Caught 50
```

Následující příklad používá ke koordinaci zrušení v příznak logické hodnoty `parallel_for` smyčky. Každý úkol spustí, protože v tomto příkladu nepoužívá `cancel` zpracování metody nebo výjimky zrušit celkové sady úloh. Proto tato technika může mít více nadměrnou výpočetní zátěž než mechanismus kterém jste předplatné zrušili.

[!code-cpp[concrt-task-tree#8](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_14.cpp)]

Každá metoda zrušení má výhody oproti ostatním. Zvolte metodu, která odpovídá vašim konkrétním potřebám.

[[Horní](#top)]

##  <a name="when"></a> Kdy nepoužívat zrušení

Použití zrušení je vhodné, když každého člena skupiny souvisejících úloh můžete ukončit včas. Existují však některé scénáře, kde zrušení nemusí být vhodné pro vaši aplikaci. Například protože zrušení úlohy je kooperativní, celkové sady úloh nebude zrušit, pokud se zablokuje všechny jednotlivé úlohy. Například pokud dosud nebyl spuštěn jeden úkol, ale odblokuje jiné aktivní úlohy, se nespustí, pokud skupina úloh se zruší. To může způsobit zablokování aplikace. Druhý příklad, kde nemusí být vhodné použít zrušení při zrušení úkolu, ale jeho podřízených úloh provádí důležité operace, jako je například uvolnění prostředku. Protože celé sadě úkolů dojde ke zrušení při zrušení nadřazeného úkolu, tato operace nebude spuštěno. Příklad, který ilustruje tento bod, najdete v článku [porozumění jak zrušení a výjimky zpracování odstraňování objektů ovlivnit](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) kapitoly osvědčené postupy v paralelních vzorcích knihovny tématu.

[[Horní](#top)]

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Postupy: Přerušení paralelní smyčky pomocí zrušení](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)|Ukazuje, jak můžete implementovat paralelního vyhledávacího algoritmu zrušení.|
|[Postupy: Přerušení paralelní smyčky pomocí zpracování výjimek](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Ukazuje způsob použití `task_group` třídu pro zápis vyhledávacího algoritmu pro základní stromové struktury.|
|[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Popisuje způsob, jakým modul runtime zpracovává výjimky, které jsou vyvolány skupiny úloh, lehkých úloh a asynchronních agentů a jak reagovat na výjimky ve vašich aplikacích.|
|[Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|Popisuje, jak se úlohy týkají u skupin úloh a použití nestrukturovaných a strukturovaných úloh ve svých aplikacích.|
|[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)|Popisuje paralelní algoritmy, které provádějí práci současně na kolekce dat|
|[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Přehled knihovny Ppl.|

## <a name="reference"></a>Odkaz

[task – třída (Concurrency Runtime)](../../parallel/concrt/reference/task-class.md)

[cancellation_token_source – třída](../../parallel/concrt/reference/cancellation-token-source-class.md)

[cancellation_token – třída](../../parallel/concrt/reference/cancellation-token-class.md)

[task_group – třída](reference/task-group-class.md)

[structured_task_group – třída](../../parallel/concrt/reference/structured-task-group-class.md)

[parallel_for – funkce](reference/concurrency-namespace-functions.md#parallel_for)

