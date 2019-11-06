---
title: Přehled potenciálních problémů s upgradem (Visual C++)
ms.date: 05/03/2019
ms.assetid: 2c99a8cb-098f-4a9d-bf2c-b80fd06ace43
ms.openlocfilehash: 2b310760b1a6623a18a00e36e3bd5378d2ebb76e
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627243"
---
# <a name="overview-of-potential-upgrade-issues-visual-c"></a>Přehled potenciálních problémů s upgradem (Visual C++)

V průběhu let se kompilátor společnosti C++ Microsoft prodělal mnoho změn, spolu se změnami samotného C++ jazyka, C++ standardní knihovny, modulu runtime jazyka C (CRT) a dalšími knihovnami, jako je například MFC a ATL. V důsledku toho může při upgradu aplikace ze starší verze sady Visual Studio dojít k chybám kompilátoru a linkeru v kódu, který byl dříve zkompilován čistě. Starší původní základ kódu, což je větší pravděpodobnost pro tyto chyby. Tento přehled shrnuje nejběžnější třídy problémů, ke kterým pravděpodobně dojde, a obsahuje odkazy na podrobnější informace.

> [!NOTE]
> V minulosti jsme doporučili, aby upgrady v různých verzích sady Visual Studio prováděly postupně jednu verzi. Tento přístup už nedoporučujeme. Zjistili jsme, že téměř vždy jednodušší je upgradovat na nejnovější verzi sady Visual Studio bez ohledu na to, jak stará verze kódu.

Dotazy nebo komentáře k procesu upgradu lze odeslat do vcupgrade@microsoft.com.

## <a name="library-and-toolset-dependencies"></a>Knihovny a sady nástrojů – závislosti

> [!NOTE]
> Tato část se týká aplikací a knihoven vytvořených pomocí Visual Studio 2013 a starších verzí. Sady nástrojů používané v sadě Visual Studio 2015, Visual Studio 2017 a Visual Studio 2019 jsou binární kompatibilní. Další informace naleznete v tématu [ C++ binární kompatibilita mezi Visual Studio 2015 a Visual Studio 2019](binary-compat-2015-2017.md).

Při upgradu aplikace na novou verzi sady Visual Studio je možné i v mnoha případech nutné k upgradu všech knihoven a knihoven DLL, na které aplikace odkazuje. Vyžaduje, abyste měli přístup ke zdrojovému kódu nebo aby dodavatel knihovny mohl poskytnout nové binární soubory zkompilované se stejnou hlavní verzí kompilátoru. Pokud je jedna z těchto podmínek pravdivá, můžete tuto část přeskočit, která se zabývá podrobnostmi o binární kompatibilitě. Pokud ani tento případ není, možná nebude možné používat knihovny v upgradované aplikaci. Informace v této části vám pomůžou pochopit, jestli můžete pokračovat v upgradu.

### <a name="toolset"></a>Sada nástrojů

Formáty souborů. obj a. lib jsou dobře definovány a zřídka se mění. V těchto formátech souborů se někdy přidávají i tyto doplňky obecně neovlivňují schopnost novějších sad nástrojů využívat soubory objektů a knihovny vytvořené staršími sadami nástrojů. Hlavní výjimka je zde, pokud kompilujete pomocí [/GL (celá optimalizace programu)](../build/reference/gl-whole-program-optimization.md). Pokud kompilujete pomocí `/GL`, výsledný soubor objektu lze propojit pouze pomocí stejné sady nástrojů, která byla použita k jeho vytvoření. Takže pokud vytvoříte soubor objektu s `/GL` a použijete kompilátor sady Visual Studio 2017 (v141), je nutné jej propojit pomocí linkeru Visual Studio 2017 (v141). Je to proto, že interní datové struktury v souborech objektů nejsou stabilní v hlavních verzích sady nástrojů a novější sady nástrojů nerozumí starším formátům dat.

C++nemá stabilní binární rozhraní aplikace (ABI). Ale Visual Studio udržuje stabilní C++ ABI pro všechny dílčí verze vydání. Visual Studio 2015 (v140), Visual Studio 2017 (v141) a Visual Studio 2019 (V142) se liší pouze v jejich dílčí verzi. Všechny mají stejné hlavní číslo verze, což je 14. Další informace naleznete v tématu [ C++ binární kompatibilita mezi Visual Studio 2015 a Visual Studio 2019](binary-compat-2015-2017.md).

