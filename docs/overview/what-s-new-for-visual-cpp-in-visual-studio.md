---
title: Co je nového v C++ v sadě Visual Studio
ms.date: 11/15/2017
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.openlocfilehash: bdf9775702b2c7099bcacc82fd462e3c1ff245bc
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786759"
---
# <a name="whats-new-for-c-in-visual-studio-2017"></a>Co je nového v C++ v sadě Visual Studio 2017

Visual Studio 2017 přináší řadu vylepšení a oprav prostředí C++. Jsme opravili víc než 250 chyb a nahlášených problémů v kompilátoru a nástrojů, řadu z nich odeslali zákazníci přes [nahlásit problém](/visualstudio/how-to-report-a-problem-with-visual-studio-2017) a [poslat návrh](https://visualstudio.uservoice.com/) možnosti v části **odeslat zpětnou vazbu** . Děkujeme vám, že hlásíte chyby! Další informace o tom, co je nového v celé sady Visual Studio, navštivte [co je nového v sadě Visual Studio 2017](/visualstudio/ide/whats-new-in-visual-studio).

<!--The compiler and tools version number in Visual Studio 2017 is 14.10.24629. -->

## <a name="c-compiler"></a>kompilátor C++

### <a name="c-conformance-improvements"></a>Vylepšení shody C++

V této verzi jsme kompilátor jazyka C++ a standardní knihovny doplnili rozšířenou podporou pro funkce C++11 a C++14, a také předběžnou podporou pro některé funkce očekávané ve standardu C++17. Podrobné informace najdete v tématu [vylepšení shody C++ v sadě Visual Studio 2017](cpp-conformance-improvements-2017.md).

**Visual Studio 2017 version 15.5**: Kompilátor podporuje přibližně 75 % funkcí, které jsou nové v C ++ 17, včetně strukturovaných vazeb `constexpr` výrazy lambda, `if constexpr`, vložených proměnných, přeložte výrazy a přidání `noexcept` do systému typů. Tyto jsou dostupné v rámci **/std: c ++ 17** možnost. Další informace najdete v tématu [vylepšení shody C++ v sadě Visual Studio 2017](cpp-conformance-improvements-2017.md)

**Visual Studio 2017 version 15.7**: Sada nástrojů kompilátoru MSVC v sadě Visual Studio verze 15.7 nyní odpovídá standardu jazyka C++. Další informace najdete v tématu [Announcing: MSVC splňuje C++ Standard](https://blogs.msdn.microsoft.com/vcblog/2018/05/07/announcing-msvc-conforms-to-the-c-standard/) a [shoda jazyka C++ společnosti Microsoft](visual-cpp-language-conformance.md).

### <a name="new-compiler-options"></a>Nové možnosti kompilátoru

- [/permissive-](../build/reference/permissive-standards-conformance.md): Povolit všechny možnosti kompilátoru shoda přísné standardy a zakázat většina kompilátoru rozšíření specifické pro společnost Microsoft (ale ne `__declspec(dllimport)`, například). Tato možnost zapnutá ve výchozím nastavení v sadě Visual Studio 2017 verze 15.5.  **/ Permissive-** režim přizpůsobení zahrnuje podporu pro dvoufázové vyhledávání názvů. Další informace najdete v tématu [vylepšení shody C++ v sadě Visual Studio 2017](cpp-conformance-improvements-2017.md).

- [/ Diagnostics](../build/reference/diagnostics-compiler-diagnostic-options.md): Povolte zobrazení číslo řádku, číslo řádku a sloupce, nebo číslo řádku a sloupce a blikající kurzor pod řádkem kódu, kde byla nalezena diagnostických chyb nebo upozornění.

- [/ Debug: fastlink](../build/reference/debug-generate-debug-info.md): Povolit až 30 % rychlejší přírůstkové propojení vyprší (vs. Visual Studio 2015) není zkopírováním všechny informace o ladění do souboru PDB. Soubor PDB se místo toho odkazuje na informace o ladění pro soubory objektů a knihovny použité k vytvoření spustitelného souboru. Zobrazit [cyklus v sadě Visual Studio "15" s/Debug: fastlink sestavení C++ rychleji](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/faster-c-build-cycle-in-vs-15-with-debugfastlink/) a [doporučení k urychlení sestavení C++ v sadě Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2016/10/26/recommendations-to-speed-c-builds-in-visual-studio/).

- Visual Studio 2017 umožňuje používat [/SDL](../build/reference/sdl-enable-additional-security-checks.md) s [/ await](../build/reference/await-enable-coroutine-support.md). Odebrali jsme [/RTC](../build/reference/rtc-run-time-error-checks.md) omezení u Korutin.

   **Visual Studio 2017 version 15.3**:

- [/ std: c ++ 14 a/std: c ++ nejnovější](../build/reference/std-specify-language-standard-version.md): Tyto možnosti kompilátoru umožňují vyjádřit výslovný souhlas pro konkrétní verze ISO C++ programovací jazyk v projektu. Většina konceptu nové funkce na úrovni standard jsou strážený **/std: c ++ nejnovější** možnost.

- [/ std: c ++ 17](../build/reference/std-specify-language-standard-version.md) umožňuje sadu funkcí C ++ 17 implementované kompilátorem. Tato možnost zakáže kompilátoru a standardní knihovny podpora pro funkce, které se mění nebo nového ve verzích konceptu práce a defect aktualizace standardu jazyka C++ za C ++ 17. Chcete-li povolit tyto funkce, použijte **/std: c ++ nejnovější**.

### <a name="codegen-security-diagnostics-and-versioning"></a>CODEGEN, zabezpečení, Diagnostika a správa verzí

Tato verze přináší několik vylepšení optimalizace, generování kódu, nástrojů pro správu verzí a Diagnostika. Mezi důležitá vylepšení patří:

- Generování vylepšené kódu smyček: Podpora automatické vektorizace dělení konstantních celých čísel, lepší identifikace vzorů memset.
- Vylepšené kód zabezpečení: Vylepšená emise diagnostiky kompilátoru přetečení vyrovnávací paměti, a [/Guard: CF](../build/reference/guard-enable-control-flow-guard.md) teď chrání příkazy switch, které generují tabulku skoků.
- Správa verzí: Hodnota předdefinované makro preprocesoru  **\_MSC\_VER** je nyní monotónně aktualizují při každé aktualizaci nástrojů Visual C++. Další informace najdete v tématu [verze kompilátoru Visual C++](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/visual-c-compiler-version/).
- Nové rozložení sady nástrojů: Kompilátor a nástroje pro související sestavení mají novou strukturu umístění a adresáře na vývojovém počítači. Nové rozložení umožňuje-souběžnými instalacemi více verzí kompilátoru. Další informace najdete v tématu [kompilátoru rozložení nástroje v sadě Visual Studio "15"](https://blogs.msdn.microsoft.com/vcblog/2016/10/07/compiler-tools-layout-in-visual-studio-15/).
- Vylepšená Diagnostika: V okně výstupu teď zobrazuje sloupec, kde dojde k chybě. Další informace najdete v tématu [vylepšení diagnostiky kompilátoru C++ v sadě Visual Studio "15" Preview 5](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-compiler-diagnostics-improvements-in-vs-15-rc/).
- Při používání společných rutin, experimentální klíčové slovo **yield** (k dispozici v rámci **/ await** možnost) byla odebrána. Váš kód by měl být aktualizován na použití `co_yield` místo. Další informace najdete v [Blogu týmu Visual C++](https://blogs.msdn.microsoft.com/vcblog/).

**Visual Studio 2017 version 15.3**:

Další vylepšení diagnostiky v kompilátoru. Další informace najdete v tématu [vylepšení diagnostiky v sadě Visual Studio 2017 15.3.0](https://blogs.msdn.microsoft.com/vcblog/2017/07/21/diagnostic-improvements-in-vs2017-15-3-0/).

**Visual Studio 2017 version 15.5**:

Výkon sady Visual C++ runtime neustále zlepšuje kvůli lepší kvalitu generovaného kódu. To znamená, že můžete jednoduše znovu zkompilovat kód a vaše aplikace běží rychleji. Některé optimalizace kompilátoru jsou úplně nové, jako je například vektorizaci podmíněných skalárních úložišť, kombinování volání `sin(x)` a `cos(x)` do nového `sincos(x)`a odstranění redundantní pokyny od Optimalizátor SSA. Další optimalizace kompilátoru jsou vylepšení stávajících funkcí, jako je například heuristiku vektorizéru pro podmíněné výrazy, lepší optimalizace smyčky a plovoucí codegen min/max. Propojovací program má nový a rychlejší **/OPT:ICF** implementaci, což může mít za následek až 9 % urychlení propojení a existují další opravy výkonu v přírůstkové propojení. Další informace najdete v tématu [/OPT (optimalizace)](../build/reference/opt-optimizations.md) a [Parametr/incremental (Inkrementální odkaz)](../build/reference/incremental-link-incrementally.md).

Kompilátor Microsoft C++ podporuje společnosti Intel AVX-512, včetně instrukcí pro délku vektoru, které přinášejí nové funkce v AVX-512 do 128 - a 256bitových širokých registrů.

[/Zc:noexceptTypes-](../build/reference/zc-noexcepttypes.md) možnosti je možné vrátit zpět do C ++ 14 verze `noexcept` přitom C ++ 17 režim obecně. To vám umožní aktualizovat váš zdrojový kód tak, aby odpovídal C ++ 17, aniž byste museli přepsat všechny vaše `throw()` kódu ve stejnou dobu. Další informace najdete v tématu [odebrání specifikace dynamických výjimek a noexcept](cpp-conformance-improvements-2017.md#noexcept_removal).

**Visual Studio 2017 version 15.7**:

- Nový přepínač kompilátoru [/qspectre ](../build/reference/qspectre.md) zmírnit před útoky na straně kanálu spekulativního spouštění. Zobrazit [zmírnění hrozby Spectre v MSVC](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc/) Další informace.
- Nové diagnostické upozornění pro chyby zabezpečení Spectre migitation. Zobrazit [chyby zabezpečení Spectre diagnostiky v sadě Visual Studio 2017 verze 15.7 Preview 4](https://blogs.msdn.microsoft.com/vcblog/2018/04/20/spectre-diagnostic-in-visual-studio-2017-version-15-7-preview-4/) Další informace.
- Nová hodnota pro /Zc, **přepínače/Zc:**, opravte umožňuje vykazování podpory standard C++. Například pokud přepínač nastavený a kompilátor probíhá/std: c ++ 17 režimu rozšíří hodnotu **201703 L**. Zobrazit [MSVC nyní správně hlásí __cplusplus](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/msvc-now-correctly-reports-__cplusplus/) Další informace.

## <a name="c-standard-library-improvements"></a>Vylepšení standardní knihovny C++

- Vedlejší `basic_string` `_ITERATOR_DEBUG_LEVEL != 0` vylepšení diagnostiky. Přeskočení kontroly IDL v sadě řetězců teď oznámí konkrétní chování, které toto přeskočení způsobilo. Například místo zprávy oznamující, že iterátor řetězce nejde přesměrovat, se teď zobrazí zpráva s oznámením, že iterátor řetězce nejde přesměrovat, protože je mimo rozsah (např. je to koncový iterátor).
- Zlepšení výkonu: provedené `basic_string::find(char)` přetížení pouze volání `traits::find` po. Toto jsme dříve implementovali jako hledání obecného řetězce s délkou 1.
- Zlepšení výkonu: `basic_string::operator==` teď kontroluje velikost řetězce před porovnáním obsahů řetězců.
- Zlepšení výkonu: odebrali jsme párování v ovládacích `basic_string`, což bylo obtížné optimalizátoru k analýze. Všimněte si, že u všech krátkých řetězců volání `reserve` má stále nenulové náklady na neprovedení.
- Přidali jsme \<jakékoli\>, \<string_view\>, `apply()`, `make_from_tuple()`.
- `std::vector` přepracována pro vyšší výkon a správnost: aliasy při vkládání a uložení je nyní správně zpracovává jako vyžaduje Standard, záruka silné výjimky je nyní k dispozici pokud to vyžaduje Standard prostřednictvím `move_if_noexcept()` a další logiky a vložení nebo uložení provádí méně operací s prvky.
- Standardní knihovny C++ teď předchází přesměrování ukazatelů null.
- Přidání \<volitelné\>, \<variant\>, `shared_ptr::weak_type`, a \<cstdalign\>.
- Povolené C ++ 14 `constexpr` v `min(initializer_list)`, `max(initializer_list)`, a `minmax(initializer_list)`, a `min_element()`, `max_element()`, a `minmax_element()`.
- Vylepšené `weak_ptr::lock()` výkonu.
- Oprava `std::promise` operátor přiřazení přesunu, který dříve mohl způsobit zablokování kódu napořád.
- Oprava chyb kompilátoru s `atomic<T*>` implicitní převod na `T*`.
- `pointer_traits<Ptr>` nyní správně rozpozná `Ptr::rebind<U>`.
- Oprava chybějící `const` kvalifikátoru v `move_iterator` operátor odčítání.
- Oprava bezobslužné nesprávné funkce codegen pro stavové uživatelem definované alokátory vyžadující `propagate_on_container_copy_assignment` a `propagate_on_container_move_assignment`.
- `atomic<T>` Nyní toleruje přetížený `operator&()`.
- Pro zvýšení propustnosti kompilátoru hlavičky standardní knihovny C++ nyní Vyhněte se deklarace pro nepotřebné vnitřní funkce kompilátoru.
- Mírně Vylepšená Diagnostika kompilátoru pro nesprávná `bind()` volání.
- Vyšší výkon `std::string` a `std::wstring` konstruktorů přesunutí více než třikrát.

Úplný seznam standardní knihovny improvments najdete v článku [standardní knihovny řeší ve VS 2017 RTM](https://blogs.msdn.microsoft.com/vcblog/2017/02/06/stl-fixes-in-vs-2017-rtm/).

### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 version 15.3

#### <a name="c17-features"></a>Funkce c ++ 17

Několik dalších funkcí C ++ 17 byly implementovány. Další informace najdete v tématu [shoda jazyka Visual C++](cpp-conformance-improvements-2017.md#improvements_153).

#### <a name="other-new-features"></a>Další nové funkce

- Implementovat P0602R0 "variant a volitelné by měl rozšířit copy/move triviality".
- Standardní knihovna teď oficiálně toleruje dynamické RTTI, protože se zakázalo prostřednictvím [/GR-](../build/reference/gr-enable-run-time-type-information.md) možnost. Obě `dynamic_pointer_cast()` a `rethrow_if_nested()` ze své podstaty vyžadují `dynamic_cast`, takže se označuje jako standardní knihovna teď `=delete` pod **/GR-**.
- I když dynamické RTTI byl zakázán prostřednictvím **/GR-**, "statické RTTI" (ve formě `typeid(SomeType)`) je stále k dispozici a využívá několik součástí standardní knihovny. Standardní knihovna teď podporuje zakázání to také prostřednictvím **/D\_HAS\_statické\_RTTI = 0**. Všimněte si, že tato akce zakáže `std::any`, `target()` a `target_type()` členské funkce `std::function`a `get_deleter()` členskou funkci friend `std::shared_ptr` a `std::weak_ptr`.

#### <a name="correctness-fixes-in-visual-studio-2017-version-153"></a>Řeší správnost v sadě Visual Studio 2017 verze 15.3

- Standardní knihovny kontejnery nyní stažení jejich `max_size()` k `numeric_limits<difference_type>::max()` místo `max()` z `size_type`. To zajistí, že výsledek `distance()` na iterátorech z tohoto kontejneru je reprezentovatelné v návratovém typu `distance()`.
- Oprava chybějící specializace `auto_ptr<void>`.
- `for_each_n()`, `generate_n()`, A `search_n()` algoritmy dříve kompilace se nezdařila. Pokud délka argument nebyl uveden celočíselného typu; nyní pokusu o převod – neintegrální délky iterátory `difference_type`.
- `normal_distribution<float>` už vydá upozornění ve standardní knihovně o zúžení double uvolnění.
- Oprava některých `basic_string` operace, které byly výsledkem porovnání s `npos` místo `max_size()` při kontrole přetečení maximální velikosti.
- `condition_variable::wait_for(lock, relative_time, predicate)` by počkejte po celou dobu relativní v případě nesprávné probuzení. Nyní bude čekat pouze jeden interval relativní časové.
- `future::get()` Nyní zruší platnost `future`, jak vyžaduje standard.
- `iterator_traits<void *>` umožňuje být závažná chyba, protože se pokusil formuláře `void&`; nyní čistě stane prázdnou strukturu k povolení použití `iterator_traits` v "je iterátor" sfinae u podmínek.
- Upozornění hlášených Clang **wsystem –--headers** jsme vyřešili.
- Také vyřešili "specifikace výjimky v deklaraci neodpovídá předchozí deklaraci" hlášených Clang **- Wmicrosoft-výjimky spec**.
- Seznam inicializátorů paměť pořadí upozornění hlášených Clang a C1XX také vyřešili.
- Neseřazené kontejnery není možné Prohodit jejich hashers nebo predikáty když byli vyměněni kontejnery sami. Nyní dělají.
- Operace prohození mnoho kontejnerů jsou nyní označeny `noexcept` (jak naši standardní knihovnu nikdy si klade za cíl vyvolání výjimky, při zjištění non -`propagate_on_container_swap` bez rovná allocator nedefinované chování podmínky).
- Mnoho `vector<bool>` operace jsou nyní označeny `noexcept`.
- Standardní knihovna teď bude vynucovat odpovídající allocator `value_type` (v C ++ 17 režimu) s výslovného nesouhlasu s únikový poklop.
- Oprava některé podmínky, kde samoobslužné-range-insert into `basic_string` by promíchání obsahu řetězce. (Poznámka: standardní stále zakazuje automatické-range-insert into vektory.)
- `basic_string::shrink_to_fit()` je již nejsou ovlivněny přidělujícího modulu `propagate_on_container_swap`.
- `std::decay` nyní zpracovává typy abominable – funkce (například typy funkce, které jsou kvalifikovaný cv a/nebo kvalifikaci ref).
- Změnit direktiv použití správné rozlišování velikosti písmen a lomítka, zlepšit přenositelnost.
- Oprava upozornění C4061 "výčet"*enumerátor*"v přepnutí výčtu'*výčet*" není explicitně zpracován popisek případu ". Toto upozornění je mimo výchozí a byla stanovena jako výjimku do standardní knihovny obecné zásady pro upozornění. (Standardní knihovna je **/W4** vyčištění, ale nebude pokoušet o být **/Wall** vyčistit. Mnoho vypnout výchozím upozornění jsou extrémně hlučného a nejsou určeny k použití v pravidelných intervalech.)
- Vylepšené `std::list` ladění kontroly. Iterátory nyní zkontrolujte seznam `operator->()`, a `list::unique()` nyní označí iterátory jako zneplatněny.
- Oprava používá allocator metaprogramování v `tuple`.

#### <a name="performancethroughput-fixes"></a>Výkon/propustnost opravy

- Pracoval kolem interakce s `noexcept` která zabránila vkládání `std::atomic` implementace do funkce, které používají strukturované zpracování výjimek (SEH).
- Změněné standardní knihovně poškodilo vnitřní `_Deallocate()` funkce optimalizace na menší kód, což umožňuje být vloženy do více míst.
- Změnit `std::try_lock()` nahrazujícím rekurze rozšíření balíčku.
- Vylepšené `std::lock()` použití algoritmu předcházení zablokování `lock()` operace namísto pokryjte na `try_lock()` na všech zámků.
- Povolené optimalizace pojmenované vrácená hodnota v `system_category::message()`.
- `conjunction` a `disjunction` nyní vytvořit instanci N + 1 typů, aniž 2 n + 2 typy.
- `std::function` už vytvoří instanci stroje podporu alokátoru pro každý typu volatelná aplikacemi, zlepšení propustnosti a snížení velikosti .obj v aplikacích, které předávají mnoho různých výrazy lambda na `std::function`.
- `allocator_traits<std::allocator>` obsahuje ručně vložit `std::allocator` operace, snížení velikosti kódu v kódu, který komunikuje s `std::allocator` prostřednictvím `allocator_traits` pouze (to znamená, že v většinu kódu).
- Standardní knihovna teď zpracovává rozhraní C ++ 11 minimálních alokátorů volání `allocator_traits` přímo, namísto obtékání přidělujícího modulu do interní třídy `_Wrap_alloc`. To snižuje velikost kód generovaný pro podpory pro allocator, zvyšuje optimalizátoru schopnost argumentovat o kontejnery standardní knihovny v některých případech a poskytuje lepší možnosti ladění (jak je vidět typ alokátoru, spíše než `_Wrap_alloc<your_allocator_type>` v ladicí program).
- Odebrat metaprogramování upravené `allocator::reference`, které alokátorů nejsou povoleny ve skutečnosti k přizpůsobení. (Alokátory: můžete vytvářet kontejnery pomocí ukazatelů, ale ne nápadité odkazy.)
- Front-end kompilátoru se museli k rozbalení ladění iterátorů v rozsahu smyčky, zvýšení výkonu sestavení pro ladění.
- `basic_string` Interní zmenšení cestu pro `shrink_to_fit()` a `reserve()` již není v cestě přerozdělení operace, snížení velikosti kódu pro všechny členy mutující.
- `basic_string` Interní růst cestu již není v cestě `shrink_to_fit()`.
- `basic_string` Mutující operace jsou nyní promítnout do Rychlá cesta přidělení a přidělení pomalou cestou funkce, díky tomu je vyšší pravděpodobnost pro běžné bez opětovné se nedá vložit do volající.
- `basic_string` Mutace operace nyní konstrukce nevyčerpané vyrovnávací paměti v požadovaném stavu, spíše než změnu velikosti na místě. Například vkládání na začátku řetězce teď přesune obsah po vložení právě jednou (mimo provoz nebo na nově přidělenou vyrovnávací paměť), namísto dvakrát v případě reallocating (nově přidělené vyrovnávací paměti a potom dolů).
- Operace volání standardní knihovny jazyka C v \<řetězec\> nyní do mezipaměti `errno` adresu odebrat opakované interakce s TLS.
- Zjednodušená `is_pointer` implementace.
- Dokončení změn na základě funkce sfinae u výrazů k `struct` a `void_t`– na základě.
- Algoritmy standardní knihovny se postincrementing iterátory.
- Oprava zkrácení upozornění při použití 32-bit alokátorů v 64bitových systémech.
- `std::vector` Přesunutí přiřazení je teď mnohem efektivnější v případě jiných POCMA rovná allocator opětovným použitím vyrovnávací paměti, pokud je to možné.

#### <a name="readability-and-other-improvements"></a>Lepší čitelnost a další vylepšení

- Standardní knihovna teď používá C ++ 14 `constexpr` bezpodmínečně, namísto podmíněně definovaná makra.
- Standardní knihovna teď používá šablony aliasů interně.
- Standardní knihovna teď používá `nullptr` interně, nikoli z `nullptr_t{}`. (Interní využití NULL byla odstraněna. Interní využití 0 jako null právě prochází čištěním postupně.)
- Standardní knihovna teď používá `std::move()` interně, namísto stylistically zneužití `std::forward()`.
- Změnit `static_assert(false, "message")` k `#error message`. To zlepšuje diagnostiky kompilátoru, protože `#error` okamžitě přeruší kompilaci.
- Standardní knihovna již označí funkce jako `__declspec(dllimport)`. Moderní linkeru technologií už nevyžaduje to.
- Extrahované sfinae u pro výchozí argumenty šablony, což snižuje nepořádku v porovnání s návratové typy a typy argumentů funkce.
- Ladění se změnami \<náhodné\> teď použít obvyklé výbavu standardní knihovny, místo vnitřní funkce `_Rng_abort()` kterou volat `fputs()` k **stderr**. Implementace této funkce je se uchovávají po dobu binární kompatibilitu, ale byla odebrána v příští verzi binární nekompatibilní standardní knihovny.

### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15.5

Některé funkce standardní knihovny byly přidány, zastaralé nebo odebrání v souladu s standard C ++ 17. Další informace najdete v části [vylepšení shody C++ v sadě Visual Studio](cpp-conformance-improvements-2017.md#improvements_155).

#### <a name="new-experimental-features"></a>Nové seznámit s experimentálními funkcemi

- Experimentální podporu pro následující paralelní algoritmy:
  - `all_of`
  - `any_of`
  - `for_each`
  - `for_each_n`
  - `none_of`
  - `reduce`
  - `replace`
  - `replace_if`
  - `sort`
- Podpisy pro následující paralelní algoritmy jsou přidána ale neparalelizovaných v tuto chvíli; profilace jsme si ukázali, žádné výhody v paralelním zpracováním algoritmy, které jsou pouze přesunutí nebo permute – elementy:
  - `copy`
  - `copy_n`
  - `fill`
  - `fill_n`
  - `move`
  - `reverse`
  - `reverse_copy`
  - `rotate`
  - `rotate_copy`
  - `swap_ranges`

#### <a name="performance-fixes-and-improvements"></a>Výkon opravy a vylepšení

- `basic_string<char16_t>` Teď provede stejné `memcmp`, `memcpy`a podobné optimalizace, které `basic_string<wchar_t>` zaujme.
- Optimalizace omezení, která mu ukazatelů na funkce nebudou vloženy vystavené naše "vyhnout kopírování funkce" pracovat v sadě Visual Studio 2015 Update 3 byla pracoval, obnovení výkon `lower_bound(iter, iter, function pointer)`.
- Režie pro iterační ladění vaší objednávky ověření vstupy `includes`, `set_difference`, `set_symmetric_difference`, a `set_union` byla snížena rozbalení iterátory před vrácením se změnami pořadí.
- `std::inplace_merge` Nyní přeskočí elementy, které jsou už v umístění.
- Vytváření `std::random_device` už sestaví a potom zničí `std::string`.
- `std::equal` a `std::partition` měl dělení na vlákna jump optimalizace průchodu, což jim porovnávání iterátoru.
- Když `std::reverse` ukazatele je předaný pro triviálně kopírovatelné `T`, odešle teď do rukou psaný vektorizovaných implementace.
- `std::fill`, `std::equal`, a `std::lexicographical_compare` byly museli jak provést odeslání `memset` a `memcmp` pro `std::byte` a `gsl::byte` (a ostatní char jako výčty a výčet tříd). Všimněte si, že `std::copy` odešle zprávu pomocí `is_trivially_copyable` a proto nebylo potřeba žádné změny.
- Standardní knihovna již nebude obsahovat žádné prázdné závorky destruktory, jehož jediným chování bylo zajistit typy bez triviálně zničitelné.

#### <a name="correctness-fixes-in-visual-studio-2017-version-155"></a>Řeší správnost v sadě Visual Studio 2017 verze 15.5

- `std::partition` nyní volání časy predikátu N místo N + 1 časy jako standardní vyžaduje.
- Pokusy o statické objekty magic ve verzi 15.3, aby byl opraven ve verzi 15.5.
- `std::atomic<T>` už nevyžaduje `T` jako výchozí constructible.
- Haldy algoritmy, které už logaritmické nespěchejte provést kontrolní výraz lineárním čase, že vstup je ve skutečnosti haldu Pokud je povolená pro iterační ladění.
- `__declspec(allocator)` je teď pro C1XX pouze, aby se zabránilo upozornění Clang, který nerozumí tento declspec chráněné.
- `basic_string::npos` je teď dostupná jako časovou konstantou kompilace.
- `std::allocator` v C ++ 17 režimu je větší než nyní správně zpracovává přidělení nadbytečně zarovnané typy, typy to znamená, jejichž zarovnání `max_align_t`, pokud zakázal **/Zc:alignedNew-**.  Například vektory objektů s 16 nebo 32bajtové zarovnání budou nyní správně zarovnané SSE a AVX pokyny.

### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 verze 15.6

- \<memory_resource >
- Knihovna základy V1
- Odstraňuje se přiřazení polymorphic_allocator
- Zlepšení odvození argumentu šablony třídy

### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

- podporu pro paralelní algoritmy, už nejsou experiemental
- novou implementaci \<filesystem >
- základní řetězec převody (částečná podpora)
- std::launder()
- std::Byte
- hypot(x,y,z)
- jak se vyhnout zbytečným decay
- speciální matematické funkce
- char_traits constexpr.
- Průvodce dedukcí pro STL

Zobrazit [shoda jazyka Visual C++](visual-cpp-language-conformance.md) Další informace.

## <a name="other-libraries"></a>Další knihovny

### <a name="open-source-library-support"></a>Podpora pro Open source knihovny

**Vcpkg** je nástroj příkazového řádku open source, který výrazně zjednodušuje proces získání a vytvoření statické knihovny opensourcového jazyka C++ a knihovny DLL v sadě Visual Studio. Další informace najdete v tématu [vcpkg: Správce balíčků pro C++](../build/vcpkg.md).

**Visual Studio 2017 version 15.5**:

### <a name="cpprest-sdk-290"></a>CPPRest SDK 2.9.0

CPPRestSDK multiplatformní webového rozhraní API jazyka C++, byla aktualizována na verzi 2.9.0. Další informace najdete v tématu [CppRestSDK 2.9.0 je k dispozici na Githubu](https://blogs.msdn.microsoft.com/vcblog/2016/10/21/cpprestsdk-2-9-0-is-available-on-github/).

### <a name="atl"></a>ATL

- Ještě další sada oprav neshod vyhledávání názvů
- Existující konstruktory přesunutí a operátory přiřazení jsou teď správně označené jako non-throwing. přesunutí a operátory
- Zrušení potlačení platný upozornění c4640 týkajícího vláknově bezpečné inicializace místních statik v atlstr.h
- Vláknově bezpečnou inicializaci místních statik byla v sadě nástrojů XP automaticky vypnutá při [použití ATL a vytváření knihovny DLL]. To již neplatí. Můžete přidat **/Zc: threadsafeinit** v nastavení projektu, pokud vlákno je žádoucí bezpečnou inicializaci vypnout.

### <a name="visual-c-runtime"></a>Modul runtime Visual C++

- Nové záhlaví "cfguard.h" pro symboly ochrany toku provádění.

## <a name="c-ide"></a>C++ IDE

- Výkon při změně konfigurace je teď vyšší u nativních projektů C++ a mnohem vyšší u projektů C++/CLI. Pokud se konfigurace řešení aktivuje poprvé, bude to teď rychlejší, přičemž všechny následné aktivace této konfigurace řešení budou prakticky okamžité.

**Visual Studio 2017 version 15.3**:

- Několik průvodců projektu a kódu je přepsaných ve stylu dialogu podpisu.
- **Přidejte třídu** teď přímo spustí průvodce Přidat třídu. Všechny ostatní položky, které byly dříve tady, jsou teď k dispozici v rámci **Přidat > Nová položka**.
- Projekty Win32 jsou teď v **Windows Desktop** kategorii **nový projekt** dialogového okna.
- **Konzoly Windows** a **aplikace klasické pracovní plochy** šablony teď vytvoří projekty bez zobrazení průvodce. Je tu nový **desktopový Průvodce pro Windows** v rámci stejné kategorie, která zobrazí stejné možnosti jako původní **Konzolová aplikace Win32** průvodce.

**Visual Studio 2017 version 15.5**:

Několik operací v jazyce C++, které používají modul IntelliSense pro refaktoring a navigace v kódu spusťte mnohem rychleji. Tato čísla jsou založeny na Visual Studio chromu řešení s projekty 3500:

|||
|-|-|
|Funkce|Zlepšení výkonu|
|přejmenování|5.3 x|
|Změnit signaturu |4.5 x|
|Najít všechny odkazy|4.7 x|

Jazyk C++ nyní podporuje Ctrl + kliknutí **přejít k definici**, usnadňuje navigace myši do definic. Vizualizér struktur z této sady nástrojů Productivity Power Tools je nyní také součástí produktu ve výchozím nastavení.

## <a name="intellisense"></a>IntelliSense

- Ve výchozím nastavení je nyní používán nový databázový stroj využívající SQLite. Tím se urychlí databázové operace jako **přejít k definici** a **najít všechny odkazy**a výrazně se zkrátí doba analýzy počátečního řešení. Nastavení se přesunulo do **nástroje > Možnosti > textový Editor > C/C++ > Upřesnit** (dříve bylo pod... C/C++ | Experimentální).

- Vylepšili jsme výkon technologie IntelliSense v projektech a souborech, které nepoužívají předkompilované hlavičky – pro hlavičky aktuálního souboru se vytvoří Automatická Předkompilovaná hlavička.

- Přidali jsme do seznamu chyb filtrování a nápovědu k chybám technologie IntelliSense. Kliknutí na sloupec s chybami teď umožní je filtrovat. Kromě toho kliknutím na konkrétní chyby nebo stisknutím klávesy F1 spustíte online vyhledávání chybové zprávy.

  ![Seznam chyb](media/ErrorList1.png "Seznam chyb")

  ![Filtrovaný seznam chyb](media/ErrorList2.png "Filtrovaný seznam chyb")

- Přidali jsme možnost filtrovat položky seznamu členů podle typu.

  ![Filtrování seznamu členů](media/mlfiltering.png "Filtrování seznamu členů")

- Přidali jsme novou experimentální funkci prediktivní IntelliSense, která poskytuje kontextově závislé filtrování toho, co se zobrazuje v seznamu členů. Zobrazit [vylepšení IntelliSense pro C++ – prediktivní IntelliSense a filtrování](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-intellisense-improvements-predictive-intellisense-filtering/)
- **Najít všechny odkazy** (Shift + F12) teď pomáhá vám snadno dostanete, i v komplexních základů kódu. Poskytuje pokročilé seskupování, filtrování, řazení, hledání v rámci výsledků a (pro některé jazyky) zabarvení, abyste se mohli pochopili, že vaše odkazy. Nové uživatelské rozhraní jazyka C++, obsahuje informace o tom, jestli jsme se čtení z nebo zápis do proměnné.
- Funkce změny tečky na šipku technologie IntelliSense se změnila z experimentální na pokročilou a teď je ve výchozím nastavení povolená. Funkce editoru **rozbalení oborů** a **rozbalení priorit** také byly přesunuté z experimentálních na Pokročilé.
- Funkce experimentálního refaktoringu **změnit signaturu** a **extrahovat funkci** jsou teď dostupné ve výchozím nastavení.
- Experimentální funkce, které je "Rychleji projektu zatížení" pro projekty C++. Při příštím otevření se projekt jazyka C++ zavede se rychleji a potom se bude zavádět skutečně rychle.
- Některé z těchto funkcí jsou společné pro ostatní jazyky a některé jsou specifické pro C++. Další informace o těchto nových funkcích najdete v tématu [oznamujeme vydání sady Visual Studio "15"](https://blogs.msdn.microsoft.com/visualstudio/2016/10/05/announcing-visual-studio-15-preview-5/).

**1027 Visual Studio verze 15.7**: Byla přidána podpora pro ClangFormat. Další informace najdete v tématu [podporu pro ClangFormat v sadě Visual Studio 2017](https://blogs.msdn.microsoft.com/vcblog/2018/03/13/clangformat-support-in-visual-studio-2017-15-7-preview-1/).

## <a name="non-msbuild-projects-with-open-folder"></a>Projekty MSBuild bez pomocí otevřít složku

Visual Studio 2017 zavádí **otevřít složku** funkci, která umožňuje kód, vytvářet a ladit ve složce obsahující zdrojový kód bez nutnosti vytvářet jakékoli řešení nebo projektů. Díky tomu je mnohem jednodušší, abyste mohli začít se sadou Visual Studio i v případě, že váš projekt není projektem založené na MSBuild. S **otevřít složku** získáte přístup k výkonné kódu principy, úpravy, sestavování a ladění funkcí, které již poskytuje Visual Studio pro projekty MSBuild. Další informace najdete v tématu [projekty otevřít složku pro jazyk C++](../build/open-folder-projects-cpp.md).

- Vylepšení prostředí Otevřít složku Přizpůsobte si prostředí pomocí tyto soubory .json:
  - CppProperties.json použijte k přizpůsobení technologie IntelliSense a prostředí procházení.
  - Tasks.json použijte k přizpůsobení kroků sestavení.
  - Launch.json použijte k přizpůsobení prostředí ladění.

**Visual Studio 2017 version 15.3**:

- Vylepšená podpora pro alternativní kompilátory a prostředí sestavení, jako je například MinGW a Cygwin. Další informace najdete v tématu [pomocí MinGW a Cygwin pomocí jazyka Visual C++ a otevřít složku](https://blogs.msdn.microsoft.com/vcblog/2017/07/19/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/).
- Byla přidána podpora pro definování proměnných prostředí určených pro konfigurace a globální CppProperties.json a CMakeSettings.json. Tyto proměnné prostředí můžete využívat v konfiguracích ladění definovaných v souboru launch.vs.json a úkolech v tasks.vs.json. Další informace najdete v tématu [přizpůsobení prostředí pomocí Visual C++ a otevřít složku](https://blogs.msdn.microsoft.com/vcblog/2017/11/02/customizing-your-environment-with-visual-c-and-open-folder/).
- Vylepšená podpora pro generátor Ninja CMake, včetně možnosti snadno cílit na 64bitové platformy.

## <a name="cmake-support-via-open-folder"></a>Podpora CMake prostřednictvím funkce Otevřít složku

Visual Studio 2017 zavádí podporu pro práci s projekty CMake bez nutnosti dalších souborech projektu MSBuild (.vcxproj). Další informace najdete v tématu [projekty CMake v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md). Otevírání projektů CMake s **otevřít složku** automaticky nakonfiguruje prostředí pro úpravy, sestavování a ladění C++.

- Technologie IntelliSense jazyka C++ funguje bez nutnosti vytvoření souboru CppProperties.json v kořenové složce. Navíc jsme přidali novou rozevírací nabídku, která uživatelům umožňuje snadno přepínat mezi konfiguracemi poskytovanými soubory CMake a CppProperties.json.

- Prostřednictvím souboru CMakeSettings.json, který je umístěný ve stejné složce jako soubor CMakeLists.txt, se podporuje další konfigurace.

  ![Otevřít složku – CMake](media/cmake_cpp.png "Otevřít složku – CMake")

**Visual Studio 2017 version 15.3**: Byla přidána podpora pro generátor CMake Ninja.

**Visual Studio 2017 version 15.5**: Byla přidána podpora pro import stávající mezipaměti CMake.

**Visual Studio 2017 version 15.7**: Přidána podpora pro CMake 3.11, analýza kódu v projektech CMake, zobrazení cílů v Průzkumníku řešení, možnosti mezipaměti, kompilaci a generování jednoho souboru. Další informace najdete v tématu [podpora CMake v sadě Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) a [projekty CMake v sadě Visual Studio](../build/cmake-projects-in-visual-studio.md).

## <a name="windows-desktop-development-with-c"></a>Vývoj pro plochu Windows v C++

Při instalaci původní úlohy pro C++ teď poskytujeme podrobnější prostředí instalace. Přidali jsme volitelné součásti, které vám umožní vybrat a nainstalovat jen ty nástroje, které potřebujete.  Všimněte si, že uvedené velikosti instalace součástí uvedené v uživatelském rozhraní instalačního programu nejsou přesné a podceňují skutečnou celkovou velikost.

Když chcete úspěšně vytvářet projekty Win32 v úloze vývoje desktopových aplikací v C++, musíte nainstalovat sadu nástrojů i sadu Windows SDK. Instalace doporučených (vybraných) komponent **nástrojů pro VC ++ 2017 v141 (x86, x64)** a **Windows 10 SDK (10.0.nnnnn)** zajišťuje, bude to fungovat. Pokud nebudou potřebné nástroje nainstalované, projekty se nevytvoří úspěšně a průvodce přestane reagovat.

**Visual Studio 2017 version 15.5**:

(Dříve dostupné jako samostatný produkt) Visual C++ Build tools jsou nyní zahrnuty jako úloha v instalačním programu sady Visual Studio. Tato úloha se nainstaluje jenom nástroje potřebné k sestavení projektů C++ bez nutnosti instalace integrovaném vývojovém prostředí sady Visual Studio. Sady nástrojů verze 141 i v140 jsou zahrnuty. Sadu nástrojů verze 141 obsahuje nejnovější vylepšení v sadě Visual Studio 2017 verze 15.5. Další informace najdete v tématu [Visual Studio Build Tools nyní zahrnují VS2017 a sady nástrojů MSVC VS2015](https://blogs.msdn.microsoft.com/vcblog/2017/11/02/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/).

## <a name="linux-development-with-c"></a>Vývoj pro Linux v C++

Oblíbené rozšíření [Visual C++ for Linux Development](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e) je teď součástí sady Visual Studio. Tato instalace nabízí všechno, co potřebujete k vývoji a ladění aplikací v jazyce C++, které se spouštějí v prostředí systému Linux.

**Visual Studio 2017 version 15.2**:

Vylepšení byly provedeny v kódu pro různé platformy pro sdílení obsahu a typu vizualizace. Další informace najdete v tématu [vylepšení Linux C++ pro různé platformy sdílení kódu a typ vizualizace](https://blogs.msdn.microsoft.com/vcblog/2017/05/10/linux-cross-platform-and-type-visualization/).

**Visual Studio 2017 version 15.5**:

- Přidána podpora pro Linux úloha **rsync** jako alternativu k **sftp** pro synchronizaci souborů do vzdáleného počítače s Linuxem.
- Byla přidána podpora pro různé cílení na ARM mikrokontrolerů po kompilaci. Chcete-li povolit v instalaci, zvolte **vývoj pro Linux v C++** úlohy a vyberte možnost pro **vložené a IoT vývoj**. To přidá kolekce gcc technologie ARM cross tools kompilace a zkontrolujte instalaci. Další informace najdete v tématu [ARM GCC křížové kompilace v sadě Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2017/10/23/arm-gcc-cross-compilation-in-visual-studio/).
- Byla přidána podpora pro CMake. Teď můžete pracovat na svém stávajícím základu CMake kódu bez nutnosti převádět na projekt sady Visual Studio. Další informace najdete v tématu [konfigurace projektu Linux CMake](../linux/cmake-linux-project.md).
- Byla přidána podpora pro spouštění vzdálené úlohy. Díky této funkci můžete spouštět jakékoli příkazy ve vzdáleném systému, který je definován v sadě Visual Studio Connection Manager. Vzdálené úlohy také poskytují možnost kopírování souborů do vzdáleného systému.
Další informace najdete v tématu [konfigurace projektu Linux CMake](../linux/cmake-linux-project.md).

**Visual Studio 2017 version 15.7**:

- Různá vylepšení scénáře úloh Linux. Další informace najdete v tématu [úlohy pro C++ Linux vylepšení systém projektu, okna konzoly systému Linux, rsync a připojit k procesu](https://blogs.msdn.microsoft.com/vcblog/2018/03/13/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/).
- IntelliSense pro záhlaví na vzdálená připojení Linuxu. Další informace najdete v tématu [technologie IntelliSense pro vzdálených hlaviček Linux](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/intellisense-for-remote-linux-headers/) a [konfigurace projektu Linux CMake](../linux/cmake-linux-project.md).

## <a name="game-development-with-c"></a>Vývoj her v C++

Využijte naplno potenciál C++ k vytváření profesionálních her využívajících technologii DirectX nebo Cocos2d.

## <a name="mobile-development-with-c-android-and-ios"></a>Vývoj mobilních aplikací pomocí C++ (Android a iOS)

Mobilní aplikace teď můžete vytvářet a ladit pomocí sady Visual Studio, která se umí zaměřit i na Android a iOS.

## <a name="universal-windows-apps"></a>Univerzální aplikace pro Windows

C++ je volitelnou součástí úlohy Universal Windows App.  Upgrade projektů C++ se v tuto chvíli musí provést ručně. Pokud v sadě Visual Studio 2017 otevřete projekt UPW cílený na verzi 140 a nemáte nainstalovanou sadu Visual Studio 2015, musíte na stránkách vlastností projektu vybrat sadu nástrojů verze 141.

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>Nové možnosti jazyka C++ na univerzální platformu Windows (UPW)
Teď máte nové možnosti pro zápis a balení aplikací pro univerzální platformu Windows a Windows Store v jazyce C++: Přemostění na Desktop infrastruktury můžete zabalit existující aplikace klasické pracovní plochy nebo objekt modelu COM pro nasazení přes Windows Store nebo prostřednictvím stávajících prodejních kanálů prostřednictvím zkušební načtení. Nové funkce ve Windows 10 vám umožňují přidat funkce UPW do aplikace klasické pracovní plochy různými způsoby. Další informace najdete v tématu [přemostění na Desktop](/windows/uwp/porting/desktop-to-uwp-root).

**Visual Studio 2017 version 15.5**: A **projekt Windows Application Packaging** šablona projektu se přidá, což výrazně zjednodušuje práci při vytváření balíčků aplikací klasické pracovní plochy s využitím přemostění na Desktop. Je k dispozici v **soubor | Nové | Projekt | Instalaci | Visual C++ | Universal Windows Platform**. Další informace najdete v tématu [balíček aplikace pomocí sady Visual Studio (přemostění na Desktop)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

Pokud zapisujete nový kód, můžete nyní použít C + +/ WinRT, standardní projekce jazyka C++ prostředí Windows runtime implementována pouze v souborech hlaviček. Umožňuje oba Autor a používání rozhraní API Windows Runtime pomocí jakýkoli standardům kompilátor jazyka C++. C + +/ WinRT je navržené pro poskytování vývojáře v jazyce C++ s přístupem k prvotřídní moderní rozhraní Windows API. Další informace najdete v tématu [C + +/ WinRT dostupný na Githubu](https://moderncpp.com/).

Od verze sestavení 17025 sady Windows SDK Insider Preview, C + +/ WinRT je součástí sady Windows SDK. Další informace najdete v tématu [C + +/ WinRT je nyní zahrnutá sady Windows SDK](https://blogs.msdn.microsoft.com/vcblog/2017/11/01/cppwinrt-is-now-included-the-windows-sdk/).

## <a name="clangc2-platform-toolset"></a>Sada nástrojů platformy clang/C2

Sada nástrojů Clang/C2, která se dodává s Visual Studio 2017 teď podporuje **/bigobj** přepnout, což je zásadní pro sestavování rozsáhlých projektů. Zahrnuje také několik důležitých oprav chyb, jak ve front-endu, tak v back-endu kompilátoru.

## <a name="c-code-analysis"></a>Analýza kódu C++

Se sadou Visual Studio se nyní distribuují moduly pro kontrolu jádra C++, které vynucují [pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines). Stačí tyto moduly pro kontrolu v povolit **rozšířeními pro analýzu kódu** stránky v stránky vlastností projektu a rozšíření se zahrnou spouštění analýz kódu. Další informace najdete v tématu [pomocí tyto moduly pro kontrolu podle dokumentu C++ Core Guidelines](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

![CppCoreCheck](media/CppCoreCheck.png "Stránka vlastností CppCoreCheck")

**Visual Studio 2017 version 15.3**: Byla přidána podpora pro pravidla týkající se správy prostředků.

**Visual Studio 2017 version 15.5**: Nové kontroly podle dokumentu C++ Core Guidelines týkají správnosti chytrých ukazatelů, správného použití globálních inicializátorů a označování použití konstruktorů, jako je `goto` a chybný přetypování.

Některá čísla upozornění, která najdete v 15.3, už nejsou k dispozici v 15.5. Tato upozornění byla nahrazena specifičtějšími kontrolami.

**Visual Studio 2017 version 15.6**:

- Byla přidána podpora pro jeden soubor analýzy a vylepšení analýzy výkonu za běhu. Další informace najdete v tématu [vylepšení statické analýzy C++ pro Visual Studio 2017 15.6 Preview 2](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/c-static-analysis-improvements-for-visual-studio-2017-15-6-preview-2/)

**Visual Studio 2017 version 15.7**:

- Podpora pro přidání [/ analyze: ruleset](../build/reference/analyze-code-analysis.md) což vám umožní určit, která pravidla analýzy kódu pro spuštění.
- Byla přidána podpora pro další pravidla podle dokumentu C++ Core Guidelines.  Další informace najdete v tématu [pomocí tyto moduly pro kontrolu podle dokumentu C++ Core Guidelines](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

## <a name="unit-testing"></a>Testování jednotek

**Visual Studio 2017 version 15.5**:

Adaptér Google Test a Boost.Test adaptér jsou teď k dispozici jako součásti **Desktop Development with C++** pracovního vytížení a jsou integrované s **Průzkumník testů**. Přidá se CTest podporu pro projekty Cmake (pomocí otevřít složku), i když plnou integraci s **Průzkumník testů** ještě není k dispozici. Další informace najdete v tématu [zápis testů jednotek pro C/C++](/visualstudio/test/writing-unit-tests-for-c-cpp).

**Visual Studio 2017 version 15.6**:

- Byla přidána podpora pro Boost.Test podpora dynamických knihoven.
- Šablony položek Boost.Test je teď k dispozici v integrovaném vývojovém prostředí.

Další informace najdete v tématu [Boost.Test testování částí: Dynamická knihovna podpory a nové šablony položky](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/boost-test-unit-testing-dynamic-library-support-and-new-item-template/).

**Visual Studio 2017 version 15.7**:

[Funkce CodeLens](/visualstudio/ide/find-code-changes-and-other-history-with-codelens) podporována pro projekty testů jednotek C++ přidat. Další informace najdete v tématu [uvedení funkce CodeLens pro testování částí C++](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/announcing-codelens-for-c-unit-testing/).

## <a name="visual-studio-graphics-diagnostics"></a>Diagnostika grafiky sady Visual Studio

Diagnostika grafiky sady Visual Studio je sada nástrojů pro zaznamenávání a analýzu problémů vykreslování a výkon v aplikacích rozhraní Direct3D. Funkce diagnostiky grafiky můžete použít s aplikacemi, které běží místně v počítači Windows v emulátoru zařízení Windows nebo na vzdálený počítač nebo zařízení.

- **Vstup a výstup pro Vertex a Geometry Shader:** Jedna z nejžádanějších funkcí byla možnost zobrazit vstup a výstup vertex shader a shader geometrie a je nyní podporována v nástrojích. Jednoduše vyberte fázi sady Visual Studio nebo GS v okně fáze zřetězení spustit kontrola vstup a výstup v následující tabulce.

  ![Vstup/výstup pro shadery](media/io-shaders.png)

- **Vyhledávání a filtrování v tabulce objektů:** Poskytuje rychlý a snadný způsob, jak najít prostředky, které hledáte.

  ![Hledat](media/search.png)

- **Historie prostředku:** Toto nové zobrazení poskytuje efektivní způsob, jak zobrazuje historii celý úpravy prostředku, jako jste použili při vykreslování zachyceného snímku. Abyste mohli vyvolat historie pro libovolné prostředky, stačí klikněte na ikonu hodin vedle libovolný prostředek hypertextový odkaz.

  ![Historie prostředku](media/resource-history.png)

  Zobrazí se nové **rie prostředku** oknem nástrojů, vyplní historii změn prostředku.

  ![Historie změn prostředků](media/resource-history-change.png)

  Všimněte si, že pokud byla zaznamenána rámce s úplnou volání zásobníku zachytávání povolené (**sady Visual Studio > Nástroje > Možnosti** pod **diagnostiky grafiky**), kontext každou událost změny může být rychle odvodit a kontrole v rámci projektu sady Visual Studio.

- **Statistika API:** Zobrazte podrobný souhrn využití rozhraní API v rámce. To může být užitečný v zjišťování volání že nemusí dobré si uvědomit, že provádíte vůbec nebo volání, které vytvoříte příliš mnoho. Toto okno je k dispozici prostřednictvím **zobrazení > Statistika API** v analyzátoru grafiky sady Visual Studio.

  ![Statistika API](media/api-stats.png)

- **Statistika paměti:** Zobrazte, kolik paměti je ovladač přidělování prostředků vytvoříte v rámci. Toto okno je k dispozici prostřednictvím **zobrazení > Statistika paměti** v **analyzátoru grafiky sady Visual Studio**. Data je možné zkopírovat do souboru CSV pro zobrazení v tabulce tak, že kliknete pravým tlačítkem a zvolíte **Kopírovat vše**.

  ![Statistika paměti](media/memory-stats.png)

- **Ověření snímku:** Nový seznam chyb a upozornění poskytuje snadný způsob, jak přejít seznamu událostí podle potenciálních problémů zjištěných vrstvu debug Direct3D. Klikněte na tlačítko **zobrazení > ověření snímku** ve Visual Studio Graphics Analyzer otevření okna. Pak klikněte na tlačítko **spustit ověření** spustit analýzu. Může trvat několik minut v závislosti na složitosti rámce.

  ![Ověření snímku](media/frame-validation.png)

- **Analýza snímků pro D3D12:** Analýzu snímků použijte k analýze výkonu volání draw s pokusy řízené "co kdyby". Přepněte na kartu analýza snímků a spuštění analýzy zobrazíte sestavu. Další informace, podívejte se [GoingNative 25: Analýza grafických snímků Visual Studio](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) videa.

  ![Analýza snímků](media/frame-analysis.png)

- **Vylepšení využití GPU:** Otevřít trasování přijatých prostřednictvím využití GPU Visual Studio profiler GPU zobrazení nebo nástroji Windows Performance Analyzer (WPA) pro podrobnější analýzu. Pokud máte není nainstalovaná sada Windows Performance Toolkit budou dva hypertextové odkazy, jeden pro WPA a druhou pro zobrazení GPU v pravém dolním rohu přehledu relace.

  ![Využití GPU](media/gpu-usage.png)

  Otevřít v zobrazení GPU prostřednictvím tohoto odkazu podpory trasování synchronizované přibližování a posouvání na časové ose mezi VS a zobrazení GPU. Zaškrtávací políčko v sadě Visual Studio je slouží ke kontrole, jestli je povolená synchronizace, nebo ne.

  ![Zobrazení GPU](media/gpu-view.png)
