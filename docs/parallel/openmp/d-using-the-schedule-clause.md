---
title: D. Pomocí klauzule plán | Microsoft Docs
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
ms.openlocfilehash: 8987c4505adfde8534d57346cd6725231efa022f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694937"
---
# <a name="d-using-the-schedule-clause"></a>D. Pomocí klauzule plán
Paralelní oblast má alespoň jeden bariéry při ukončení a může mít další překážky v něm. V každé bariéry ostatní členové týmu musí čekat poslední vlákno k doručení. Chcete-li minimalizovat této čekací doby, by měly být distribuovány sdílené pracovní tak, aby přicházejí všechna vlákna na bariéry v přibližně ve stejnou dobu. Pokud některé této sdílené je součástí pracovní **pro** vytvoří, `schedule` klauzuli lze použít pro tento účel.  
  
 Po opakovaných odkazy na stejné objekty, volba plán **pro** konstrukce může určit především vlastnosti paměti systému, jako je například přítomnosti a velikost mezipaměti a jestli přístup k paměti časy jsou uniform nebo nonuniform. Tyto informace může být vhodnější tak, aby měl každý podproces konzistentně odkazovat na stejnou sadu prvky pole v řadě smyčky, i když některé vláken přiřazené relativně. méně práce v některých smyčky. To můžete provést pomocí **statické** plán se stejným hranice pro všechny smyčky. V následujícím příkladu, Všimněte si, že nula slouží jako dolní hranice v druhé smyčky, i když **tisíc** by přirozenější, pokud plán nejsou důležité.  
  
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
  
 V zbývající příkladech se předpokládá, že paměť není přístup dominantní pozornost a pokud není uvedeno jinak, že všechna vlákna přijímat porovnatelný z hlediska výpočetní prostředky. V těchto případech volba plán pro **pro** konstrukce závisí na sdílených práci, kterou má být provedeno mezi nejbližší předchozí bariéry a bariéry předpokládané ukončovací nebo nejbližší následné bariéry, pokud existuje `nowait` klauzule. Pro každý typ plánu krátké příklad ukazuje, jak je pravděpodobně nejlepší volbou tento typ plánu. Stručný popis následuje každý příklad.  
  
 **Statické** plán je také vhodné pro nejjednodušším případě paralelní oblast obsahující jeden **pro** vytvořit, přičemž při každém opakování nutnosti stejné množství práce.  
  
```  
#pragma omp parallel for schedule(static)  
for(i=0; i<n; i++) {  
  invariant_amount_of_work(i);  
}  
```  
  
 **Statické** plán je charakteristické vlastnosti, každé vlákno získá přibližně stejný počet iterací jako jiné vlákno, a každé vlákno můžete určit nezávisle iterací přiřazen. Proto je třeba distribuovat práce žádná synchronizace a za předpokladu, že každé iteraci vyžaduje stejné množství práce, všechna vlákna by měly být dokončeny v přibližně ve stejnou dobu.  
  
 Pro tým `p` vláken, umožní *ceiling(n/p)* být celé číslo *q*, který splňuje *n = p\*q - r* s *0 < = r < p* . Jednu implementaci **statické** naplánování pro tento příklad přiřazujete *q* iterací prvního *p-1* vláken, a *q-r* opakování poslední vlákno.  Bude přiřazen jiný přijatelné implementace *q* iterací prvního *p – r* vláken, a *q-1* iterací zbývající *r*vláken. To ukazuje, proč program neměli spoléhat na podrobnosti o konkrétní implementace.  
  
 **Dynamické** plán je vhodný pro případ **pro** vytvořit s iterací nutnosti různých nebo i nepředvídatelným množství práce.  
  
```  
#pragma omp parallel for schedule(dynamic)  
  for(i=0; i<n; i++) {  
    unpredictable_amount_of_work(i);  
}  
```  
  
 **Dynamické** plán je charakteristické vlastnosti, která žádné vlákno čeká na bariéry pro trvá déle, než jiné vlákno k provedení jeho poslední iterací. To vyžaduje, že iterací být přiřazen jeden po druhém vláken Jakmile budou k dispozici, se synchronizací pro každé přiřazení. Může snížit režii synchronizace určení velikosti bloku minimální *tisíc* větší než 1, takže vláken přiřazené *tisíc* najednou, dokud méně než *tisíc* zůstanou. To zaručuje, že žádný přístup z více vláken čeká na bariéry déle, než bude trvat jiné vlákno k provedení jeho poslední bloků dat z (maximálně) *tisíc* iterací.  
  
 **Dynamické** plán může být užitečné, pokud vláken přijímat různých výpočetní prostředky, který má mnohem stejného efektu jako různá množství práce pro každou iteraci. Podobně můžete také být užitečné, pokud vláken přicházejí na dynamické plán **pro** vytvořit v různou dobu, i když se vyskytuje v některých případech **na základě** plán může být vhodnější.  
  
 **Na základě** plán je vhodné v případech, ve kterém může v různých časech v doručení vláken **pro** vytvořit s každou iteraci nutnosti o stejné množství práce. To může dojít, pokud, například **pro** konstrukce předchází jednoho nebo více oddílů nebo **pro** vytvoří s `nowait` klauzule.  
  
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
  
 Jako **dynamické**, **na základě** naplánovat záruky, které žádný přístup z více vláken čeká na bariéry déle, než bude trvat jiné vlákno k provedení jeho poslední iterace nebo konečné *tisíc* Pokud velikost bloku dat iterací *tisíc* je zadán. Mezi tyto plány **na základě** plán je charakteristické vlastnosti, vyžaduje nejmenší počet synchronizace. Pro velikost bloku *tisíc*, přiřadí Typická implementace *q = ceiling(n/p)* iterací první dostupné vlákno, nastavte *n* se větší z *n-q* a *p\*tisíc*a opakujte, dokud jsou přiřazeny všech iterací.  
  
 Pokud není volba optimální plán vymazat, protože je pro tyto příklady **runtime** plán je vhodné pro zkoušení různé plány a velikosti bloku, aniž byste museli upravit a znovu zkompiluje program. Může také být užitečné při optimální plán závisí (nějakým způsobem předvídatelný) na vstupní data, ke které se použije program.  
  
 Pokud chcete zobrazit příklad kompromis mezi různé plány, vezměte v úvahu sdílení 1000 iterací mezi 8 vláken. Předpokládejme, že je neutrální množství práce při každé iteraci a použít jej jako jednotka času.  
  
 Pokud všechna vlákna spuštění ve stejnou dobu, **statické** způsobí, že plán konstrukce na provedení v 125 jednotky se žádná synchronizace. Ale Předpokládejme, že jedno vlákno je 100 jednotky pozdní v přicházejících. Počkejte, pak zbývající sedm vláken pro 100 jednotky v bariéry a dobu provádění u celé konstrukce zvýší na 225.  
  
 Vzhledem k tomu, jak **dynamické** a **na základě** plány zajistit, aby žádné vlákno čeká víc než jednu jednotku na bariéry, zpožděné vlákno způsobí, že časy jejich provádění for – konstrukce zvýšit pouze na 138 jednotky, případně zvýšené zpožděními z synchronizace. Pokud takové zpoždění nejsou zanedbatelné, bude důležité, aby počet synchronizace 1000 pro **dynamické** , ale pouze 41 pro **na základě**, za předpokladu, že výchozí velikost bloku jednoho. S velikost bloku dat 25 **dynamické** a **na základě** obě dokončit v 150 jednotky a žádné zpoždění z požadované synchronizace, které teď číslo pouze 40 a 20, v uvedeném pořadí.