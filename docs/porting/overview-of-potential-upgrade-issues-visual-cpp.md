---
title: Přehled potenciálních problémů s upgradem (Visual C++)
ms.date: 05/03/2019
ms.assetid: 2c99a8cb-098f-4a9d-bf2c-b80fd06ace43
ms.openlocfilehash: 44fcb6776118e829fe7c96e54f3f51615604ac31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368489"
---
# <a name="overview-of-potential-upgrade-issues-visual-c"></a>Přehled potenciálních problémů s upgradem (Visual C++)

V průběhu let kompilátor Microsoft C++ prošel mnoha změnami, spolu se změnami v samotném jazyce C++, standardní knihovně C++, runtime C (CRT) a dalších knihovnách, jako je knihovna MFC a ATL. V důsledku toho při inovaci aplikace ze starší verze sady Visual Studio můžete setkat s chybami kompilátoru a propojovacím programem v kódu, který byl dříve zkompilován čistě. Čím starší je původní základ kódu, tím větší je potenciál pro takové chyby. Tento přehled shrnuje nejběžnější třídy problémů, se kterými se pravděpodobně setkáte, a obsahuje odkazy na podrobnější informace.

> [!NOTE]
> V minulosti jsme doporučili, aby upgrady, které pokrývají několik verzí sady Visual Studio, byly prováděny postupně jednu verzi najednou. Tento přístup již nedoporučujeme. Zjistili jsme, že je téměř vždy jednodušší upgradovat na nejnovější verzi sady Visual Studio bez ohledu na to, jak starý základ kódu.

Dotazy nebo komentáře k procesu vcupgrade@microsoft.comupgradu lze odeslat společnosti .

## <a name="library-and-toolset-dependencies"></a>Závislosti knihovny a sady nástrojů

> [!NOTE]
> Tato část se vztahuje na aplikace a knihovny vytvořené pomocí sady Visual Studio 2013 a starší. Sady nástrojů používané ve Visual Studiu 2015, Visual Studio 2017 a Visual Studio 2019 jsou binární kompatibilní. Další informace naleznete v [tématu C++ binární kompatibilita mezi Visual Studio 2015 a Visual Studio 2019](binary-compat-2015-2017.md).

Při upgradu aplikace na novou verzi sady Visual Studio je vhodné a v mnoha případech nutné také upgradovat všechny knihovny a knihovny DLL, na které aplikace odkazuje. Vyžaduje buď, že máte přístup ke zdrojovému kódu, nebo že dodavatel knihovny může poskytnout nové binární soubory zkompilované se stejnou hlavní verzí kompilátoru. Pokud je splněna jedna z těchto podmínek, můžete tuto část přeskočit, která se zabývá podrobnostmi o binární kompatibilitě. Pokud ani není tento případ, pak nemusí být možné použít knihovny v upgradované aplikaci. Informace v této části vám pomohou pochopit, zda můžete pokračovat v inovaci.

### <a name="toolset"></a>Sada nástrojů

Formáty souborů OBJ a LIB jsou dobře definované a zřídka se mění. Někdy jsou do těchto formátů souborů provedeny dodatky, ale tyto dodatky obecně nemají vliv na schopnost novějších sad nástrojů využívat soubory objektů a knihovny vytvořené staršími sadami nástrojů. Hlavní výjimkou je zde, pokud kompilujete pomocí [/GL (Optimalizace celého programu)](../build/reference/gl-whole-program-optimization.md). Pokud kompilujete pomocí `/GL`, lze výsledný soubor objektu propojit pouze pomocí stejné sady nástrojů, která byla použita k jeho vytvoření. Takže pokud vytvoříte soubor `/GL` objektu s kompilátorem Visual Studio 2017 (v141) a používáte ho, musíte ho propojit pomocí propojovacího zařízení Visual Studio 2017 (v141). Je to proto, že vnitřní datové struktury v souborech objektů nejsou stabilní v hlavních verzích sady nástrojů a novější sady nástrojů nerozumí starším formátům dat.

C++ nemá stabilní binární rozhraní aplikace (ABI). Ale Visual Studio udržuje stabilní C++ ABI pro všechny dílčí verze verze. Visual Studio 2015 (v140), Visual Studio 2017 (v141) a Visual Studio 2019 (v142) se liší pouze v jejich dílčí verzi. Všechny mají stejné číslo hlavní verze, což je 14. Další informace naleznete v [tématu C++ binární kompatibilita mezi Visual Studio 2015 a Visual Studio 2019](binary-compat-2015-2017.md).

