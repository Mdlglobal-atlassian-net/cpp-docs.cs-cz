---
title: Sémantika typu hodnota | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interior_ptr keyword [C++]
- virtual functions, value types
- inheritance, value types
- pinning pointers
- pin_ptr keyword [C++]
- __pin keyword
ms.assetid: 7f065589-ad25-4850-baf1-985142e35e52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 72dc6a613616d13e9ff92e8af0c39c63dfe63162
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413793"
---
# <a name="value-type-semantics"></a>Sémantika typu hodnoty

Sémantika typu hodnoty byly změněny z spravovaných rozšíření jazyka C++ pro Visual C++.

Tady je Kanonická hodnota jednoduchého typu používané spravovaných rozšíření pro C++ specifikace:

```
__value struct V { int i; };
__gc struct R { V vr; };
```

Ve spravovaných rozšíření můžete máme čtyři syntaktické varianty hodnotového typu (kde formulářů 2 a 3 jsou stejné sémanticky):

```
V v = { 0 };       // Form (1)
V *pv = 0;         // Form (2) an implicit form of (3)
V __gc *pvgc = 0;  // Form (3)
__box V* pvbx = 0; // Form (4) must be local
```

## <a name="invoking-inherited-virtual-methods"></a>Vyvolání zděděné virtuální metody

`Form (1)` je objekt Kanonická hodnota a je poměrně dobře srozumitelný, s výjimkou případů, kdy někdo pokusí vyvolat zděděné virtuální metody, jako `ToString()`. Příklad:

```
v.ToString(); // error!
```

Abyste mohli vyvolat tuto metodu, protože není v přepsána `V`, kompilátor musí mít přístup k tabulce přidružené virtuální základní třídy. Protože typy hodnot jsou ve stavu úložiště bez přidružené ukazatele na příslušné virtuální tabulky (vptr), to vyžaduje, aby `v` použít boxing. V návrhu spravovaných rozšíření jazyka implicitní zabalení se nepodporuje, ale musí být explicitně určena programátora, stejně jako v

```
__box( v )->ToString(); // Managed Extensions: note the arrow
```

Primární motiv za tento návrh je pedagogický: základní mechanismus musí být viditelný na programátorovi, aby porozuměl "náklady na" neposkytují instance v rámci její typ hodnoty. Byly `V` tak, aby obsahovala instance `ToString`, nebude zabalení nezbytné.

Lexikální složitosti explicitně zabalení objektu, ale ne základní náklady na zabalení samotného, se už v nové syntaxi:

```
v.ToString(); // new syntax
```

ale za cenu může být zavádějící návrháře tříd náklady tím, že k dispozici explicitní instance `ToString` metody v rámci `V`. Upřednostňují implicitního zabalení je, že je obvykle pouze jeden návrhář tříd, existují neomezený počet uživatelů, z nichž žádný bude mít možnost Upravit `V` eliminovat explicitní pole může být obtížné.

Kritéria, podle kterého chcete určit, jestli se mají zadat instanci přepsání `ToString` třída v rámci hodnoty by měly být četnost a umístění jeho použití. Pokud je volána jen velmi zřídka, je samozřejmě málo výhodné v její definici. Podobně pokud je volána v oblastech nenáročných aplikace, jeho přidání přidá také není zlepšení života na zemi obecné informace o výkonu aplikace. Alternativně můžete zachovat sledovací popisovač zabalené hodnoty a volání prostřednictvím tohoto popisovače nepotřebuje zabalení.

## <a name="there-is-no-longer-a-value-class-default-constructor"></a>Výchozí konstruktor třídy hodnota již neplatí.

Další rozdíl s typem hodnoty mezi spravovaných rozšíření a nové syntaxe je odstranění podpory pro výchozí konstruktor. Je to proto, že existují situace při provádění modulu CLR ve kterém můžete vytvořit instanci typu hodnoty bez vyvolání přidružena výchozí konstruktor. To znamená pokus v rámci spravovaného rozšíření podporují výchozí konstruktor do typu hodnoty může v praxi není zaručena. Zadaný této neexistence záruky, bylo považováno za lepší podporu zcela vynechat, než bude Nedeterministický ve své aplikaci.

