---
title: Zápis přetypování a úvod safe_cast&lt; &gt; | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- casting
- C-style casts and /clr, motivation for new cast notation
- safe_cast keyword [C++]
ms.assetid: 4eb1d000-3b93-4394-a37b-8b8563f8dc4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 88e8165bde08b65b4f078c4b48863c2088132fca
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427859"
---
# <a name="cast-notation-and-introduction-of-safecastltgt"></a>Zápis přetypování a úvod do operace safe_cast&lt;&gt;

Zápis přetypování změnil ze spravovaného rozšíření jazyka C++ pro Visual C++.

Úprava existující strukturu je jiné a obtížnější prostředí než vytvoření počáteční struktury. Existují menší počet stupňů volnosti a začne blížit ke kompromis mezi ideální Změna struktury a co je to proveditelné vzhledem existujícího závislosti strukturální řešení.

Rozšíření jazyka je další příklad. Zpět v rané fázi 1990s jako objektově orientované programování začal být důležité paradigma, potřebu zařízení downcast zajišťující bezpečnost typů v jazyce C++ se stisknutím klávesy. Přetypování na nižší je uživatel explicitního převodu ukazatele základní třídy nebo odkaz na ukazatel nebo odkaz na odvozené třídy. Přetypování na nižší, vyžaduje explicitní přetypování. Důvodem je, že skutečný typ ukazatele základní třídy je určitý aspekt modulu runtime; Kompilátor proto nelze zkontrolovat ho. Nebo jinak řečeno, jeho přetypování směrem dolů zařízení, stejně jako volání virtuální funkce, vyžaduje určitou formu dynamické řešení. To vyvolá dvě otázky:

- Proč by měl být downcast nezbytné v objektově orientované paradigma? Není dostatek mechanismu virtuální funkce? To znamená, proč nelze jedna deklarace identity, že všechny potřeby pro přetypování dolů (nebo výraz přetypování jakéhokoli druhu) je selhání návrhu?