Pokud máte soubor objektu, který má externí symboly s propojením jazyka C++, nemusí být tento soubor objektu správně propojen se soubory objektů vytvořenými jinou hlavní verzí sady nástrojů. Existuje mnoho možných výsledků: odkaz může selhat úplně (například pokud název dekorace změnil). Odkaz může být úspěšný a věci nemusí fungovat za běhu (například pokud se změní rozložení typu). Nebo v mnoha případech se může stát, že věci fungují a nic se nepokazí. Všimněte si také, zatímco C++ ABI není stabilní, C ABI a podmnožinu C++ ABI potřebné pro COM jsou stabilní.

Pokud propojíte knihovnu importu, může být za běhu použita jakákoli pozdější verze redistribuovatelných knihoven sady Visual Studio, které zachovávají kompatibilitu SBI. Pokud je například vaše aplikace zkompilovaná a propojená pomocí sady nástrojů Visual Studio 2015 Update 3, můžete použít libovolné znovu distribuovatelné visual studio 2017 nebo Visual Studio 2019, protože knihovny 2015, 2017 a 2019 si zachovaly zpětnou binární kompatibilitu. Opak není pravdou: Redistribuovatelné nelze použít pro starší verzi sady nástrojů, než jste použili k vytvoření kódu, i když mají kompatibilní ABI.

### <a name="libraries"></a>Knihovny