Pokud máte soubor objektu, který má externí symboly s C++ propojením, tento soubor objektu nemusí správně propojit s soubory objektů vytvořenými jinou hlavní verzí sady nástrojů. Existuje mnoho možných výsledků: odkaz může být zcela neúspěšný (například při změně názvu dekorace). Odkaz může být úspěšný a akce nemusí fungovat za běhu (například při změně rozložení typu). V mnoha případech se může stát, že věci budou fungovat a nic se nestane nesprávným. Všimněte si také, že C++ ABI není stabilní, C ABI a podmnožina C++ ABI požadovaná pro model COM je stabilní.

Pokud propojíte knihovnu importu, všechny novější verze distribuovatelných knihoven sady Visual Studio, které zachovávají kompatibilitu ABI, lze použít za běhu. Například pokud je vaše aplikace kompilována a propojena pomocí sady nástrojů Visual Studio 2015 Update 3, můžete použít jakoukoli sadu Visual Studio 2017 nebo Visual Studio 2019 Redistributable, protože knihovny 2015, 2017 a 2019 zachovávají zpětnou binární kompatibilitu. Tato změna není pravdivá: nemůžete použít Distribuovatelný pro starší verzi sady nástrojů, než jste použili k sestavení kódu, a to i v případě, že mají kompatibilní ABI.

### <a name="libraries"></a>Knihovny

