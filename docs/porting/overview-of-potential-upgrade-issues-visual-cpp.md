---
title: "Přehled upgradu potenciální problémy (Visual C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c99a8cb-098f-4a9d-bf2c-b80fd06ace43
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ccdd667898cf2043e10137fa301eb42ee3877fc8
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2018
---
# <a name="overview-of-potential-upgrade-issues-visual-c"></a>Přehled upgradu potenciální problémy (Visual C++)

V průběhu let Microsoft Visual C++ compiler podstoupila mnoho změn, společně s změny v samotné jazyk C++, standardní knihovna C++, C runtime (CRT) a další knihovny například MFC a ATL. V důsledku toho při upgradu aplikace ze starší verze sady Visual Studio můžete setkat kompilátoru a linkeru chyby a upozornění v kódu, který dříve zkompiluje ještě jednou. Starší původní kód základní, tím větší potenciální takové chyby. Tento přehled obsahuje souhrn nejčastějších třídy problémy se můžete setkat, a poskytuje odkazy na podrobnější informace.

Poznámka: V minulosti jste je doporučeno, upgrady, které jsou rozmístěny v několika verzích sady Visual Studio by měl být provádí postupně jednu verzi současně. Doporučujeme, abyste už tento přístup. Zjistili jsme, že je téměř vždy jednodušší upgradujte na nejnovější verzi sady Visual Studio, bez ohledu na to, kolik základu kódu.

Dotazy nebo připomínky týkající se procesu upgradu lze odeslat buď do vcupgrade@microsoft.com.

## <a name="library-and-toolset-dependencies"></a>Sada nástrojů pro knihovny a závislosti

Při upgradu aplikace na novou verzi sady Visual Studio, se důrazně doporučuje a v mnoha případech nutné také upgradovat všechny knihovny a knihovny DLL, které obsahuje odkazy na aplikace. To vyžaduje, abyste měli přístup ke zdrojovému kódu, nebo že dodavatele knihovny může poskytovat nové binární soubory kompilovat s stejnou hlavní verzi kompilátoru. Pokud platí jedna z těchto podmínek, můžete tuto část, která se zabývá podrobnosti o binární kompatibilitu přeskočit. Pokud žádná z těchto se tak, pak nebudete moci používat knihovny v aplikaci upgradovaný. Informace v této části vám pomůže pochopit, zda budete moci pokračovat v upgradu.

### <a name="toolset"></a>Sada nástrojů

Formáty souboru .obj a .lib jsou dobře definovaný a zřídka změnu. V některých případech jsou vytvářeny dodatky do těchto formátů souboru, ale tyto dodatky obecně neovlivní možnost modulové novější využívají objekt soubory a knihovny vyprodukované starší modulové. Zde jeden velký výjimkou je, pokud zkompilujete pomocí [/GL (optimalizace celého programu)](../build/reference/gl-whole-program-optimization.md). Pokud zkompilujete pomocí **/GL**, bude výsledný soubor objekt lze propojit jen pomocí stejné sady nástrojů, která byla použita k vytvoření ho. Takže pokud se vytvoří soubor objektu s **/GL** a pomocí kompilátoru Visual Studio 2017 (v141), je nutné ji propojit pomocí linkeru Visual Studio 2017 (v141). Je to proto, že interní datové struktury v rámci soubory objektů nejsou v hlavních verzích sady nástrojů stabilní a novější modulové není srozumitelný starší data formátů.

C++ nemá binární stabilní aplikační rozhraní (ABI). Visual Studio udržuje stabilní ABI C++ pro všechny podverze verze. Například Visual Studio 2017 a všechny její aktualizace jsou binární kompatibilní. Ale ABI není nutně kompatibilní mezi hlavní verze sady Visual Studio (s výjimkou 2015 a 2017, který _jsou_ binární kompatibilní). To znamená můžeme provést zásadní změny typu rozložení C++, dekorování názvů, výjimek a dalšími částmi C++ ABI. Proto pokud budete mít soubor objekt, který má externí symboly C++ propojení, tento objekt soubor nemusí propojení správně objekt soubory vytvořené na jiný hlavní verzi sady nástrojů. Všimněte si, že zde "nemusí fungovat" má mnoho možných výsledků: odkaz může selhat zcela (například změnu dekorování názvů), odkaz může být úspěšné, a věcí, nemusí fungovat v době běhu (například změnu typu rozložení), nebo pro práci v mnoha případech může dojít věcí a nic přejde wro NG. Také Upozorňujeme, že při C++ ABI není ustájení C ABI a C++ ABI do něj podmnožinu vyžadované pro COM jsou stabilní.

