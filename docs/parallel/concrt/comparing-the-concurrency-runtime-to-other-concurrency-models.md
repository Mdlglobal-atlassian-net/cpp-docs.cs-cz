---
title: Porovnání modelu Concurrency Runtime s jinými modely souběžného zpracování
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, compared to other models
ms.assetid: d8b9a1f4-f15f-43c3-a5b4-c0991edf9c86
ms.openlocfilehash: 5bc6691f6d0b166bb3084091ee6af70474937568
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422253"
---
# <a name="comparing-the-concurrency-runtime-to-other-concurrency-models"></a>Porovnání modelu Concurrency Runtime s jinými modely souběžného zpracování

Tento dokument popisuje rozdíly mezi funkcemi a programovacími modely Concurrency Runtime a dalších technologií. Když pochopíte, jak výhody Concurrency Runtime porovnávají s výhodami jiných programovacích modelů, můžete vybrat technologii, která nejlépe splňuje požadavky vašich aplikací.

Pokud aktuálně používáte jiný programovací model, jako je například fond vláken systému Windows nebo OpenMP, existují situace, kdy může být vhodné provést migraci na Concurrency Runtime. Například téma [migrace z OpenMP na Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md) popisuje, kdy může být vhodné migrovat z openmp do Concurrency Runtime. Pokud jste ale spokojeni s výkonem aplikace a aktuální podporou ladění, migrace se nevyžaduje.

Můžete využít výhody funkcí a produktivity Concurrency Runtime k doplnění existující aplikace, která používá jiný model souběžnosti. Concurrency Runtime nemůže zaručit vyrovnávání zatížení, pokud více plánovačů úloh soutěží o stejné výpočetní prostředky. Pokud se ale úlohy nepřekrývají, je tento efekt minimální.

## <a name="top"></a>Řezů