Pokud kompilujete zdrojový soubor pomocí konkrétní verze souborů hlaviček knihoven sady Visual Studio C++ (pomocí #including hlaviček), musí být výsledný soubor objektu propojen se stejnou verzí knihoven. Pokud je například zdrojový soubor kompilován pomocí > sady Visual Studio 2015 Update 3 \<immintrin. h, je nutné propojit s knihovnou vcruntime sady Visual Studio 2015 Update 3. Podobně platí, že pokud je zdrojový soubor kompilován pomocí sady Visual Studio 2017 verze 15,5 \<> iostream –, musíte propojit se sadou Visual Studio 2017 15,5 verze standard C++ , MSVCPRT. Kombinování a spárování není podporováno.

Pro C++ standardní knihovnu bylo kombinování a spárování explicitně zakázáno prostřednictvím použití `#pragma detect_mismatch` ve standardních hlavičkách od sady Visual Studio 2010. Pokud se pokusíte propojit nekompatibilní soubory objektů nebo pokud se pokusíte propojit s nesprávnou standardní knihovnou, odkaz nebude úspěšný.

Pro CRT, kombinování a spárování se nikdy nepodporovalo, ale často se jednalo o alespoň do sady Visual Studio 2015 a univerzálního CRT, protože se plocha rozhraní API v průběhu času nezměnila. Univerzální CRT podařilo přerušit zpětnou kompatibilitu, takže v budoucnu můžeme zajistit zpětnou kompatibilitu. Jinými slovy, nemáme v budoucnu žádné plány na zavedení nových, univerzálních binárních souborů CRT s verzí. Místo toho se teď existující Univerzální CRT místně aktualizuje.

Abychom zajistili částečnou kompatibilitu s objekty (knihovny) a soubory objektů (knihovny), které jsou kompilovány se staršími verzemi hlaviček modulu runtime jazyka C, poskytujeme knihovnu legacy_stdio_definitions. lib se sadou Visual Studio 2015 nebo novější. Tato knihovna poskytuje symboly kompatibility pro většinu funkcí a exportů dat odebraných z univerzálního CRT. Sada symbolů kompatibility poskytnutá legacy_stdio_definitions. lib je dostačující pro splnění většiny závislostí, včetně všech závislostí v knihovnách, které jsou součástí Windows SDK. Existují však některé symboly, které byly odebrány z Univerzální CRT, pro které není možné poskytnout symboly kompatibility. Mezi tyto symboly patří některé funkce (například \_\_IOB\_Func) a exporty dat (například \_\_IMP\_\_\_IOB, \_\_IMP\_\_@no__ t_12_ pctype, \_\_IMP\_\_\_MB\_je\_max).

Pokud máte statickou knihovnu, která byla sestavena se starší verzí hlaviček modulu runtime jazyka C, doporučujeme následující akce v tomto pořadí:

1. Znovu sestavte statickou knihovnu pomocí nové verze sady Visual Studio a hlavičkových hlaviček Universal CRT pro podporu propojení s univerzálním CRT. Tento přístup je plně podporovaná (a proto nejlepší) možnost.

1. Pokud nemůžete (nebo nechcete) znovu sestavit statickou knihovnu, můžete se pokusit propojit se staršími\_stdio\_definitions. lib. Pokud vyhovuje závislosti v době propojení vaší statické knihovny, budete chtít důkladně otestovat statickou knihovnu, protože se používá v binárním souboru, aby se zajistilo, že nebude mít nepříznivý vliv na jakékoli [změny chování provedené v univerzálním CRT](visual-cpp-change-history-2003-2015.md#BK_CRT) . .

1. Pokud se neshodují žádné závislosti statické knihovny\_stdio\_definitions. lib nebo pokud knihovna nepracuje s univerzálním CRT z důvodu výše uvedených změn chování, doporučujeme zapouzdření statické knihovny. do knihovny DLL, kterou propojíte se správnou verzí modulu runtime jazyka C. Pokud byla například Statická knihovna sestavena pomocí Visual Studio 2013, je vhodné vytvořit tuto knihovnu DLL pomocí Visual Studio 2013 a také knihoven Visual Studio 2013 C++ . Sestavením knihovny do knihovny DLL zapouzdřete podrobnosti implementace, které jsou jeho závislostí na konkrétní verzi modulu runtime jazyka C. Budete chtít mít pozor, aby rozhraní knihovny DLL neuniklo podrobnosti o tom, který modul runtime jazyka C používá, například vrácením souboru * napříč hranicí knihovny DLL nebo vrácením ukazatele s přiděleným objektem, který očekává, že volající uvolňuje.

Použití vícenásobných CRTs v jednom procesu není v a samotném případě problematické (ve skutečnosti ale většina procesů ukončí načítání více knihoven DLL CRT, například komponenty operačního systému Windows budou záviset na knihovně Msvcrt. dll a CLR bude záviset na vlastní privátní CRT. Problémy vznikají při Jumble stavu z různých CRTs. Například byste neměli přidělovat paměť pomocí msvcr110. dll! a pokusit se uvolnit paměť pomocí msvcr120. dll! Free a neměli byste se pokoušet o otevření souboru pomocí msvcr110! fopen a pokus o čtení z tohoto souboru pomocí msvcr120! fread. Pokud nejumblete stav z různých CRTs, můžete v jednom procesu bezpečně načítat víc CRTs.

Další informace najdete v tématu [Upgrade kódu na univerzální CRT](upgrade-your-code-to-the-universal-crt.md).

## <a name="errors-due-to-project-settings"></a>Chyby z důvodu nastavení projektu

Chcete-li zahájit proces upgradu, otevřete starší projekt/řešení/pracovní prostor v nejnovější verzi sady Visual Studio. Visual Studio vytvoří nový projekt na základě starého nastavení projektu. Pokud má starší projekt knihovnu nebo obsahují cesty, které jsou pevně kódované na nestandardní umístění, je možné, že soubory v těchto cestách nebudou viditelné pro kompilátor, pokud projekt používá výchozí nastavení. Další informace najdete v tématu [Nastavení programu linker Výstupní_soubor](porting-guide-spy-increment.md#linker_output_settings).

Obecně je teď vhodná doba k tomu, abyste kód projektu správně uspořádali, aby se zjednodušila údržba projektu a co nejrychleji bylo snazší kompilovat upgradovaný kód. Pokud je váš zdrojový kód již dobře uspořádán a váš starší projekt je zkompilován pomocí sady Visual Studio 2010 nebo novější, můžete ručně upravit soubor projektu pro podporu kompilace na starém i novém kompilátoru. Následující příklad ukazuje, jak zkompilovat jak pro Visual Studio 2015, tak pro Visual Studio 2017:

```xml
<PlatformToolset Condition="'$(VisualStudioVersion)'=='14.0'">v140</PlatformToolset>
<PlatformToolset Condition="'$(VisualStudioVersion)'=='15.0'">v141</PlatformToolset>
```

### <a name="lnk2019-unresolved-external"></a>LINKERŮ LNK2019: nevyřešené externí

Pro nerozpoznané symboly může být nutné opravit nastavení projektu.

- Pokud je zdrojový soubor ve výchozím umístění, přidejte cestu k adresářům include projektu?

- Pokud je externí definován v souboru. lib, zadali jste cestu lib ve vlastnostech projektu a je to správná verze souboru. lib, který tam najdete?

- Pokoušíte se připojit k souboru. lib, který byl zkompilován s jinou verzí sady Visual Studio? Pokud ano, přečtěte si předchozí část týkající se závislostí knihovny a sady nástrojů.

- Jsou typy argumentů na webu volání ve skutečnosti shodné s existujícím přetížením funkce? Ověřte základní typy pro všechny definice typedef v signatuře funkce a v kódu, který volá funkci, je to, co očekáváte.

K řešení chyb nevyřešených symbolů můžete zkusit použít nástroj DUMPBIN. exe k prohlédnutí symbolů definovaných v binárním souboru. Zkuste zobrazit symboly definované v knihovně pomocí následujícího příkazového řádku:

```cmd
dumpbin.exe /LINKERMEMBER somelibrary.lib
```

### <a name="zcwchar_t-wchar_t-is-native-type"></a>/Zc:wchar_t (wchar_t je nativní typ)

(V jazyce Microsoft C++ Visual 6,0 a starším, **wchar_t** nebylo implementováno jako vestavěný typ, ale byla deklarována v WCHAR. h jako typedef pro znaménko short.) C++ Standard vyžaduje, aby **wchar_t** byl vestavěný typ. Použití verze typedef může způsobit problémy s přenositelností. Pokud upgradujete z dřívějších verzí sady Visual Studio a dojde k chybě kompilátoru upozornění C2664, protože kód se snaží implicitně převést **wchar_t** na **unsigned short**, doporučujeme, abyste změnili kód, abyste chybu opravili, místo nastavení @no__t _2_ . Další informace naleznete v tématu [/Zc: wchar_t (Wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

### <a name="upgrading-with-the-linker-options-nodefaultlib-entry-and-noentry"></a>Upgrade pomocí možností linkeru/NODEFAULTLIB,/ENTRY a/NOENTRY

Možnost linkeru `/NODEFAULTLIB` (nebo ignorovat všechny výchozí knihovny vlastnosti linkeru) říká linkeru, aby se automaticky neodkazoval na výchozí knihovny, jako je CRT. To znamená, že každá knihovna musí být uvedena jako vstup samostatně. Tento seznam knihoven je uveden ve vlastnosti **Další závislosti** v části **linker** dialogového okna **vlastností projektu** .

Projekty, které používají tuto možnost, představují problém při upgradu, protože obsah některých výchozích knihoven byl refaktorované. Vzhledem k tomu, že každá knihovna musí být uvedena ve vlastnosti **Další závislosti** nebo na příkazovém řádku linkeru, je třeba aktualizovat seznam knihoven tak, aby používaly všechny aktuální názvy.

V následující tabulce jsou uvedeny knihovny, jejichž obsah se změnil od aplikace Visual Studio 2015. Chcete-li upgradovat, je nutné přidat nové názvy knihoven do druhého sloupce do knihoven v prvním sloupci. Některé z těchto knihoven jsou importovat knihovny, ale nezáleží na tom.

|||
|-|-|
|Pokud jste používali:|Je potřeba použít tyto knihovny:|
|Libcmt. lib|Libcmt. lib, libucrt. lib, libvcruntime. lib|
|LIBCMTD. lib|LIBCMTD. lib, libucrtd. lib, libvcruntimed. lib|
|Msvcrt. lib|Msvcrt. lib, UCRT. lib, vcruntime. lib|
|msvcrtd. lib|msvcrtd. lib, ucrtd. lib, vcruntimed. lib|

Stejný problém platí také v případě, že použijete možnost `/ENTRY` nebo možnost `/NOENTRY`, která má také účinek na obcházení výchozích knihoven.

## <a name="errors-due-to-improved-language-conformance"></a>Chyby z důvodu vylepšené shody jazyků

Kompilátor společnosti C++ Microsoft průběžně vylepšuje svůj soulad se C++ standardem v průběhu let. Kód, který se zkompiluje v dřívějších verzích, se nemusí podařit zkompilovat v novějších verzích sady Visual Studio, protože kompilátor správně označí chybu, kterou dřív ignoroval nebo explicitně povolil.

Například přepínač `/Zc:forScope` byl zaveden brzy v historii MSVC. Povoluje nevyhovující chování pro proměnné smyčky. Tento přepínač je teď zastaralý a v budoucích verzích ho může odebrat. Při upgradu kódu se důrazně doporučuje tento přepínač Nepoužívat. Další informace najdete v tématu [/Zc: forScope-je zastaralé](porting-guide-spy-increment.md#deprecated_forscope).

Jedním z příkladů běžné chyby kompilátoru, která se může zobrazit při upgradu, je předána nekonstantní argument do parametru const. Starší verze kompilátoru neohlásily, že by byly vždy označeny jako chyby. Další informace naleznete v tématu [striktní převody kompilátoru](porting-guide-spy-increment.md#stricter_conversions).

Další informace o konkrétních vylepšeních shody naleznete v tématu [vizuální C++ Změna historie 2003 – 2015](visual-cpp-change-history-2003-2015.md) a [ C++ vylepšení shody v aplikaci Visual Studio](../overview/cpp-conformance-improvements.md).

## <a name="errors-involving-stdinth-integral-types"></a>Chyby týkající se \<stdin. h > integrálních typů

Hlavička \<stdin. h > definuje definice typedef a makra, která na rozdíl od vestavěných integrálních typů jsou zaručena, že mají zadanou délku na všech platformách. Některé příklady jsou `uint32_t` a `int64_t`. V aplikaci Visual Studio 2010 bylo přidáno záhlaví > \<stdin. h. Kód, který byl napsán před 2010, mohl poskytnout privátní definice pro tyto typy a tyto definice nemusí být vždy konzistentní s > definice \<stdin. h.

Pokud je chyba C2371 a je zapojen typ `stdint`, pravděpodobně to znamená, že typ je definován v záhlaví buď v kódu, nebo v souboru LIB třetí strany. Při upgradu byste měli odstranit všechny vlastní definice \<typu stdin. h >, ale nejprve Porovnejte vlastní definice s aktuálními standardními definicemi, abyste se ujistili, že nezavádíte nové problémy.

Stisknutím klávesy **F12** (**Přejít k definici**) můžete zobrazit, kde je daný typ definován.

Možnost kompilátoru [/showIncludes](../build/reference/showincludes-list-include-files.md) může být užitečná tady. V dialogovém okně **stránky vlastností** projektu otevřete **C++ stránku > ** **Upřesnit** a nastavte **Zobrazit zahrnutí** na **Ano**. Pak projekt znovu sestavte a zobrazte seznam `#include`s v okně výstup. Každé záhlaví je odsazené pod hlavičkou, která ho obsahuje.

## <a name="errors-involving-crt-functions"></a>Chyby zahrnující funkce CRT

V modulu runtime jazyka C bylo během let provedeno mnoho změn. Bylo přidáno mnoho zabezpečených verzí funkcí a některé z nich byly odebrány. Jak je popsáno výše v tomto článku, byla implementace CRT od společnosti Microsoft refaktored v rámci sady Visual Studio 2015 do nových binárních souborů a přidružených souborů lib.

Pokud chyba zahrnuje funkci CRT, prohledejte [ C++ v aplikaci Visual Studio](../overview/cpp-conformance-improvements.md) [historii vizuálních C++ změn 2003-2015](visual-cpp-change-history-2003-2015.md) nebo vylepšení shody, abyste viděli, jestli tyto články obsahují nějaké další informace. Pokud je chyba LINKERŮ LNK2019, nevyřešené externí, ujistěte se, že funkce nebyla odebrána. V opačném případě, pokud jste si jisti, že funkce stále existuje a že je volající kód správný, zkontrolujte, zda projekt používá `/NODEFAULTLIB`. Pokud ano, budete muset aktualizovat seznam knihoven tak, aby projekt používal nové univerzální knihovny (UCRT). Další informace najdete v části o knihovně a závislostech výše.

Pokud chyba zahrnuje `printf` nebo `scanf`, ujistěte se, že nebudete soukromě definovat žádnou funkci bez zahrnutí stdio. h. Pokud ano, odeberte buď privátní definice, nebo odkaz na starší\_stdio\_definitions. lib. Tuto knihovnu můžete nastavit v dialogovém okně **stránky vlastností** v části **Vlastnosti konfigurace** > **vstupu** > **linkeru** ve vlastnosti **Další závislosti** . Pokud propojujete s Windows SDK 8,1 nebo starším, přidejte starší verze\_stdio\_definitions. lib.

Pokud chyba zahrnuje argumenty formátovacích řetězců, je pravděpodobné, že kompilátor je striktní o vynucování Standard. Další informace najdete v tématu o historii změn. Věnujte pozornost případným chybám, protože mohou potenciálně představovat bezpečnostní riziko.

## <a name="errors-due-to-changes-in-the-c-standard"></a>Chyby z důvodu změn ve C++ standardu

Samotná C++ úroveň Standard se vyvinula způsobem, který není vždy zpětně kompatibilní. Úvod do C++ 11 sémantiky přesunutí, nová klíčová slova a další funkce jazyka a standardní knihovny mohou potenciálně způsobit chyby kompilátoru a dokonce i jiné běhové chování.

Starý C++ program může například obsahovat hlavičku iostream –. h. Tato hlavička byla brzy zastaralá v historii C++ a byla nakonec zcela odstraněna ze sady Visual Studio. V takovém případě budete muset použít \<iostream – > a přepsat kód. Další informace najdete v tématu [aktualizace starého kódu iostreams](porting-guide-spy-increment.md#updating_iostreams_code).

### <a name="c4838-narrowing-conversion-warning"></a>C4838: upozornění na zúžení převodu

C++ Standard nyní určuje, že převod z nepodepsaných na celočíselné hodnoty se považuje za zužující převody. Kompilátor vyvolal toto upozornění před verzí sady Visual Studio 2015. Zkontrolujte jednotlivé výskyty, abyste se ujistili, že zúžení nemá vliv na správnost kódu.

## <a name="warnings-to-use-secure-crt-functions"></a>Upozornění na použití zabezpečených funkcí CRT

V průběhu let byly zavedeny zabezpečené verze běhových funkcí jazyka C. I když jsou staré, nezabezpečené verze stále k dispozici, doporučuje se změnit kód na použití zabezpečených verzí. Kompilátor vydá upozornění na použití nezabezpečených verzí. Tato upozornění můžete zakázat nebo ignorovat. Chcete-li zakázat upozornění pro všechny projekty v řešení, otevřete **zobrazení** > **Správce vlastností**, vyberte všechny projekty, pro které chcete zakázat upozornění, pak klikněte pravým tlačítkem na vybrané položky a zvolte možnost **vlastnosti**. V dialogovém **okně stránky vlastností** v části **Vlastnosti konfigurace** > **CC++ /**  > **Upřesnit**vyberte možnost **Zakázat specifická upozornění**. Klikněte na šipku rozevíracího seznamu a potom klikněte na **Upravit**. Do textového pole zadejte 4996. (Nezahrnovat předponu ' C '.) Další informace najdete v tématu [přenos pro použití zabezpečeného CRT](porting-guide-spy-increment.md#porting_to_secure_crt).

## <a name="errors-due-to-changes-in-windows-apis-or-obsolete-sdks"></a>Chyby z důvodu změn v rozhraních API systému Windows nebo zastaralých sadách SDK

V průběhu let se přidaly rozhraní API a datové typy Windows a někdy se změnily nebo odebraly. K dispozici jsou také další sady SDK, které nepatří do základního operačního systému. Starší programy mohou proto obsahovat volání rozhraní API, která již neexistují. Mohou také obsahovat volání rozhraní API v jiných sadách Microsoft SDK, které již nejsou podporovány. Pokud se zobrazí chyba týkající se rozhraní API systému Windows nebo rozhraní API ze starší sady Microsoft SDK, je možné, že rozhraní API bylo odebráno nebo nahrazeno novější a bezpečnější funkcí.

Další informace o aktuální sadě rozhraní API a minimálních podporovaných operačních systémech pro konkrétní rozhraní API systému Windows najdete v tématu rozhraní API pro [Microsoft a referenční katalog](https://msdn.microsoft.com/library) a přechod na příslušné rozhraní API.

### <a name="windows-version"></a>Verze Windows

Při upgradu programu, který používá rozhraní Windows API buď přímo, nebo nepřímo, se musíte rozhodnout, jaká je minimální verze Windows, která se má podporovat. Ve většině případů je Windows 7 dobrou volbou. Další informace najdete v tématu [problémy se soubory hlaviček](porting-guide-spy-increment.md#header_file_problems). `WINVER` makro definuje nejstarší verzi Windows, na které je program určený ke spuštění. Pokud váš program knihovny MFC nastaví program WINVER na 0x0501 (Windows XP), zobrazí se upozornění, protože knihovna MFC již nepodporuje systém XP, i když má samotný kompilátor režim XP.

Další informace najdete v tématu [aktualizace cílové verze Windows](porting-guide-spy-increment.md#updating_winver) a [zastaralých hlavičkových souborů](porting-guide-spy-increment.md#outdated_header_files).

## <a name="atl--mfc"></a>ATL/MFC

ATL a MFC jsou poměrně stabilní rozhraní API, ale změny se provádějí občas. Další informace najdete v tématu [o C++ historii vizuálních změn 2003 – 2015](visual-cpp-change-history-2003-2015.md), [co je nového C++ pro vizuál v aplikaci Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)a [ C++ vylepšení shody v aplikaci Visual Studio](../overview/cpp-conformance-improvements.md).

### <a name="lnk-2005-_dllmain12-already-defined-in-msvcrtdlib"></a>LNK 2005 _DllMain@12 již definován v MSVCRTD. lib

K této chybě může dojít v aplikacích knihovny MFC. Označuje problém objednávání mezi knihovnou CRT a knihovnou MFC. Knihovna MFC musí být nejprve propojena, aby poskytovala nové a odstranit operátory. Chcete-li chybu opravit, použijte přepínač `/NODEFAULTLIB` pro ignorování těchto výchozích knihoven: MSVCRTD. lib a mfcs140d. lib. Pak přidejte stejné knihovny jako další závislosti.

## <a name="32-vs-64-bit"></a>32 vs 64 bitů

Pokud je váš původní kód kompilován pro 32 systémy, máte možnost vytvořit si 64 verzi namísto nástroje nebo kromě nové aplikace 32. Obecně byste měli nejprve získat program, který bude kompilován v 32ovém režimu, a potom se pokusit o 64 bitovou kopii. Kompilace pro 64-bit je jednoduchá, ale v některých případech může odhalit chyby, které byly skryty pomocí 32 sestavení.

Také byste si měli být vědomi možných potíží při kompilaci a při spuštění, které se týkají velikosti ukazatelů, času a velikosti, a specifikátory formátu ve funkcích printf a scanf. Další informace najdete v tématu [Konfigurace vizuálu C++ pro 64, cíle x64](../build/configuring-programs-for-64-bit-visual-cpp.md) a [běžné problémy s migrací C++ pro Visual 64](../build/common-visual-cpp-64-bit-migration-issues.md). Další tipy k migraci najdete v tématu [Průvodce programováním pro 64-bit Windows](/windows/win32/WinProg64/programming-guide-for-64-bit-windows).

## <a name="unicode-vs-mbcsascii"></a>Unicode vs – MBCS/ASCII

Předtím, než byl kód Unicode standardizován, mnoho programů použil vícebajtovou znakovou sadu (MBCS) k reprezentaci znaků, které nebyly obsaženy v sadě znaků ASCII. Ve starších projektech knihovny MFC bylo výchozím nastavením znakové sady MBCS a při upgradu takového programu se zobrazí upozornění upozorňující na místo toho použití Unicode. Pokud se rozhodnete, že převod do kódování Unicode nestojí za náklady na vývoj, můžete toto upozornění zakázat nebo ignorovat. Pokud ho chcete zakázat pro všechny projekty v řešení, otevřete **zobrazení** > **Správce vlastností**, vyberte všechny projekty, pro které chcete upozornění zakázat, a pak klikněte pravým tlačítkem na vybrané položky a zvolte **vlastnosti**. V dialogovém okně **stránky vlastností** vyberte možnost **Vlastnosti konfigurace** > **C/C++**  > **Upřesnit**. Ve vlastnosti **Zakázat specifická upozornění** otevřete rozevírací šipku a zvolte možnost **Upravit**. Do textového pole zadejte 4996. (Nezahrnovat předponu ' C '.) Kliknutím na **tlačítko OK** vlastnost uložte a pak kliknutím na **tlačítko OK** uložte změny.

Další informace najdete v tématu [přenos ze znakové sady MBCS do kódování Unicode](porting-guide-spy-increment.md#porting_to_unicode). Obecné informace o znakové sadě MBCS vs. Unicode naleznete [v tématu text a řetězce C++ v jazyce vizuálů](../text/text-and-strings-in-visual-cpp.md) a [mezinárodní](../c-runtime-library/internationalization.md) .

## <a name="see-also"></a>Viz také:

[Upgrade projektů z dřívějších verzí sady VisualC++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Vylepšení shody C++ se sadou Visual Studio](../overview/cpp-conformance-improvements.md)