Toto není chybný, jak může zpočátku zdát. Důvodem je, že každý objekt hodnotového typu je automaticky vynulován (každý typ je inicializován na výchozí hodnotu). V důsledku toho nejsou členy místní instanci nikdy definovány. V tomto smyslu ke ztrátě schopnosti definovat triviální výchozí konstruktor není ve skutečnosti ke ztrátě všech – a ve skutečnosti je mnohem efektivnější, když provádí CLR.

Problém je, když uživatel spravovaných rozšíření definuje nejsou v netriviálních výchozí konstruktor. Tato akce nemá žádné mapování na novou syntaxi. Kód v rámci konstruktoru bude nutné migrovat do pojmenované inicializační metodu, která by bylo nutné explicitně vyvolat uživatelem.

Deklarace objektu typu hodnoty v nové syntaxi, jinak se nezmění. Dolů na straně tohoto je, že typy hodnot nejsou z následujících důvodů: uspokojivé pro obtékání nativní typy:

- Není dostupná podpora pro destruktor v rámci typu hodnoty. To znamená, že neexistuje žádný způsob, jak automatizovat sadu akcí, které aktivuje na konci životnosti objektu.

- Nativních tříd mohou být zahrnuty pouze v rámci spravovaného typu jako ukazatel, který je pak přidělena na nativní haldě.

Rádi bychom se zabalení malé nativních tříd v typu hodnoty a nikoli typ odkazu k přidělení haldy double: nativní haldy pro uložení nativní typ a haldě modulu CLR pro uložení spravované obálky. Zabalení nativních tříd v rámci typu hodnoty vám umožní vyhnout spravované haldě, ale poskytuje žádný způsob, jak automatizovat recyklaci nativní halda paměti. Odkazové typy jsou pouze proveditelné spravovaného typu, ve kterých se má zabalit netriviální nativních tříd.

## <a name="interior-pointers"></a>Vnitřních ukazatelů

`Form (2)` a `Form (3)` výše můžete vyřešit prakticky cokoliv v tomto světě nebo další (to znamená, že vše spravované nebo nativní). Například jsou tedy všechny následující povolené v spravovaného rozšíření:

```
__value struct V { int i; };
__gc struct R { V vr; };

V v = { 0 };  // Form (1)
V *pv = 0;  // Form (2)
V __gc *pvgc = 0;  // Form (3)
__box V* pvbx = 0;  // Form (4)

R* r;

pv = &v;            // address a value type on the stack
pv = __nogc new V;  // address a value type on native heap
pv = pvgc;          // we are not sure what this addresses
pv = pvbx;          // address a boxed value type on managed heap
pv = &r->vr;        // an interior pointer to value type within a
                    //    reference type on the managed heap
```

Ano `V*` může vyřešit umístění v rámci bloku místní (a proto může být dangling), v globálním rozsahu, v rámci nativní haldy (například, pokud již byl odstraněn objekt, zaměřuje se na), v haldě modulu CLR (a proto se bude sledovat Pokud by měl přemístění během uvolňování paměti) a v rámci vnitřních odkaz na objekt na haldě modulu CLR (vnitřní ukazatel, tento postup se nazývá, je také transparentně sleduje).

Ve spravovaných rozšíření neexistuje žádný způsob, jak oddělit nativní aspekty `V*`; to znamená na jeho (včetně), je zpracováván, která zpracovává možnost jeho adresy objektu nebo podobjektu na spravované haldě.

V nové syntaxi, je ukazatel s hodnotou typu rozdělen do dvou typů: `V*`, což je omezená na umístění mimo CLR na haldě a vnitřní ukazatel `interior_ptr<V>`, který umožňuje, ale nevyžaduje adresu v rámci spravované haldě.

```
// may not address within managed heap
V *pv = 0;

// may or may not address within managed heap
interior_ptr<V> pvgc = nullptr;
```

`Form (2)` a `Form (3)` spravovaných rozšíření mapování do `interior_ptr<V>`. `Form (4)` sledovací popisovač je. Zaměřuje se na celý objekt, který byl zabalen ve spravované haldě. Je přeložen v nové syntaxi na `V^`,

```
V^ pvbx = nullptr; // __box V* pvbx = 0;
```