- Proč by měl podporu přetypování dolů se jednat o problém v jazyce C++? Koneckonců, není problém v objektově orientované jazyků, jako jsou Smalltalk (nebo následně, Java a C#)? Co je to o jazyce C++, které podpora zařízení downcast obtížné?

Virtuální funkce představuje běžné algoritmu závislé na typu rodinu typů. (Jsme nejsou zvážení rozhraní, které nejsou podporovány v ISO-C++, ale jsou k dispozici v CLR programování a které představují alternativní zajímavé návrh). Návrh dané řadě obvykle představuje hierarchie třídy, ve kterém je abstraktní základní třída deklarace společné rozhraní (virtuální funkce) a sadu konkrétních odvozených tříd, které představují skutečná řady typů v aplikaci domény.

A `Light` hierarchie v počítači generované Trénováním CGI () doméně aplikace, například mají společné atributy, jako `color`, `intensity`, `position`, `on`, `off`, a tak dále. Několik světlo, jeden můžete řídit pomocí společného rozhraní bez obav, jestli je konkrétní světla spotlightu, směrové světlo, jiné směrové světlo (zvažte slunce) nebo možná reflektor světla. V takovém případě je zbytečné přetypování na nižší pro konkrétní typ světla vykonávat své virtuální rozhraní. V produkčním prostředí ale rychlost je nezbytné. Jeden může jeho přetypování směrem dolů a explicitně volat jednotlivé metody Pokud tímto způsobem tak provést přiřazeného provedení volání namísto použití mechanismu virtuální.

Jedním z důvodů pro přetypování směrem dolů v jazyce C++ je tedy potlačit virtuálního mechanismu výrazné zvýšení výkonu modulu runtime. (Upozorňujeme, že automatizace této ruční optimalizace aktivní oblasti výzkumu. Je ale obtížnější než nahrazení explicitní použití řešení `register` nebo `inline` – klíčové slovo.)

Druhý důvod pro přetypování směrem dolů nespadala duální povaze polymorfismu. Jedním ze způsobů Zamyslete se nad Polymorfismus je rozdělené do pár pasivní a dynamických formulářů.

Virtuální volání (a zařízení downcast) představuje dynamické použití polymorfismu: jeden provádí akce v závislosti na skutečný typ ukazatele základní třídy na tuto konkrétní instanci za běhu programu.

Přiřazení objektu odvozené třídy jeho ukazatele základní třídy, ale je pasivní formu polymorfismus; Polymorfismus používá jako mechanismus přenosu. Toto je hlavní použití `Object`, například v CLR programování. Když se použije jenom pasivně, ukazatele základní třídy, které jste zvolili pro přenos a úložiště obvykle nabízí rozhraní, které je příliš abstraktní. `Object`, například poskytuje zhruba pět metod pomocí rozhraní; jakékoli další specifické chování vyžaduje explicitní přetypování směrem dolů. Například pokud chcete nastavit úhel našem výběru nebo vlastní sazby fall vypnout, by musíme downcast explicitně. Virtuální rozhraní v rámci rodiny podtypy prakticky nemůže být nadmnožinou všechny možné metody jeho mnoho podřízených objektů a proto jeho přetypování směrem dolů zařízení bude vždy potřeba v rámci objektově orientovaný jazyk.

Pokud bezpečný downcast zařízení je potřeba v objektově orientovaný jazyk, a proč ho trvala C++ tak dlouho pro přidání jednoho? Problém spočívá v tom, jak zpřístupnit informace o tom, run-time typu ukazatele. V případě virtuální funkce běhových informací je nastavení ve dvou částech kompilátorem:

- Objekt třídy obsahuje další virtuální tabulky ukazatele člena (buď na začátku nebo konci objektu třídy; to je zajímavé historie sám o sobě), který zajišťuje odpovídající virtuální tabulky. Například objekt spotlight adresy spotlight virtuální tabulky, směrové světlo, směrové světlo virtuální tabulku a tak dále

- Každá virtuální funkce má přiřazený oprava slot v tabulce a skutečná instance pro vyvolání je reprezentována adrese uložené v tabulce. Například virtuální `Light` destruktor může být přidružen k slot 0, `Color` s pozice 1 a tak dále. To je efektivní, pokud je pevná strategie, protože je nastavený v době kompilace a představuje minimální režií.

Problém, pak je postup zpřístupnění informací o typu ukazatel beze změny velikosti ukazatele C++ tak, že přidáte druhý adresu nebo po přímém přidání nějaký druh typu kódování. To by být přijatelné pro programátory (a aplikace), který rozhodnot nepoužívat objektově orientované paradigma – což byla stále dominantní komunita uživatelů. Další možností byla k uvození zvláštní ukazatele pro typy polymorfní třídy, ale to by být matoucí a nastavte ji ztěžovalo dvě, zejména s problémy aritmetiku ukazatele. Nebylo by také přijatelné pro údržbu tabulky za běhu, která přidružuje každý ukazatel jeho aktuálně přidruženého typu a dynamicky aktualizuje.

Problém je pár komunit uživatelů, které mají odlišné, ale legitimní programovací cíli. Řešení musí být kompromis mezi dvěma komunit, umožňující každé pouze jejich aspiraci, ale umožňuje vzájemnou spolupráci. To znamená, že by mohly být neřešitelné řešení nabízená na obou stranách a toto řešení je implementované nakonec bude menší než ideální. Skutečné rozlišení zásadní kolem definice polymorfní třídy: polymorfní třídy je ten, který obsahuje virtuální funkce. Polymorfní třídy podporuje dynamické typově přetypování směrem dolů. Problém byl vyřešen zachovat--ukazatel jako adresa vzhledem k tomu, že všechny polymorfní třídy obsahují tohoto člena další ukazatel na jejich přidružené virtuální tabulku. Přidružený typ informace, proto může být uloženy v struktury rozšířené virtuální tabulky. Náklady na typově bezpečné přetypování směrem dolů je lokalizován (téměř) pro uživatele zařízení.

Další problém s typově bezpečné přetypování směrem dolů se její syntaxe. Protože se jedná přetypování, původní návrh výboru ISO-C++ používá syntaxi prostým přetypování, jako v následujícím příkladu:

```
spot = ( SpotLight* ) plight;
```

ale to byl odmítnut výbor, protože neumožňuje uživateli řídit náklady přetypování. Pokud dynamické typově bezpečné přetypování směrem dolů má stejnou syntaxi jako dříve unsafe, ale statický zápis přetypování a pak stane nahrazení a uživatel nemá schopnost potlačit nároky na modul runtime, když je pravděpodobně příliš nákladné a zbytečné.

Obecně platí v jazyce C++ je vždycky mechanismus, pomocí kterého můžete potlačit funkce podporované kompilátorem. Například můžeme virtuální mechanismus vypnout s použitím operátoru oboru třídy (`Box::rotate(angle)`) nebo vyvoláním virtuální metody prostřednictvím objektu třídy (spíše než ukazatel nebo odkaz této třídy). Tento druhý potlačení není vyžadováno pro jazyk, ale je kvalitu implementace problém, podobně jako potlačení konstrukce dočasných v deklaraci ve tvaru:

```
// compilers are free to optimize away the temporary
X x = X::X( 10 );
```

Návrh se dostanete zpět k dalšímu zvážení a byla zvážena alternativní několik zápisy, takže ten vrátili výboru byla ve formě (`?type`), které označeny jeho neurčenou – to znamená, Dynamická povaha. To dalo schopnost přepínat mezi dvě různými formami – statické nebo dynamické – uživatel, ale nikdo se příliš opravdu radost, že s ním. Proto se zpět do panelu Kreslení. Třetí a úspěšný zápis je nyní standardní `dynamic_cast<type>`, který byl zobecněn na sadu čtyři notací nový styl přetypování.

V ISO-C++ `dynamic_cast` vrátí `0` při použít na nevhodný typ ukazatele a vyvolá výjimku `std::bad_cast` výjimka při použití pro typ odkazu. Ve spravovaných rozšíření jazyka C++ použití `dynamic_cast` na typ pro spravované referenční materiály (z důvodu jeho reprezentaci ukazatele) vždy vrátí `0`. `__try_cast<type>` byla zavedená jako analogie výjimku vyvolání variant `dynamic_cast`, s tím rozdílem, že ji vyvolá `System::InvalidCastException` pokud přetypování selže.

```
public __gc class ItemVerb;
public __gc class ItemVerbCollection {
public:
   ItemVerb *EnsureVerbArray() [] {
      return __try_cast<ItemVerb *[]>
         (verbList->ToArray(__typeof(ItemVerb *)));
   }
};
```

V nové syntaxi `__try_cast` byla přepracována jako `safe_cast`. Tady je stejného fragmentu kódu v nové syntaxi:

```
public ref class ItemVerb;
public ref class ItemVerbCollection {
public:
   array<ItemVerb^>^ EnsureVerbArray() {
      return safe_cast<array<ItemVerb^>^>
         ( verbList->ToArray( ItemVerb::typeid ));
   }
};
```

Ve spravovaném světě je potřeba povolit ověřitelný kód tím, že omezíte možnost programátorů přetypování mezi typy takovým způsobem, který ponechte neověřitelný kód. Toto je důležitý aspekt dynamické programovacího paradigmatu reprezentována nové syntaxe. Z tohoto důvodu výskyty přetypování ve starém stylu jsou přepracována interně jako přetypování za běhu, takže, například:

```
// internally recast into the
// equivalent safe_cast expression above
( array<ItemVerb^>^ ) verbList->ToArray( ItemVerb::typeid );
```

Na druhé straně protože polymorfismus obsahuje aktivní a pasivní režim, je někdy potřeba provést jenom pro získání přístupu k rozhraní API nevirtuální podtypu downcast. Tato situace může nastat, například s členy třídy, který chcete adresu každém typu v rámci hierarchie (pasivní polymorfismu jako mechanismus přenosu), ale pro který se označuje aktuální instanci v kontextu konkrétní aplikace. V takovém případě může kontrola běhu přetypování být nepřijatelné režijní náklady. Pokud novou syntaxi má sloužit jako spravovaných systémech programovací jazyk, musíte zadat některé prostředky, umožňující za kompilace (tedy statické) jeho přetypování směrem dolů. To je důvod, proč použití `static_cast` zápis můžou zůstat přetypování směrem dolů v době kompilace:

```
// ok: cast performed at compile-time.
// No run-time check for type correctness
static_cast< array<ItemVerb^>^>(verbList->ToArray(ItemVerb::typeid));
```

Problém je, že neexistuje žádný způsob, jak zaručit, že programátorů to `static_cast` je správná a úmyslného; to znamená, že neexistuje žádný způsob, jak vynutit spravovanému kódu být možné ověřit. Urgentnější obavy za dynamické program paradigma než pod nativní, ale nestačí v rámci systému programovací jazyk pro Zakáže uživateli možnost přepínat mezi statické a za běhu přetypování.

Je depeše výkonu a trávení v nové syntaxi, ale. V nativním programování, není žádný rozdíl ve výkonu mezi zápisem přetypování ve stylu starý a nový styl `static_cast` zápis. Ale v nové syntaxi, je výrazně dražší než použití nový styl zápis přetypování ve starém stylu `static_cast` zápis. Důvodem je, že kompilátor transformuje interně pomocí starého typu notation na kontrolu za běhu, který vyvolá výjimku. Kromě toho také změní profilu spuštění kódu způsobí, že nezachycená výjimka dolů aplikace – možná uvážlivě, protože stejná chyba nezpůsobila tuto výjimku, pokud `static_cast` notation byly použity. Může být jeden tvrdí, že to pomůže produkčním uživatelům v notaci nový styl. Ale jenom v případě, že selže; v opačném případě by programy, které používají starého typu notation na výrazně pomalejší bez viditelné pochopení příčiny, podobně jako následující nástrahy programátorů:

```
// pitfall # 1:
// initialization can remove a temporary class object,
// assignment cannot
Matrix m;
m = another_matrix;

// pitfall # 2: declaration of class objects far from their use
Matrix m( 2000, 2000 ), n( 2000, 2000 );
if ( ! mumble ) return;
```

## <a name="see-also"></a>Viz také

[Obecné jazykové změny (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
[Přetypování C-Style s parametrem/CLR (C + +/ CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)<br/>
[safe_cast](../windows/safe-cast-cpp-component-extensions.md)