---
title: "Zápis přetypování a úvod safe_cast&lt; &gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- casting
- C-style casts and /clr, motivation for new cast notation
- safe_cast keyword [C++]
ms.assetid: 4eb1d000-3b93-4394-a37b-8b8563f8dc4d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 80d1a6e8b1a1691b4e76bfdc1232c95c22d01408
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cast-notation-and-introduction-of-safecastltgt"></a>Zápis přetypování a úvod safe_cast&lt;&gt;
Zápis přetypování změnil ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 Úprava existující strukturu je jiné a obtížnější prostředí než vytvoření počáteční struktury. Existují méně stupeň volnosti a řešení obvykle ke kompromisu mezi ideální změnu struktury a co je to bude možné daná existující strukturální závislosti.  
  
 Jazyková rozšíření je další příklad. Zpět v časná 1990s jako objektově orientované programování se aktivovala důležité zlepší, stala potřebu přetypování dolů budovy bezpečnost typů v jazyce C++ stiskněte. Přetypování dolů je uživatel explicitní převod ukazatele základní třídy nebo odkaz na ukazatel nebo odkaz odvozené třídy. Přetypování dolů vyžaduje explicitní přetypování. Důvodem je, že skutečný typ ukazatele základní třídy je aspektem modulu runtime; Kompilátor proto nelze zkontrolovat ho. Nebo jinak řečeno, budovy přetypování dolů, stejně jako volání virtuální funkce, vyžaduje určitou formu dynamické řešení. To vyvolává dvě otázky:  
  
-   Proč by měl přetypování dolů být nutné v zlepší objektově orientované? Není dostatek virtuální funkce mechanismus? To znamená, proč nelze jedna deklarace identity, nutnost přetypování dolů (nebo převodu jakéhokoli druhu) je selhání návrhu?  
  
