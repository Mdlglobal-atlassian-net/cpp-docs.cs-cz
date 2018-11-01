---
title: Životní cyklus objektů a správa prostředků (moderní verze jazyka C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8aa0e1a1-e04d-46b1-acca-1d548490700f
ms.openlocfilehash: d7bf45881ef82ecf0d11892e5ddf3d3c16a437cf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609934"
---
# <a name="object-lifetime-and-resource-management-modern-c"></a>Životní cyklus objektů a správa prostředků (moderní verze jazyka C++)

Na rozdíl od spravovaných jazyků nemá C++ kolekce paměti (GC), který automaticky uvolní prostředky bez delší používané paměti při spuštění programu. V jazyce C++ správu prostředků přímo souvisí s životního cyklu objektu. Tento dokument popisuje faktory, které ovlivňují dobu života objektu v jazyce C++ a jak ho spravovat.

C++ nemá uvolňování paměti, především proto, že nezpracuje bez paměťových prostředků. Podobné těm v jazyce C++ deterministické destruktory pouze dokáže zpracovat prostředky paměti a které nejsou paměťově stejně. Globální Katalog má také jiné problémy, jako je vyšší nároky na paměť a využití procesoru a umístění. Ale obecnosti je základní problém, který není možné řešit prostřednictvím inteligentní optimalizace.

## <a name="concepts"></a>Koncepty

Důležitá věc, kterou ve správě životního cyklu objektu je zapouzdření, kdo je použití objektu nemusí vědět, co vlastní prostředky, které objekt, nebo jak zbavit, nebo dokonce Určuje, zda vlastní všechny prostředky ve všech. Má jenom ke zničení objektu. Jazyk C++ core je navržený tak, aby, že objekty jsou zničeny, ve správnou dobu, to znamená, jak bloky jsou se ukončil, v opačném pořadí konstrukce. Pokud objekt je zničen, jejích základních tříd a členů jsou zničeny v určitém pořadí.  Jazyk automaticky odstraní objekty, dokud neprovedete speciální věci, jako je velikost haldy nebo nové umístění.  Například [inteligentní ukazatele](../cpp/smart-pointers-modern-cpp.md) jako `unique_ptr` a `shared_ptr`, a kontejnery standardní knihovny C++, jako jsou `vector`, zapouzdření **nové** /  **Odstranit** a `new[]` / `delete[]` v objektech, které mají destruktory. To je důvod, proč je tedy potřeba použít inteligentní ukazatele a kontejnery standardní knihovny C++.

Dalším důležitým konceptem ve správě životního cyklu: destruktory. Destruktory zapouzdření uvolnění prostředků.  (Obvykle použila se mnemotechnika je RRID uvolnění prostředků je zničení.)  Prostředek je něco, co můžete získat z "systém" a dát později.  Paměť je nejběžnější prostředků, ale existují také soubory, sokety, textury a jiné než paměťových prostředků. "Vlastnit" prostředek znamená, že můžete použít, když ho potřebujete, ale taky je potřeba ji uvolnit, až budete hotovi s ním.  Pokud objekt je zničen, jeho destruktor uvolní prostředky, které jej vlastní.

Poslední koncept je orientovaného acyklického grafu (orientovaného Acyklického grafu).  Struktura vlastnictví v aplikaci tvoří DAG. Žádný objekt může vlastnit sebe sama –, který je nejen nemožné, ale také ze své podstaty nemá význam. Ale dva objekty můžou sdílet vlastnictví třetí objekt.  Několik druhů odkazy je možné ve skupině DAG takto: A je členem skupiny B (B vlastníkem A), úložiště jazyka C `vector<D>` (C vlastní každý prvek D), ukládá E `shared_ptr<F>` (E sdílí vlastnictví F, případně s jinými objekty), a tak dále.  Za předpokladu, neexistují žádné cykly a každý odkaz v tomto orientovaném acyklickém grafu je reprezentován objektem, který má destruktor (namísto nezpracovaný ukazatel, popisovač nebo jiný mechanismus) a potom nedostatku prostředků jsou nemožné, protože jazyk se nedají. Uvolnění prostředků ihned poté, co jste už nepotřebujete, bez systému uvolňování paměti spuštěna. Sledování životnosti je režie bez pro obor zásobníku, základních tříd, členů a související případy a cenově dostupné pro `shared_ptr`.

### <a name="heap-based-lifetime"></a>Doba života haldy

Doba života objektu haldy, použijte [inteligentní ukazatele](../cpp/smart-pointers-modern-cpp.md). Použití `shared_ptr` a `make_shared` jako výchozí ukazatel a alokátorem. Použití `weak_ptr` přerušit cykly, ukládání do mezipaměti, a sledujte objekty bez ovlivnění nebo za předpokladu, že nic o jejich životnosti.

```cpp
void func() {

auto p = make_shared<widget>(); // no leak, and exception safe
...
p->draw();

} // no delete required, out-of-scope triggers smart pointer destructor
```

Použití `unique_ptr` jedinečné vlastnictví, například v *ukazatel na implementaci* idiom. (Viz [ukazatel na implementaci pro zapouzdření za kompilace](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md).) Ujistěte se, `unique_ptr` primární cílem všechny explicitní **nové** výrazy.

```cpp
unique_ptr<widget> p(new widget());
```

Nezpracované ukazatele můžete použít pro jiné vlastnictví a zjišťování. Může dangle-vlastnící ukazatele, ale nemůže způsobit únik těchto.

```cpp
class node {
  ...
  vector<unique_ptr<node>> children; // node owns children
  node* parent; // node observes parent, which is not a concern
  ...
};
node::node() : parent(...) { children.emplace_back(new node(...) ); }
```

Když se vyžaduje optimalizace výkonu, budete nejspíš muset použít *dobře zapouzdřený* vlastnící ukazatele a explicitního volání odstranit. Příkladem je při implementaci nízké úrovně datovou strukturu.

### <a name="stack-based-lifetime"></a>Doba života založené na zásobníku

V moderním jazyce C++ *založené na zásobníku oboru* je efektivní způsob, jak zapisovat robustního kódu, protože spojuje automatické *zásobníku životnost* a *datový člen životnost* s vysokou efektivitu – Doba života pro sledování je v podstatě zdarma režijní náklady. Doba života objektu haldy vyžaduje pečlivé ruční správy a může sloužit jako zdroj pro nedostatku prostředků a nedostatků, zejména v případě, že pracujete s nezpracované ukazatele. Vezměte v úvahu tento kód, který ukazuje obor založené na zásobníku:

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

Používejte opatrně statickou životnost (globální statické, místní statické funkce) vzhledem k tomu může dojít k problémům. Co se stane, když se vyvolá výjimku konstruktoru na globální objekt? Obvykle aplikace chyby způsobem, který může být obtížné ladit. Pořadí konstrukce je problematické pro objekty statickou životnost a není bezpečná pro souběžnost. Nejenže je konstrukce objektu problém, pořadí zničení může být složité, zejména v případě, že je zahrnuta polymorfismu. I v případě, že objekt nebo proměnná není polymorfní a nemá komplexní konstrukce/destrukce řazení, je stále problém souběžnosti bezpečné pro vlákna. Aplikace s více podprocesy nelze bezpečně upravovat data v statické objekty bez nutnosti místní úložiště vláken, zámky prostředků a jiné zvláštní opatření.

## <a name="see-also"></a>Viz také:

[C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)