- [Porovnání nepřerušeného plánování s kooperativním plánováním](#models)

- [Porovnání Concurrency Runtime s rozhraním API systému Windows](#winapi)

- [Porovnání Concurrency Runtime s OpenMP](#openmp)

## <a name="models"></a>Porovnání nepřerušeného plánování s kooperativním plánováním

Modely bezpostupné modelu a plánování spolupráce jsou dva běžné způsoby, jak povolit více úloh sdílení výpočetních prostředků, například procesorů nebo hardwarových vláken.

### <a name="preemptive-and-cooperative-scheduling"></a>Preventivní a kooperativní plánování

Beznabídkovým *plánováním* je mechanismus založený na prioritách, který poskytuje každému úkolu výhradní přístup k výpočetnímu prostředku za dané časové období a pak přepne na jiný úkol. Při práci s více úlohami, jako je Windows, se běžně používá přerušení plánování. *Kooperativní plánování* je mechanismus, který poskytuje všem úlohám výhradní přístup k výpočetnímu prostředku, dokud úloha neskončí nebo dokud úloha nevrátí svůj přístup k prostředku. Concurrency Runtime používá kooperativní plánování spolu s nespojitým plánovačem operačního systému za účelem dosažení maximálního využití prostředků zpracování.

### <a name="differences-between-preemptive-and-cooperative-schedulers"></a>Rozdíly mezi bezoperativními a kooperativními plánovači

Bezstavové plánovače hledají více vláken, která mají stejný přístup k výpočetních prostředků, aby bylo zajištěno, že každé vlákno provede průběh. V počítačích, které mají mnoho výpočetních prostředků, se zajištění spravedlivého přístupu bude méně problematické. Nicméně zajištění efektivního využití prostředků bude problematickější.

Nepřerušený Plánovač v režimu jádra vyžaduje, aby kód aplikace při rozhodování o plánování spoléhat na operační systém. V opačném případě Plánovač spolupráce v uživatelském režimu umožňuje kódu aplikace vytvářet vlastní rozhodnutí o plánování. Vzhledem k tomu, že kooperativní plánování umožňuje aplikaci provádět mnoho rozhodnutí, snižuje se množství režie, která je přidružená k synchronizaci v režimu jádra. Kooperativní Plánovač obvykle odloží rozhodnutí o plánování do jádra operačního systému, pokud nemá žádnou jinou práci, kterou by bylo možné naplánovat. V případě, že dojde k blokující operaci, která je předávána jádru, Plánovač spolupráce se také odloží do plánovače operačního systému, ale tato operace není oznámena plánovači v uživatelském režimu.

### <a name="cooperative-scheduling-and-efficiency"></a>Plánování a efektivita spolupráce

U nefunkčního plánovače se bude shodovat veškerá práce, která má stejnou úroveň priority. Nepřepnutý Plánovač obvykle plánuje vlákna v pořadí, ve kterém jsou vytvořeny. Beznabídkový Plánovač navíc poskytuje každé vlákno časové řezy v kruhovém dotazování na základě priority vlákna. I když tento mechanismus poskytuje spravedlivě (každé vlákno předává pokrok), dostává se za nějaké náklady. Například mnohé algoritmy náročné na výpočetní výkon nevyžadují spravedlivé. Místo toho je důležité, aby související úlohy byly dokončeny v nejméně celkovém čase. Plánování spolupráce umožňuje aplikaci efektivněji naplánovat práci. Zvažte například aplikaci, která má mnoho vláken. Plánování vláken, která nesdílejí prostředky pro souběžné spouštění, můžou snížit režijní náklady na synchronizaci a zvýšit tak efektivitu. Dalším efektivním způsobem, jak plánovat úlohy, je spustit kanály úloh (kde každá úloha funguje na výstupu předchozí) na stejném procesoru, aby vstup každé fáze kanálu byl již načten do mezipaměti paměti.

### <a name="using-preemptive-and-cooperative-scheduling-together"></a>Použití nespojitého a kooperativního plánování

Plánování spolupráce neřeší všechny problémy s plánováním. Například úlohy, které se poměrně nepočítají jiným úlohám, mohou využívat všechny dostupné výpočetní prostředky a zabránit v provádění dalších úkolů. Concurrency Runtime využívá výhody efektivního plánování v rámci spolupráce, které doplňují záruky při nerovnosti plánování. Ve výchozím nastavení Concurrency Runtime poskytuje Plánovač spolupráce, který využívá algoritmus pro efektivní distribuci práce mezi výpočetními prostředky. Plánovač Concurrency Runtime také spoléhá na nepřesný Plánovač operačního systému, aby bylo možné poměrně distribuovat prostředky mezi aplikacemi. Můžete také vytvořit vlastní plánovače a zásady plánovače ve svých aplikacích, abyste vytvořili jemně odstupňovanou kontrolu nad prováděním vlákna.

[[Nahoře](#top)]

## <a name="winapi"></a>Porovnání Concurrency Runtime s rozhraním API systému Windows

Programovací rozhraní aplikace systému Microsoft Windows, které se obvykle označuje jako rozhraní API systému Windows (dříve označované jako Win32), poskytuje programovací model, který ve vašich aplikacích povoluje souběžnost. Concurrency Runtime vytváří rozhraní Windows API, které poskytuje další programovací modely, které nejsou k dispozici v podkladovém operačním systému.

Concurrency Runtime vytváří v modelu vláken rozhraní Windows API k provádění paralelní práce. Používá taky mechanismy správy paměti rozhraní Windows API a místních úložišť pro vlákna. V systémech Windows 7 a Windows Server 2008 R2 používá podporu rozhraní Windows API pro plánovatelná vlákna a počítače, které mají více než 64 hardwarových vláken. Concurrency Runtime rozšiřuje model rozhraní Windows API tím, že poskytuje Plánovač úloh pro spolupráci a algoritmus pro pracovní krádeži, který maximalizuje používání výpočetních prostředků a povoluje více souběžných instancí plánovače.

### <a name="programming-languages"></a>Programovací jazyky

Rozhraní Windows API používá programovací jazyk C k vystavení programovacího modelu. Concurrency Runtime poskytuje C++ programovací rozhraní, které využívá nejnovější funkce v C++ jazyce. Například lambda funkce poskytují pro definování paralelních pracovních funkcí výstižný typově bezpečný mechanismus. Další informace o nejnovějších C++ funkcích, které používá Concurrency Runtime, najdete v tématu [Přehled](../../parallel/concrt/asynchronous-message-blocks.md).

### <a name="threads-and-thread-pools"></a>Vlákna a fondy vláken

Hlavním mechanismem souběžnosti v rozhraní API systému Windows je vlákno. K vytváření vláken obvykle používáte funkci [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) . I když jsou vlákna relativně snadno vytvářet a používat, operační systém přiděluje značnou dobu a další prostředky pro jejich správu. I když je u každého vlákna zaručeno, že získá stejnou dobu spuštění jako jakékoli jiné vlákno na stejné úrovni priority, je nutné, abyste vytvořili dostatečně velké úkoly. U menších nebo podrobnějších úloh může režijní náklady spojené s souběžnou analýzou využít výhod souběžného spouštění úkolů.

Fondy vláken představují jeden ze způsobů, jak snížit náklady na správu vláken. Vlastní fondy vláken a implementace fondu vláken, které poskytuje rozhraní API systému Windows, umožňují efektivně souběžně běžet s malými pracovními položkami. Fond vláken systému Windows udržuje pracovní položky ve frontě first-in, First-out (FIFO). Každá pracovní položka je spuštěna v pořadí, ve kterém byla přidána do fondu.

Concurrency Runtime implementuje algoritmus pro pracovní krádeži pro rozšiřování mechanismu plánování FIFO. Algoritmus přesouvá úlohy, které ještě nebyly spuštěny, do vláken, která vychází z pracovních položek. I když je možné vyrovnávat zatížení algoritmem pracovní krádeže, může také dojít k přeřazení pracovních položek. Tento proces přeřazení může způsobit, že se pracovní položka spustí v jiném pořadí, než bylo odesláno. To je užitečné u rekurzivních algoritmů, kde je lepší pravděpodobnost, že data jsou sdílena mezi novějšími úlohami než mezi staršími. Získání nových položek, které se mají spustit jako první, znamená menší počet přístupů do mezipaměti a pravděpodobně méně chyb stránek.

V perspektivě operačního systému je odcizení práce nenekalé. Nicméně, když aplikace implementuje algoritmus nebo úlohu, aby běžela paralelně, nezáleží na rovnosti mezi dílčími úkoly. Co je to, jak rychle je dokončená celková úloha. Pro jiné algoritmy je FIFO vhodná strategie plánování.

### <a name="behavior-on-various-operating-systems"></a>Chování v různých operačních systémech

V systému Windows XP a Windows Vista se aplikace, které používají Concurrency Runtime se chovají podobně, s tím rozdílem, že je výkon haldy vylepšený v systému Windows Vista.

V systémech Windows 7 a Windows Server 2008 R2 podporuje operační systém i souběžnost a škálovatelnost. Tyto operační systémy například podporují počítače, které mají více než 64 hardwarových vláken. Aby bylo možné využít tyto nové funkce, je nutné upravit existující aplikaci, která používá rozhraní API systému Windows. Aplikace používající Concurrency Runtime ale tyto funkce automaticky používá a nevyžaduje úpravy.

[základní. uživatel – mode_scheduling](/windows/win32/procthread/user-mode-scheduling)

[[Nahoře](#top)]

## <a name="openmp"></a>Porovnání Concurrency Runtime s OpenMP

Concurrency Runtime povoluje celou řadu programovacích modelů. Tyto modely mohou překrývat nebo doplnit modely jiných knihoven. Tato část porovnává Concurrency Runtime se [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp).

Programovací model OpenMP je definován otevřeným standardem a má jasně definované vazby na modul FORTRAN aC++ programovací jazyky jazyka C. Verze OpenMP 2,0 a 2,5 jsou vhodné pro paralelní algoritmy, které jsou iterativní; To znamená, že provádí paralelní iteraci na poli dat. OpenMP je nejúčinnější, pokud je stupeň paralelismu předem určen a odpovídá dostupným prostředkům v systému. Model OpenMP je obzvláště dobrým rozdílem pro vysoce výkonné výpočetní prostředí, ve kterém jsou distribuovány velmi velké výpočetní problémy mezi prostředky zpracování v jednom počítači. V tomto scénáři je známé hardwarové prostředí a vývojář může rozumně očekávat výhradní přístup k výpočetním prostředkům při spuštění algoritmu.

Nicméně jiné, méně omezené výpočetní prostředí nemusí být vhodné pro OpenMP. Například rekurzivní problémy (například quicksort Algorithm nebo prohledávání stromu dat) jsou obtížnější k implementaci pomocí OpenMP. Concurrency Runtime doplňuje možnosti OpenMP poskytnutím [knihovny paralelních vzorů](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) a [knihovny asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md). Na rozdíl od OpenMP Concurrency Runtime poskytuje dynamický Plánovač, který se přizpůsobí k dostupným prostředkům a upravuje stupeň paralelismu při změně zatížení.

Mnohé z funkcí v Concurrency Runtime lze rozšířit. Existující funkce můžete také kombinovat a vytvářet nové. Protože OpenMP spoléhá na direktivy kompilátoru, nelze jej snadno rozšířit.

Další informace o tom, jak Concurrency Runtime porovnává se OpenMP a jak migrovat existující kód OpenMP pro použití Concurrency Runtime, naleznete v tématu [migrace z OpenMP do Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md).

[[Nahoře](#top)]

## <a name="see-also"></a>Viz také

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)<br/>
[Přehled](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Knihovna PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)