### <a name="libraries"></a>Knihovny

Pokud při kompilaci zdrojového souboru pomocí konkrétní verzi soubory hlaviček knihoven Visual Studio C++ (podle #including hlavičky), bude výsledný soubor objekt musí být propojena se stejnou verzí knihoven. Ano, například pokud je váš zdrojový soubor kompilovat s Visual Studio 2017 \<immintrin.h >, je nutné propojit s knihovnou vcruntime Visual Studio 2017. Podobně pokud je váš zdrojový soubor kompilovat s Visual Studio 2017 \<iostream >, je nutné propojit s knihovnou Visual Studio 2017 standardní C++ msvcprt. Kombinování a odpovídající není podporována.

Standardní knihovny C++, kombinování a odpovídající byla explicitně zakázal prostřednictvím použití `#pragma detect_mismatch` v hlavičkách standardní od sady Visual Studio 2010. Pokud se pokusíte propojit soubory nekompatibilní objektů nebo pokud se pokusíte propojit s knihovnou nesprávný standardní, propojení se nezdaří.

Pro CRT kombinování a odpovídající byl nikdy podporován, ale to často právě šlo, alespoň dokud Visual Studio 2015 a Universal CRT, protože plochy rozhraní API mnohem časem nezměnila. Universal CRT překročila zpětné kompatibility tak, aby v budoucnu jsme můžete zachování zpětné kompatibility. Jinými slovy máme žádný plán zavedení nových verzí na Universal CRT binárních souborů v budoucnu. Místo toho existující Universal CRT je nyní aktualizovat na místě.

Pokud chcete zadat částečné odkaz kompatibilitu s objekt soubory (a knihovny) kompilovat s starší verze Microsoft C Runtime hlavičky, poskytujeme knihovnu legacy_stdio_definitions.lib s Visual Studiem 2015 a novější. Tato knihovna nabízí kompatibility symboly pro většinu funkcí a data exportuje, které byly odebrány z Universal CRT. Sada symbolů kompatibility poskytované legacy_stdio_definitions.lib není dostatečná pro uspokojení většina závislosti, včetně všech závislostí v knihovny, které jsou součástí sady Windows SDK. Existují však některé znaky, které byly odebrány z Universal CRT, pro kterou není možné zajistit kompatibilitu symboly takto. Některé funkce zahrnují tyto symboly (například \_ \_iob\_func) a exportuje data (například \_ \_Import sady Management Pack\_\_\_iob, \_ \_Import sady Management Pack\_\_\_pctype –, \_ \_Import sady Management Pack\_\_\_mb\_Měna\_max).

Pokud máte statickou knihovnu, která byla vytvořena ve starší verzi hlaviček C Runtime, doporučujeme následující akce (v tomto pořadí):

1. Znovu sestavte se statickou knihovnou pomocí Visual Studio 2017 a Universal CRT hlavičky, které podporují propojování s Universal CRT. Toto je možnost plně podporované (a tedy doporučené).

1. Pokud jste nelze (nebo nechcete) znovu sestavit statickou knihovnu, můžete se pokusit propojení s starší\_stdio\_definitions.lib. Splňuje propojování závislostí statickou knihovnu, budete chtít důkladně otestovat se statickou knihovnou, protože se používá v binárním, abyste měli jistotu, že ji nebude nepříznivě podle těchto sloupců [chování změny, které byly provedeny Universal CRT](visual-cpp-change-history-2003-2015.md#BK_CRT).

1. Pokud nejsou splněny závislosti statické knihovny pomocí starší verze\_stdio\_definitions.lib nebo pokud knihovny nefunguje s Universal CRT z důvodu zmíněnými chování změn, bychom doporučili zapouzdřením vaší statické knihovny do knihovny DLL, která propojení se správnou verzí Microsoft C Runtime. Pokud se statickou knihovnou byl vytvořený pomocí sady Visual Studio 2013, by například chcete vytvořit tuto knihovnu DLL pomocí sady Visual Studio 2013 a na Visual Studio 2013 C++ knihovny. Podle budovy knihovny do knihovny DLL, zapouzdření podrobností implementace, která je závislá na konkrétní verzi Microsoft C Runtime. (Všimněte si, že budete chtít dávejte pozor na to, že rozhraní DLL není úniku podrobnosti, které C runtime použije, například vrácením souboru * přes hranice knihovny DLL nebo vrácení přidělené malloc – ukazatel a byla očekávána volajícího, aby ho volné.)

Použití více CRTs v jediném procesu není v a sám sebe problematické (skutečně, většina procesy dojdete k načítání knihoven DLL více CRT; například Windows, které jsou součástí operačního systému bude záviset na msvcrt.dll a modul CLR bude záviset na jeho vlastní privátní CRT). Když jumble stav z různých CRTs vzniknou problémy. Například by nemělo přidělit paměť pomocí msvcr110.dll!malloc a pokusí se zrušit přidělení paměti, že pomocí msvcr120.dll!free a byste neměli otevřete soubor pomocí msvcr110! fopen – a pokus o čtení z tohoto souboru pomocí msvcr120! fread –. Tak dlouho, dokud není jumble stav z různých CRTs, můžete mít bezpečně více CRTs načíst v jediném procesu.

Další informace najdete v tématu [upgradu kódu na Universal CRT](upgrade-your-code-to-the-universal-crt.md).

## <a name="errors-due-to-project-settings"></a>Chyby z důvodu nastavení projektu

Chcete-li zahájit proces upgradu, jednoduše starší projekt nebo řešení nebo pracovní prostor služby otevřete v nejnovější verzi sady Visual Studio. Visual Studio vytvoří nový projekt na základě původní nastavení projektu. Pokud starší projekt má knihovny nebo zahrnout cesty, které jsou pevně zakódovaná do nestandardních umístění, je možné, že soubory v těchto cestách nebude viditelný pro kompilátor projektu používá výchozí nastavení. Další informace najdete v tématu [nastavení výstupní soubor Linkeru](porting-guide-spy-increment.md#linker_output_settings).

Obecně platí teď je nejvhodnější doba pro uspořádání projektu kódu správně za účelem zjednodušení projektu údržby a pomůžou upgradovaný kódu kompilování co nejdříve. Pokud váš zdrojový kód je již dobře uspořádány a kompiluje starší projekt s Visual Studio 2010 nebo novější, můžete upravit ručně nový soubor projektu pro podporu kompilace na staré a nové kompilátoru. Následující příklad ukazuje, jak zkompilovat pro Visual Studio 2015 a Visual Studio 2017:

```xml
<PlatformToolset Condition="'$(VisualStudioVersion)'=='14.0'">v140</PlatformToolset>
<PlatformToolset Condition="'$(VisualStudioVersion)'=='15.0'">v141</PlatformToolset>
```

### <a name="lnk2019-unresolved-external"></a>LNK2019: Nerozpoznané externí

Nerozpoznané symbolů možná budete muset oprava nastavení projektu.

- Pokud zdrojový soubor je v jiné než výchozí umístění, se můžete přidat cestu do projektu zahrnout adresáře?

- Pokud externí je definována v souboru LIB, jste zadali cestu lib ve vlastnostech projektu a je správnou verzi souboru LIB skutečně existuje umístěné?

- Se pokoušíte vytvořit odkaz na soubor .lib, který byl kompilován s jinou verzí sady Visual Studio? Pokud ano, najdete v předchozí části na knihovny a sady nástrojů závislosti.

- Typy argumentů v lokalitě volání ve skutečnosti neodpovídají existující přetížení funkce? Ověřte, zda očekávat mají být základní typy pro všechny – definice TypeDef v podpis funkce a kód, který volá funkci.

Chcete-li vyřešit chyby nerozpoznané symbol, můžete zkusit pomocí dumpbin.exe prozkoumat symboly definované v binární. Zkuste následující příkazový řádek pro zobrazení symbolů definovaných v knihovně:

```cmd
dumpbin.exe /LINKERMEMBER somelibrary.lib
```

### <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t (wchar_t je nativní typ)

(V aplikaci Microsoft Visual C++ 6.0 a starší, `wchar_t` nebyla implementována jako předdefinovaný typ, ale byla deklarována v wchar.h jako definice typu pro prostě nepodepsané.) Standardní C++ vyžaduje, aby `wchar_t` být předdefinovaný typ. Pomocí verze typedef může způsobit problémy přenositelnost. Pokud jste upgrade z předchozích verzí sady Visual Studio a stane Chyba kompilátoru C2664, protože se pokouší kód implicitně převést `wchar_t` k `unsigned short`, doporučujeme vám, že změníte kód, který řešení chyby, místo nastavení **/ Zc:wchar_t-**. Další informace najdete v tématu [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

### <a name="upgrading-with-the-linker-options-nodefaultlib-entry-and-noentry"></a>Upgrade pomocí možnosti linkeru /NODEFAULTLIB/Entry a /NOENTRY

**/NODEFAULTLIB** – možnost linkeru (nebo vlastnost linkeru ignorovat všechny výchozí knihovny) informuje linkeru nechcete automaticky na odkaz v výchozí knihovny, například CRT. To znamená, že jednotlivých knihoven musí být uvedeny jednotlivě jako vstup. Tento seznam knihovny je uveden v **Další závislosti** vlastnost **Linkeru** části **vlastnosti projektu** dialogové okno.

Projekty, které používají tuto možnost k dispozici k potížím při upgradu, protože se změnily názvy některé výchozí knihovny. Protože každý knihovny musí být uvedené v **Další závislosti** vlastnost nebo na příkazovém řádku linkeru, budete muset aktualizovat seznam knihoven použít aktuální názvy.

V následující tabulce jsou uvedeny v knihovnách, jejichž názvy změnit od verze sady Visual Studio 2015. Pokud chcete upgradovat, je třeba nahradit názvy v první sloupec s názvy v druhém sloupci. Některé tyto knihovny jsou knihoven importovat, ale který by neměl vás.

|||
|-|-|
|Pokud používáte:|Budete muset nahraďte ho:|
|libcmt.lib|libucrt.lib, libvcruntime.lib|
|libcmtd.lib|libucrtd.lib, libvcruntimed.lib|
|msvcrt.lib|ucrt.lib, vcruntime.lib|
|msvcrtd.lib|ucrtd.lib, vcruntimed.lib|

Stejný problém platí také v případě, že používáte **/Entry** možnost nebo **/NOENTRY** možnost, která také mít za následek obcházení výchozí knihovny.

## <a name="errors-due-to-improved-language-conformance"></a>Chyby z důvodu shoda lepší jazyk

Microsoft Visual C++ compiler má průběžně vylepšuje její shoda pro standardní C++ průběhu let. Kód, který kompilovat v dřívějších verzích se nemusí podařit kompilovat v Visual Studio 2017, protože kompilátor správně flags chybu, která je dříve ignorovat nebo výslovně povolené.

Například **/Zc:forScope** přepínače byla zavedena v historii MSVC rané fázi. Umožňuje nonkonformní chování pro proměnné smyčky. Tento přepínač je nyní zastaralý a v budoucích verzích může být odstraněna. Důrazně doporučujeme nechcete použít tento přepínač při upgradu vašeho kódu. Další informace najdete v tématu [/Zc:forScope-je zastaralý](porting-guide-spy-increment.md#deprecated_forscope).

Jedním z příkladů běžné chyby kompilátoru, mohou být zobrazeny při upgradu je při bez const argument předaný parametr const. Starší verze kompilátoru není vždy příznak to za chybu. Další informace najdete v tématu [více striktní převody kompilátoru](porting-guide-spy-increment.md#stricter_conversions).

Další informace o vylepšeních konkrétní shoda, najdete v části [historie 2003 2015 změn Visual C++](visual-cpp-change-history-2003-2015.md) a [C++ shoda vylepšení v nástroji Visual Studio 2017](../cpp-conformance-improvements-2017.md).

## <a name="errors-involving-stdinth-integral-types"></a>Chyby zahrnující \<stdint.h > celočíselné typy

\<Stdint.h > záhlaví definuje – definice TypeDef a makra, která na rozdíl od vestavěné integrální typy zaručeně mají zadané délky na všech platformách. Mezi příklady patří `uint32_t` a `int64_t`. \<Stdint.h > záhlaví byl přidán v sadě Visual Studio 2010. Kód, který byla zapsána před 2010 může mít k dispozici privátní definice pro tyto typy a tyto definice nemusí být vždy konzistentní s \<stdint.h > definice.

Pokud je chyba C2371 a typu stdint je zahrnuta, pravděpodobně to znamená, že typ je definována v hlavičce buď v kódu nebo soubor lib třetích stran. Při upgradu, můžete je vyloučit všechny vlastní definice \<stdint.h > typy, ale první porovnat vlastní definice pro aktuální standardní definice zajistit nejsou Představujeme nové problémy.

Stisknutím klávesy F12 **přechod na definici** zobrazíte, kde je definován typ nejistá.

[/Showincludes vložených](../build/reference/showincludes-list-include-files.md) – možnost kompilátoru může být užitečná v tomto poli. V **stránky vlastností** dialogové okno pro svůj projekt, otevřete **C/C++** > **Upřesnit** stránky a nastavte **zobrazit zahrnuje** na **Ano**. Poté znovu sestavte projekt a zobrazit seznam #includes v okně výstupu. Každá hlavička odsadí pod záhlaví, který ji obsahuje.

## <a name="errors-involving-crt-functions"></a>Chyby zahrnující CRT – funkce

Mnoho změn byly provedeny do C runtime průběhu let. Byly přidány mnoho bezpečné verze funkcí a některé byly odebrány. Taky jak je popsáno výše v tomto článku, implementace společnosti Microsoft CRT byl rozdělili ve Visual Studiu 2015 do nové binární soubory a soubory .lib přidružené.

Pokud k chybě zahrnuje funkce CRT, hledání [historie 2003 2015 změn Visual C++](visual-cpp-change-history-2003-2015.md) nebo [C++ shoda vylepšení v nástroji Visual Studio 2017](../cpp-conformance-improvements-2017.md) chcete zobrazit, pokud tato témata obsahují jakýchkoli dalších informací. Pokud je chyba LNK2019, nerozpoznané externí, zkontrolujte, zda že funkce nebyl odstraněn. Jinak, pokud jste si jistí, že funkce stále existuje a je správný kód volání, zkontrolujte, zda projektu používá **/NODEFAULTLIB**. V takovém případě musíte aktualizovat seznam knihoven tak, aby projektu používá nový univerzální knihovny (UCRT). Na knihovny a závislosti pro další informace najdete v části výše.

Pokud chyba zahrnuje `printf` nebo `scanf`, ujistěte se, že jste nejsou definování soukromě buď funkce bez zahrnutí stdio.h. Pokud ano, buď odeberte privátní definice nebo odkaz na starší verze\_stdio\_definitions.lib. Můžete nastavit v **stránky vlastností** dialogové okno pod **vlastnosti konfigurace** > **Linkeru** > **vstup**v **Další závislosti** vlastnost. Pokud jste propojení se systémem Windows 8.1 SDK nebo starší, přidejte starší\_stdio\_definitions.lib.

Pokud chyba zahrnuje argumenty řetězce formátu, je to pravděpodobně proto kompilátor je přísnější o vynucování standardní. Zobrazit historii změn pro další informace. Prosím zaměřte na případné chyby zde protože potenciálně může představovat bezpečnostní riziko.

## <a name="errors-due-to-changes-in-the-c-standard"></a>Chyby z důvodu změn ve verzi C++ standard

Standardní C++ samotné má vyvinuly způsoby, které nejsou vždy zpětně kompatibilní. Zavedení v C ++ 11 sémantiku přesunutí, nová klíčová slova a další jazyka a funkce standardní knihovny může potenciálně způsobit chyby kompilátoru a dokonce i jiný modul runtime chování.

Například původní programu C++ mohou zahrnovat iostream.h záhlaví. Tuto hlavičku byla zrušena již v rané fázi v historii C++ a byla úplně odstraněny ze sady Visual Studio. V takovém případě budete muset použít \<iostream > a přepište kód. Další informace najdete v tématu [aktualizace starý kód iostreams](porting-guide-spy-increment.md#updating_iostreams_code).

### <a name="c4838-narrowing-conversion-warning"></a>C4838: zužující převod upozornění

Standardní C++ nyní určuje, že jsou považovány za převody z nepodepsaných podepsaný celočíselné hodnoty jako zužující převody. Kompilátor nevydala toto upozornění před Visual Studio 2015. Měli byste zkontrolovat každý výskyt zajistit narrowing nemá vliv na správnost vašeho kódu.

## <a name="warnings-to-use-secure-crt-functions"></a>Upozornění k použití zabezpečeného CRT – funkce

V průběhu let byly zavedeny bezpečné verze funkcí jazyka C runtime. I když původní, nezabezpečené verze jsou stále k dispozici, se doporučuje Změna kódu pro použití zabezpečeného verzí. Kompilátor vydá upozornění pro využití nezabezpečené verzí. Můžete zakázat nebo tato upozornění ignorovat. Chcete-li zakázat upozornění pro všechny projekty v řešení, otevřete **zobrazení** > **Správce vlastností**, vybrat všechny projekty, pro které chcete zakázat upozornění a potom klikněte pravým tlačítkem na vybrané položky a zvolte **vlastnosti**. V **stránky vlastností** dialogové okno pod **vlastnosti konfigurace** > **C/C++** > **Upřesnit**, Vyberte **zakázat konkrétní varování**. Klikněte na šipku rozevíracího seznamu a potom klikněte na **upravit**. Do textového pole zadejte 4996. (Není obsahovat předponu "C".) Další informace najdete v tématu [přenosy používat zabezpečení CRT](porting-guide-spy-increment.md#porting_to_secure_crt).

## <a name="errors-due-to-changes-in-windows-apis-or-obsolete-sdks"></a>Chyby z důvodu změn v rozhraní API systému Windows nebo zastaralé sady SDK

V průběhu let rozhraní API systému Windows a datové typy byly přidány a někdy změnit nebo odebrat. Také jiné sady SDK, které nepatřily do základní operační systém mít pocházet a zmizel. Starší programy proto může obsahovat volání rozhraní API, které už existují. Mohou také obsahovat volání rozhraní API v jiné společnosti Microsoft SDKs které již nejsou podporovány. Pokud uvidíte chybu zahrnující rozhraní API systému Windows nebo rozhraní API z starší Microsoft SDK, je možné, že rozhraní API byla odebrat nebo nahrazena novější, bezpečnější funkce.

Další informace o rozhraní API pro aktuální nastavení a minimální podporované operační systémy pro konkrétní rozhraní API systému Windows, najdete v části [Microsoft API a referenční informace katalogu](https://msdn.microsoft.com/library) a přejděte na dotyčném rozhraní API.

### <a name="windows-version"></a>Verze systému Windows

Při upgradu program, který používá rozhraní API systému Windows, buď přímo nebo nepřímo, musíte se rozhodnout, minimální verze Windows na podporu. Ve většině případů Windows 7 je dobrá volba. Další informace najdete v části [záhlaví souboru problémy](porting-guide-spy-increment.md#header_file_problems). Makro WINVER definuje nejstarší verze systému Windows, který váš program slouží ke spuštění. Pokud váš program MFC nastaví WINVER 0x0501 (Windows XP) zobrazí se upozornění protože MFC již nepodporuje XP, i když kompilátoru samotné má XP režim.  

Další informace najdete v tématu [aktualizace systému Windows verze cíle](porting-guide-spy-increment.md#updating_winver) a [více zastaralých soubory hlaviček](porting-guide-spy-increment.md#outdated_header_files).

## <a name="atl--mfc"></a>ATL / MFC

ATL a MFC jsou relativně stabilní rozhraní API, ale někdy změn. Najdete v článku [historie 2003 2015 změn Visual C++](visual-cpp-change-history-2003-2015.md) Další informace a [co je nového pro Visual C++ v aplikaci Visual Studio 2017](../what-s-new-for-visual-cpp-in-visual-studio.md) a [C++ shoda vylepšení v nástroji Visual Studio 2017](../cpp-conformance-improvements-2017.md).

### <a name="lnk-2005-dllmain12-already-defined-in-msvcrtdlib"></a>LNK 2005 _DllMain@12 již definována v MSVCRTD.lib

Této chybě může dojít v aplikacích MFC. Označuje, řazení problém mezi knihovna MFC a Knihovna CRT. MFC musí být propojená nejprve tak, aby poskytuje nové a odstranit operátory. Chcete-li opravit chyby, použijte přepínač /NODEFAULTLIB ignorovat tyto výchozí knihovny: MSVCRTD.lib a mfcs140d.lib. Pak přidejte tyto stejné knihovny jako další závislosti.

## <a name="32-vs-64-bit"></a>32 vs 64 bit

Pokud je původní kód zkompilován pro 32bitové systémy, máte možnost vytvořit 64bitovou verzi místo nebo kromě nového 32bitovou aplikaci. Obecně platí by měl získat váš program kompilace v režimu 32-bit první a pokusíte se 64-bit. Kompilování pro 64bitové prostředí je jednoduchá, ale v některých případech může odhalit chyby, které byly skryt. 32bitová verze sestavení.

Také byste měli znát možné problémy kompilaci a runtime týkající se velikost ukazatele, čas a hodnoty velikosti a specifikátory formátu v funkce printf a scanf. Další informace najdete v tématu [konfigurace Visual C++ pro 64bitové, x64 cíle](../build/configuring-programs-for-64-bit-visual-cpp.md) a [problémy s migrací běžné Visual C++ 64-bit](../build/common-visual-cpp-64-bit-migration-issues.md). Tipy pro další migraci najdete v tématu [Průvodce programováním pro 64bitový systém Windows](https://msdn.microsoft.com/library/windows/desktop/bb427430\(v=vs.85\).aspx).

## <a name="unicode-vs-mbcsascii"></a>Unicode vs MBCS/ASCII

Předtím, než byla standardizované znakové sady Unicode, mnoho programů vícebajtových znakovou sadu (MBCS) používá k reprezentování znaky, které nebyly zahrnuty ve znakové sadě ASCII. V starší projekty MFC MBCS bylo výchozí nastavení a při upgradu takového programu, zobrazí se upozornění, která poradit místo toho použít kódování Unicode. Můžete se rozhodnout zakázat nebo ignorovat upozornění, pokud se rozhodnete, že převod na kódování Unicode není vhodné vývoj náklady. Chcete-li zakázat pro všechny projekty v řešení, otevřete **zobrazení** > **Správce vlastností**, vybrat všechny projekty, pro které chcete zakázat upozornění a potom klikněte pravým tlačítkem na vybrané položky a Zvolte **vlastnosti**. V **stránky vlastností** dialogovém okně, vyberte **vlastnosti konfigurace** > **C/C++** > **Upřesnit**. V **zakázat konkrétní varování** vlastnost, otevřete na šipku rozevíracího seznamu a potom zvolte **upravit**. Do textového pole zadejte 4996. (Není obsahovat předponu "C".) Zvolte **OK** uložit vlastnost, zvolte **OK** uložte provedené změny.

Další informace najdete v tématu [Portování ze MBCS do kódu Unicode](porting-guide-spy-increment.md#porting_to_unicode). Obecné informace o rozhraní MBCS vs. Znakové sady Unicode, najdete v části [Text a řetězce v jazyce Visual C++](../text/text-and-strings-in-visual-cpp.md) a [internacionalizace](../c-runtime-library/internationalization.md) .

## <a name="see-also"></a>Viz také

[Upgrade projektů z dřívějších verzí Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
[Vylepšení shody C++ se sadou Visual Studio 2017](../cpp-conformance-improvements-2017.md)  
