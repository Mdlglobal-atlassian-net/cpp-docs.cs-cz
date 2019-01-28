---
title: D. Klauzule schedule
ms.date: 01/22/2019
ms.assetid: bf3d8f51-ea05-4803-bf55-657c12e91efe
ms.openlocfilehash: 89e011784c5cccedc4a75f38d553458ea2e5d7e0
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087285"
---
# <a name="d-the-schedule-clause"></a>D. Klauzule schedule

Paralelní oblasti má alespoň jednu bariéry, na jeho konci a může obsahovat další překážky v něm. U každé bariéry musíte počkat, ostatní členové týmu pro poslední vlákno k doručení. Chcete-li minimalizovat tato čekací doba, sdílených pracovních mají distribuovat, aby všechna vlákna doručení bariéře na přibližně ve stejnou dobu. Pokud některé z těchto sdílených je součástí pracovní `for` vytvoří, `schedule` klauzuli lze použít pro tento účel.

Při opakované odkazy na stejné objekty volba plán `for` konstruktor může být stanoveno především podle vlastností paměti systému, například prezentace a velikost mezipaměti a zda je jednotný čas přístupu paměti nebo nonuniform. Tyto důvody může být vhodnější mít každý podproces konzistentně odkazovat na stejnou sadu prvků pole v řadě smyčky, i v případě, že některá vlákna jsou přiřazeny relativně méně práce v některé z smyčky. Toto nastavení lze provést pomocí `static` plán se stejným hranice pro všechny smyčky. V následujícím příkladu, nula slouží jako dolní mez v druhé smyčky, i když `k` by přirozenější, plán nejsou důležité.

```cpp
#pragma omp parallel
{
#pragma omp for schedule(static)
  for(i=0; i<n; i++)
    a[i] = work1(i);
#pragma omp for schedule(static)
  for(i=0; i<n; i++)
    if(i>=k) a[i] += work2(i);
}
```

Ve zbývajících příkladech se předpokládá, že tuto paměť přístup není dominantní pozornost. Pokud není uvedeno jinak, že všechna vlákna přijímat srovnatelné výpočetní prostředky. V těchto případech se možnost plánu pro `for` konstrukce závisí na sdílených pracovních, který se má provést mezi nejbližší předchozí odbourejte překážky bránící a předpokládané uzavírací bariéry nebo nejbližší nadcházející bariéry, pokud je `nowait` klauzule. Pro každý druh plán krátký příklad ukazuje, jak tento typ plánu je pravděpodobně nejlepší volbou. Následuje stručný popis každý příklad.

`static` Plánu je také vhodný pro nejjednodušším případě paralelní oblasti obsahující jeden `for` vytvořit s každou iterací, které vyžadují stejné množství práce.

```cpp
#pragma omp parallel for schedule(static)
for(i=0; i<n; i++) {
  invariant_amount_of_work(i);
}
```

`static` Plánu je charakteristické vlastnosti, která každého vlákna vrací přibližně stejný počet iterací jako jakékoli jiné vlákno, a každé vlákno může určit nezávisle na sobě iterace přiřazené k němu. Proto je třeba distribuovat práce žádná synchronizace a za předpokladu, že každé iteraci vyžaduje stejné množství práce, všechna vlákna měl dokončit v přibližně ve stejnou dobu.

Pro tým *p* vlákna, umožní *ceiling(n/p)* být celé číslo *q*, který splňuje *n = p\*q - r* s *0 < = r < p*. Jednu implementaci `static` naplánovat pro tento příklad by přiřadit *q* iterací na první *p-1* vlákna, a *q-r* iterací na poslední vlákno.  Bude přiřazen jiné přijatelné implementace *q* iterací na první *p – r* vlákna, a *q-1* iterací zbývající *r*vlákna. Tento příklad ukazuje důvod, proč program neměli byste tedy spoléhat na podrobnostech konkrétní implementaci.

`dynamic` Plán je vhodný pro případ `for` vytvořit pomocí iterací, které vyžadují různé nebo dokonce nepředvídatelné množství práce.