Následující deklarace ve spravovaných rozšíření všechny namapovat na vnitřních ukazatelů v nové syntaxi. (Jsou typy hodnot v rámci `System` oboru názvů.)

```
Int32 *pi;   // => interior_ptr<Int32> pi;
Boolean *pb; // => interior_ptr<Boolean> pb;
E *pe;       // => interior_ptr<E> pe; // Enumeration
```

Předdefinované typy nejsou považovány za spravované typy, i když bude sloužit jako aliasy pro typy v rámci `System` oboru názvů. Proto následující mapování uchovávat true mezi spravovaných rozšíření a nové syntaxe:

```
int * pi;     // => int* pi;
int __gc * pi2; // => interior_ptr<int> pi2;
```

Při překládání `V*` v existující aplikaci, je vždy zapnout nejrestriktivnější strategie `interior_ptr<V>`. To je, jak byla vyhodnocena v rámci spravovaného rozšíření. V nové syntaxi programátor má povolenou možnost omezení typu hodnoty na jiné spravované haldy adresy tak, že zadáte `V*` místo vnitřní ukazatel. Pokud při překladu programu, můžete provést tranzitivní uzavření všech jeho použití a ujistěte se, že není přiřazena žádná adresa ve spravované haldě, pak se v něm jako `V*` je v pořádku.

## <a name="pinning-pointers"></a>Přídavné ukazatele

Uvolňování paměti může volitelně přesunout objekty, které se nacházejí na haldě modulu CLR do různých umístění v rámci haldy, obvykle během fáze komprimace. Tento přesun není problém sledování popisovače, sledování odkazů a vnitřních ukazatelů, které transparentně aktualizovat tyto entity. Tento přesun je nějaký problém, ale pokud uživatel úspěšně prošel adresu objektu na haldě modulu CLR mimo prostředí runtime. V takovém případě volatile pohyb objektu je pravděpodobně způsobí selhání běhového prostředí. Vyloučené objekty takovéto z přesouvaných jsme musíte místně připínat je na jejich umístění v rozsahu vnějšího využití.

Ve spravovaných rozšíření *ukazatel Připnutí* deklaroval s prohlášením `__pin` – klíčové slovo. Tady je příklad mírně upravit ze spravovaných rozšíření specifikace:

```
__gc struct H { int j; };

int main()
{
   H * h = new H;
   int __pin * k = & h -> j;

   // ...
};
```

Do nového jazyka návrhu je Připnutí ukazatel deklarovaný pomocí syntaxe podobná vnitřní ukazatel.

```
ref struct H
{
public:
   int j;
};

int main()
{
   H^ h = gcnew H;
   pin_ptr<int> k = &h->j;

   // ...
}
```

Ukazatel připnutí v nové syntaxi je zvláštní případ vnitřní ukazatel. Zůstanou původní omezení na ukazatel Připnutí. Například nelze použít jako parametr nebo návratový typ metody; mohou být deklarovány pouze na místní objekt. Počet dalších omezení, ale byly přidány v nové syntaxi.

Výchozí hodnota ukazatel Připnutí je `nullptr`, nikoli `0`. A `pin_ptr<>` nejde inicializovat ani přiřadit `0`. Všechna přiřazení `0` v existujícím kódu bude nutné změnit tak, aby `nullptr`.

Ukazatel připnutí v rámci spravovaného rozšíření bylo povoleno adresovat celý objekt, jako v následujícím příkladu na základě specifikace spravovaného rozšíření:

```
__gc class G {
public:
   void incr(int* pi) { pi += 1; }
};
__gc struct H { int j; };
void f( G * g ) {
   H __pin * pH = new H;
   g->incr(& pH -> j);
};
```

V nové syntaxi, připínání celý objekt vrácený `new` výraz není podporován. Místo toho adresa vnitřní člen je potřeba připnout. Například

```
ref class G {
public:
   void incr(int* pi) { *pi += 1; }
};
ref struct H { int j; };
void f( G^ g ) {
   H ^ph = gcnew H;
   Console::WriteLine(ph->j);
   pin_ptr<int> pj = &ph->j;
   g->incr(  pj );
   Console::WriteLine(ph->j);
}
```

## <a name="see-also"></a>Viz také

[Hodnotové typy a jejich chování (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)<br/>
[pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)