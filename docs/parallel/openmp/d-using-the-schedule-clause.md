---
title: D. Použití klauzule schedule | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bf3d8f51-ea05-4803-bf55-657c12e91efe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d40b22a5e724f8d8b587e2928d3d1305a7fa807a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446137"
---
# <a name="d-using-the-schedule-clause"></a>D. Použití klauzule schedule

Paralelní oblasti má alespoň jednu bariéry, na jeho konci a může obsahovat další překážky v něm. U každé bariéry musíte počkat, ostatní členové týmu pro poslední vlákno k doručení. Chcete-li minimalizovat tato čekací doba, sdílených pracovních mají distribuovat, aby všechna vlákna doručení bariéře na přibližně ve stejnou dobu. Pokud některé z těchto sdílených je součástí pracovní **pro** vytvoří, `schedule` klauzuli lze použít pro tento účel.

Když jsou opakované odkazy na stejné objekty volba plán pro **pro** konstruktor může být stanoveno především podle vlastností paměti systému, například prezentace a velikost mezipaměti a zda přístup k paměti jednotná nebo nonuniform jsou časy. Tyto důvody může být vhodnější mít každý podproces konzistentně odkazovat na stejnou sadu prvků pole v řadě smyčky, i v případě, že některá vlákna jsou přiřazeny relativně méně práce v některé z smyčky. To můžete udělat pomocí **statické** plán se stejným hranice pro všechny smyčky. V následujícím příkladu, Všimněte si, že nula slouží jako dolní mez v druhé smyčky, i když **k** by přirozenější, plán nejsou důležité.

```
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

Ve zbývajících příkladech, předpokládá se, že paměť není přístup dominantní pozornost a pokud není uvedeno jinak, že všechna vlákna přijímat srovnatelné výpočetní prostředky. V těchto případech se možnost plánu pro **pro** konstrukce závisí na sdílených pracovních, který se má provést mezi nejbližší předchozí odbourejte překážky bránící a předpokládané uzavírací bariéry nebo nejbližší následné bariéry, pokud existuje `nowait` klauzuli. Pro každý druh plán krátký příklad ukazuje, jak tento typ plánu je pravděpodobně nejlepší volbou. Následuje stručný popis každý příklad.

**Statické** plánu je také vhodný pro nejjednodušším případě paralelní oblasti obsahující jeden **pro** vytvořit s každou iterací, které vyžadují stejné množství práce.

```
#pragma omp parallel for schedule(static)
for(i=0; i<n; i++) {
  invariant_amount_of_work(i);
}
```

**Statické** plánu je charakteristické vlastnosti, která každého vlákna vrací přibližně stejný počet iterací jako jakékoli jiné vlákno, a každé vlákno může určit nezávisle na sobě iterace přiřazené k němu. Proto je třeba distribuovat práce žádná synchronizace a za předpokladu, že každé iteraci vyžaduje stejné množství práce, všechna vlákna měl dokončit v přibližně ve stejnou dobu.

Pro tým `p` vlákna, umožní *ceiling(n/p)* být celé číslo *q*, který splňuje *n = p\*q - r* s *0 < = r < p* . Jednu implementaci **statické** naplánovat pro tento příklad by přiřadit *q* iterací na první *p-1* vlákna, a *q-r* iterace na poslední vlákno.  Bude přiřazen jiné přijatelné implementace *q* iterací na první *p – r* vlákna, a *q-1* iterací zbývající *r*vlákna. To ukazuje, proč program neměli byste tedy spoléhat na podrobnostech konkrétní implementaci.

**Dynamické** plán je vhodný pro případ **pro** vytvořit pomocí iterací, které vyžadují různé nebo dokonce nepředvídatelné množství práce.

```
#pragma omp parallel for schedule(dynamic)
  for(i=0; i<n; i++) {
    unpredictable_amount_of_work(i);
}
```

**Dynamické** plánu je charakteristické vlastnosti, která žádné vlákno čeká bariéře trvá déle, než kolik jich jiné vlákno k provedení jeho poslední iterace. Tento postup vyžaduje, aby iterace přiřadit postupně po jednom vlákna, jakmile budou dostupné, se synchronizací pro každé přiřazení. Lze snížit režii synchronizace tak, že určíte velikost bloku dat minimální *k* větší než 1, tak, aby vlákna jsou přiřazeny *k* po druhém, dokud méně než *k* zůstanou. Zaručí se tak, že žádné vlákno čeká bariéře déle, než se používá jiné vlákno k provedení jeho poslední blok (maximálně) *k* iterací.

**Dynamické** plán může být užitečné, pokud vlákna zobrazí různé výpočetní prostředky, které má mnohem stejný účinek jako různé množství práce pro každou iteraci. Naopak dynamický plán může být také užitečné, pokud vlákna přejít na **pro** vytvořit v různou dobu, i když se vyskytuje v některých případech **s asistencí** plán může být vhodnější.

**s asistencí** plán je vhodný pro případ, ve kterém může do vlákna v různou dobu na **pro** sestavit bez nutnosti každé iteraci o stejné množství práce. K tomu může dojít, pokud, například **pro** konstrukce předchází jednoho nebo více oddílů nebo **pro** vytvoří s `nowait` klauzule.

```
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

Stejně jako **dynamické**, **s asistencí** naplánovat záruky, které žádné vlákno čeká bariéře déle, než se používá jiné vlákno k provedení jeho poslední iterace nebo konečné *k* Pokud velikost bloku dat iterace *k* určena. Mezi tyto plány **s asistencí** plánu je charakteristické vlastnosti, že vyžaduje nejmíň synchronizace. Pro velikost deduplikačního bloku dat *k*, obvyklá implementace přiřadí *q = ceiling(n/p)* iterací do první dostupné vlákna, nastavte *n* na větší z *n-q* a *p\*k*a opakujte, dokud jsou přiřazeny všech iterací.

Při výběru optimální plán není jasné, protože je pro tyto příklady **runtime** plánu je vhodné pro experimentování s různé plány a velikostí bloku, aniž byste museli změnit a znovu kompilovat program. Může také být užitečné při optimální plán závisí (nějakým způsobem předvídatelné) na vstupní data, ke které se použije program.

Pokud chcete zobrazit příklad kompromisy mezi různé plány, vezměte v úvahu sdílení 1000 iterací mezi 8 vláken. Předpokládejme, že není invariantní množství práce při každé iteraci, který budete používat jako jednotka času.

Pokud ve stejnou dobu spuštění všech vláken **statické** způsobí, že plán konstrukce kvadrantu 125 jednotky, se žádná synchronizace. Ale Předpokládejme, že jedno vlákno je 100 jednotek v dorazily. Zbývající vlákna sedm potom počkejte 100 jednotek bariéře a zvýší dobu provádění u celé konstrukce na 225.

Vzhledem k tomu, jak **dynamické** a **s asistencí** plány zajistit, aby žádné vlákno čeká víc než jedné jednotky bariéře, opožděné vlákno způsobí, že spuštění s úspěšností for – konstrukce zvýšit jenom na 138 jednotky, může být zvýšena zpoždění z synchronizace. Pokud takové zpoždění nejsou zanedbatelné, je důležité, že číslo synchronizace je 1000 **dynamické** , ale pouze 41 pro **s asistencí**, za předpokladu, že výchozí velikost bloku jednoho. S 25; velikost bloku dat **dynamické** a **s asistencí** obě dokončit v 150 jednotky a zpoždění, od požadovaných synchronizace, které nyní číslo pouze 40 až 20, v uvedeném pořadí.