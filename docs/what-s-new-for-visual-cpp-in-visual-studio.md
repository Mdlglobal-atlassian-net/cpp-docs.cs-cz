---
title: Co je nového pro Visual C++ v sadě Visual Studio | Microsoft Docs
ms.date: 11/15/2017
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f280ed28a65db4aa71ee6dea36521b1b8606b190
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
---
# <a name="whats-new-for-visual-c-in-includevsdev15mdmiscincludesvsdev15mdmd"></a>Co je nového pro Visual C++ v [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)]

[!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] poskytuje mnoho aktualizací a opravy pro prostředí Visual C++. Jsme vyřešili více než 250 chyb a hlášené problémy v kompilátoru a nástroje, mnoho odeslané zákazníky pomocí [nahlásit problém](/visualstudio/how-to-report-a-problem-with-visual-studio-2017) a [poskytují zlepšení](https://visualstudio.uservoice.com/) možnosti v části **odeslat zpětnou vazbu** . Děkujeme vám, že hlásíte chyby! Další informace o co je nového ve všech sady Visual Studio, navštivte [co je nového v [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] ](https://go.microsoft.com/fwlink/p/?linkid=834481).

<!--The compiler and tools version number in [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] is 14.10.24629. -->

## <a name="c-compiler"></a>kompilátor C++

### <a name="c-conformance-improvements"></a>Vylepšení shoda C++

V této verzi jsme kompilátor jazyka C++ a standardní knihovny doplnili rozšířenou podporou pro funkce C++11 a C++14, a také předběžnou podporou pro některé funkce očekávané ve standardu C++17. Podrobné informace najdete v tématu [C++ shoda vylepšení v nástroji Visual Studio 2017](cpp-conformance-improvements-2017.md).
**Visual Studio 2017 verze 15,5**:  

   Kompilátor podporuje přibližně 75 % funkce, které jsou nové v C ++ 17, včetně strukturovaných vazby `constexpr` lambdas, `if constexpr`, vložené proměnné přeložte výrazy a přidání `noexcept` typ systému. Tyto jsou k dispozici v části **/std: c ++ 17** možnost. Další informace najdete v tématu [C++ shoda vylepšení v nástroji Visual Studio 2017](cpp-conformance-improvements-2017.md)

**Visual Studio 2017 verze 15.7**:  

Sada nástrojů kompilátoru MSVC v sadě Visual Studio verze 15.7 nyní splňuje normu C++ Standard. Další informace najdete v tématu [Announcing: MSVC vyhovuje C++ Standard](https://blogs.msdn.microsoft.com/vcblog/2018/05/07/announcing-msvc-conforms-to-the-c-standard/) a [přizpůsobení jazyka Visual C++](visual-cpp-language-conformance.md).

### <a name="new-compiler-options"></a>Nové možnosti kompilátoru

- [/ projektovou-](build/reference/permissive-standards-conformance.md): všechny shoda striktní standardy – možnosti kompilátoru povolení a zakázání rozšíření kompilátoru většina specifické pro společnost Microsoft (ale ne `__declspec(dllimport)`, například). Tato možnost je ve výchozím nastavení v aplikaci Visual Studio 2017 verze 15,5 na.  **/ Projektovou-** shoda režimu zahrnuje podporu pro vyhledání dvoufázového názvu. Další informace najdete v tématu [C++ shoda vylepšení v nástroji Visual Studio 2017](cpp-conformance-improvements-2017.md).

- [/Diagnostics](build/reference/diagnostics-compiler-diagnostic-options.md): povolení zobrazení číslo řádku, číslo řádku a sloupce, nebo číslo řádku a sloupce a šipka nahoru v rámci řádku kódu, kde byl nalezen diagnostiky chyby nebo upozornění.

- [/Debug:fastlink](build/reference/debug-generate-debug-info.md): povolit až 30 % rychlejší přírůstkové odkaz krát (vs. Visual Studio 2015) není zkopírováním všechny informace o ladění do souboru PDB. Soubor PDB místo odkazuje na informace o ladění pro objekt a knihovna soubory použít k vytvoření spustitelného souboru. V tématu [rychlejší C++ sestavení cyklu v sadě VS "15" s /Debug:fastlink](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/faster-c-build-cycle-in-vs-15-with-debugfastlink/) a [doporučení, která rychlost sestavení C++ v sadě Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2016/10/26/recommendations-to-speed-c-builds-in-visual-studio/).

- [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] umožňuje používat [SDL](build/reference/sdl-enable-additional-security-checks.md) s [/ await](build/reference/await-enable-coroutine-support.md). Jsme odebrali [/RTC](build/reference/rtc-run-time-error-checks.md) omezení coroutines.

   **Visual Studio 2017 verze 15.3**:  
- [/ std: c ++ 14 a/std: c ++ nejnovější](build/reference/std-specify-language-standard-version.md): tyto možnosti kompilátoru umožňují vyslovení souhlasu s konkrétní verze ISO C++ programovací jazyk v projektu. Většina nového konceptu standardní funkce se budou dát **/std: c ++ nejnovější** možnost.

- [/ std: c ++ 17](build/reference/std-specify-language-standard-version.md) umožňuje sadu funkce C ++ 17 implementované kompilátoru. Tato možnost zakáže kompilátoru a standardní knihovny podpora pro funkce, které se změnily nebo nové verze aktualizací práce koncept a vadou standardní C++ po C ++ 17. Chcete-li tyto funkce povolit, použijte **/std: c ++ nejnovější**.


### <a name="codegen-security-diagnostics-and-versioning"></a>CODEGEN, zabezpečení, diagnostiky a správy verzí

Tato verze přináší několik vylepšení v optimalizace, generování kódu, Správa verzí nástrojů a diagnostiky. Mezi důležitá vylepšení patří:

- Vylepšené generování kódu smyček: Podpora automatické vektorizace dělení konstantních celých čísel, lepší identifikace vzorů memset
- Vylepšené zabezpečení kódu: vylepšené emisí diagnostics kompilátoru přetečení vyrovnávací paměti, a [/guard:cf](build/reference/guard-enable-control-flow-guard.md) nyní chrání přepínač příkazy, které generují přechod tabulky.
- Správa verzí: Hodnota předdefinované makro preprocesoru  **\_MSC\_VER** je nyní monotónně aktualizované při každé aktualizaci nástrojů Visual C++. Další informace najdete v tématu [verze kompilátoru Visual C++](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/visual-c-compiler-version/).
- Nové rozložení nástrojů: kompilátoru a související sestavovací nástroje mají nové umístění a strukturu adresáře na vývojovém počítači. Nové rozložení umožňuje vedle sebe instalace více verzí kompilátoru. Další informace najdete v tématu [kompilátoru nástroje rozložení v sadě Visual Studio "15"](https://blogs.msdn.microsoft.com/vcblog/2016/10/07/compiler-tools-layout-in-visual-studio-15/).
- Vylepšené diagnostiky: ve výstupním okně teď zobrazuje sloupec, kde dojde k chybě. Další informace najdete v tématu [diagnostiky vylepšení kompilátoru C++ v sadě VS "15" Preview 5](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-compiler-diagnostics-improvements-in-vs-15-rc/).
- Při použití rutiny společné, experimentální – klíčové slovo **yield** (k dispozici v části **/ await** možnost) byl odebrán. Váš kód by měl aktualizovat, a použít `co_yield` místo. Další informace najdete v [Blogu týmu Visual C++](https://blogs.msdn.microsoft.com/vcblog/).

**Visual Studio 2017 verze 15.3**:

Další vylepšení diagnostiky v kompilátoru. Další informace najdete v tématu [diagnostiky vylepšení v nástroji Visual Studio 2017 15.3.0](https://blogs.msdn.microsoft.com/vcblog/2017/07/21/diagnostic-improvements-in-vs2017-15-3-0/).

**Visual Studio 2017 verze 15,5**:

Výkon modulu runtime Visual C++ dál vylepšit kvůli lepší kvalitu generovaného kódu. To znamená, že jednoduše znovu zkompiluje kódu a vaše aplikace běží rychleji. Některé z optimalizace kompilátoru se nikdy nepracovali, jako je například vectorization podmíněného skalární úložišť, kombinování volání `sin(x)` a `cos(x)` do nového `sincos(x)`a odstranění redundantní pokyny z Optimalizátor SSA. Další optimalizace kompilátoru jsou vylepšení stávajících funkcí jako je například nástrojů pro vektorizaci heuristiky pro podmíněné výrazy, lepší optimalizace smyčky a codegen minimální nebo maximální float. Linkeru má nový a rychlejší **/OPT:ICF** implementace, což může vést k až 9 % propojit speedups čas, a v přírůstkové propojování jsou ostatní opravy výkonu. Další informace najdete v tématu [/OPT (optimalizace)](https://docs.microsoft.com/en-us/cpp/build/reference/opt-optimizations) a [/incremental (přírůstkově odkaz)](https://docs.microsoft.com/en-us/cpp/build/reference/incremental-link-incrementally).

Visual C++ podporuje AVX společnosti Intel-512, včetně vektoru délka pokynů, které přinášejí nové funkce v AVX-512 do široké registry 128 a 256 bitů.

[/Zc:noexceptTypes-](build/reference/zc-noexcepttypes.md) možnost je možné vrátit k C ++ 14 verzi `noexcept` při použití C ++ 17 režim obecně. To vám umožní aktualizovat vašeho zdrojového kódu tak, aby odpovídala C ++ 17 bez přepsání všechny vaše `throw()` kódu ve stejnou dobu. Další informace najdete v tématu [odebrání specifikace dynamické výjimky a noexcept](cpp-conformance-improvements-2017.md#noexcept_removal).

**Visual Studio 2017 verze 15.7**:

- Nový přepínač kompilátoru [/Qspectre ](build/reference/qspectre.md) pro zmírnění proti útokům na straně kanál spekulativní provádění. V tématu [jejich zmírnění spektrum v MSVC](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc/) Další informace.
- Nové diagnostické upozornění pro spektrum migitation. V tématu [spektrum diagnostiky ve Visual Studio 2017 verze 15.7 Preview 4](https://blogs.msdn.microsoft.com/vcblog/2018/04/20/spectre-diagnostic-in-visual-studio-2017-version-15-7-preview-4/) Další informace.
- Nové hodnoty pro /Zc, **/Zc:__cplusplus**, umožňuje opravte reporting podpory standardní C++. Například když je nastaven na přepínač a kompilátor probíhá/std: c ++ 17 režimu hodnota zasahuje do **201703 L**. V tématu [MSVC nyní správně hlásí __cplusplus](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/msvc-now-correctly-reports-__cplusplus/) Další informace.

## <a name="c-standard-library-improvements"></a>Vylepšení standardní knihovna C++

- Méně závažné `basic_string` `_ITERATOR_DEBUG_LEVEL != 0` vylepšení diagnostiky. Přeskočení kontroly IDL v sadě řetězců teď oznámí konkrétní chování, které toto přeskočení způsobilo. Například místo zprávy oznamující, že iterátor řetězce nejde přesměrovat, se teď zobrazí zpráva s oznámením, že iterátor řetězce nejde přesměrovat, protože je mimo rozsah (např. je to koncový iterátor).
- Zlepšení výkonu: provedené `basic_string::find(char)` přetížení pouze volání `traits::find` po. Toto jsme dříve implementovali jako hledání obecného řetězce s délkou 1.
- Zlepšení výkonu: `basic_string::operator==` nyní kontroluje velikost řetězec před porovnáním obsah na řetězce.
- Zlepšení výkonu: odebrat řízení spojovacích v `basic_string`, který se těžko optimalizace kompilátoru k analýze. Všimněte si, že se pro všechny krátké řetězce volání `reserve` má stále nenulové hodnoty náklady se nic nestane.
- Jsme přidali \<žádné\>, \<string_view\>, `apply()`, `make_from_tuple()`.
- `std::vector` má byla přepracována správnost a výkon: aliasy během vkládání a. uložení je nyní správně spravovány jako vyžadovanou standardní, záruku silné výjimky se teď poskytují pokud to vyžaduje standardní prostřednictvím `move_if_noexcept()` a jiné logiky a vkládání nebo. uložení provádět méně operace s elementy.
- Standardní knihovna C++ nyní zabraňuje vyhodnocení zvláštní ukazatelé s hodnotou null.
- Přidat \<volitelné\>, \<variant\>, `shared_ptr::weak_type`, a \<cstdalign\>.
- Povolit C ++ 14 `constexpr` v `min(initializer_list)`, `max(initializer_list)`, a `minmax(initializer_list)`, a `min_element()`, `max_element()`, a `minmax_element()`.
- Vylepšené `weak_ptr::lock()` výkonu.
- Pevné `std::promise` přesunutí přiřazení operátor, který dříve by mohlo způsobit kód blokování navždy.
- Chyby kompilátoru s pevnou `atomic<T*>` implicitní převod na `T*`.
- `pointer_traits<Ptr>` nyní správně rozpozná `Ptr::rebind<U>`.
- Pevné chybějící `const` kvalifikátor v `move_iterator` operátor odčítání.
- Pevné bezobslužná nesprávná funkce codegen pro stavových vlastní alokátorů požaduje `propagate_on_container_copy_assignment` a `propagate_on_container_move_assignment`.
- `atomic<T>` Nyní toleruje přetížený `operator&()`.
- Ke zvýšení propustnosti kompilátoru, hlavičky standardní knihovna C++ nyní vyhnout, včetně deklarace pro vnitřní funkce kompilátoru zbytečné.
- Mírně vylepšení kompilátoru diagnostiku pro nesprávné `bind()` volání.
- Vylepšený výkon `std::string` a `std::wstring` přesunout konstruktory tak, že více než třikrát.

Úplný seznam standardní knihovny najdete v části improvments [standardní knihovny opravy v VS 2017 RTM](https://blogs.msdn.microsoft.com/vcblog/2017/02/06/stl-fixes-in-vs-2017-rtm/).

### <a name="visual-studio-2017-version-153"></a>Visual Studio 2017 verze 15.3

#### <a name="c17-features"></a>C ++ 17 funkce

Je implementovaná několik dalších funkce C ++ 17. Další informace najdete v tématu [přizpůsobení jazyka Visual C++](cpp-conformance-improvements-2017.md#improvements_153).

#### <a name="other-new-features"></a>Další nové funkce

- Implementována P0602R0 "variant a volitelné by měl rozšířit kopírování nebo přesunutí triviality".
- Standardní knihovna teď oficiálně toleruje dynamické RTTI zakazuje prostřednictvím [/GR-](build/reference/gr-enable-run-time-type-information.md) možnost. Obě `dynamic_pointer_cast()` a `rethrow_if_nested()` ze své podstaty vyžadují `dynamic_cast`, takže standardní knihovna nyní označí je jako `=delete` pod **/GR-**.
- I když dynamické RTTI byla zakázána prostřednictvím **/GR-**, "statické RTTI" (ve formě `typeid(SomeType)`) je stále k dispozici a zajišťuje několik součástí standardní knihovny. Standardní knihovna teď podporuje to příliš, zakázání prostřednictvím **/D\_HAS\_statické\_RTTI = 0**. Všimněte si, že tato akce zakáže `std::any`, `target()` a `target_type()` členské funkce `std::function`a `get_deleter()` členské funkce friend `std::shared_ptr` a `std::weak_ptr`.

#### <a name="correctness-fixes-in-visual-studio-2017-version-153"></a>Správnost opravy v aplikaci Visual Studio 2017 verze 15.3

- Standardní knihovna kontejnery nyní svorka jejich `max_size()` k `numeric_limits<difference_type>::max()` místo `max()` z `size_type`. To zajistí, že výsledek `distance()` na iterátory kontejneru, v němž je reprezentovat návratový typ `distance()`.
- Pevné nalezen specializace `auto_ptr<void>`.
- `for_each_n()`, `generate_n()`, A `search_n()` algoritmy se dříve nepodařilo kompilovat argument délka nebyla integrální typu; se nyní pokusí převést délky celé číslo iterátory `difference_type`.
- `normal_distribution<float>` už vydá upozornění ve standardní knihovně o zužující z dvojitou na float.
- Některé pevné `basic_string` operací, které byly porovnávání s `npos` místo `max_size()` při kontrole přetečení maximální velikost.
- `condition_variable::wait_for(lock, relative_time, predicate)` by počkejte po celou dobu relativní v případě nesprávné probuzení. Nyní bude čekat pouze jeden interval relativní času.
- `future::get()` teď by způsobila neplatnost `future`, protože vyžaduje standardní.
- `iterator_traits<void *>` použít za chybu hardwaru, protože se pokusil formuláře `void&`; nyní řádně informovat prázdná struktura k povolení použití `iterator_traits` v "je iterator" podmínky sfinae u výrazů.
- Některá upozornění hlášené Clang **wsystem –--headers** jsme vyřešili.
- Také vyřešili "specifikace výjimek v deklaraci neodpovídá předchozí deklarace" hlášené Clang **- Wmicrosoft. výjimka specifikace**.
- Také vyřešili mem. inicializátoru seznamu hlášené Clang a C1XX řazení upozornění.
- Neseřazený kontejnery není Prohodit jejich hashers nebo predikáty při kontejnery sami byly vzájemně zaměněny. Nyní dělají.
- Mnoho operací swap kontejneru, jsou nyní označeny `noexcept` (protože naše standardní knihovna nikdy chtít vyvolat výjimku při zjišťování jinou hodnotu než`propagate_on_container_swap` bez rovná allocator undefined chování podmínku).
- Mnoho `vector<bool>` operace jsou nyní označeny `noexcept`.
- Standardní knihovna teď vynutí odpovídající allocator `value_type` (v C ++ 17 režim) s vyjádření výslovného nesouhlasu s řídicí šrafování.
- Pevné některé podmínky, kde samoobslužných-range-vložení do `basic_string` by promíchání obsahu řetězce. (Poznámka: standardní stále zakazuje samoobslužných-range-vložení do vektory.)
- `basic_string::shrink_to_fit()` už je ovlivňován přidělujícího modulu `propagate_on_container_swap`.
- `std::decay` Teď zpracovává typy abominable funkce (tj. typů funkce, které jsou kvalifikovaný odchylka nákladů nebo kvalifikovaný ref).
- Změnit zahrnují direktivy používat správné rozlišování velkých a malých písmen a lomítka, vylepšení přenositelnost.
- Pevné upozornění C4061 "enumerátor '*enumerátor*'v přepínači výčtu'*– výčet*' není explicitně zpracovávaných případu popisek". Toto upozornění je vypnuto výchozím a byla opravena jako výjimku do zásad obecné standardní knihovna pro upozornění. (Standardní knihovna je **/W4** vyčistit, ale nebude pokoušet o být **/horní** vyčistit. Mnoho vypnout výchozím upozornění jsou velmi aktivní a není určena pro použití v pravidelných intervalech.)
- Vylepšené `std::list` ladění kontroly. Seznam iterátory nyní kontrola `operator->()`, a `list::unique()` nyní označí iterátory jako zrušena.
- Pevné používá allocator metaprogramování v `tuple`.

#### <a name="performancethroughput-fixes"></a>Výkon nebo propustnost opravy

- Práce na incidentu kolem interakce s `noexcept` která zabránila vložené `std::atomic` implementace do funkcí, které používají strukturované zpracování výjimek (SEH).
- Změněné standardní knihovna je interní `_Deallocate()` funkce optimalizace do menší kódu, díky kterému jej jako vložená do více místech.
- Změnit `std::try_lock()` používat rozšíření pack namísto rekurze.
- Vylepšené `std::lock()` zablokování předcházení algoritmu použití `lock()` operations místo roztočený na `try_lock()` na všech zámků.
- Povolené pojmenované návratovou hodnotu optimalizace v nástroji `system_category::message()`.
- `conjunction` a `disjunction` nyní doložit N + 1 typy místo 2 n + 2 typy.
- `std::function` už vytvoří strojů podporu přidělování pro každý typ vymazat volatelná aplikacemi, vylepšení propustnost a snížení velikosti .obj v programech, které předat mnoho různých lambdas k `std::function`.
- `allocator_traits<std::allocator>` obsahuje ručně vložená `std::allocator` operace, zmenšení velikosti kódu v kódu, který komunikuje s `std::allocator` prostřednictvím `allocator_traits` pouze (to znamená, ve většině kód).
- Rozhraní C ++ 11 minimální allocator teď používá standardní knihovna volání `allocator_traits` přímo, namísto zabalení přidělujícího modulu v interní třída `_Wrap_alloc`. To snižuje velikost kódu vygenerované allocator podpory, zlepšuje schopnost okně Optimalizace důvod o standardní knihovna kontejnery v některých případech a nabízí lepší ladění prostředí (jak je vidět typ vašeho allocator místo `_Wrap_alloc<your_allocator_type>` v ladicí program).
- Odebrat metaprogramování upravené `allocator::reference`, které alokátorů nejsou povoleny ve skutečnosti k přizpůsobení. (Alokátorů provádět kontejnery použít zvláštní ukazatele, ale není zvláštní odkazy.)
- Front-endu kompilátoru byl výukové rozbalení ladění iterátory v založený na rozsahu pro smyčky, zvýšení výkonu sestavení pro ladění.
- `basic_string` Interní zmenšení cestu pro `shrink_to_fit()` a `reserve()` již není v cestě k nové přidělení operace, zmenšení velikosti kódu pro všechny mutating členy.
- `basic_string` Interní růst cesta již není v cestě `shrink_to_fit()`.
- `basic_string` Mutace operace se teď promítnou do-přidělování Rychlá cesta a vyhrazování funkce pomalou cestou, což pravděpodobnější častých případech ne opětovné být vložená do volající.
- `basic_string` Mutace operations teď konstrukce opětovnému přidělení vyrovnávací paměti s požadovaným stavem než změna velikosti na místě. Například vložení na začátku řetězec teď přesune obsah po vložení právě jednou (dolů nebo do nově přidělených vyrovnávací paměti), místo dvakrát v případě, že reallocating (do nově přidělených vyrovnávací paměti a potom dolů).
- Operace volání standardní knihovny jazyka C v \<řetězec\> teď do mezipaměti `errno` adresu odebrat opakovaných interakci s TLS.
- Zjednodušená `is_pointer` implementace.
- Změna na základě funkce výraz sfinae u výrazů k dokončení `struct` a `void_t`– na základě.
- Standardní knihovny algoritmů teď Vyhněte se postincrementing iterátory.
- Opravené zkrácení upozornění při použití 32-bit alokátorů na 64bitových systémech.
- `std::vector` Přesuňte přiřazení je nyní efektivnější v případě jiných POCMA rovná allocator opětovným použitím vyrovnávací paměti, pokud je to možné.

#### <a name="readability-and-other-improvements"></a>Přehlednosti a další vylepšení

- Standardní knihovna teď používá C ++ 14 `constexpr` bezpodmínečně, místo podmíněně definovány makra.
- Standardní knihovna teď používá šablony alias interně.
- Standardní knihovna teď používá `nullptr` interně, místo provedení `nullptr_t{}`. (Interní použití Null byla odstraněna. Interní použití 0 jako null je ještě čistí postupně.)
- Standardní knihovna teď používá `std::move()` interně místo stylistically zneužití `std::forward()`.
- Změnit `static_assert(false, "message")` k `#error message`. To zvyšuje kompilátoru diagnostics, protože `#error` okamžitě zastaví kompilace.
- Standardní knihovna již označí funkce jako `__declspec(dllimport)`. Moderní linkeru technologie už vyžaduje to.
- Extrahované sfinae u výrazů pro výchozí šablony argumenty, což snižuje zbytečné soubory ve srovnání s vrátí typy a typy argumentů funkce.
- Ladění kontroluje \<náhodných\> místo interní funkce teď používat standardní knihovně obvyklé stroje, `_Rng_abort()` který volá `fputs()` k **stderr**. Implementace této funkce je uchovávané pro binární kompatibilitu, ale byla odebrána v příští verzi binární kompatibilní standardní knihovny.

### <a name="visual-studio-2017-version-155"></a>Visual Studio 2017 verze 15,5

Několik funkce standardní knihovny byly přidány, zastaralé nebo odebrat v souladu s C ++ 17 standard. Další informace najdete v části [vylepšení shoda C++ v sadě Visual Studio](cpp-conformance-improvements-2017.md#improvements_155).

#### <a name="new-experimental-features"></a>Nové povolenými experimentálními funkcemi

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
- Podpisy pro následující paralelní algoritmy jsou přidány, ale není paralelizovaná málo v tuto chvíli; profilace ukázalo žádné výhody v paralelním prováděním algoritmy, které pouze přesunout nebo permute prvky:
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

#### <a name="performance-fixes-and-improvements"></a>Vylepšení a opravy výkonu

- `basic_string<char16_t>` Nyní zapojí stejné `memcmp`, `memcpy`a podobné optimalizace, které `basic_string<wchar_t>` zapojí.
- Omezení optimalizace, které brání ukazatelů na funkce nebudou vloženou obslužnou vystavené naše "vyhnout kopírování funkcí" v sadě Visual Studio 2015 Update 3 byla fungovala kolem, obnovení výkon `lower_bound(iter, iter, function pointer)`.
- Režii iterator ladění je pořadí ověření vstupy `includes`, `set_difference`, `set_symmetric_difference`, a `set_union` se snížila o rozbalení iterátory před zaškrtnutím pořadí.
- `std::inplace_merge` Nyní přeskočí přes prvky, které jsou již v pozici.
- Vytváření `std::random_device` už vytvoří a pak zničí `std::string`.
- `std::equal` a `std::partition` měli přechod threading průchodu optimalizace, které ukládá porovnávání iterator.
- Když `std::reverse` předaný ukazatele trivially kopírovatelná `T`, bude nyní dispatch psané vectorized implementaci.
- `std::fill`, `std::equal`, a `std::lexicographical_compare` byly výukové postupy, do kterého se má `memset` a `memcmp` pro `std::byte` a `gsl::byte` (a další výčty jako char a výčet tříd). Všimněte si, že `std::copy` odešle zprávu pomocí `is_trivially_copyable` a proto nebylo nutné žádné změny.
- Standardní knihovna již obsahuje prázdný závorky destruktory jejichž pouze chování byla aby jiný trivially zničitelné typy.

#### <a name="correctness-fixes-in-visual-studio-2017-version-155"></a>Správnost opravy v aplikaci Visual Studio 2017 verze 15,5

- `std::partition` nyní volání predikát N časy místo N + 1 dobu, jako standardní vyžaduje.
- Pokusí se vyhnout statické objekty magic ve verzi 15.3 opravili ve verzi 15,5.
- `std::atomic<T>` nevyžaduje již `T` jako výchozí zkonstruovatelný.
- Halda algoritmy, které už logaritmické časově udělat lineární čas assertion, že vstup je ve skutečnosti haldy Pokud je povoleno ladění iterátorů.
- `__declspec(allocator)` Nyní je chráněn pro C1XX pouze, aby se zabránilo upozornění Clang, který nerozumí tento declspec.
- `basic_string::npos` je k dispozici jako konstanta doba kompilace.
- `std::allocator` v C ++ 17 režimu je větší než teď správně obslužné rutiny přidělení přepsání zarovnaný typy, typy to znamená, jejichž zarovnání `max_align_t`, pokud zakázal **/Zc:alignedNew-**.  Například vektory objektů s 16 nebo 32 bajtů zarovnání bude nyní správně zarovnán SSE a AVX pokyny.

### <a name="visual-studio-2017-version-156"></a>Visual Studio 2017 verze 15,6 operací

- \<memory_resource >
- Knihovna základy V1
- Odstranění polymorphic_allocator přiřazení
- Odvození argumentu šablony vylepšení – třída

### <a name="visual-studio-2017-version-157"></a>Visual Studio 2017 verze 15.7

- Podpora pro paralelní algoritmy již není experiemental
- na nové implementace \<filesystem >
- základní řetězec převody (částečné)
- std::launder()
- std::Byte
- hypot(x,y,z)
- vyloučení nepotřebných decay
- speciální matematické funkce
- char_traits – constexpr
- odvození příručky pro STL

V tématu [přizpůsobení jazyka Visual C++](visual-cpp-language-conformance.md) Další informace.

## <a name="other-libraries"></a>Další knihovny

### <a name="open-source-library-support"></a>Podpora knihovny s otevřeným zdrojem

**Vcpkg** je nástroj příkazového řádku open source, který výrazně se zjednodušuje proces získávání a vytváření statické knihovny C++ s otevřeným zdrojem a knihovny DLL v sadě Visual Studio. Další informace najdete v tématu [vcpkg: Správce balíčků pro C++](vcpkg.md).

**Visual Studio 2017 verze 15,5**:

### <a name="cpprest-sdk-290"></a>CPPRest SDK 2.9.0

CPPRestSDK, a platformy webového rozhraní API jazyka C++, je aktualizovaná verze 2.9.0. Další informace najdete v tématu [CppRestSDK 2.9.0 je dostupná na Githubu](https://blogs.msdn.microsoft.com/vcblog/2016/10/21/cpprestsdk-2-9-0-is-available-on-github/).

### <a name="atl"></a>ATL

- Ještě další sadu opravy vyhledání názvu shoda
- Existující přesunutí konstruktory a operátory přiřazení jsou nyní správně označené jako jiný vyvolávání přesunout
- Zrušení potlačit platný upozornění C4640 týkající se bezpečného init vlákno z místní statické objekty v atlstr.h
- Vlákno bezpečné inicializace místní statické objekty se automaticky vypnulo v sadě nástrojů XP při [pomocí knihovny ATL a vytváření knihovny DLL]. To již neplatí. Můžete přidat **/Zc:threadSafeInit-** v nastavení projektu, pokud má přístup z více vláken se požaduje bezpečné inicializace vypnout.

### <a name="visual-c-runtime"></a>Modulu runtime Visual C++

- Nové záhlaví "cfguard.h" pro řízení toku ochrana symboly.

## <a name="c-ide"></a>C++ IDE

- Výkon při změně konfigurace je teď vyšší u nativních projektů C++ a mnohem vyšší u projektů C++/CLI. Pokud se konfigurace řešení aktivuje poprvé, bude to teď rychlejší, přičemž všechny následné aktivace této konfigurace řešení budou prakticky okamžité.

**Visual Studio 2017 verze 15.3**:

- Několik průvodců projektu a kódu je přepsaných ve stylu dialogu podpisu.
- **Přidání třídy** nyní přímo spustí průvodce Přidat třídu. Všechny položky, které byly dříve tady jsou nyní k dispozici v části **Přidat > Nová položka**.
- Win32 projekty jsou nyní v části **Windows Desktop** kategorie v **nový projekt** dialogové okno.
- **Konzoly Windows** a **plochy aplikace** šablony nyní vytvoří projektů bez zobrazení průvodce. Nová **Windows Desktop průvodce** v rámci stejné kategorii, která zobrazí stejné možnosti jako starý **Konzolová aplikace Win32** průvodce.

**Visual Studio 2017 verze 15,5**:

Několik operací v jazyce C++ využívající modul IntelliSense pro refaktoring a kód navigační spustit mnohem rychlejší. Následující čísla je založena na řešení Visual Studio chromu s 3500 projekty:

|||
|-|-|
|Funkce|Zlepšení výkonu|
|přejmenování|5.3 x|
|Změna podpisu |4.5 x|
|Najít všechny odkazy|4.7 x|

C++ teď podporuje Ctrl + kliknutí **přejít k definici**, usnadňuje navigace myši do definice. Struktura vizualizér ze sady kancelářským nástrojům Power pack je nyní také součástí produktu ve výchozím nastavení.

## <a name="intellisense"></a>IntelliSense

- Ve výchozím nastavení je nyní používán nový databázový stroj využívající SQLite. Tím se urychlí databázové operace jako **přejít k definici** a **najít všechny odkazy**a budou výrazně zvýšit doba analýza prvotního řešení. Nastavení se přesunula do **nástroje > Možnosti > textový Editor > C/C++ > Upřesnit** (dříve bylo pod... C/C++ | Experimentální).

- Vylepšili jsme výkon IntelliSense v projektech a soubory bez použití předkompilovaných hlaviček – pro hlavičky v aktuální soubor bude vytvořeno automatické předkompilovaných hlaviček.

- Přidali jsme do seznamu chyb filtrování a nápovědu k chybám technologie IntelliSense. Kliknutí na sloupec s chybami teď umožní je filtrovat. Kromě toho kliknutím na konkrétní chyby nebo stisknutím klávesy F1 spustíte online vyhledávání chybové zprávy.

  ![Seznam chyb](media/ErrorList1.png "Seznam chyb")

  ![Filtrovaný seznam chyb](media/ErrorList2.png "Filtrovaný seznam chyb")

- Přidali jsme možnost filtrovat položky seznamu členů podle typu.

  ![Filtrování seznamu členů](media/mlfiltering.png "Filtrování seznamu členů")

- Přidali jsme novou experimentální funkci prediktivní IntelliSense, která poskytuje kontextově závislé filtrování toho, co se zobrazuje v seznamu členů. V tématu [C++ IntelliSense vylepšení - prediktivní IntelliSense & filtrování](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/c-intellisense-improvements-predictive-intellisense-filtering/)
- **Najít všechny odkazy** (Shift + F12) teď základy pomáhá získáte snadno, i v komplexní kódu. Poskytuje pokročilé seskupení, filtrování, řazení, vyhledávání v rámci výsledky a (pro některé jazyky) zabarvení, abyste získali jasné vaše odkazy. Nové uživatelské rozhraní pro jazyk C++, obsahuje informace o tom, jestli jsou jsme čtení nebo zápisu do proměnné.
- Funkce změny tečky na šipku technologie IntelliSense se změnila z experimentální na pokročilou a teď je ve výchozím nastavení povolená. Funkce editor **rozbalte obory** a **rozbalte přednost** také byly přesunuté z experimentální na Upřesnit.
- Povolenými experimentálními funkcemi refaktoringu **změnu podpis** a **extrahovat funkce** jsou nyní k dispozici ve výchozím nastavení.
- Experimentální 'Rychlejší projektu zatížení' funkci pro projekty C++. Při příštím otevření se projekt jazyka C++ zavede se rychleji a potom se bude zavádět skutečně rychle.
- Některé z těchto funkcí jsou společné pro jiné jazyky a některé jsou specifické pro C++. Další informace o těchto nových funkcích najdete v tématu [uvedení Visual Studio "15"](https://blogs.msdn.microsoft.com/visualstudio/2016/10/05/announcing-visual-studio-15-preview-5/).

**Visual Studio 1027 verze 15.7**: přidána podpora pro ClangFormat. Další informace najdete v tématu [ClangFormat podporu Visual Studio 2017](https://blogs.msdn.microsoft.com/vcblog/2018/03/13/clangformat-support-in-visual-studio-2017-15-7-preview-1/).

## <a name="non-msbuild-projects-with-open-folder"></a>Bez MSBuild projekty s otevřít složku

Visual Studio 2017 zavádí **otevřít složku** funkci, která umožňuje kód, vytvářet a ladit ve složce obsahující zdrojový kód, aniž by bylo nutné vytvořit všechny projekty nebo řešení. Díky tomu je mnohem jednodušší začít pracovat s Visual Studio, i když projektu není projektu na základě MSBuild. S **otevřít složku** získat přístup k efektivní kód pochopení, úpravy, sestavování a ladění možnosti, které Visual Studio poskytuje již pro projektů MSBuild. Další informace najdete v tématu [otevřít složku projektů v jazyce Visual C++](ide/non-msbuild-projects.md).

- Vylepšení prostředí Otevřít složku V těchto souborech .json můžete přizpůsobit prostředí:
  - CppProperties.json použijte k přizpůsobení technologie IntelliSense a prostředí procházení.
  - Tasks.json použijte k přizpůsobení kroků sestavení.
  - Launch.json použijte k přizpůsobení prostředí ladění.

**Visual Studio 2017 verze 15.3**:

- Vylepšená podpora pro alternativní kompilátory a prostředí sestavení, jako je například MinGW a emulaci. Další informace najdete v tématu [pomocí MinGW a emulaci s Visual C++ a otevřít složku](https://blogs.msdn.microsoft.com/vcblog/2017/07/19/using-mingw-and-cygwin-with-visual-cpp-and-open-folder/).
- Byla přidána podpora specifické konfigurace a globální proměnné prostředí lze definovat v CppProperties.json a CMakeSettings.json. Konfigurace ladění definované v launch.vs.json a úkoly v tasks.vs.json mohou být spotřebovávána těchto proměnných prostředí. Další informace najdete v tématu [přizpůsobení prostředí s Visual C++ a otevřít složku](https://blogs.msdn.microsoft.com/vcblog/2017/11/02/customizing-your-environment-with-visual-c-and-open-folder/).
- Vylepšená podpora pro generátor expertem CMake společnosti, včetně možnosti snadno cílí na 64bitových platformách.

## <a name="cmake-support-via-open-folder"></a>CMake na podporu přes otevřít složku

Visual Studio 2017 zavádí podporu pro použití CMake projektů bez převodu do souborů projektu nástroje MSBuild (VCXPROJ). Další informace najdete v tématu [CMake projektů v jazyce Visual C++](ide/cmake-tools-for-visual-cpp.md). Otevírání projektů CMake s **otevřít složku** automaticky nakonfiguruje prostředí pro jazyk C++ úpravy, sestavování a ladění.

- C++ IntelliSense funguje bez nutnosti vytvoření souboru CppProperties.json v kořenové složce. Navíc jsme přidali novou rozevírací nabídku, která uživatelům umožňuje snadno přepínat mezi konfiguracemi poskytovanými soubory CMake a CppProperties.json.

- Prostřednictvím souboru CMakeSettings.json, který je umístěný ve stejné složce jako soubor CMakeLists.txt, se podporuje další konfigurace.

  ![Otevřít složku – CMake](media/cmake_cpp.png "Otevřít složku – CMake")

**Visual Studio 2017 verze 15.3**: přidána podpora pro generátor CMake expertem. 

**Visual Studio 2017 verze 15,5**: Import existující CMake přidala se podpora ukládá do mezipaměti. 

**Visual Studio 2017 verze 15.7**: CMake 3.11, analýza kódu v projektech CMake, přidala se podpora cílem zobrazit v Průzkumníku řešení, možnosti mezipaměti generování a kompilace jeden soubor. Další informace najdete v tématu [CMake podpory v sadě Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/cmake-support-in-visual-studio-targets-view-single-file-compilation-and-cache-generation-settings/) a [CMake projektů v jazyce Visual C++](ide/cmake-tools-for-visual-cpp.md).

## <a name="windows-desktop-development-with-c"></a>Vývoj aplikací systému Windows s C++

Při instalaci původní úlohy pro C++ teď poskytujeme podrobnější prostředí instalace. Přidali jsme volitelné součásti, které vám umožní vybrat a nainstalovat jen ty nástroje, které potřebujete.  Všimněte si, že uvedené velikosti instalace součástí uvedené v uživatelském rozhraní instalačního programu nejsou přesné a podceňují skutečnou celkovou velikost.

Když chcete úspěšně vytvářet projekty Win32 v úloze vývoje desktopových aplikací v C++, musíte nainstalovat sadu nástrojů i sadu Windows SDK. Instalace komponenty doporučené (vybrané) **VC ++ 2017 v141 nástrojů (x86, x64)** a **Windows 10 SDK (10.0.nnnnn)** zajišťuje to bude fungovat. Pokud nebudou potřebné nástroje nainstalované, projekty se nevytvoří úspěšně a průvodce přestane reagovat.

**Visual Studio 2017 verze 15,5**:

Nástroje sestavení Visual C++ (dříve k dispozici jako samostatný produkt) jsou nyní zahrnuty jako zatížení v instalačním programu Visual Studio. Tato zatížení nainstaluje jenom nástroje potřebné k sestavení projektů C++ bez instalace Visual Studio IDE. Modulové v140 i v141 jsou zahrnuty. Sada nástrojů v141 obsahuje nejnovější vylepšení v aplikaci Visual Studio 2017 verze 15,5. Další informace najdete v tématu [sestavení nástroje sady Visual Studio nyní zahrnují VS2017 a VS2015 MSVC modulové](https://blogs.msdn.microsoft.com/vcblog/2017/11/02/visual-studio-build-tools-now-include-the-vs2017-and-vs2015-msvc-toolsets/).

## <a name="linux-development-with-c"></a>Vývoj pro Linux s C++

Oblíbené rozšíření [Visual C++ for Linux Development](https://visualstudiogallery.msdn.microsoft.com/725025cf-7067-45c2-8d01-1e0fd359ae6e) je teď součástí sady Visual Studio. Tato instalace nabízí všechno, co potřebujete k vývoji a ladění aplikací v jazyce C++, které se spouštějí v prostředí systému Linux.

**Visual Studio 2017 verze 15.2**:

Byla vylepšena ve sdílení a typ vizualizace kódu napříč platformami. Další informace najdete v tématu [vylepšení Linux C++ pro různé platformy kód sdílení a zadejte vizualizace](https://blogs.msdn.microsoft.com/vcblog/2017/05/10/linux-cross-platform-and-type-visualization/).

**Visual Studio 2017 verze 15,5**:

- Linux zatížení přidala podporu pro **rsync** jako alternativu k **sftp** pro synchronizaci souborů do vzdáleného počítače se systémem Linux.
- Byla přidána podpora křížové kompilace cílení ARM microcontrollers. Chcete-li povolit v instalaci, zvolte **Linux development s jazykem C++** zatížení a vyberte možnost pro **vložených a vývoj IoT**. Tento postup přidá RSZ ARM pro různé nástroje pro kompilaci a ujistěte se do instalace. Další informace najdete v tématu [ARM RSZ křížové kompilace v sadě Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2017/10/23/arm-gcc-cross-compilation-in-visual-studio/).
- Byla přidána podpora pro CMake. Teď můžete pracovat na váš stávající kód CMake základní bez nutnosti ho převést na projekt sady Visual Studio. Další informace najdete v tématu [konfigurace projektu CMake Linux](linux/cmake-linux-project.md).
- Byla přidána podpora pro spuštění vzdálené úlohy. Díky této funkci můžete spustit libovolný příkaz na vzdáleném systému, který je definován v sadě Visual Studio Správce připojení. Vzdálené úlohy také poskytují možnost Kopírovat soubory do vzdáleného systému.
Další informace najdete v tématu [konfigurace projektu CMake Linux](linux/cmake-linux-project.md).

**Visual Studio 2017 verze 15.7**:

- Vylepšení různé scénáře zatížení systému Linux. Další informace najdete v tématu [Linux C++ zatížení vylepšení systému projektu okna konzoly Linux, rsync a připojit k procesu](https://blogs.msdn.microsoft.com/vcblog/2018/03/13/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/).
- IntelliSense pro hlavičky na vzdálená připojení Linux. Další informace najdete v tématu [IntelliSense pro vzdálené hlavičky Linux](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/intellisense-for-remote-linux-headers/) a [konfigurace projektu CMake Linux](linux/cmake-linux-project.md).

## <a name="game-development-with-c"></a>Vývoj her s C++

Využijte naplno potenciál C++ k vytváření profesionálních her využívajících technologii DirectX nebo Cocos2d.

## <a name="mobile-development-with-c-android-and-ios"></a>Mobilní vývoj s jazykem C++ (Android a iOS)

Mobilní aplikace teď můžete vytvářet a ladit pomocí sady Visual Studio, která se umí zaměřit i na Android a iOS.

## <a name="universal-windows-apps"></a>Univerzální aplikace pro Windows

C++ je volitelnou součástí úlohy Universal Windows App.  Upgrade projektů C++ se v tuto chvíli musí provést ručně. Pokud v sadě Visual Studio 2017 otevřete projekt UPW cílený na verzi 140 a nemáte nainstalovanou sadu Visual Studio 2015, musíte na stránkách vlastností projektu vybrat sadu nástrojů verze 141.

## <a name="new-options-for-c-on-universal-windows-platform-uwp"></a>Nové možnosti pro C++ na univerzální platformu Windows (UWP)

Nyní máte nové možnosti pro zápis a balení aplikací C++ pro univerzální platformu Windows a Microsoft Store. Převaděč aplikace Desktop vám pomůže balíček plochy aplikace pro nasazení prostřednictvím Microsoft Store. Další informace najdete v tématu [pomocí modulu Runtime Visual C++ v projektu Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project/) a [přineste vaší aplikace na ploše do univerzální platformu Windows (UWP) s most plochy](/windows/uwp/porting/desktop-to-uwp-root).

**Visual Studio 2017 verze 15,5**:

A **balení projekt aplikace Windows** projektu šablona se přidá, který podporuje balení aplikací klasické pracovní plochy pomocí most plochy. Je k dispozici v části **soubor > Nový > projekt** pod **nainstalovaná > Visual C++ > univerzální platformu Windows** při instalaci zatížení univerzální aplikace pro Windows.

Při zápisu nový kód, teď můžete použít C + +/ WinRT, standardní projekce jazyka C++ pro prostředí Windows Runtime implementována pouze v záhlaví soubory. Ho můžete obě autorovi a využívat žádné kompatibilní se standardy kompilátoru C++ pomocí rozhraní API systému Windows Runtime. C + +/ WinRT určená k poskytování C++ vývojáři prvotřídní přístup k moderní rozhraní API systému Windows. Další informace najdete v tématu [C + +/ WinRT dostupná na Githubu](https://moderncpp.com/).

Od [sestavení 17025 ve Windows SDK zevnitř Preview](https://blogs.windows.com/buildingapps/2017/11/01/windows-10-sdk-preview-build-17025/#ryPH3zAy6yk2cIRX.97), C + +/ WinRT je součástí sady Windows SDK. Další informace najdete v tématu [C + +/ WinRT je nyní zahrnutá Windows SDK](https://blogs.msdn.microsoft.com/vcblog/2017/11/01/cppwinrt-is-now-included-the-windows-sdk/).

## <a name="clangc2-platform-toolset"></a>Sada nástrojů platformy clang/C2

Sada nástrojů Clang/C2, který se dodává s [!INCLUDE[vs_dev15_md](misc/includes/vs_dev15_md.md)] teď podporuje **/bigobj** přepínač, který je zásadní pro sestavování rozsáhlých projektů. Zahrnuje také několik důležitých oprav chyb, jak ve front-endu, tak v back-endu kompilátoru.

## <a name="c-code-analysis"></a>Analýza kódu C++

Se sadou Visual Studio se nyní distribuují moduly pro kontrolu jádra C++, které vynucují [pokyny pro jádro C++](https://github.com/isocpp/CppCoreGuidelines). Jednoduše povolit programy v **rozšíření analýzy kódu** stránku v stránky vlastností projektu a rozšíření budou zahrnuty při spuštění analýzy kódu. Další informace najdete v tématu [pomocí kameny C++ základní pokyny](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

![CppCoreCheck](media/CppCoreCheck.png "Stránka vlastností CppCoreCheck")

**Visual Studio 2017 verze 15.3**: přidána podpora pro pravidla související se správou prostředků.

**Visual Studio 2017 verze 15,5**: kontroluje nové C++ základní pokyny zahrnují správnost chytré ukazatele, správné použití globální inicializátory a označování příznaky použití konstrukce jako `goto` a chybný přetypování.

Některá čísla upozornění, která najdete v 15.3, už nejsou k dispozici v 15.5. Tato upozornění byla nahrazena specifičtějšími kontrolami.

**Visual Studio 2017 verze 15,6 operací**:  
Byla přidána podpora pro jeden soubor analýzy a vylepšení výkonu spuštění analýzy. Další informace najdete v tématu [statické vylepšení Analysis C++ pro Visual Studio 2017 15,6 operací Preview 2](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/c-static-analysis-improvements-for-visual-studio-2017-15-6-preview-2/)

**Visual Studio 2017 verze 15.7**:  

- Přidala se podpora [/ analyze: ruleset](build/reference/analyze-code-analysis.md) který můžete určit, které pravidel analýzy kódu pro spuštění.
- Byla přidána podpora pro další pravidla C++ základní pokynů.  Další informace najdete v tématu [pomocí kameny C++ základní pokyny](/visualstudio/code-quality/using-the-cpp-core-guidelines-checkers).

## <a name="unit-testing"></a>Testování jednotek

**Visual Studio 2017 verze 15,5**:

Test adaptéru Google a Boost.Test jsou nyní k dispozici jako součásti **vývoj plochy s jazykem C++** pracovního vytížení a jsou integrovány s **Průzkumníka testů**. Cmake projektů (pomocí otevřít složku) je přidána podpora CTest, i když Úplná integrace s **Průzkumníka testů** dosud nejsou k dispozici. Další informace najdete v tématu [zápis testů částí pro C/C++](/visualstudio/test/writing-unit-tests-for-c-cpp).

**Visual Studio 2017 verze 15,6 operací**:

- Podpora dynamických knihoven Boost.Test přidala se podpora.
- Šablony položek Boost.Test je teď dostupná v prostředí IDE.

Další informace najdete v tématu [Boost.Test jednotkové testování: Podpora dynamických knihoven a nové šablony položky](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/boost-test-unit-testing-dynamic-library-support-and-new-item-template/). 

**Visual Studio 2017 verze 15.7**:

[Codelensu](https://docs.microsoft.com/en-us/visualstudio/ide/find-code-changes-and-other-history-with-codelens) podporované přidat pro C++ projektů testování částí. Další informace najdete v tématu [uvedení Codelensu pro testování jednotky C++](https://blogs.msdn.microsoft.com/vcblog/2018/04/09/announcing-codelens-for-c-unit-testing/).

## <a name="visual-studio-graphics-diagnostics"></a>Diagnostika grafiky Visual Studio

Diagnostika grafiky Visual Studio je sada nástrojů pro zaznamenávání a analýzu vykreslování a výkonu problémům v Direct3D – aplikace. Funkce diagnostiky grafiky lze použít s aplikacemi, které běží místně na počítači s Windows v emulátoru Windows zařízení nebo na vzdálený počítač nebo zařízení.

- **Vstup a výstup pro vrchol a Geometry shadery:** možnost vstup a výstup vrchol shadery a shadery geometry, musí být jednou z nejžádanějších funkcí a je teď podporuje v nástrojích pro. Jednoduše vyberte fázi VS nebo GS v zobrazení fázemi kanálu spuštění kontroly vstupní a výstupní v následující tabulce.

  ![Vstupní a výstupní pro shadery](media/io-shaders.png)

- **Hledat a filtr v tabulce objektů:** poskytuje rychlý a snadný způsob, jak najít prostředky, které hledáte.

  ![Hledat](media/search.png)

- **Historie prostředků:** toto nové zobrazení nabízí efektivní způsob, jak zobrazit historii celý úpravy prostředku, jak byla použita při vykreslování zaznamenané rámce. K vyvolání historie pro jakýkoli prostředek, jednoduše klikněte na ikonu hodiny vedle jakéhokoli hypertextového odkazu prostředku.

  ![Historie prostředků](media/resource-history.png)

  Bude se zobrazovat nové **historie prostředků** okno nástroje naplněný historii změn prostředku.

  ![Změna zdroje historie](media/resource-history-change.png)

  Všimněte si, že pokud vaše rámce zaznamenaná s úplnou volání zásobníku zaznamenávání povoleno (**Visual Studio > Nástroje > Možnosti** pod **diagnostiky grafiky**), pak kontextu jednotlivých událostí změn lze rychle odvodit a prověřovány v rámci projektu sady Visual Studio.

- **Rozhraní API statistiky:** zobrazit podrobný souhrn využití rozhraní API vašeho rámce. To může být užitečný v zjišťování nemusí Uvědomte si, že na všech děláte volání nebo volání, které provádíte příliš mnoho. Toto okno je k dispozici prostřednictvím **zobrazení > statistiky rozhraní API** ve Visual Studio Graphics Analyzer.

  ![Rozhraní API statistiky](media/api-stats.png)

- **Statistiky paměti:** zobrazit, kolik paměti je ovladač přidělování pro prostředky vytvoříte v rámečku. Toto okno je k dispozici prostřednictvím **zobrazení > paměti statistiky** v **Visual Studio Graphics Analyzer**. Data je možné zkopírovat do souboru CSV pro zobrazení v tabulce tak, že kliknete pravým tlačítkem a vyberete **všechny kopie**.

  ![Statistiky paměti](media/memory-stats.png)

- **Rámce ověření:** nového seznamu chyb a varování poskytuje snadný způsob, jak přejděte seznamu událostí podle potenciálních problémů zjištěných vrstvě Direct3D – ladění. Klikněte na tlačítko **zobrazení > rámce ověření** ve Visual Studio Graphics Analyzer otevřete okno. Pak klikněte na tlačítko **spusťte ověření** zahájíte analýzu. To může trvat několik minut v závislosti na složitosti rámečku.

  ![Rámce ověření](media/frame-validation.png)

- **Rámce analýzy pro D3D12:** analýza snímků použít k analýze výkonu volání kreslení směrované experimenty "co kdyby". Přepněte na kartu analýza snímků a spustit analýzu na Zobrazit sestavu. Další informace, podívejte se [GoingNative 25: Analýza grafických snímků Visual Studio](https://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) videa.

  ![Analýza snímků](media/frame-analysis.png)

- **Vylepšení využití GPU:** otevřít trasování prováděné prostřednictvím profileru využití GPU Visual Studio s grafickým Procesorem zobrazení nebo nástroj Analyzátor výkonu systému Windows (WPA) podrobné analýzy. Pokud máte bude sady nástrojů výkonu systému Windows existuje nainstalované dva hypertextové odkazy, jednu pro WPA a druhou pro zobrazení GPU, v pravém dolním rohu Přehled relace.

  ![Využití GPU](media/gpu-usage.png)

  Trasování otevřít v zobrazení GPU přes tato podpora odkaz synchronizovány přibližování a posouvání v časové ose mezi VS a GPU zobrazení. Zaškrtávací políčko v sadě VS je slouží ke kontrole, zda je povolena synchronizace, nebo ne.

  ![Zobrazení GPU](media/gpu-view.png)