```cpp
#pragma omp parallel for schedule(dynamic)
  for(i=0; i<n; i++) {
    unpredictable_amount_of_work(i);
}
```

`dynamic` Plánu je charakteristické vlastnosti, která žádné vlákno čeká bariéře trvá déle, než kolik jich jiné vlákno k provedení jeho poslední iterace. Tento požadavek znamená, že iterací se musí přiřadit postupně po jednom vlákna, jakmile budou dostupné, se synchronizací pro každé přiřazení. Lze snížit režii synchronizace tak, že určíte velikost bloku dat minimální *k* větší než 1, tak, aby vlákna jsou přiřazeny *k* po druhém, dokud méně než *k* zůstanou. Zaručí se tak, že žádné vlákno čeká bariéře déle, než se používá jiné vlákno k provedení jeho poslední blok (maximálně) *k* iterací.

`dynamic` Plán může být užitečné, pokud vlákna zobrazí různé výpočetní prostředky, které má mnohem stejný účinek jako různé množství práce pro každou iteraci. Naopak dynamický plán může být také užitečné, pokud vlákna přejít na `for` vytvořit v různou dobu, i když se vyskytuje v některých případech `guided` plán může být vhodnější.

`guided` Plán je vhodný pro případ, ve kterém může do vlákna v různou dobu na `for` sestavit bez nutnosti každé iteraci o stejné množství práce. Tato situace může nastat, pokud, například `for` konstrukce předchází jednoho nebo více oddílů nebo `for` vytvoří s `nowait` klauzule.

```cpp
#pragma omp parallel
{
  #pragma omp sections nowait
  {
    // ...
  }
  #pragma omp for schedule(guided)
  for(i=0; i<n; i++) {
    invariant_amount_of_work(i);
  }
}
```

Stejně jako `dynamic`, `guided` naplánovat záruky, které žádné vlákno čeká bariéře déle, než se používá jiné vlákno k provedení jeho poslední iterace nebo konečné *k* iterací, pokud velikost bloku dat *k* určena. Mezi tyto plány `guided` plánu je charakteristické vlastnosti, že vyžaduje nejmíň synchronizace. Pro velikost deduplikačního bloku dat *k*, obvyklá implementace přiřadí *q = ceiling(n/p)* iterací do první dostupné vlákna, nastavte *n* na větší z *n-q* a *p\*k*a opakujte, dokud jsou přiřazeny všech iterací.

Při výběru optimální plán není jasné, protože je pro tyto příklady `runtime` plánu je vhodné pro experimentování s různé plány a velikostí bloku, aniž byste museli změnit a znovu kompilovat program. Může také být užitečné při optimální plán závisí (nějakým způsobem předvídatelné) na vstupní data, ke které se použije program.

Chcete-li zobrazit příklad kompromisy mezi různé plány, vezměte v úvahu sdílení 1000 iterací mezi osmi vlákna. Předpokládejme, že není invariantní množství práce při každé iteraci, který budete používat jako jednotka času.

Pokud ve stejnou dobu spuštění všech vláken `static` způsobí, že plán konstrukce kvadrantu 125 jednotky, se žádná synchronizace. Ale Předpokládejme, že jedno vlákno je 100 jednotek v dorazily. Zbývající vlákna sedm potom počkejte 100 jednotek bariéře a zvýší dobu provádění u celé konstrukce na 225.

Vzhledem k tomu, jak `dynamic` a `guided` plány Ujistěte se, že žádné vlákno čeká víc než jedné jednotky bariéře, opožděné vlákno způsobí, že spuštění s úspěšností for – konstrukce zvýšit pouze na 138 jednotek, může být zvýšena zpoždění z synchronizace. Pokud takové zpoždění nejsou zanedbatelné, je důležité, že číslo synchronizace je 1000 `dynamic` , ale pouze 41 pro `guided`, za předpokladu, že jedna výchozí velikost bloku. S 25; velikost bloku dat `dynamic` a `guided` obě dokončit v 150 jednotky a zpoždění, od požadovaných synchronizace, které nyní číslo pouze 40 až 20, v uvedeném pořadí.