-   Proč by se podpoře přetypování dolů jednat o problém v jazyce C++? Po všech se nejedná o problém v objektově orientované jazyků, například Smalltalk (nebo následně, Java a C#)? Co je to v jazyce c++ je podpora budovy přetypování dolů obtížné?  
  
 Virtuální funkce představuje řadu typy závislá na zvoleném typu algoritmus, který je běžné. (Jsme nejsou zvažování rozhraní, které nejsou podporovány v ISO-C++, ale jsou k dispozici v CLR – programování a které představují alternativu zajímavé návrhu). Návrh této rodiny je obvykle reprezentována hierarchie tříd, ve kterém je abstraktní základní třídu deklarace společné rozhraní (virtuální funkce) a sadu konkrétních odvozených tříd, které představují skutečné typy rodiny v aplikaci domény.  
  
 A `Light` hierarchie v počítači generované dokumentů (CGI) aplikace, například bude mít běžné atributy, jako `color`, `intensity`, `position`, `on`, `off`a tak dále. Několik indikátory jeden můžete řídit pomocí společné rozhraní bez obav, zda je konkrétní lehký spotlight, směrové, nesměrové (Považujte sun) nebo možná lehkým reflektor. V takovém případě je zbytečné přetypování dolů na konkrétní typ light vykonávat své virtuální rozhraní. V produkčním prostředí ale rychlost je nezbytné. Jeden může přetypování dolů a explicitně vyvolat každou metodu Pokud pomocí tohoto postupu, vložené spouštění volání lze provést místo použití virtuálního mechanismu.  
  
 Ano jeden důvodem přetypování dolů v jazyce C++ je potlačit virtuálního mechanismu výrazné zvýšení výkonu modulu runtime. (Všimněte si, že automatizace této ruční optimalizace je aktivní oblastí výzkumu. Je však obtížnější než nahrazení explicitní použití vyřešit `register` nebo `inline` – klíčové slovo.)  
  
 Druhý důvod pro přetypování dolů spadá mimo duální povaha polymorfismus. Jedním ze způsobů zamyslet nad Polymorfismus je rozdělení na pasivní a dynamické páry formulářů.  
  
 Virtuální volání (a budovy přetypování dolů) představuje dynamické polymorfismus použití: jeden provádí akci založenou na skutečný typ ukazatele základní třídy na tuto konkrétní instanci při provádění tohoto programu.  
  
 Přiřazení objektu odvozené třídy k jeho základní třída ukazatele, ale je pasivní formu polymorfismus; používá polymorfismus jako přenosového mechanismu. Toto je hlavní použití `Object`, například v programování CLR. Při pasivním použití ukazatele základní třídy zvolené pro přenos a ukládání obvykle poskytuje rozhraní, které je příliš abstraktní. `Object`, například poskytuje přibližně pět metod prostřednictvím svého rozhraní; žádné zvláštní chování vyžaduje explicitní přetypování dolů. Například pokud nám chcete upravit úhel našich spotlight nebo jeho rychlost patří vypnout, budeme muset přetypování dolů explicitně. Virtuální rozhraní v rámci rodiny podtypů prakticky nemůže být nadmnožinou všechny možné metody podřízené mnoho, a proto budovy přetypování dolů bude vždy potřeba v rámci objektově orientovaný jazyk.  
  
 Pokud sejfu přetypování dolů zařízení je potřeba v jazyce objektově orientované, pak proč trvalo C++ tak dlouho okna Přidat? Problém je v tom, jak zpřístupnit informace o tom, běhového typu ukazatele. V případě virtuální funkci informace o běhu nastavená ve dvou částech kompilátorem:  
  
-   Objekt třídy obsahuje člena ukazatel další virtuální tabulku (buď na začátku nebo na konec objektu třídy; to je zajímavé historie má sama o sobě), který se týká příslušnou virtuální tabulku. Například objekt spotlight adresy virtuální tabulku spotlight, směrové, směrovou světla virtuální tabulku a tak dále  
  
-   Každý virtuální funkce má přidružené pevné slot v tabulce a skutečná instance pro vyvolání je reprezentována adresu uložená v tabulce. Například virtuální `Light` destruktor může být přidružen k pozici 0, `Color` s pozice 1 a tak dále. Toto je efektivní, pokud je pevná strategie, protože je nastavený při kompilaci a představuje minimální režii.  
  
 Problém, pak je zpřístupnění informací o typu ukazatele bez změny velikosti ukazatelů C++, buď přidáním druhou adresu, nebo přímo přidáním nějaká typ kódování. To nebude přijatelné pro programátory (a programy), nechcete používat zlepší objektově orientované – což se stále dominantní komunita uživatelů. Další možností bylo zavést zvláštní ukazatel pro typy polymorfní třídy, ale to by být matoucí a činit obtížné mezi kombinovat dva, zejména s problémy aritmetika ukazatele. Nebylo by také přijatelné udržovat běhu tabulku, která přidruží každý ukazatel typ aktuálně přidružené a dynamicky ji aktualizovat.  
  
 Problém je pár komunit uživatelů, které mají odlišné, ale legitimní programovací cíli. Řešení musí být kompromis mezi dvěma komunity, tím umožňuje jejich pouze jejich aspiraci, ale umožňuje vzájemnou spolupráci. To znamená, že by mohly být je nemožné řešení, které nabízí obou stranách a implementované řešení nakonec být menší než úplně bez chyby. Skutečná řešení se pohybuje kolem definice polymorfní třídy: polymorfní třídy je ten, který obsahuje virtuální funkce. Polymorfní třídy podporuje dynamické typově bezpečné přetypování dolů. Problém byl vyřešen zachování the ukazatele jako adresy proto, že všechny polymorfní třídy obsahují další člen ukazatele k jejich přidružené virtuální tabulce. Přidružený typ informace, proto může být uloženy v strukturu rozšířené virtuální tabulku. Náklady na přetypování dolů typ safe je (téměř) lokalizovaná k uživatelům zařízení.  
  
 Dalším problémem s přetypování dolů typ safe se její syntaxe. Protože je přetypování, původní návrh výbor ISO C++ použít syntaxi prostým přetypování, jako v následujícím příkladu:  
  
```  
spot = ( SpotLight* ) plight;  
```  
  
 ale to byl odmítnut výbor, protože neumožňuje uživateli řídit náklady na přetypování. Pokud má dynamické typ safe přetypování dolů stejnou syntaxi jako dříve unsafe, ale statické zápis přetypování, pak se změní na nahrazení a uživatel má schopnost potlačit režii modulu runtime, když je zbytečné a pravděpodobně příliš nákladné.  
  
 Obecně platí v jazyce C++, je vždy mechanismus jak potlačit funkce kompilátoru podporované. Například můžeme virtuální mechanismus vypnout buď pomocí operátoru rozsahu třídy (`Box::rotate(angle)`) nebo vyvoláním virtuální metody prostřednictvím objektu třídy (nikoli ukazatel nebo odkazu této třídy). Této druhé potlačení není vyžadován na základě jazyka, ale je kvalitou problému, implementace, podobně jako potlačení konstrukce dočasného v deklaraci ve tvaru:  
  
```  
// compilers are free to optimize away the temporary  
X x = X::X( 10 );  
```  
  
 Tak, aby Návrh pořízení zpět k dalšímu zvážení a považovány za několik alternativní zápisy a ta k výbor byla ve formě (`?type`), která uvedena jeho neurčenou – to znamená, dynamické povahy. To dalo uživateli možnost přepnout mezi dvěma formuláři - statickou nebo dynamickou – ale nikdo je příliš s radostí s ním. Aby bylo zpět na panelu Kreslení. Třetí a úspěšný zápis je teď standardní `dynamic_cast<type>`, který byl zobecněn na sadu čtyř notací přetypování nového stylu.  
  
 V ISO-C++ `dynamic_cast` vrátí `0` při použít na nevhodný typ ukazatele a vyvolá výjimku `std::bad_cast` výjimka při použití odkazového typu. Ve spravovaných rozšíření jazyka C++ použití `dynamic_cast` typu spravovaný odkaz (z důvodu jeho znázornění ukazatelem) vždy vrátí `0`. `__try_cast<type>`byl představen jako analogie s variantou vyvolávající výjimky `dynamic_cast`, s tím rozdílem, že vyvolává `System::InvalidCastException` pokud přetypování selže.  
  
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
  
 V nové syntaxe `__try_cast` znovu byla vydána jako `safe_cast`. Zde je stejného fragmentu kódu v nové syntaxe:  
  
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
  
 Ve spravovaném světě je potřeba povolit ověřitelný kód omezením schopnosti programátorů přetypovat mezi typy způsoby, které nechte neověřitelný kód. Toto je zásadní aspekt dynamické programování zlepší reprezentována nové syntaxe. Z tohoto důvodu instance přetypování starého stylu jsou přepracována interně jako běhu přetypování tak, aby například:  
  
```  
// internally recast into the   
// equivalent safe_cast expression above  
( array<ItemVerb^>^ ) verbList->ToArray( ItemVerb::typeid );   
```  
  
 Na druhé straně protože polymorfismus poskytuje aktivní a pasivní režim, je někdy nutné provést přetypování dolů právě k získání přístupu k rozhraní API bez virtuální podtypu. Tato situace může nastat, například s členy třídy chcete adresu všechny zadejte v rámci hierarchie (pasivní polymorfismus jako přenosový mechanismus), ale pro který se označuje skutečného instance v rámci určitého programu kontextu. V takovém případě může kontrola běhu přetypování být nepřijatelné režijní náklady. Pokud nové syntaxe, která bude sloužit jako spravované systémy programovací jazyk, je nutné zadat některé prostředky, umožňující v čase kompilace (to znamená, statické) přetypování dolů. To je důvod, proč použití `static_cast` zápis povoleno pro zachování přetypování dolů v době kompilace:  
  
```  
// ok: cast performed at compile-time.   
// No run-time check for type correctness  
static_cast< array<ItemVerb^>^>(verbList->ToArray(ItemVerb::typeid));  
```  
  
 Problém je, že žádný způsob, jak zaručit, že to programátorů `static_cast` správný a úmyslného; to znamená, neexistuje žádný způsob, jak vynutit spravovaného kódu ověřené. To je urgentnější zájmem v dynamické program zlepší než nativního, ale není dostatečná systému programovací jazyk pro Zakáže uživateli možnost přepnout mezi statické a běhu přetypování.  
  
 Depeše výkonu a nebezpečí v nové syntaxe, ale nastane. V nativním programování není žádný rozdíl ve výkonu mezi zápis přetypování stylu starý a nový styl `static_cast` zápis. Ale v nové syntaxe je výrazně dražší než použití nového stylu zápis přetypování starého `static_cast` zápis. Důvodem je, že kompilátor interně transformuje použití starého zápisu do běhu zkontrolujte, zda vyvolá výjimku. Kromě toho také změní profil spuštění kódu protože způsobuje, že nezachycená výjimka dolů aplikace – možná uvážlivě, ale nebude stejná chyba způsobit této výjimky, pokud `static_cast` použit zápis. Někdo může uvádět, že to pomůže produkčním uživatelům v notaci nového stylu. Ale pouze v případě, že selže; jinak, může to způsobit programy, které používají starého zápisu poběží výrazně pomaleji bez viditelné znalosti příčiny, podobně jako následující nástrahy programátorů:  
  
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
 [Obecné jazykové změny (C + +/ CLI)](../dotnet/general-language-changes-cpp-cli.md)   
 [Přetypování ve stylu jazyka pomocí možnosti/CLR (C + +/ CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)   
 [safe_cast](../windows/safe-cast-cpp-component-extensions.md)