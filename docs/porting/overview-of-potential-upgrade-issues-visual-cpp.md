---
title: Přehled potenciálních problémů s upgradem (Visual C++)
ms.date: 05/03/2019
ms.assetid: 2c99a8cb-098f-4a9d-bf2c-b80fd06ace43
ms.openlocfilehash: e22a3a0889bfc9352a8fe9d2a79fe37bcb757107
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448893"
---
# <a name="overview-of-potential-upgrade-issues-visual-c"></a>Přehled potenciálních problémů s upgradem (Visual C++)

V průběhu let Microsoft C++ kompilátoru prošla řadou změn spolu se změnami C++ samotný, jazyk C++ standardní knihovny C runtime (CRT) a dalších knihoven, jako je například knihovny MFC a ATL. V důsledku toho při upgradu aplikace ze starší verze sady Visual Studio můžete setkat, kompilátoru a linkeru chyby a upozornění v kódu, který dříve zkompilován čistě. Starší základní původního kódu, tím větší potenciál pro takové chyby. Tento přehled obsahuje souhrn třídy většiny běžných problémů, budete pravděpodobně dojde, a nabízí odkazy k podrobnějším informacím.

> [!NOTE]
> V minulosti doporučujeme mít, upgrady, které jsou rozmístěny v několika verzích sady Visual Studio měli provádět přírůstkové jedné verze najednou. Doporučujeme, abyste už tento přístup. Zjistili jsme, že je téměř vždy jednodušší pro upgrade na nejnovější verzi sady Visual Studio bez ohledu na to, kolik základu kódu.

Je možné odeslat dotazy nebo připomínky k upgradu vcupgrade@microsoft.com.

## <a name="library-and-toolset-dependencies"></a>Závislosti knihoven a nástrojů

> [!NOTE] 
> Tato část se týká aplikací a knihoven, které jsou vytvořené pomocí sady Visual Studio 2013 a starší. Sady nástrojů používá v sadě Visual Studio 2015, Visual Studio 2017 a Visual Studio 2019 jsou binární kompatibilní. Další informace najdete v tématu [ C++ binární kompatibilitu mezi Visual Studio 2015 a Visual Studio 2019](binary-compat-2015-2017.md).

Při upgradu aplikace na novou verzi sady Visual Studio, se důrazně doporučuje a v mnoha případech nutné také upgradovat všechny knihovny a knihovny DLL, které aplikace se odkazuje na. To vyžaduje, abyste měli přístup ke zdrojovému kódu, nebo, dodavatele knihovny můžete zadat nové binární soubory zkompilovány se stejnou hlavní verzí kompilátoru. Pokud je splněna jedna z těchto podmínek, můžete přeskočit tuto část, která se zabývá podrobnosti binární kompatibilitu. Pokud ani jeden z jsou případu, pak nebudete moci používat knihovny v aplikaci upgradovaný. Informace v této části vám pomůže pochopit, jestli vám pokračujte v upgradu.

### <a name="toolset"></a>Sada nástrojů

Formáty souborů .obj a. lib jsou dobře definovaný a jen zřídka mění. Někdy jsou dodatky provedené do těchto formátů souborů, ale tyto doplňky obecně vliv na schopnost novější sady nástrojů využívat objektových souborů a knihoven vytvářených starší sady nástrojů. Zde jeden velký výjimkou je, pokud kompilujete pomocí [/GL (optimalizace celého programu)](../build/reference/gl-whole-program-optimization.md). Pokud kompilujete pomocí `/GL`, výsledný soubor objektu lze propojit pouze pomocí stejné sady nástrojů, který byl použit k jeho vytvoření. Pokud vytvoříte soubor objektu se tedy `/GL` a pomocí kompilátoru Visual Studio 2017 (verze 141), je třeba propojit pomocí sady Visual Studio 2017 (verze 141) linkeru. Je to proto, že interní datové struktury v rámci objektu soubory nejsou stabilní mezi hlavními verzemi sady nástrojů a novější sady nástrojů není srozumitelný starší formáty data.

C++ nemá binární rozhraní stabilní aplikace (ABI). Visual Studio udržuje stabilní, ale C++ ABI pro všechny dílčí verze na verzi. Visual Studio 2015 (v140), Visual Studio 2017 (verze 141) a Visual Studio 2019 (v142) se liší pouze v jejich podverze. Všichni mají stejné číslo hlavní verze, která je 14. Další informace najdete v tématu [ C++ binární kompatibilitu mezi Visual Studio 2015 a Visual Studio 2019](binary-compat-2015-2017.md). 

