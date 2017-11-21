---
title: "Objekt životnost a Správa prostředků (moderní verze jazyka C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 8aa0e1a1-e04d-46b1-acca-1d548490700f
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0da7872ab6a93b737bf402ded085a4fb18551798
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="object-lifetime-and-resource-management-modern-c"></a>Životní cyklus objektů a správa prostředků (moderní verze jazyka C++)
Na rozdíl od spravované jazyky nemá C++ uvolňování (GC), který automaticky uvolní prostředky, ne delší použité paměti při spuštění programu. V jazyce C++ Správa prostředků přímo souvisí s doba života objektu. Tento dokument popisuje faktory, které ovlivňují doba života objektu v jazyce C++ a postup k její správě.  
  
 C++ nemá GC především proto ho nemůže pracovat bez paměťových prostředků. Deterministické destruktory stejně jako v C++ pouze může zpracovávat prostředky paměti a jiných paměti rovnoměrně. Globální Katalog má také jiné problémy, jako je vyšší režijní náklady v paměti a příkon procesoru a polohu. Ale všeobecné je základní problém, který nemůže být omezeny prostřednictvím inteligentní optimalizace.  
  
## <a name="concepts"></a>Koncepty  
 Je důležité si ve správě doba života objektu zapouzdření – kdo používá objekt nemá vědět, co vlastní prostředky, které objektu, nebo postup zbavit nebo i jestli vlastní všechny prostředky vůbec. Právě má odstranění objektu. Základní jazyk C++ slouží k zajištění, že jsou objekty zničen ve správném čase, to znamená, jako jsou opustil bloky, v opačném pořadí v konstrukce. Pokud objekt zničení, jeho základů a členů jsou zničen v určitém pořadí.  Jazyk automaticky odstraní objekty, dokud neprovedete speciální třeba přidělení haldy nebo nové umístění.  Například [inteligentní ukazatele](../cpp/smart-pointers-modern-cpp.md) jako `unique_ptr` a `shared_ptr`, a jako standardní knihovna C++ kontejnery `vector`, zapouzdření `new` / `delete` a `new[]` / `delete[]` v objektech, které mají destruktory. Proto je tak důležité používat chytré ukazatele a standardní knihovny C++ kontejnery.  
  
 Další důležité koncept ve správě životního cyklu: destruktory. Destruktory pro zapouzdření uvolnění prostředků.  (Běžně používané symbolické je RRID prostředků verze je likvidace.)  Prostředek je něco, co můžete získat z "systém" a dát později.  Paměť je nejběžnější prostředků, ale existují také soubory, sokety, textury a dalších bez paměťových prostředků. "Vlastnícího" prostředek znamená, že můžete použít, pokud to potřebujete, ale máte také k uvolnění ho, až budete hotovi s ním.  Pokud objekt zničení, jeho – destruktor uvolní prostředky, které je vlastní.  
  
 Poslední koncept je DAG (směrované Acyklické grafu).  Struktura vlastnictví v programu tvoří DAG. Žádný objekt můžete vlastní sám sebe, který není pouze znemožňuje, ale také ze své podstaty smysl. Ale dva objekty můžete sdílet vlastnictví třetí objektu.  Několik druhů odkazy jsou možné u DAG takto: A je členem skupiny B (B vlastní A), C úložiště `vector<D>` (C vlastní každý prvek D), úložiště E `shared_ptr<F>` (E sdílí vlastnictví F, případně s jinými objekty), a tak dále.  Jak dlouho, dokud nejsou žádné cykly a všech propojení v DAG je reprezentována objekt, který nemá – destruktor (namísto nezpracovaná ukazatel, popisovač nebo jinému kontrolnímu mechanismu.), bude nedostatku prostředků nejsou možné, protože brání jazyk, je. Ihned po jejich už nejsou potřeba, bez systém uvolňování paměti systémem uvolnění prostředků. Životnost sledování je bez režie pro obor zásobníku, základů, členů a související případech a nenákladné pro `shared_ptr`.  
  
### <a name="heap-based-lifetime"></a>Doba platnosti na základě haldy  
 Doba života objektu haldy, použijte [inteligentní ukazatele](../cpp/smart-pointers-modern-cpp.md). Použití `shared_ptr` a `make_shared` jako výchozí ukazatel a přidělení. Použití `weak_ptr` rozdělit cykly, uděláte ukládání do mezipaměti a sledovat objekty bez ovlivnění nebo za předpokladu, že nic o jejich životnosti.  
  
```cpp  
void func() {  
  
auto p = make_shared<widget>(); // no leak, and exception safe  
...  
p->draw();   
  
} // no delete required, out-of-scope triggers smart pointer destructor  
  
```  
  
 Použití `unique_ptr` jedinečný vlastnictví, například v *pimpl* stylu. (Viz [Pimpl pro kompilaci zapouzdření](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md).) Ujistěte se, `unique_ptr` primární cílem všechny explicitní `new` výrazy.  
  
```cpp  
unique_ptr<widget> p(new widget());  
```  
  
 Nezpracovaná ukazatele můžete použít pro jiný vlastnictví a pozorování. Ukazatel vlastnící může dangle, ale nemůže úniku.  
  
```cpp  
class node {  
  ...  
  vector<unique_ptr<node>> children; // node owns children  
  node* parent; // node observes parent, which is not a concern  
  ...  
};  
node::node() : parent(...) { children.emplace_back(new node(...) ); }  
  
```  
  
 Pokud se vyžaduje optimalizace výkonu, můžete chtít použít *dobře zapouzdřené* vlastnící ukazatelů a explicitní volání odstranit. Příkladem je při implementaci strukturu nízké úrovně data.  
  
### <a name="stack-based-lifetime"></a>Doba platnosti na základě zásobníku  
 V moderní verze jazyka C++ *oboru na základě zásobníku* je efektivní způsob, jak napsat kód robustní, protože kombinuje automatické *zásobníku životnost* a *životnost člen dat* s vysoce účinné – Doba platnosti sledování je v podstatě zdarma režie. Doba života objektu haldy vyžaduje péče ruční správy a může být zdrojem nedostatku prostředků a umožňuje zvýšit efektivitu, zejména v případě, že pracujete s nezpracovaná ukazatele. Vezměte v úvahu tento kód, který ukazuje na základě zásobníku oboru:  
  
```cpp  
class widget {  
private:  
    gadget g;   // lifetime automatically tied to enclosing object  
public:  
    void draw();  
};  
  
void functionUsingWidget () {  
    widget w;   // lifetime automatically tied to enclosing scope  
                // constructs w, including the w.g gadget member  
    // ...
    w.draw();  
    // ...
} // automatic destruction and deallocation for w and w.g  
  // automatic exception safety,   
  // as if "finally { w.dispose(); w.g.dispose(); }"  
```  
  
 Doporučujeme používat statické doba platnosti (globální statické, místní statické funkce) vzhledem k tomu může dojít k problémům. Co se stane, když konstruktoru globální objektu vyvolá výjimku? Obvykle aplikace chyb způsobem, který může být obtížné ladění. Vytváření pořadí je problematické statické životnosti objektů a není bezpečné souběžnosti. Ne jenom k potížím při vytváření objektů, odstraňování pořadí může být složité, zejména v případě, že je zahrnuta polymorfismus. I když objekt nebo proměnné není polymorfní a nemá komplexní vytváření/odstraňování řazení, je stále problém souběžnosti vláken. Vícevláknové aplikace nemohou bezpečně upravovat data v statické objekty bez nutnosti úložiště thread-local, uzamčení prostředků a jiné zvláštní opatření.  
  
## <a name="see-also"></a>Viz také  
 [C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)