Pokud kompilujete zdrojový soubor pomocí konkrétní verze souborů hlaviček knihoven sady Visual Studio C++ (podle #including záhlaví), musí být výsledný soubor objektu propojen se stejnou verzí knihoven. Pokud je například zdrojový soubor zkompilován pomocí> immintrin.h sady Visual Studio 2015 Update 3, \<musíte se propojit s knihovnou vcruntime aktualizace 3 sady Visual Studio. Podobně pokud je zdrojový soubor kompilován s> iostream u \<sady Visual Studio 2017 verze 15.5, musíte propojit s knihovnou 15.5 Standard C++ sady Visual Studio verze 15.5 Standard, msvcprt. Míchání a párování není podporováno.

Pro standardní knihovnu Jazyka C++ bylo míchání a párování explicitně `#pragma detect_mismatch` zakázáno pomocí použití ve standardních záhlavích od visual studia 2010. Pokud se pokusíte propojit nekompatibilní soubory objektů nebo pokud se pokusíte propojit s nesprávnou standardní knihovnou, odkaz se nezdaří.

Pro CRT míchání a porovnávání nebyl nikdy podporován, ale často jen pracoval, alespoň do Visual Studio 2015 a Univerzální CRT, protože povrch rozhraní API se v průběhu času příliš nezměnil. Univerzální CRT zlomil zpětnou kompatibilitu, takže v budoucnu můžeme zachovat zpětnou kompatibilitu. Jinými slovy, nemáme v plánu zavést nové, verze Universal CRT binární soubory v budoucnu. Místo toho je existující univerzální CRT nyní aktualizován na místě.

Abychom zajistili částečnou kompatibilitu s objektovými soubory (a knihovnami) zkompilovanými se staršími verzemi hlaviček Microsoft C Runtime, poskytujeme knihovnu legacy_stdio_definitions.lib s Visual Studio 2015 a novější. Tato knihovna poskytuje symboly kompatibility pro většinu funkcí a exporty dat, které byly odebrány z univerzální crt. Sada symbolů kompatibility poskytovaná souborem legacy_stdio_definitions.lib je dostatečná k uspokojení většiny závislostí, včetně všech závislostí v knihovnách zahrnutých v sadě Windows SDK. Existují však některé symboly, které byly odebrány z univerzální CRT, pro které není možné poskytnout symboly kompatibility. Tyto symboly zahrnují některé \_ \_funkce\_(například iob func) \_ \_a\_\_\_exportdat \_ \_(například imp iob, imp\_\_\_ \_ \_pctype,\_\_\_imp mb\_cur\_max).

Pokud máte statickou knihovnu, která byla vytvořena se starší verzí záhlaví C Runtime, doporučujeme následující akce v tomto pořadí:

1. Znovu sestavte statickou knihovnu pomocí nové verze sady Visual Studio a univerzálních hlaviček CRT pro podporu propojení s univerzálním crtem. Tento přístup je plně podporovanou (a tedy nejlepší) možností.

1. Pokud nemůžete (nebo nechcete) znovu vytvořit statickou knihovnu, můžete\_zkusit\_propojení s odkazem stdio definitions.lib. Pokud splňuje závislosti v době propojení statické knihovny, budete chtít důkladně otestovat statickou knihovnu, jak se používá v binárním souboru, abyste se ujistili, že není nepříznivě ovlivněna žádnou změnou [chování, která byla provedena v univerzálním CRT](visual-cpp-change-history-2003-2015.md#BK_CRT).

1. Pokud nejsou závislosti statické knihovny splněny\_starším\_souborem stdio definitions.lib nebo pokud knihovna nefunguje s univerzálním crtem z důvodu výše uvedených změn chování, doporučujeme zavést statickou knihovnu do knihovny DLL, kterou propojíte se správnou verzí systému Microsoft C Runtime. Například pokud byla vytvořena statická knihovna pomocí Visual Studia 2013, měli byste vytvořit tuto knihovnu DLL pomocí Visual Studio 2013 a Visual Studio 2013 C++ knihovny stejně. Vytvořením knihovny do knihovny DLL zapouzdřte podrobnosti implementace, která je její závislost na konkrétní verzi microsoft c runtime. Budete chtít být opatrní, že rozhraní Knihovny DLL nepropustí podrobnosti o tom, který C Runtime používá, například vrácením SOUBORu* přes hranici knihovny DLL nebo vrácením ukazatele přiděleného malloc a očekáváním, že ho volající uvolní.

Použití více CRT v jednom procesu není samo o sobě problematické (většina procesů nakonec načte více knihoven DLL CRT; například součásti operačního systému Windows budou záviset na msvcrt.dll a CLR bude záviset na vlastní privátní CRT). Problémy vznikají, když změť stavu z různých CRTs. Například byste neměli přidělovat paměť pomocí msvcr110.dll!malloc a pokusit se tuto paměť navrátit pomocí msvcr120.dll!free a neměli byste se pokoušet otevřít soubor pomocí msvcr110!fopen a pokusit se číst z tohoto souboru pomocí msvcr120!fread. Tak dlouho, dokud nezměť stavu z různých CRTs, můžete bezpečně mít více CRTs načtenv jednom procesu.

Další informace naleznete v [tématu Upgrade kódu na univerzální CRT](upgrade-your-code-to-the-universal-crt.md).

## <a name="errors-due-to-project-settings"></a>Chyby způsobené nastavením projektu

Chcete-li zahájit proces upgradu, otevřete starší projekt/řešení/pracovní prostor v nejnovější verzi sady Visual Studio. Visual Studio vytvoří nový projekt založený na nastavení starého projektu. Pokud starší projekt obsahuje knihovnu nebo obsahuje cesty, které jsou pevně zakódovány do nestandardních umístění, je možné, že soubory v těchto cestách nebudou viditelné kompilátoru, když projekt používá výchozí nastavení. Další informace naleznete v tématu [Nastavení výstupu linkeru](porting-guide-spy-increment.md#linker_output_settings).

Obecně platí, že nyní je skvělý čas správně uspořádat kód projektu, aby se zjednodušila údržba projektu a pomohla vám co nejrychleji sestavit upgradovaný kód. Pokud je zdrojový kód již dobře uspořádaný a starší projekt je zkompilován pomocí sady Visual Studio 2010 nebo novější, můžete ručně upravit nový soubor projektu pro podporu kompilace na starém i novém kompilátoru. Následující příklad ukazuje, jak zkompilovat pro Visual Studio 2015 a Visual Studio 2017:

```xml
<PlatformToolset Condition="'$(VisualStudioVersion)'=='14.0'">v140</PlatformToolset>
<PlatformToolset Condition="'$(VisualStudioVersion)'=='15.0'">v141</PlatformToolset>
```

### <a name="lnk2019-unresolved-external"></a>LNK2019: Nevyřešené externí

U nevyřešených symbolů může být nutné opravit nastavení projektu.

- Pokud je zdrojový soubor ve nevýchozím umístění, přidali jste cestu k adresářům zahrnutí projektu?

- Pokud je externí definován v souboru LIB, zadali jste cestu lib ve vlastnostech projektu a je správná verze souboru LIB umístěná tam?

- Pokoušíte se vytvořit odkaz na soubor LIB, který byl zkompilován s jinou verzí sady Visual Studio? Pokud ano, podívejte se na předchozí část o závislostech knihovny a sady nástrojů.

- Odpovídají typy argumentů na webu volání ve skutečnosti existujícímu přetížení funkce? Ověřte základní typy pro všechny typedefs v podpisu funkce a v kódu, který volá funkce jsou to, co očekáváte, že budou.

Chcete-li odstranit nevyřešené chyby symbolů, můžete zkusit pomocí dumpbin.exe prozkoumat symboly definované v binárním souboru. Chcete-li zobrazit symboly definované v knihovně, vyzkoušejte následující příkazový řádek:

```cmd
dumpbin.exe /LINKERMEMBER somelibrary.lib
```

### <a name="zcwchar_t-wchar_t-is-native-type"></a>/Zc:wchar_t (wchar_t je nativní typ)

(V jazyce Microsoft Visual C++ 6.0 a **starší, wchar_t** nebyl implementován jako předdefinovaný typ, ale byl deklarován v wchar.h jako typedef pro nepodepsané krátké.) Standard C++ vyžaduje, **aby wchar_t** je vestavěný typ. Použití verze typedef může způsobit problémy s přenositelností. Pokud inovujete z dřívějších verzí sady Visual Studio a dojdek k chybě kompilátoru C2664, protože se kód pokouší implicitně `/Zc:wchar_t-`převést **wchar_t** na **nepodepsané krátké**, doporučujeme změnit kód a opravit chybu namísto nastavení . Další informace naleznete v tématu [/Zc:wchar_t (wchar_t je nativní typ).](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)

### <a name="upgrading-with-the-linker-options-nodefaultlib-entry-and-noentry"></a>Inovace s možnostmi propojovacího zařízení /NODEFAULTLIB, /ENTRY a /NOENTRY

Možnost `/NODEFAULTLIB` propojovacího systému (nebo vlastnost Ignorovat všechny výchozí knihovny propojovacího zařízení) říká propojovacímu zařízení, aby automaticky nepropojil ve výchozích knihovnách, jako je například CRT. To znamená, že každá knihovna musí být uvedena jako vstup jednotlivě. Tento seznam knihoven je uveden ve **vlastnosti Další závislosti** v části **Propojovací zařízení** v dialogovém okně **Vlastnosti projektu.**

Projekty, které používají tuto možnost představují problém při upgradu, protože obsah některé výchozí knihovny byly refaktorovány. Vzhledem k tomu, že každá knihovna musí být uvedena ve **vlastnosti Další závislosti** nebo na příkazovém řádku linkeru, je třeba aktualizovat seznam knihoven, aby bylo možné použít všechny aktuální názvy.

V následující tabulce jsou uvedeny knihovny, jejichž obsah se změnil počínaje Visual Studio 2015. Chcete-li upgradovat, je třeba přidat nové názvy knihoven v druhém sloupci do knihoven v prvním sloupci. Některé z těchto knihoven jsou importní knihovny, ale na tom by nemělo záležet.

|||
|-|-|
|Pokud jste používali:|Musíte použít tyto knihovny:|
|libcmt.lib|libcmt.lib, libucrt.lib, libvcruntime.lib|
|libcmtd.lib|libcmtd.lib, libucrtd.lib, libvcruntimed.lib|
|msvcrt.lib|msvcrt.lib, ucrt.lib, vcruntime.lib|
|msvcrtd.lib|msvcrtd.lib, ucrtd.lib, vcruntimed.lib|

Stejný problém platí také v `/ENTRY` případě, `/NOENTRY` že použijete možnost nebo možnost, které mají také za následek vynechání výchozí knihovny.

## <a name="errors-due-to-improved-language-conformance"></a>Chyby způsobené lepší shodou jazyka

Kompilátor Microsoft C++ v průběhu let neustále vylepšoval shodu se standardem C++. Kód, který byl kompilován v dřívějších verzích, se nemusí zkompilovat v novějších verzích sady Visual Studio, protože kompilátor správně označí chybu, kterou dříve ignoroval nebo explicitně povolil.

Například `/Zc:forScope` přepínač byl zaveden na počátku historie MSVC. Umožňuje nevyhovující chování pro proměnné smyčky. Tento přepínač je nyní zastaralé a může být odebrán v budoucích verzích. Důrazně doporučujeme nepoužívat tento přepínač při upgradu kódu. Další informace naleznete v tématu [/Zc:forScope- je zastaralé](porting-guide-spy-increment.md#deprecated_forscope).

Jedním z příkladů běžné chyby kompilátoru, která se může zobrazit při upgradu je, když je argument non-const předán parametru const. Starší verze kompilátoru ne vždy příznak jako chybu. Další informace naleznete [v tématu přísnější převody kompilátoru](porting-guide-spy-increment.md#stricter_conversions).

Další informace o konkrétnívylepšení shody naleznete v [tématu Visual C++ historie změn 2003 - 2015](visual-cpp-change-history-2003-2015.md) a [C++ vylepšení shody v sadě Visual Studio](../overview/cpp-conformance-improvements.md).

## <a name="errors-involving-stdinth-integral-types"></a>Chyby \<zahrnující stdint.h> integrální typy

Hlavička \<> stdint.h definuje typedefs a makra, která na rozdíl od předdefinovaných integrálních typů mají zaručenou zadanou délku na všech platformách. Některé příklady `uint32_t` `int64_t`jsou a . Hlavička \<> stdint.h byla přidána do sady Visual Studio 2010. Kód, který byl napsán před rokem 2010 může mít za předpokladu, soukromé \<definice pro tyto typy a tyto definice nemusí být vždy v souladu s definicemi> stdint.h.

Pokud je chyba C2371 `stdint` a jedná se o typ, pravděpodobně to znamená, že typ je definován v záhlaví buď v kódu, nebo v souboru lib jiného výrobce. Při upgradu byste měli odstranit všechny \<vlastní definice typů> stdint.h, ale nejprve porovnat vlastní definice s aktuálnístandardní definice zajistit, že nejste zavedení nových problémů.

Stisknutím **klávesy F12** (**Přejít na definici)** zobrazíte, kde je daný typ definován.

Možnost kompilátoru [/showIncludes](../build/reference/showincludes-list-include-files.md) může být užitečná zde. V dialogovém okně **Stránky vlastností** projektu otevřete stránku **C/C++** > **Advanced** a nastavte **zobrazit zahrnutí** na **hodnotu Ano**. Potom znovu sestavte projekt `#include`a podívejte se na seznam s ve výstupním okně. Každé záhlaví je odsazeno pod záhlavím, které jej obsahuje.

## <a name="errors-involving-crt-functions"></a>Chyby týkající se funkcí CRT

V průběhu let bylo provedeno mnoho změn v běhu C. Bylo přidáno mnoho zabezpečených verzí funkcí a některé byly odebrány. Také, jak je popsáno výše v tomto článku, Microsoft implementace CRT byl refaktored v sadě Visual Studio 2015 do nové binární soubory a přidružené soubory LIB.

Pokud chyba zahrnuje funkci CRT, vyhledejte [Visual C++ historie změn 2003 - 2015](visual-cpp-change-history-2003-2015.md) nebo [C++ vylepšení shody v sadě Visual Studio](../overview/cpp-conformance-improvements.md) a zjistěte, zda tyto články obsahují další informace. Pokud je chyba LNK2019, nevyřešené externí, ujistěte se, že funkce nebyla odebrána. V opačném případě, pokud jste si jisti, že funkce stále existuje a volající `/NODEFAULTLIB`kód je správný, zkontrolujte, zda váš projekt používá . Pokud ano, je třeba aktualizovat seznam knihoven tak, aby projekt používá nové univerzální (UCRT) knihovny. Další informace naleznete v části výše na knihovnu a závislosti.

Pokud chyba `printf` zahrnuje `scanf`nebo , ujistěte se, že nejste soukromě definování buď funkce bez zahrnutí stdio.h. Pokud ano, odeberte soukromé definice\_nebo\_odkaz na starší stdio definitions.lib. Tuto knihovnu můžete nastavit v dialogovém okně **Stránky vlastností** v části**Vstup****linkeru** >  **vlastností** > konfigurace ve **vlastnosti Další závislosti.** Pokud propojujete se sadou Windows SDK\_8.1 nebo starší, přidejte starší stdio\_definitions.lib.

Pokud chyba zahrnuje argumenty řetězce formátu, je to pravděpodobně proto, že kompilátor je přísnější o vynucení standardu. Další informace naleznete v historii změn. Věnujte velkou pozornost všem chybám, protože mohou potenciálně představovat bezpečnostní riziko.

## <a name="errors-due-to-changes-in-the-c-standard"></a>Chyby způsobené změnami ve standardu C++

Samotný standard C++ se vyvinul způsobem, který není vždy zpětně kompatibilní. Úvod v jazyce C++ 11 přesunout sémantiku, nová klíčová slova a další jazyk a standardní funkce knihovny může potenciálně způsobit chyby kompilátoru a dokonce i různé chování za běhu.

Starý program jazyka C++ může například obsahovat záhlaví iostream.h. Toto záhlaví bylo zastaralé na začátku historie jazyka C++ a nakonec byl zcela odebrán z sady Visual Studio. V takovém případě budete muset \<použít> iostream a přepsat kód. Další informace naleznete [v tématu Aktualizace starého kódu iostreams](porting-guide-spy-increment.md#updating_iostreams_code).

### <a name="c4838-narrowing-conversion-warning"></a>C4838: upozornění na zužující převod

Standard Jazyka C++ nyní určuje, že převody z nepodepsaných na podepsané integrální hodnoty jsou považovány za zužující se převody. Kompilátor nevyvolal toto upozornění před Visual Studio 2015. Zkontrolujte každý výskyt a ujistěte se, že zúžení nemá vliv na správnost kódu.

## <a name="warnings-to-use-secure-crt-functions"></a>Upozornění na použití zabezpečených funkcí CRT

V průběhu let byly zavedeny zabezpečené verze funkcí runtime C. Přestože staré, nezabezpečené verze jsou stále k dispozici, doporučujeme změnit kód tak, aby používal zabezpečené verze. Kompilátor vydá upozornění pro použití nezabezpečených verzí. Tato upozornění můžete zakázat nebo ignorovat. Chcete-li upozornění zakázat pro všechny projekty v řešení, otevřete **možnost Zobrazit** > **Správce vlastností**, vyberte všechny projekty, u kterých chcete upozornění zakázat, klikněte pravým tlačítkem myši na vybrané položky a zvolte **Vlastnosti**. V dialogovém okně **Stránky vlastností** v části **Vlastnosti** > konfigurace**C/C++** > **Upřesnit**vyberte **Zakázat konkrétní upozornění**. Klikněte na šipku rozevíracího seznamu a potom klikněte na **Upravit**. Do textového pole zadejte 4996. (Nezahrnujte předponu "C".) Další informace naleznete v [tématu Porting a použijte zabezpečené crt](porting-guide-spy-increment.md#porting_to_secure_crt).

## <a name="errors-due-to-changes-in-windows-apis-or-obsolete-sdks"></a>Chyby způsobené změnami v instalačních programech systému Windows nebo zastaralých sadách SDK

V průběhu let byla přidána a někdy změněna nebo odebrána okna WINDOWS API a datové typy. Také ostatní sady SDK, které nepatřily do základního operačního systému, přicházejí a odcházejí. Starší programy proto mohou obsahovat volání api, která již neexistují. Mohou také obsahovat volání rozhraní API v jiných sadách Microsoft SDK, které již nejsou podporovány. Pokud se zobrazí chyba zahrnující rozhraní API systému Windows nebo rozhraní API ze starší sady Microsoft SDK, je možné, že rozhraní API bylo odebráno nebo nahrazeno novější, bezpečnější funkcí.

Další informace o aktuální sadě rozhraní API a minimálních podporovaných operačních systémech pro konkrétní rozhraní API systému Windows naleznete v tématu [Microsoft API a referenční katalog](https://msdn.microsoft.com/library) a přejděte k dotyčnému rozhraní API.

### <a name="windows-version"></a>Verze systému Windows

Při inovaci programu, který používá rozhraní API systému Windows přímo nebo nepřímo, budete muset rozhodnout minimální verzi systému Windows pro podporu. Ve většině případů je Windows 7 dobrou volbou. Další informace naleznete v tématu [Problémy se souborem záhlaví](porting-guide-spy-increment.md#header_file_problems). Makro `WINVER` definuje nejstarší verzi systému Windows, ve které je program určen ke spuštění. Pokud program knihovny MFC nastaví winver na 0x0501 (Windows XP), zobrazí se upozornění, protože knihovna MFC již nepodporuje xp, i když samotný kompilátor má režim XP.

Další informace naleznete [v tématu Aktualizace cílové verze systému Windows](porting-guide-spy-increment.md#updating_winver) a další zastaralé soubory [hlaviček](porting-guide-spy-increment.md#outdated_header_files).

## <a name="atl--mfc"></a>KNIHOVNA ATL / Knihovna

KNIHOVNY ATL a Knihovny MFC jsou relativně stabilní, ale občas se provádějí změny. Další informace naleznete v [tématu Visual C++ historie změn 2003 - 2015](visual-cpp-change-history-2003-2015.md), [Co je nového pro Visual C++ v sadě Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)a vylepšení [shody Jazyka C++ v sadě Visual Studio](../overview/cpp-conformance-improvements.md).

### <a name="lnk-2005-_dllmain12-already-defined-in-msvcrtdlib"></a>LNK 2005 _DllMain@12 již definována v MSVCRTD.lib

K této chybě může dojít v aplikacích knihovny MFC. Označuje problém s řazením mezi knihovnou CRT a knihovnou knihovny MFC. Knihovna MFC musí být nejprve propojena, aby poskytovala nové a odstraňovala operátory. Chcete-li chybu opravit, použijte `/NODEFAULTLIB` přepínač ignorovat tyto výchozí knihovny: MSVCRTD.lib a mfcs140d.lib. Pak přidejte stejné libs jako další závislosti.

## <a name="32-vs-64-bit"></a>32 vs 64 bitů

Pokud je původní kód kompilován pro 32bitové systémy, máte možnost vytvořit 64bitovou verzi namísto nebo vedle nové 32bitové aplikace. Obecně byste měli nejprve sestavit program v 32bitovém režimu a pak se pokusit o 64bitový pokus. Kompilace pro 64bitové je jednoduché, ale v některých případech může odhalit chyby, které byly skryty 32bitovými sestaveními.

Také byste si měli být vědomi možných problémů s kompilováním a za běhu týkajícími se velikosti ukazatele, hodnot času a velikosti a specifikátorů formátu ve funkcích printf a scanf. Další informace naleznete [v tématu Konfigurace visual c++ pro 64bitové cíle x64](../build/configuring-programs-for-64-bit-visual-cpp.md) a [běžné problémy s 64bitovou migrací jazyka Visual C++](../build/common-visual-cpp-64-bit-migration-issues.md). Další tipy pro migraci najdete [v tématu Programming Guide pro 64bitový systém Windows](/windows/win32/WinProg64/programming-guide-for-64-bit-windows).

## <a name="unicode-vs-mbcsascii"></a>Unicode vs MBCS/ASCII

Před standardizováním unicode mnoho programů používalo vícebajtovou znakovou sadu (MBCS) k reprezentaci znaků, které nebyly zahrnuty do znakové sady ASCII. Ve starších projektech knihovny MFC byla výchozí hodnota mbcs a při upgradu takového programu se zobrazí upozornění, která doporučují místo toho používat kódování Unicode. Pokud se rozhodnete, že převod na unicode nestojí za náklady na vývoj, můžete toto upozornění zakázat nebo ignorovat. Chcete-li jej zakázat pro všechny projekty ve vašem řešení, otevřete **možnost Zobrazit** > **Správce vlastností**, vyberte všechny projekty, u kterých chcete upozornění zakázat, klikněte pravým tlačítkem myši na vybrané položky a zvolte **Vlastnosti**. V dialogovém okně **Stránky vlastností** vyberte **Vlastnosti** > konfigurace**C/C++** > **Upřesnit**. Ve vlastnosti **Zakázat konkrétní upozornění** otevřete šipku rozevíracího seznamu a pak zvolte **Upravit**. Do textového pole zadejte 4996. (Nezahrnujte předponu "C".) Chcete-li vlastnost uložit, zvolte **OK** a pak zvolte **OK,** chcete-li uložit změny.

Další informace naleznete v [tématu Porting from MBCS to Unicode](porting-guide-spy-increment.md#porting_to_unicode). Obecné informace o mbcs vs Unicode naleznete [v tématu Text a řetězce ve visual c++](../text/text-and-strings-in-visual-cpp.md) a [internacionalizace](../c-runtime-library/internationalization.md) .

## <a name="see-also"></a>Viz také

[Inovace projektů z dřívějších verzí visual c++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Vylepšení shody C++ se sadou Visual Studio](../overview/cpp-conformance-improvements.md)