Pokud máte soubor objektu, který má externích symbolů se C++ propojení, tento objekt soubor nemusí správně propojit pomocí objektu soubory vytvořenými pomocí různých hlavní verzi sady nástrojů. Všimněte si, že tady "nemusí fungovat" má mnoho možných výsledků: odkaz nemusí zcela (například ke změně dekorování názvů), může být úspěšné, propojení a nemusí fungovat věci za běhu (například pokud změnit typ rozložení), nebo se může stát pro práci v řadě případů a ne věc, kterou může pokazit. Všimněte si také, že C++ ABI není stabilní, C ABI a dílčí sadu C++ ABI požadované pro COM jsou stabilní.

Pokud odkaz na knihovnu importu, všechny novější verze sady Visual Studio distribuovatelných knihoven, které zachování kompatibility ABI lze za běhu. Například pokud vaše aplikace je kompilována a propojené pomocí sady nástrojů Visual Studio 2015 Update 3, můžete všechny sady Visual Studio 2017 nebo Visual Studio 2019 distribuovatelné součásti, protože knihovny 2015 a 2017 mají zachovají binární zpětné kompatibility. Opak není pravdou; nelze použít distribuovatelné součásti pro starší verzi sady nástrojů než použijete k sestavení vašeho kódu i v případě, že mají kompatibilní ABI.

### <a name="libraries"></a>Knihovny

Pokud kompilujete zdrojový soubor pomocí konkrétní verzi soubory hlaviček knihoven Visual Studio C++ (podle #including záhlaví), výsledný soubor objektu musí být spojen se stejnou verzí knihoven. Tak například, pokud zdrojový soubor je zkompilován s Visual Studio 2015 Update 3 \<immintrin.h >, je třeba propojit s knihovnou vcruntime Visual Studio 2015 Update 3. Podobně pokud zdrojový soubor je zkompilován pomocí sady Visual Studio 2017 verze 15.5 \<iostream – >, je třeba propojit s Visual Studio 2017 verze 15.5 standardní knihovně C++, msvcprt. Kombinování a odpovídající se nepodporuje.

Pro standardní knihovny C++, kombinování a odpovídající byl explicitně zakázán prostřednictvím použití `#pragma detect_mismatch` v záhlaví standardní od verze Visual Studio 2010. Pokud se pokusíte propojit nekompatibilní objekt soubory nebo pokud se pokusíte připojit pomocí nesprávného standardní knihovny, propojení se nezdaří.

Pro CRT kombinování a odpovídající se nikdy podporované, ale často právě pracoval, alespoň až do sady Visual Studio 2015 a Universal CRT, protože většinu časem nezměnil plochy rozhraní API. Universal CRT tak, aby v budoucnu může udržujeme zpětné kompatibility se podařilo přerušit zpětné kompatibility. Jinými slovy nemáme žádné plány zavést nové, verze binárních souborů Universal CRT v budoucnu. Místo toho stávající Universal CRT je teď aktualizace na místě.

Pro zajištění kompatibility částečný odkaz s objektem soubory (a knihoven) kompilaci se staršími verzemi Microsoft C Runtime záhlaví, poskytujeme knihovnu legacy_stdio_definitions.lib pomocí sady Visual Studio 2015 a novější. Tato knihovna poskytuje kompatibilitu symboly pro většinu exporty funkce a data, kteří byli odebráni z Universal CRT. Sada kompatibility symbolů poskytovaných legacy_stdio_definitions.lib není dostatečná pro uspokojení většina závislosti, včetně všech závislostí knihoven, které jsou součástí sady Windows SDK. Existují však některé symboly, které byly odebrány ze Universal CRT, pro kterou není možné zajistit kompatibilitu symboly následujícím způsobem. Některé funkce zahrnují tyto symboly (například \_ \_iob –\_func) a export dat (například \_ \_imp\_\_\_iob –, \_ \_imp\_\_\_pctype –, \_ \_imp\_\_\_mb\_Měna\_maximální).

Pokud budete mít statickou knihovnu, která byla vytvořena pomocí starší verze záhlaví modulu C Runtime, doporučujeme následující akce (v uvedeném pořadí):

1. Znovu sestavte pomocí sady Visual Studio 2017 a Universal CRT záhlaví pro podporu propojení s Universal CRT statické knihovny. Toto je možnost plně podporované (a tedy nejlepší).

1. Pokud je nemůžete (nebo nechcete) znovu vytvořit statické knihovny, můžete zkusit propojení s starší verze\_stdio\_definitions.lib. Pokud splňuje závislosti propojování statické knihovny, budete chtít důkladně otestovat statické knihovny, protože se používá v binárním souboru, abyste měli jistotu, že není nepříznivě ovlivněny podle těchto sloupců [nějaké změny, které byly provedeny Universal CRT](visual-cpp-change-history-2003-2015.md#BK_CRT).

1. Pokud nejsou splněné statickou knihovnu závislosti pomocí starší verze\_stdio\_definitions.lib nebo pokud knihovny nefunguje s Universal CRT kvůli výše uvedené nějaké změny, doporučujeme zapouzdření vaší Statická knihovna na knihovnu DLL, propojení se správnou verzí modulu Runtime jazyka C společnosti Microsoft. Pokud se statickou knihovnou byl vytvořen pomocí sady Visual Studio 2013, by například chcete sestavit tuto knihovnu DLL pomocí sady Visual Studio 2013 a na Visual Studio 2013 C++ knihovny. Vytvořením knihovny do knihovny DLL zapouzdřit podrobnosti implementace, která je závislá na konkrétní verzi modulu Runtime jazyka C společnosti Microsoft. (Všimněte si, že můžete mít na paměti, že rozhraní DLL není úniku podrobností, které C runtime používá, třeba tak, že vrací soubor * přes hranice knihovny DLL nebo vrací se ukazatel přidělené malloc a očekává volajícím uvolnit ji.)

Použití více CRTs v jediném procesu není v a sám sebe problematické (ve skutečnosti většina procesů skončí načítání knihoven DLL více CRT, například Windows součásti operačního systému bude záviset na msvcrt.dll a modul CLR bude záviset na vlastní privátní CRT). Když jumble stav z různých CRTs vzniknou problémy. Například by neměla přidělení paměti pomocí msvcr110.dll!malloc a pokus o navrátit tuto paměť msvcr120.dll!free a by se neměly pokoušet otevřete soubor pomocí msvcr110! fopen – a pokus o čtení od souboru pomocí msvcr120! fread –. Tak dlouho, dokud není jumble stav z různých CRTs, budete moci bezpečně více CRTs načten v jediném procesu.

Další informace najdete v tématu [Upgrade kódu na Universal CRT](upgrade-your-code-to-the-universal-crt.md).

## <a name="errors-due-to-project-settings"></a>Chyby vzniklé v důsledku nastavení projektu

Chcete-li zahájit proces upgradu, jednoduše otevřete starší projekt/řešení/pracovní prostor služby v nejnovější verzi sady Visual Studio. Visual Studio vytvoří nový projekt založený na staré nastavení projektu. Pokud starší projekt má knihovna nebo zahrnout cesty, které jsou pevně zakódovaný do nestandardních umístění, je možné, že soubory v těchto cestách se nezobrazí kompilátor při projekt používá výchozí nastavení. Další informace najdete v tématu [nastavení Linkeru OutputFile](porting-guide-spy-increment.md#linker_output_settings).

Obecně platí teď je vhodná doba k uspořádání kódu projektu správně pro zjednodušení údržby projektu a pomůžou upgradovaný kódu kompilaci co nejrychleji. Pokud už je dobře organizovaný zdrojový kód a starší projekt je zkompilován s Visual Studio 2010 nebo novější, můžete ručně upravit nový soubor projektu pro podporu kompilace na starý a nový kompilátor. Následující příklad ukazuje, jak kompilovat pro Visual Studio 2015 i Visual Studio 2017:

```xml
<PlatformToolset Condition="'$(VisualStudioVersion)'=='14.0'">v140</PlatformToolset>
<PlatformToolset Condition="'$(VisualStudioVersion)'=='15.0'">v141</PlatformToolset>
```

### <a name="lnk2019-unresolved-external"></a>LNK2019: Nevyřešené externí

Pro nevyřešené symboly může být nutné se opravit nastavení projektu.

- Pokud zdrojový soubor v jiné než výchozí umístění, nebyl je přidat cestu k projektu zahrnout adresáře?

- Pokud externí je definována v souboru LIB, mají zadané cesta ke knihovně ve vlastnostech projektu a správnou verzi .lib soubor skutečně existuje umístěné?

- Se snažíte propojit .lib soubor, který byl zkompilován s jinou verzí sady Visual Studio? Pokud ano, viz předchozí oddíl na závislosti knihoven a nástrojů.

- Typy argumentů v lokalitě volání skutečně neshodují s existující přetížení funkce? Ověřte, zda jsou tyto základní typy pro jakékoli definice TypeDef v signatuře funkce a v kódu, který volá funkci co očekáváte, že je jako.

Řešení potíží s chybami nevyřešeného symbolu, můžete zkusit použít dumpbin.exe prozkoumat symboly definované v binární soubor. Vyzkoušejte následující příkazový řádek pro zobrazení symbolů definovaných v knihovně:

```cmd
dumpbin.exe /LINKERMEMBER somelibrary.lib
```

### <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t (wchar_t je nativní typ)

(V Microsoft Visual C++ 6.0 a starší, **wchar_t** nebyl implementován jako předdefinovaný typ, ale byl deklarován v souboru wchar.h jako definice typu pro unsigned short.) C++ Standard vyžaduje, aby **wchar_t** předdefinovaným typem. Pomocí typedef verze může způsobit problémy s přenositelností. Pokud upgradujete ze starší verze sady Visual Studio a dojde k chybě kompilátoru C2664 protože kód se snaží implicitně převést **wchar_t** k **unsigned short**, doporučujeme vám, že změníte Kód opravit chybu, nikoli nastavením parametru `/Zc:wchar_t-`. Další informace najdete v tématu [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

### <a name="upgrading-with-the-linker-options-nodefaultlib-entry-and-noentry"></a>Upgrade pomocí možnosti linkeru: / NODEFAULTLIB/Entry a NOENTRY

`/NODEFAULTLIB` – Možnost linkeru (nebo vlastnost linkeru ignorovat všechny výchozí knihovny) dá linkeru pokyn, aby automaticky propojení v výchozích knihoven, jako je například CRT. To znamená, že každou knihovnu musí být uvedena jako vstup jednotlivě. Tento seznam knihoven je uveden v **Další závislosti** vlastnost **Linkeru** část **vlastnosti projektu** dialogového okna.

Projekty, které používají tuto možnost představovat problém při upgradu, protože názvy některých výchozích knihoven změnily. Protože každou knihovnu musí být uvedené v **Další závislosti** vlastnost nebo na příkazovém řádku linkeru, je potřeba aktualizovat seznam knihovny, které chcete použít aktuální názvy.

V následující tabulce jsou uvedeny knihoven, jejichž názvy změněn od verze Visual Studio 2015. Pokud chcete upgradovat, je třeba nahradit názvy v prvním sloupci s názvy ve druhém sloupci. Některé z těchto knihoven jsou knihovny importu, ale nemělo záležet, který.

|||
|-|-|
|Pokud jste používali:|Budete muset nahraďte ji:|
|libcmt.lib|libucrt.lib, libvcruntime.lib|
|libcmtd.lib|libucrtd.lib, libvcruntimed.lib|
|msvcrt.lib|ucrt.lib, vcruntime.lib|
|msvcrtd.lib|ucrtd.lib, vcruntimed.lib|

Stejný problém platí také v případě, že používáte `/ENTRY` možnost nebo `/NOENTRY` možnost, která mají také vliv na obcházení výchozích knihoven.

## <a name="errors-due-to-improved-language-conformance"></a>Chyby vzniklé v důsledku shoda lepší jazyka

Microsoft C++ kompilátoru se zvýšil průběžně jeho shody C++ standard v průběhu let. Kód, který zkompiluje v dřívějších verzích se nemusí podařit kompilovat v novějších verzích sady Visual Studio, protože kompilátor správně označí chybu, která dříve ignorovat nebo explicitně povolená.

Například `/Zc:forScope` přepínače byla zavedena v rané fázi historie MSVC. IT specialistovi nonkonformní chování proměnné smyčky. Tento přepínač je nyní zastaralá a v budoucích verzích může být odstraněna. Důrazně doporučujeme používat tento přepínač při upgradu vašeho kódu. Další informace najdete v tématu [zastaralé /Zc:forScope-](porting-guide-spy-increment.md#deprecated_forscope).

Jedním z příkladů běžné chyby kompilátoru, které se můžete setkat při upgradu je při nekonstantní argument je předán parametr const. Starší verze kompilátoru není vždy příznakem to za chybu. Další informace najdete v tématu [přísnější převody kompilátoru](porting-guide-spy-increment.md#stricter_conversions).

Další informace o konkrétní vylepšení naleznete v tématu [změn Visual C++ 2003 – 2015 historie](visual-cpp-change-history-2003-2015.md) a [vylepšení shody C++ v sadě Visual Studio](../overview/cpp-conformance-improvements.md).

## <a name="errors-involving-stdinth-integral-types"></a>Chyby zahrnující \<stdint.h > celočíselných typů

\<Stdint.h > záhlaví definuje – definice TypeDef a makra, která na rozdíl od integrovaných celočíselných typů, je zaručená mít zadané délky na všech platformách. Tady je několik příkladů `uint32_t` a `int64_t`. \<Stdint.h > bylo přidáno záhlaví v sadě Visual Studio 2010. Kód, který byl zapsán před 2010 může poskytnout privátní definice pro tyto typy a tyto definice nemusí být vždy konzistentní s \<stdint.h > definice.

Pokud je chyba C2371 a `stdint` typ je zahrnuta, pravděpodobně znamená, že typ je definován v záhlaví v kódu nebo soubor lib třetích stran. Při upgradu, by měl odstranit všechny vlastní definice \<stdint.h > typy, ale první porovnání vlastní definice a aktuální standardní definice zajistit nejsou Představujeme nové problémy.

Stisknutím klávesy **F12** (**přejít k definici**) zobrazíte, kde je definován typ nejistá.

[/Showincludes](../build/reference/showincludes-list-include-files.md) – možnost kompilátoru může být užitečné tady. V **stránky vlastností** dialogové okno pro váš projekt, otevřete **C/C++** > **Upřesnit** stránku a nastavit **zobrazit zahrnuje** do **Ano**. Potom znovu sestavit projekt a zobrazit seznam `#include`s ve výstupním okně. Každá hlavička je odsazený pod záhlaví, který ji obsahuje.

## <a name="errors-involving-crt-functions"></a>Chyby zahrnující funkce CRT

Mnoho změny byly provedeny na modul runtime jazyka C v průběhu let. Byly přidány bezpečné verze funkcí a některé byly odebrány. Také jak je popsáno výše v tomto článku, výlučně implementace Microsoftu CRT se teď vyčleněný v sadě Visual Studio 2015 do nové binární soubory a soubory .lib přidružené.

Pokud k chybě zahrnuje funkce CRT, Hledat [změn Visual C++ 2003 – 2015 historie](visual-cpp-change-history-2003-2015.md) nebo [vylepšení shody C++ v sadě Visual Studio](../overview/cpp-conformance-improvements.md) zobrazíte, pokud tato témata obsahují jakékoli další informace. Pokud je chyba LNK2019 nevyřešené externí, zkontrolujte, zda že funkce nebyla odebrána. Jinak, pokud jste si jistí, že stále existuje funkce a volající kód je správný, zkontrolujte, zda váš projekt používá `/NODEFAULTLIB`. V takovém případě musíte aktualizovat seznam knihoven tak, aby projekt využívá nový univerzální knihovny (UCRT). Další informace najdete v části výše na knihovny a závislosti.

Pokud chyba zahrnuje `printf` nebo `scanf`, ujistěte se, že jste nejsou definování soukromě buď funkce bez zahrnutí stdio.h. Pokud ano, buď odeberte privátní definice, nebo odkaz na starší verzi\_stdio\_definitions.lib. Tento parametr můžete nastavit **stránky vlastností** dialogového okna v části **vlastnosti konfigurace** > **Linkeru** > **vstup**v **Další závislosti** vlastnost. Pokud se propojení s Windows SDK 8.1 nebo starší, přidejte starší verze\_stdio\_definitions.lib.

Pokud chyba zahrnuje formátování argumentů řetězců, to je pravděpodobně vzhledem k tomu, že kompilátor je přísnější o vynucování standardní. Další informace najdete v historii změn. Prosím pozornosti tady nějaké chyby protože potenciálně může představovat bezpečnostní riziko.

## <a name="errors-due-to-changes-in-the-c-standard"></a>Chyby z důvodu změn ve standardu jazyka C++

Způsoby, které nejsou vždycky zpětně kompatibilní se vyvinula v samotném standardu C++. Úvod do jazyka C ++ 11 sémantiku přesunutí, nových klíčových slov a další jazyka a funkce standardní knihovny může potenciálně způsobit chyby kompilátoru a dokonce i jiný modul runtime chování.

Například původnímu programu C++ může obsahovat hlavičku iostream.h. Tato hlavička se přestala nabízet v rané fázi historie jazyka C++ a byla nakonec k úplnému odebrání ze sady Visual Studio. V takovém případě budete muset použít \<iostream – > a revize kódu. Další informace najdete v tématu [aktualizuje původní kód iostreams](porting-guide-spy-increment.md#updating_iostreams_code).

### <a name="c4838-narrowing-conversion-warning"></a>C4838: zužující převod upozornění

C++ standard nyní určuje, že převody z nepodepsaných na podepsané integrální hodnoty se považují za zužujících převodů. Kompilátor nevydala toto upozornění před Visual Studio 2015. Měli byste zkontrolovat všechny výskyty k Ujistěte se, že zužující nemá negativní vliv na správnost vašeho kódu.

## <a name="warnings-to-use-secure-crt-functions"></a>Upozornění na zabezpečené funkce CRT

Během let byly zavedeny bezpečné verze funkcí jazyka C runtime. Ačkoli staré, nezabezpečené verze jsou stále k dispozici, se doporučuje změnit kód Refaktorovat pro použití bezpečné verze. Kompilátor vygeneruje upozornění pro využití nebezpečných verzí. Můžete zakázat nebo ignorovat těchto upozornění. Chcete-li zakázat upozornění pro všechny projekty v řešení, otevřete **zobrazení** > **Správce vlastností**, vyberte všechny projekty, u kterých chcete toto upozornění zakážete a potom klikněte pravým tlačítkem na vybrané položky a zvolte **vlastnosti**. V **stránky vlastností** dialogového okna v části **vlastnosti konfigurace** > **C/C++** > **Upřesnit**, Vyberte **zakázat specifická upozornění**. Klikněte na šipku rozevíracího seznamu a potom klikněte na **upravit**. Do textového pole zadejte 4996. (Není obsahovat předponu "C".) Další informace najdete v tématu [přenosy použít zabezpečení CRT](porting-guide-spy-increment.md#porting_to_secure_crt).

## <a name="errors-due-to-changes-in-windows-apis-or-obsolete-sdks"></a>Chyby z důvodu změn v rozhraní Windows API nebo zastaralý sady SDK

V průběhu let rozhraní API pro Windows a datové typy byly přidány a někdy změnit nebo odebrat. Také dalších sad SDK, které nepatří do jádra operačního systému mají pocházet a pryč. Starší programy mohou obsahovat proto volání rozhraní API, která už neexistuje. Mohou také obsahovat volání rozhraní API v jiné společnosti Microsoft SDKs, která již nejsou podporovány. Pokud se zobrazí chyba týkající se rozhraní API Windows nebo rozhraní API z starší Microsoft SDK, je možné, že rozhraní API byla odebrána nebo nahrazena novějšími, bezpečnějšími funkce.

Další informace o aktuálním rozhraní API a minimální podporované operační systémy pro konkrétní rozhraní API Windows, naleznete v tématu [Microsoft API a referenční katalog](https://msdn.microsoft.com/library) a přejděte na dotyčném rozhraní API.

### <a name="windows-version"></a>Verze Windows

Při upgradu program, který používá rozhraní Windows API přímo nebo nepřímo, je potřeba rozhodnout, minimální verze Windows na podporu. Windows 7 ve většině případů je dobrou volbou. Další informace najdete v tématu [záhlaví souboru problémy](porting-guide-spy-increment.md#header_file_problems). `WINVER` Makra definuje nejstarší verzi Windows, který program je navržený pro spouštění. Pokud váš program knihovny MFC nastaví WINVER 0x0501 (Windows XP) se zobrazí upozornění protože MFC už nepodporuje XP, přestože kompilátor sám má režim XP.

Další informace najdete v tématu [aktualizuje cílovou verzi Windows](porting-guide-spy-increment.md#updating_winver) a [více zastaralé soubory hlaviček](porting-guide-spy-increment.md#outdated_header_files).

## <a name="atl--mfc"></a>ATL / MFC

ATL a MFC jsou poměrně stabilní rozhraní API, ale v některých změn. Najdete v článku [změn Visual C++ 2003 – 2015 historie](visual-cpp-change-history-2003-2015.md) Další informace a [co je nového v jazyce Visual c++ v sadě Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) a [vylepšení shody C++ v sadě Visual Studio](../overview/cpp-conformance-improvements.md).

### <a name="lnk-2005-dllmain12-already-defined-in-msvcrtdlib"></a>LNK 2005 _DllMain@12 již definována v MSVCRTD.lib

Této chybě může dojít v aplikacích MFC. Označuje chybu pořadí mezi knihovny CRT a knihovnu MFC. Knihovny MFC je potřeba nejprve propojené, takže poskytuje nové a odstranit operátory. Chcete-li chybu opravit, použijte `/NODEFAULTLIB` přepnout na hodnotu ignorovat tyto výchozí knihovny: A mfcs140d.lib MSVCRTD.lib. Pak přidejte tyto stejné knihovny jako další závislosti.

## <a name="32-vs-64-bit"></a>32 vs 64 bit

Pokud váš původním kód je zkompilován pro 32bitové systémy, máte možnost vytvořit 64bitovou verzi místo nebo kromě nového 32bitovou aplikaci. Obecně platí by měl získat první program v 32bitovém režimu kompilace a pokusíte se 64-bit. Kompilování pro 64bitovou verzi je jednoduchý, ale v některých případech může odhalit chyb, které byly skryté pomocí 32bitová verze sestavení.

Také byste měli vědět o možných problémech kompilace a modulu runtime týkající se velikost ukazatele, čas a hodnoty velikosti a specifikátory formátu v funkce printf a scanf. Další informace najdete v tématu [konfigurovat Visual C++ pro 64bitové, x64 cíle](../build/configuring-programs-for-64-bit-visual-cpp.md) a [problémy s migrací běžné Visual C++ 64-bit](../build/common-visual-cpp-64-bit-migration-issues.md). Tipy pro další migrace najdete v tématu [Průvodce programováním pro Windows 64-bit](/windows/desktop/WinProg64/programming-guide-for-64-bit-windows).

## <a name="unicode-vs-mbcsascii"></a>Kódování Unicode a MBCS/ASCII

Předtím, než byla standardizované Unicode, mnoho aplikací používá k reprezentování znaky, které nejsou zahrnuty ve znakové sadě ASCII vícebajtové znakové sady (MBCS). Ve starších projektech knihovny MFC znakové sady MBCS je výchozí nastavení a při upgradu takového programu, zobrazí se upozornění, které dokáží místo toho použít kódování Unicode. Můžete zakázat nebo upozornění ignorovat, pokud se rozhodnete, že převod do kódu Unicode není vhodné vývoj nákladů. Chcete-li zakázat pro všechny projekty v řešení, otevřete **zobrazení** > **Správce vlastností**, vyberte všechny projekty, u kterých chcete toto upozornění zakážete a potom klikněte pravým tlačítkem na vybrané položky a Zvolte **vlastnosti**. V **stránky vlastností** dialogového okna, vyberte **vlastnosti konfigurace** > **C/C++** > **Upřesnit**. V **zakázat specifická upozornění** vlastnost, otevřete na šipku rozevíracího seznamu a klikněte na tlačítko **upravit**. Do textového pole zadejte 4996. (Není obsahovat předponu "C".) Zvolte **OK** k uložení vlastnosti, klikněte na tlačítko **OK** uložte provedené změny.

Další informace najdete v tématu [Portování ze znakové sady MBCS do kódu Unicode](porting-guide-spy-increment.md#porting_to_unicode). Obecné informace o znakové sady MBCS vs. Kódování Unicode naleznete v tématu [Text a řetězce v jazyce Visual C++](../text/text-and-strings-in-visual-cpp.md) a [internacionalizace](../c-runtime-library/internationalization.md) .

## <a name="see-also"></a>Viz také:

[Upgrade projektů z dřívějších verzí Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Vylepšení shody C++ se sadou Visual Studio](../overview/cpp-conformance-improvements.md)