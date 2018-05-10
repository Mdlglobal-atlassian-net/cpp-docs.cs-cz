---
title: Upozornění kompilátoru kompilátoru verzí | Microsoft Docs
ms.custom: ''
ms.date: 01/31/2018
ms.technology:
- devlang-cpp
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- warnings, by compiler version
- cl.exe compiler, setting warning options
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 789121e3adb42cb74087339bb33bb82cb7604a10
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warnings-by-compiler-version"></a>Upozornění kompilátoru verzí kompilátoru

Kompilátor můžete potlačit upozornění, které byly zavedeny po na verzi, můžete zadat pomocí [/Wv](../../build/reference/compiler-option-warning-level.md) – možnost kompilátoru. To je užitečné pro správu vašeho procesu sestavení při zavádění nové verze sady nástrojů a chcete dočasně potlačení nové upozornění. Tato možnost není potlačit nové chybové zprávy. Nedoporučujeme potlačení všechny nové upozornění trvale! Doporučujeme vždy zkompilujete na nejvyšší úrovni regulární upozornění, __/W4__a odeberte __/Wv__ možnost v buildu co nejdříve. 

Tyto verze kompilátoru zavedl nový upozornění:

| Produkt | Číslo verze kompilátoru |
|-|-|
| Visual C++ 2002 | 13.00.9466 |
| Visual C++ 2003 | 13.10.3077 |
| Visual C++ 2005 | 14.00.50727.762 |
| Visual C++ 2008 | 15.00.21022.08 |
| Visual C++ 2010 | 16.00.40219.01 |
| Visual C++ 2012 | 17.00.51106.1 |
| Visual C++ 2013 | 18.00.21005.1 |
| Visual C++ 2015 RTM | 19.00.23026.0 |
| Visual C++ 2015 Update 1 | 19.00.23506.0 |
| Visual C++ 2015 Update 2 | 19.00.23918.0 |
| Visual C++ 2015 Update 3 | 19.00.24215.1 |
| Visual C++ 2017 RTM | 19.10.24903.0 |
| Visual C++ 2017 verze 15.1 | 19.10.25017.0 |
| Visual C++ 2017 verze 15.3 | 19.11.25506.0 |
| Visual C++ 2017 verze 15,5 | 19.12.25827.0 |

Můžete zadat pouze hlavní číslo, hlavní a podverze čísla nebo hlavní, vedlejší verzi a sestavení čísla, která __/Wv__ možnost. Sestavy všech upozornění, které se shodují verzí, které začínají zadané číslo a potlačí všechny výstrahy pro větší než zadané číslo verze. Například __/Wv:17__ sestavy všech upozornění zavedená v nebo před všechny verze sady Visual Studio 2012 a potlačí všechny upozornění zaváděné žádné kompilátoru ze sady Visual Studio 2013 (verze 18) nebo novější. Potlačit upozornění byla zavedená v sadě Visual Studio 2015 update 2 a novější, můžete použít __/Wv:19.00.23506__. Použití __/Wv:19.11__ k hlášení všech upozornění byla zavedená v libovolné verzi sady Visual Studio před Visual Studio 2017 verze 15,5, ale potlačí upozornění byla zavedená v aplikaci Visual Studio 2017 verze 15,5 a novější.

Následující části uvádějí upozornění zaváděné každou verzi Visual C++, který můžete potlačit tím, že pomocí __/Wv__ – možnost kompilátoru. __/Wv__ možnost nelze potlačení upozornění, které nejsou uvedené, které platila před zadaná verze kompilátoru.

## <a name="warnings-introduced-in-visual-c-2017-version-155-compiler-version-1912258270"></a>Upozornění byla zavedená v 2017 Visual C++ verze 15,5 (verze 19.12.25827.0 kompilátoru)

Tato upozornění a všech upozornění v novějších verzích, které jsou potlačovány pomocí možnosti kompilátoru __/Wv:19.11__.

|||
|-|-|
C5044|Argument pro možnost příkazového řádku *možnost* odkazuje na cestu, '*cesta*, který neexistuje

## <a name="warnings-introduced-in-visual-c-2017-version-153-compiler-version-1911255060"></a>Upozornění byla zavedená v 2017 Visual C++ verze 15.3 (verze 19.11.25506.0 kompilátoru)

Tato upozornění a všech upozornění v novějších verzích, které jsou potlačovány pomocí možnosti kompilátoru __/Wv:19.10__.

|||
|-|-|
C4843|'*type1*': Obslužná rutina výjimky z odkazu na typ pole nebo funkce nedostupný, použijte '*type2*' místo toho
C4844|"export modulu *module_name*;' je nyní upřednostňované syntaxe deklarace rozhraní modulu
C5039|'*funkce*': ukazatel nebo odkaz na potenciálně vyvolání funkce předaný funkci extern C v části - EHc. Nedefinované chování může dojít, pokud je tato funkce vyvolá výjimku.
C5040|specifikace výjimek dynamické jsou platné pouze v C ++ 14 a starší; práce jako s noexcept(false)
C5041|'*definice*':--line definice pro constexpr statických dat člena není potřebné a je zastaralý součástí C ++ 17
C5042|'*deklarace*': deklarace funkcí v oboru bloku nemůže být zadaný, vložené' ve standardní C++; odeberte specifikátor 'vložené.
C5043|'*specifikace*': specifikace výjimek neodpovídá předchozí deklarace

## <a name="warnings-introduced-in-visual-c-2017-version-151-compiler-version-1910250170"></a>Upozornění byla zavedená v 2017 Visual C++ verze 15.1 (verze 19.10.25017.0 kompilátoru)

Tato upozornění a všech upozornění v novějších verzích, které jsou potlačovány pomocí možnosti kompilátoru __/Wv:19.10.24903__.

|||
|-|-|
C4597|není definována chování: *popis*
C4604|'*typ*': předání argumentů hodnotou mezi nativní a spravovaná hranic vyžaduje platný kopírovacího konstruktoru. Jinak není definován chování za běhu
C4749|podmíněná podporována: *popis*
C4768|atributy __declspec před specifikaci propojení se ignorují.
C4834|Hodnota vrácená funkcí s atributem 'nodiscard' zahození
C4841|nestandardní rozšíření používané: *rozšíření*
C4842|výsledek offsetof "–", které se použijí k typu pomocí vícenásobná dědičnost nemusí být konzistentní mezi verzemi kompilátoru
C4869|'nodiscard, může použít pouze pro třídy, výčty a funkce s návratový typ není void
C5033|'*třídy úložiště*' je již třída podporované úložiště
C5034|použití vnitřní '*vnitřní*' způsobí, že funkce *funkce* sestavují jako kód hosta
C5035|pomocí funkce '*funkce*' způsobí, že funkce *funkce* sestavují jako kód hosta
C5036|vararg funkce Převod ukazatele, když kompilujete s /hybrid:x86arm64 '*type1*'do'*type2*.
C5037|'*– členská funkce*': definici z přesahujících člena třídy šablony nemůže mít výchozí argumenty
C5038|– datový člen '*člen1*'bude inicializován po – datový člen'*člen2*.

## <a name="warnings-introduced-in-visual-c-2017-rtm-compiler-version-191024903"></a>Upozornění byla zavedená v Visual C++ 2017 RTM (verze 19.10.24903 kompilátoru)

Tato upozornění a všech upozornění v novějších verzích, které jsou potlačovány pomocí možnosti kompilátoru __/Wv:19.00__.

|||
|-|-|
C4468|'fallthrough': atribut musí být následováno případu štítek nebo výchozí štítek
C4698|'*funkce*, je pro zkušební účely pouze a mohou podléhat změnám nebo odebrání v budoucích aktualizací.
C4839|nestandardní použití třídy se*třída*' jako argument funkce variadická
C4840|Použijte jiný přenositelností třídy se*– třída*' jako argument funkce variadická

## <a name="warnings-introduced-in-visual-c-2015-update-3-compiler-version-1900242151"></a>Upozornění byla zavedená v Visual C++ 2015 Update 3 (verze 19.00.24215.1 kompilátoru)

Tato upozornění a všech upozornění v novějších verzích, které jsou potlačovány pomocí možnosti kompilátoru __/Wv:19.00.23918__.

|||
|-|-|
C4467|použití atributů ATL je zastaralý.
C4596|'*název*': Neplatný kvalifikovaný název do deklarace členů
C4598|' #include \< *záhlaví*\>': číslo záhlaví *číslo* v *zdroj* neodpovídá *zdroj* v daném okamžiku pozice
C4599|'*argument*': *zdroj* číslo argumentu *číslo* neodpovídá *zdroje*

## <a name="warnings-introduced-in-visual-c-2015-update-2-compiler-version-1900239180"></a>Upozornění byla zavedená v Visual C++ 2015 Update 2 (verze 19.00.23918.0 kompilátoru)

Tato upozornění a všech upozornění v novějších verzích, které jsou potlačovány pomocí možnosti kompilátoru __/Wv:19.00.23506__.

|||
|-|-|
C4466|Nelze provést elision coroutine haldy
C4595|'*třída*': new – operátor třetí nebo funkce odstranění nemusí být deklarován vložené
C4828|Soubor obsahuje znak, začínající na posunu 0 x*hodnotu* , je neplatný v aktuální sadě znaku zdroje (codepage *číslo*).
C4868|Kompilátor nemusí vynutit pořadí vyhodnocení zleva doprava v seznamu braced inicializátoru

## <a name="warnings-introduced-in-visual-c-2015-update-1-compiler-version-1900235060"></a>Upozornění byla zavedená v Visual C++ 2015 Update 1 (verze 19.00.23506.0 kompilátoru)

Tato upozornění a všech upozornění v novějších verzích, které jsou potlačovány pomocí možnosti kompilátoru __/Wv:19.00.23026__.

|||
|-|-|
C4426|Optimalizace příznaky změněno poté, co včetně záhlaví, může být způsobeno #pragma optimize()
C4654|Kód umístěna před patří předkompilovaných hlaviček řádek bude ignorován. Přidávání kódu do předkompilovaných hlaviček.
C5031|#pragma warning(pop): pravděpodobně neshoda, odebrání nabídnutých v jiném souboru stavu upozornění
C5032|zjištěna #pragma warning(push) se žádné odpovídající warning(pop) #pragma

## <a name="warnings-introduced-in-visual-c-2015-rtm-compiler-version-1900230260"></a>Upozornění byla zavedená v Visual C++ 2015 RTM (verze 19.00.23026.0 kompilátoru)

Tato upozornění a všech upozornění v novějších verzích, které jsou potlačovány pomocí možnosti kompilátoru __/Wv:18__.

|||
|-|-|
C4427|'*chyba*': přetečení v konstantní dělení nedefinované chování
C4438|'*typ*': nelze bezpečně volat / await: clrcompat režimu. Pokud se*typ*' volání do modulu CLR může vést k poškození head CLR
C4455|' operátor *název*': identifikátory literálu přípon, které není začínat podtržítkem jsou vyhrazeny
C4456|prohlášení o '*název*' skryje předchozí místní deklarace
C4457|prohlášení o '*název*' skryje funkce parametr
C4458|prohlášení o '*název*' skryje třídy člena
C4459|prohlášení o '*název*' skryje globální deklarace
C4462|'*typ*': Nelze určit identifikátor GUID typu. Program může při běhu selhat.
C4463|přetečení; přiřazení *hodnotu* bitová pole, které může obsahovat pouze hodnoty z *hodnotu* k *hodnota*
C4473|'*funkce*': předáno není dostatečný počet argumentů pro řetězec formátu
C4474|'*funkce*': předáno příliš mnoho argumentů pro řetězec formátu
C4475|'*funkce*': délka modifikátor '*modifikátor*"nelze použít s – znak typu pole"*znak*' ve formátu specifikátor
C4476|'*funkce*': Neznámý typ pole znak '*znak*' v specifikace formátu
C4477|'*funkce*': řetězec formátu,*řetězec*, vyžaduje argument typu'*typ*', ale argument variadická *číslo* má typ '*typu*.
C4478|'*funkce*': poziční a – poziční zástupné symboly nelze směšovat do jednoho řetězce formátu
C4494|'*typ*': ignorování __declspec(allocator), protože funkce návratový typ není ukazatel nebo odkaz
C4495|nestandardní rozšíření '__super používané: nahraďte názvem explicitní základní třída
C4496|nestandardní rozšíření 'pro každou' použito: nahraďte pohyboval pro příkaz
C4497|nestandardní rozšíření 'zapečetěné' používané: nahraďte 'konečné.
C4498|nestandardní rozšíření používané: '*rozšíření*.
C4499|'*specializace*': explicitní specializace nemůže mít třídy úložiště (Ignorovat)
C4576|v závorkách typ a inicializačním seznam je syntaxe převod nestandardní explicitního typu
C4577|použít s žádná výjimka zpracování zadaný; režim noexcept ukončení na výjimka není zaručena. Zadejte /EHsc
C4578|'abs': převod '*typ*'do'*typ*', možné ztrátě dat. (měli jste na mysli volat '*název*' nebo #include <cmath>?)
C4582|'*typ*': konstruktor není volán implicitně
C4583|'*typ*': implicitně nevolá – destruktor
C4587|'*typ*': změna v chování: už implicitně volání konstruktoru
C4588|'*typ*': změna v chování: už implicitně destruktoru
C4589|Konstruktor abstraktní třídy*typ*'ignoruje inicializátoru pro virtuální třídy base'*typu*.
C4591|limit hloubku volání 'constexpr' *číslo* překročena (nebo constexpr:depth<NUMBER>)
C4592|'*typ*': symbol bude dynamicky inicializována (implementace omezení)
C4593|'*typ*': 'constexpr' volání vyhodnocení krok limit *hodnotu* překročena; použít /constexpr:steps<NUMBER> o zvýšení limitu
C4647|Změna v chování: __is_pod (*typu*) má jinou hodnotu v předchozích verzích
C4648|standardní atribut 'carries_dependency' je ignorován
C4649|v tomto kontextu jsou ignorovány atributy
C4753|Nelze najít rozsah ukazatele; Vnitřní funkce MPX ignorovat
C4771|Rozsah musí být vytvořen pomocí jednoduchého ukazatel; Vnitřní funkce MPX ignorovat
C4774|'*popis*': v argument byl očekáván řetězec formátu *číslo* není řetězec literálu
C4775|nestandardní rozšíření používané ve formátovacím řetězci '*řetězec*"funkce"*funkce*.
C4776|' %*znak*není povolená, ve formátovacím řetězci funkce'*funkce*.
C4777|'*popis*': řetězec formátu,*řetězec*, vyžaduje argument typu'*typ*', ale argument variadická *číslo* má typ '*typu*.
C4778|'*popis*': neukončený řetězec formátu,*řetězec*.
C4838|Převod z '*typ*'do'*typu*se vyžaduje zužující převod
C5022|'*typ*': více přesunutí konstruktory zadaný
C5023|'*typ*': více operátory přiřazení pro přesunutí zadaný
C5024|'*deklarace*': přesunout konstruktor byl implicitně definován jako odstranit
C5025|'*deklarace*': přesunout operátor přiřazení byl implicitně definován jako odstranit
C5026|'*typ*': přesunout konstruktor byl implicitně definován jako odstranit
C5027|'*typ*': přesunout operátor přiřazení byl implicitně definován jako odstranit
C5028|'*název*': zarovnání zadaný v deklaraci předchozích (*číslo*) nebyly zadány v definici
C5029|nestandardní rozšíření používané: zarovnání atributy v jazyce C++ vztahuje na proměnné, datové členy a pouze typy značek
C5030|atribut '*atribut*' nebyla rozpoznána

## <a name="warnings-introduced-in-visual-c-2013-compiler-version-1800210051"></a>Upozornění zavedená v prostředí Visual C++ 2013 (verze 18.00.21005.1 kompilátoru)

Tato upozornění a všech upozornění v novějších verzích, které jsou potlačovány pomocí možnosti kompilátoru __/Wv:17__.

|||
|-|-|
C4301|'*typ*': přepisování virtuální funkce pouze se liší od '*deklarace*' kvalifikátorem const nebo volatile
C4316|'*typ*': objekt přidělené v haldě nemusí být zarovnána *číslo*
C4380|'*typ*': výchozí konstruktor nemůže být zastaralé.
C4388|'*tokenu*': Neshoda podepsané nepodepsaných
C4423|'std::bad_alloc': bude zachycena podle třídy ('*typ*") na řádku *číslo*
C4424|catch pro '*typ*'sebou'*typ*' na řádku *číslo*; nepředvídatelné chování může dojít, pokud je vyvolána 'std::bad_alloc'
C4425|Poznámky SAL nelze použít na '...
C4464|zahrnují relativní cesta obsahuje '..'
C4575|'__vectorcall' není kompatibilní s ' nebo clr' možnost: převod '__stdcall.
C4609|'*typ*'je odvozena z výchozí rozhraní'*typ*'na typ"*typ*'. Použijte jiný výchozí rozhraní pro '*typ*", nebo přerušení vztahu základní nebo odvozené.
C4754|Převod pravidel pro aritmetické operace porovnání v *popis*(*číslo*) znamená, že jeden větve nelze provést. Přetypování '*typ*'do'*typ*' (nebo podobné *číslo* bajtů).
C4755|Převod pravidel pro aritmetické operace porovnání v *popis*(*číslo*) znamená, že jeden větve nelze provést v vložená funkce. Přetypování '*typ*'do'*typ*' (nebo podobné *číslo* bajtů).
C4767|název sekce '*název*' je delší než 8 znaků a bude zkrácen podle linkeru
C4770|částečně ověřit výčtu '*název*se používá jako index
C4827|Veřejná metoda 'ToString' s 0 parametry by měl být označen jako virtuální a přepsání
C4882|předání functors s operátory volání bez const concurrency::parallel_for_each je zastaralý.
C4973|'*typ*': označené jako zastaralé
C4974|'*typ*': označené jako zastaralé
C4981|Warbird: funkce '*deklarace*' označen jako __forceinline není vložená protože obsahuje sémantiku výjimky
C4990|Warbird: *zpráv*
C4991|Warbird: funkce '*deklarace*' označen jako __forceinline není vložená protože je větší než nadřazené úrovně ochrany inlinee
C4992|Warbird: funkce '*deklarace*' označen jako __forceinline není vložená protože obsahuje vložené sestavení, které nelze chránit

## <a name="warnings-introduced-in-visual-c-2012-compiler-version-1700511061"></a>Upozornění zavedená v sadě Visual C++ 2012 (verze 17.00.51106.1 kompilátoru)

Tato upozornění a všech upozornění v novějších verzích, které jsou potlačovány pomocí možnosti kompilátoru __/Wv:16__.

|||
|-|-|
C4330|atribut '*atribut*'pro oddíl'*části*' ignorovat
C4415|duplicate __declspec(code_seg('*name*'))
C4416|__declspec(code_seg(...)) obsahuje prázdný řetězec: Ignorovat
C4417|Vytvoření instance šablony explicitní nemůže mít __declspec(code_seg(...)): Ignorovat
C4418|__declspec(code_seg(...)) u výčtu ignorovat
C4419|'*název*'nemá žádný vliv, při použití privátního ref class'*typ*'.
C4435|'*typ*': objekt rozložení pod /vd2 se změní z důvodu virtuální základní '*typu*.
C4436|dynamic_cast z virtuální základní '*typ*'do'*typ*' v konstruktoru nebo destruktor může selhat s částečně sestavený objekt
C4437|dynamic_cast z virtuální základní '*typ*'do'*typ*' by mohlo selhat v některých kontextech
C4443|Parametr očekávané – Direktiva pragma '0', '1' nebo '2.
C4446|'*typ*': nelze mapovat člen '*název*se do tohoto typu, z důvodu konfliktu s názvem typu. Metoda byla přejmenována na '*název*.
C4447|"hlavní" podpis nalezen bez model vláken. Zvažte použití, int hlavní (Platform::Array\<Platform::String ^ > ^ argumentů)'.
C4448|'*typu*' nemá výchozí rozhraní zadaný v metadatech. Výdej: '*typ*', který může selhat v době běhu.
C4449|'*typ*' nezapečetěné typ by měl být označen jako [WebHostHidden]
C4450|'*typ*' by měl být označen jako [WebHostHidden] protože je odvozen z'*typu*.
C4451|'*typ*': použití třídy ref*typ*' uvnitř tohoto kontextu může vést k neplatný zařazování objektu v kontextu
C4452|'*typ*': veřejného typu nemůže být v globálním oboru. Musí být v oboru názvů, který je podřízeným názvu výstupního souboru, .winmd.
C4453|'*typ*': Nepoužívejte typu [WebHostHidden] na povrchu publikované veřejného typu, který není [WebHostHidden]
C4454|'*typ*"je větší než počet vstupních parametrů přetížené bez nutnosti [DefaultOverload] zadán. Výběr '*deklarace*se jako výchozí přetížení
C4471|'*název*': deklaraci předat dál bez ohledu na obor výčtu musí mít základní typ (int předpokládá, že)
C4472|'*název*' je nativní výčet: přidejte specifikátor přístupu (soukromého a veřejného) deklarovat spravované nebo WinRT výčtu
C4492|'*typ*': odpovídá základní metody třídy ref '*typ*', ale nebyla označena jako 'přepsat.
C4493|odstranění výraz nemá žádný účinek jako destruktoru objektu '*typ*' nemá 'veřejné' usnadnění přístupu
C4585|'*typ*': A WinRT 'veřejné ref class' musí být buď zapečetěné nebo odvozena z existující nezapečetěné – třída
C4586|'*typ*': veřejného typu nelze deklarovat v nejvyšší úrovně obor názvů s názvem "Windows.
C4695|#pragma execution_character_set: '*argument*' není podporované argument: je podporována aktuálně jedinou 'UTF-8.
C4703|proměnné potenciálně Neinicializovaný místní ukazatele '*název*se používá
C4728|/ Yi – možnost ignorován, protože se vyžaduje odkaz na PCH
C4745|volatile přístup '*název*, nelze ji přijmout z důvodu jeho velikosti
C4746|volatile přístup '*název*' podléhá/volatile:\<iso\|ms > nastavení; zvažte použití __iso_volatile_load/úložiště vnitřní funkce
C4872|plovoucí bodu dělení nulou zjistil při kompilování graf volání pro concurrency::parallel_for_each v: '*popis*.
C4880|přetypování z '*typ*'do'*typ*': přetypování rychle constness z ukazatel nebo odkaz může vést k nedefinované chování v amp omezený funkci
C4881|v konstruktoru nebo destruktoru nebude možné volat pro proměnnou tile_static '*typu*.
C4966|'*popis*' má anotaci __code_seg s názvem nepodporované segmentu, poznámky ignorovat
C4988|'*typ*': proměnná deklarována mimo rozsah třídy nebo funkce
C4989|'*popis*': typ má konfliktní definice.

## <a name="warnings-introduced-in-visual-c-2010-compiler-version-16004021901"></a>Upozornění zavedená ve Visual C++ 2010 (verze 16.00.40219.01 kompilátoru)

Tato upozornění a všech upozornění v novějších verzích, které jsou potlačovány pomocí možnosti kompilátoru __/Wv:15__.

|||
|-|-|
C4352|'*název*': již definována – vnitřní funkce
C4573|použití "*typu*se vyžaduje kompilátor k zachycení ', ale aktuální režim zachytávání výchozí neumožňuje
C4574|'*název*'je definován jako ' 0': měli jste na mysli používat ' #if *název*'?
C4689|'*znak*': Nepodporovaný znak v #pragma detect_mismatch; #pragma ignorovat
C4751|/ arch AVX příznak nelze použít u Streaming SIMD Extensions Intel(R), která jsou v rámci vložené ASM
C4752|Najít Intel(R) Advanced vektoru rozšíření; Zvažte použití odpovídající/arch AVX příznak
C4837|trigraph zjistil: '?? *znak*"nahradit"*znak*.
C4986|'*deklarace*': specifikace výjimek neodpovídá předchozí deklarace
C4987|použito nestandardní rozšíření: 'throw (...)'

## <a name="warnings-introduced-in-visual-c-2008-compiler-version-15002102208"></a>Upozornění zavedená ve Visual C++ 2008 (verze 15.00.21022.08 kompilátoru)

Tato upozornění a všech upozornění v novějších verzích, které jsou potlačovány pomocí možnosti kompilátoru __/Wv:14__.

|||
|-|-|
C4396|'*typ*': specifikátor vložené nelze použít, když deklaraci friend odkazuje specializace šablony funkcí
C4413|'*deklarace*': referenční dokumentace je inicializován do dočasného, který není zachován po ukončení konstruktoru
C4491|'*popis*': má neplatný formát verze IDL
C4603|'*název*': Makro není definováno nebo ho definici se liší po použití předkompilovaných hlaviček
C4627|'*popis*': při vyhledávání předkompilované hlavičky použití přeskočen
C4750|'*popis*': funkce s _alloca() vložená do smyčky
C4910|'*typ*': '__declspec(dllexport)' a 'extern, jsou nekompatibilní na explicitní vytvoření instance
C4985|'*deklarace*': atributy není k dispozici na předchozí deklarace.

## <a name="warnings-introduced-in-visual-c-2005-compiler-version-140050727762"></a>Upozornění zavedena v systému Visual C++ 2005 (verze 14.00.50727.762 kompilátoru)

Tato upozornění a všech upozornění v novějších verzích, které jsou potlačovány pomocí možnosti kompilátoru __/Wv:13__.

|||
|-|-|
C4000|Neznámý upozornění Zvolte prosím příkaz se na technickou podporu v nabídce Nápověda Visual C++, nebo otevřít soubor nápovědy se na technickou podporu pro další informace
C4272|'*typ*': je označena deklarace __declspec(dllimport); musíte zadat nativní konvence volání, při importu funkce.
C4333|'*výraz*': posunutí doprava o příliš velké množství, ztráty dat
C4334|'*výraz*': výsledek 32-bit shift implicitně převést na 64 bitů (byla určena shift 64-bit?)
C4335|Formát souboru Mac zjistil: prosím převést zdrojový soubor formátu DOS nebo UNIX
C4342|Změna v chování: '*typu*se volá, ale byla zavolána operátor členů v předchozích verzích
C4350|Změna v chování: '*deklarace*'názvem místo'*deklarace*.
C4357|argument pole param nenachází v seznamu formální argument pro delegáta '*deklarace*'ignorovat při generování'*typu*.
C4358|'*výraz*': návratový typ kombinované Delegáti není 'void'; vrácená hodnota není definován
C4359|'*typ*': zarovnání specifikátor je menší než skutečná zarovnání (*číslo*) a budou ignorovány.
C4362|'*typ*': zarovnání větší než 8 bajtů nepodporuje CLR
C4364|#using pro sestavení '*název*' dříve zobrazit při *popis*(*číslo*) bez atribut as_friend; as_friend nebyly použity
C4365|'*výraz*': převod '*typ*'do'*typ*', podepsané nepodepsaných neshoda
C4366|Výsledkem unární '*operátor*' operátor může nezarovnané
C4367|Převod z '*typ*'do'*typu*, může způsobit, že chybné zarovnání výjimka datový typ
C4368|nelze definovat '*název*, jako je členem spravovaná'*typ*': smíšený typy nejsou podporovány
C4369|'*typ*': hodnotu výčtu,*číslo*'nemůže být reprezentován jako'*typ*', hodnota je'*číslo*.
C4374|'*deklarace*': nevirtuálních metoda nebude implementovat metodu rozhraní '*deklarace*.
C4375|Metoda neveřejný '*deklarace*'nepřepisuje'*deklarace*'
C4376|přístup k specifikátor '*specifikátor*:' již není podporována: použijte '*specifikátor*:' místo
C4377|nativní typy jsou privátní ve výchozím nastavení; -d1PrivateNativeTypes je zastaralý.
C4378|Musíte získat ukazatelů na funkce Spustit inicializátory; Vezměte v úvahu System::ModuleHandle::ResolveMethodHandle
C4379|Verze *verze* common language runtime nepodporuje tento kompilátoru. Pomocí této verze může vést k neočekávaným výsledkům
C4381|'*deklarace*': metoda neveřejný nebude implementovat metodu rozhraní '*deklarace*.
C4382|vyvolání '*typ*': typu s __clrcall – destruktor nebo kopírovacího konstruktoru pouze zachytit v/CLR: pure modulu
C4383|'*typ*': význam vyhodnocení popisovač lze změnit, pokud definovaný uživatelem,*operátor*' existuje; zápis operátor jako statické funkce jako explicitní o operand – operátor
C4384|#pragma '*– direktiva*' musí být použit pouze v globálním oboru
C4393|'*typ*': const nemá žádný vliv *popis* – datový člen; ignorovat
C4394|'*typ*': by neměl být označen symbol na appdomain __declspec (*hodnotu*)
C4395|'*typ*': funkce člen, který bude vyvolán na kopii initonly datový člen '*typ*.
C4397|DefaultCharSetAttribute je ignorována.
C4398|'*typ*': globální objektu na proces nemusí pracovat správně s více domén; zvažte použití __declspec(appdomain)
C4399|'*typ*': symbol na proces by neměl být označené jako __declspec (*hodnotu*) při kompilaci s volbou/CLR: čisté
C4400|'*typ*': const nebo volatile kvalifikátory u tohoto typu nejsou podporovány.
C4412|'*deklarace*': podpis funkce obsahuje typ '*typ*'; Objekty C++ jsou unsafe předat mezi čistý kód a smíšený nebo nativní.
C4429|možné neúplný nebo nesprávně vytvořený universal znak name
C4430|chybějící specifikátor typu: předpokládá se int Poznámka: C++ nepodporuje výchozí int
C4431|chybějící specifikátor typu: předpokládá se int Poznámka: C již nepodporuje výchozí int.
C4434|Statický konstruktor musí mít privátní usnadnění; Změna privátní přístup
C4439|'*typ*': definice funkce spravovaného typu v podpisu musí mít __clrcall konvenci volání
C4441|konvence volání,*konvence*' ignorován; '*konvence*' místo toho použít
C4445|'*deklarace*': v typu spravované nebo WinRT virtuální metoda nemůže být privátní
C4460|Operátor CLR nebo WinRT '*typ*', byl předán parametr odkazem. Operátor CLR nebo WinRT '*operátor*, má jinou sémantiku z C++ operátor'*operátor*', máte v úmyslu předat hodnotu?
C4461|'*typ*': Tato třída má finalizační metody '! *typ*, ale žádné – destruktor ' ~*typ*.
C4470|direktivy s plovoucí desetinnou čárkou řízení ignorovat v/CLR
C4480|nestandardní rozšíření používané: určení podkladovým typem výčtu '*typu*.
C4481|nestandardní rozšíření používané: override – specifikátor '*specifikátor*.
C4482|nestandardní rozšíření používané: výčtu '*typu*se používá kvalifikovaný název
C4483|Chyba syntaxe: očekáváno C++ – klíčové slovo
C4484|'*typ*': odpovídá základní metody třídy ref '*typ*', ale nebyla označena 'virtuální', 'nové' nebo 'přepsat'; se předpokládá, new' (a ne virtuální)
C4485|'*typ*': odpovídá základní metody třídy ref '*typ*', ale není označen jako 'nové' nebo 'přepsání'; 'nové (a "virtuální") se předpokládá, že
C4486|'*typ*': privátní virtuální metoda ref třídy nebo – hodnotová třída by měl být označen 'zapečetěné.
C4487|'*typ*': odpovídá zděděná nevirtuálních metoda '*typ*', ale nebyla označena jako explicitně, nové
C4488|'*typ*': vyžaduje se*– klíčové slovo*'implementovat metodu rozhraní – klíčové slovo'*typ*'
C4489|'*– klíčové slovo*': není povoleno pro metodu rozhraní '*název*'; přepsání specifikátory jsou povolená jenom u metody třídy ref třídy a hodnota
C4490|'*– klíčové slovo*': nesprávné použití přepsání specifikátor; '*typ*' neodpovídá metodu základní ref – třída
C4538|'*typ*': const nebo volatile kvalifikátory u tohoto typu nejsou podporovány.
C4559|'*typ*': předefinování; __declspec zvýšení – funkce (*hodnotu*)
C4565|'*typ*': předefinování; symbol bylo dříve deklarované s __declspec (*hodnotu*)
C4566|znak reprezentována universal znak name "*znak*' nemůže být reprezentován na aktuální stránce kódu (*číslo*)
C4568|'*typ*': žádní členové odpovídat podpis explicitní přepsání
C4569|'*typ*': žádní členové odpovídat podpis explicitní přepsání
C4570|'*typ*': není explicitně deklarovány jako abstraktní, ale nemá abstraktní funkce
C4571|Informační: catch(...) sémantiku změněné od Visual C++ 7.1; strukturované výjimky (SEH) jsou již zachyceny
C4572|Atribut [ParamArray] je zastaralá v/CLR, použijte "..." místo
C4580|[atribut] je zastaralá; Místo toho zadejte *zadaný*atribut jako základní třída
C4581|zastaralé chování: ' "*název*", nahradí se*název*' do atribut procesu
C4606|#pragma – upozornění: '*číslo*' ignorován; Upozornění analýzy kódu nejsou přidružené úrovně varování
C4631|MSXML nebo není k dispozici, XPath dokumentu XML, který komentáře nebude zpracováno. *Popis*
C4632|Komentář dokumentu XML: *popis* – přístup byl odepřen: *popis*
C4633|Komentář dokumentu XML*popis*: Chyba: *popis*
C4634|Komentář dokumentu XML*popis*: nelze použít: *popis*
C4635|Komentář dokumentu XML*popis*: chybně formátovanou XML: *popis*
C4636|Komentář dokumentu XML*popis*: značka vyžaduje neprázdný '*popis*' atribut.
C4637|Komentář dokumentu XML*popis*: <include> značky zahozeny. *Popis*
C4638|Komentář dokumentu XML*popis*: odkaz na neznámé symbol '*popis*'.
C4639|Chyba MSXML, dokument XML, který komentáře nebude zpracováno. *Popis*
C4641|Komentář dokumentu XML má nejednoznačný křížových odkazů: 
C4678|Základní třída se*deklarace*je méně přístupný než*název*.
C4679|'*popis*': nelze importovat člena
C4687|'*typ*': zapečetěné abstraktní třídy nelze implementovat rozhraní '*typu*.
C4688|'*název*': omezení seznam obsahuje privátní typ sestavení '*deklarace*.
C4690|[ emitidl – ( pop ) ]: více bodů POP než nabízených oznámení
C4691|'*typ*': byl očekáván typ odkazovat ve které se neodkazuje *modulu* '*popis*', typem definovaným v místo toho použít aktuální překlad jednotky
C4692|'*název*': podpis privátního člena obsahuje privátní nativní typ sestavení '*deklarace*.
C4693|'*typ*': zapečetěné abstraktní třídy nemůže mít u členů instancí*název*.
C4694|'*typ*': zapečetěné abstraktní třídy nemají základní třídy*typu*.
C4720|řádek assembleru sestavy: '*popis*.
C4721|'*popis*': není k dispozici jako vnitřní funkce
C4722|'*popis*': destruktor nikdy vrátí, potenciální nevracení paměti
C4726|ARM arch4/4T podporuje pouze ' < cpsr_f > nebo < spsr_f >' okamžitou hodnotou
C4727|PCH s názvem *název* s stejné časovým razítkem v nalezen *název* a *název*.  Pomocí prvního PCH.
C4729|Funkce, které jsou příliš dlouhé pro graf toku na základě upozornění
C4730|'*popis*': kombinování _m64 a plovoucí bodu výrazy může vést k nesprávným kódem
C4731|'*popis*': registrace ukazatel s rámečkem '*zaregistrovat*' upraveném kódu vnořeného sestavení
C4732|vnitřní '*vnitřní*' není podporován v této architektuře
C4733|Vložené asm přiřazení k 'FS:0': není registrován jako bezpečné obslužné rutiny obslužná rutina
C4734|Více než 64 tisíc čísla řádků v COFF ladění informace o části; Zastavit generování čísla řádků COFF ladění pro modul se*modulu*.
C4738|ukládání 32bitového plovoucího výsledku do paměti, možná ztráta
C4739|odkaz na proměnnou '*proměnná*' překračuje jeho prostorem úložiště
C4740|tok nebo zrušení vloženého kódu asm potlačí globální optimalizace
C4742|'*proměnná*'má v různé zarovnání'*umístění*'a'*umístění*': *číslo* a *číslo*
C4743|'*název*, má jinou velikost v'*umístění*'a'*umístění*': *číslo* a *číslo* bajtů
C4744|'*název*'má jiný typ v'*umístění*'a'*umístění*': '*typ*'a'*typu*.
C4747|Volání metody spravované '*typ*': spravovaného kódu nemusí být možné spustit v zavaděči, včetně vstupní bod knihovny DLL a volání z vstupní bod knihovny DLL
C4761|integrální velikost Neshoda v argumentu; Převod zadaný
C4764|Nelze zarovnat catch objektů na větší než 16 bajtů
C4788|'*identifikátor*': identifikátor byl zkrácen na '*číslo*' znaků
C4789|vyrovnávací paměti se*název*' velikosti *číslo* bajtů bude přetečení; *číslo* bude zapsáno bajtů začínající na posunu *číslo*
C4801|Vrátí odkazem není ověřitelný: *popis*
C4819|Tento soubor obsahuje znak, který není možné vyjádřit v aktuální znakové stránky (*číslo*). Uložte soubor ve formátu Unicode, aby se zabránilo ztrátě dat.
C4826|Převod z '*typ*'do'*typ*' je rozšířeny. To může způsobit neočekávané modul runtime chování.
C4829|Může být nesprávné parametry hlavní funkce. Vezměte v úvahu, int hlavní (Platform::Array\<Platform::String ^ > ^ argv –).
C4835|'*typ*': inicializátoru pro exportovaná data se nespustí, dokud spravovaný kód je nejdřív provést v sestavení hostitele
C4867|'*typ*': nestandardní syntaxe; použijte 'a' vytvořte ukazatel na člena
C4936|Tato __declspec je podporována pouze, když kompilujete s/CLR nebo/CLR: pure
C4937|'*název*'a'*název*se neodlišuje jako argumenty pro*možnost*.
C4938|'*typ*': plovoucí redukční proměnnou bod může způsobit nekonzistentní výsledky v rámci /fp: striktní nebo fenv_access – #pragma
C4939|#pragma vtordisp je zastaralá a budou odebrány v budoucí verzi Visual C++
C4947|'*typ*': označené jako zastaralé
C4949|direktivy 'spravované' a 'nespravované, dávat smysl jenom v případě, že kompilovat s ' / clr [: možnost].
C4950|'*typ*': označené jako zastaralé
C4955|'*popis*': importu ignorován; již byla naimportována ze '*zdroj*.
C4956|'*typ*': Tento typ není ověřitelný
C4957|'*výraz*': explicitní přetypování z '*typ*'do'*typ*' není ověřitelný
C4958|'*výraz*': není ověřitelný aritmetika ukazatele
C4959|nelze definovat *třída* '*typ*' v/CLR: safe vzhledem k tomu, že přístup k jeho členy vypočítá neověřitelný kód
C4960|'*popis*' je příliš dlouhý pro být vytvořený profil
C4961|Žádná data profilu se sloučí se*umístění*', zakázat optimalizace na základě profilu
C4962|'*popis*': optimalizace na základě profilu zakázán, protože optimalizace způsobily nekonzistenci dat profilu
C4963|'*popis*': nalezena žádná data profilu; kompilátoru různé možnosti, které byly používány v instrumentovaného sestavení
C4964|Nebyly zadány žádné možnosti optimalizace; informace o profilu nebudou shromažďovány.
C4965|implicitní pole celé číslo 0; použít nullptr nebo explicitní přetypování
C4970|Delegovat konstruktor: cílový objekt ignorován, protože se*deklarace*' je statický
C4971|Argument pořadí: \<cílový objekt >, \<cíle funkce > pro konstruktor delegáta je zastaralý, pomocí \<cíle funkce >, \<cílový objekt >
C4972|Přímo změnou nebo práce výsledek operace unbox jako lvalue neověřitelný

## <a name="warnings-introduced-in-visual-c-2003-compiler-version-13103077"></a>Upozornění zavedené v roce 2003 Visual C++ (verze 13.10.3077 kompilátoru)

Tato upozornění a všech upozornění v novějších verzích, které jsou potlačovány pomocí možnosti kompilátoru __/Wv:13.00.9466__.

|||
|-|-|
C4343|Optimalizace #pragma (*popis*, vypnutí) přepsání /Og – možnost
C4344|Změna v chování: použijte explicitní šablony argumenty výsledků volání '*deklarace*.
C4346|'*typ*': závislé název není typu
C4348|'*deklarace*': předefinování výchozího parametru: Parametr *číslo*
C4356|'*typ*': člen statických dat nelze inicializovat prostřednictvím odvozené třídy
C4408|Anonymní *struktura* nedeklaruje žádné datové členy
C4544|'*deklarace*': výchozí šablony argument ignorovat na toto prohlášení šablony
C4545|výraz před čárkou vyhodnocuje na funkci, která nemá k dispozici seznam argumentů
C4546|volání funkce před čárkou nemá seznamu argumentů
C4547|'*výraz*': operátor před čárkou nemá žádný vliv; očekávaný operátoru s vedlejším účinkem
C4548|výraz před čárkou nemá žádný vliv; očekávaný výraz s vedlejším účinkem
C4549|'*výraz*': operátor před čárkou nemá žádný vliv; nebyla hodláte '*výraz*'?
C4628|spřežky nejsou podporovány se -Ze. Znak pořadí '*pořadí*'nebyl interpretován jako alternativní token pro'*tokenu*.
C4629|spřežka používá, sekvence znaků '*pořadí*'interpretovat jako token'*tokenu*' (Vložit mezeru mezi dva znaky, pokud se jedná, není to v pořádku)
C4671|'*popis*': konstruktor copy je nedostupná
C4676|'*popis*': destruktoru je nedostupná
C4677|'*název*': podpis privátního člena obsahuje privátní typ sestavení '*deklarace*.
C4686|'*typ*': vrátit změnu v hodnotě UDT možné změnu v chování konvence volání
C4812|zastaralé deklarace styl: použijte '*typ*::*název*' místo toho
C4813|'*typ*': funkce friend místní třídy musí mít bylo dříve deklarované
C4821|Nelze určit typ kódování Unicode, uložte soubor s podpisem (BOM)
C4822|'*typ*': místní třídy – členská funkce nemá text
C4823|'*typ*': používá přídavných ukazatelů ale unwind sémantiku nejsou povoleny. Zvažte použití/EHa
C4913|uživatel definované binární operátor ',' existuje, ale žádné přetížení může převést všechny operandy, výchozí integrovanou binární operátor ',' použité
C4948|Návratový typ se*deklarace*' neodpovídá poslední parametr typ odpovídající nastavovací metoda
C4951|'*popis*' bylo upraveno od data nebyla shromážděna, profil nepoužívá data profilu – funkce
C4952|'*popis*': v databázi programu nalezena žádná data profilu se*popis*.
C4953|Inlinee '*popis*' bylo upraveno od data nebyla shromážděna, profil data profilu nepoužívá
C4954|'*popis*': není profilovaným (obsahuje výraz přepínače __int64)

## <a name="warnings-introduced-in-visual-c-2002-compiler-version-13009466"></a>Upozornění byla zavedená v 2002 Visual C++ (verze 13.00.9466 kompilátoru)

Tato upozornění a všech upozornění v novějších verzích, které jsou potlačovány pomocí možnosti kompilátoru __/Wv:12__.

|||
|-|-|
C4096|'*typ*': rozhraní není rozhraní modelu COM; nebude vygenerované k IDL
C4097|Parametr – Direktiva pragma jako "obnovení" nebo "vypnuto"
C4165|"HRESULT" je převáděn na 'bool'; jste si jistí, že je to, co chcete použít?
C4183|'*název*': chybí návratový typ; předpokládá se, že vrácení, int, členské funkce
C4199|*Popis*
C4255|'*název*': žádné funkce prototypu zadané: převádění (')' do '(void).
C4256|'*deklarace*': '...' má konstruktor pro třídu s virtuální základů; volání nemusí být kompatibilní se starší verzí aplikace Visual C++
C4258|'*název*': definice z pro smyčky je ignorován; slouží k definici z nadřazeného oboru
C4263|'*deklarace*': členská funkce nepřepisuje všechny základní třídy člena virtuální funkce
C4264|'*deklarace*': přepsání není k dispozici pro člena virtuální funkci z základní '*– třída*'; funkce je skrytá.
C4265|'*typ*': třída má virtuální funkce, ale není destruktor virtuální instance této třídy nemusí být správně destructed
C4266|'*deklarace*': přepsání není k dispozici pro člena virtuální funkci z základní '*– třída*'; funkce je skrytá.
C4267|'*výraz*': převod 'size_t' do '*typ*', možné ztrátě dat.
C4274|#ident ignorován; naleznete v dokumentaci k #pragma komentář (exestr, 'řetězec')
C4277|importované položky '*typ*::*název*' existuje jako – datový člen a členské funkce; ignorovat – datový člen
C4278|'*název*': identifikátor v knihovny typů,*popis*' je již makra; použít kvalifikátor 'přejmenovat.
C4279|'*název*': identifikátor v knihovny typů,*popis*' je klíčové slovo; použít kvalifikátor 'přejmenovat.
C4287|'*výraz*': Neshoda konstantní bez znaménka nebo záporná
C4288|nestandardní rozšíření používané: '*název*': mimo obor cyklu for se používá proměnná řízení smyčky deklarované v pro smyčky; je v konfliktu s deklaraci ve vnějším oboru
C4289|nestandardní rozšíření používané: '*název*': mimo obor cyklu for se používá proměnná řízení smyčky deklarované v pro – smyčky
C4293|'*výraz*': posunutí počet záporný nebo příliš velký, není definovaná chování
C4295|'*typ*': pole je příliš malá, aby zahrnují ukončující znak hodnoty null
C4296|'*výraz*': výraz je vždy *hodnota*
C4297|'*typ*': funkce předpokládá, že není však výjimku
C4298|'*název*': identifikátor v knihovny typů '*popis*' je již makra; přejmenování k ' __*název*.
C4299|'*název*': identifikátor v knihovny typů '*popis*' je klíčové slovo; přejmenování k ' __*název*.
C4302|'*výraz*': zkrácení z '*typ*'do'*typu*.
C4303|*převod* z '*typ*'do'*typ*' je zastaralý, použít static_cast, __try_cast nebo dynamic_cast
C4314|Parametr očekávané – Direktiva pragma '32' nebo '64.
C4315|'*typ*":"this"ukazatele pro člena '*typ*, nemusí být zarovnána *číslo* podle očekávání tím konstruktoru
C4318|předání konstantní nula jako délku memset –
C4319|'*výraz*': nulové rozšíření '*typ*'do'*typ*' větší velikosti
C4321|Automatické generování IID pro rozhraní '*typu*.
C4322|Automatické generování CLSID pro třídu*typu*.
C4323|opakované použití zaregistrován CLSID pro třídu*typu*.
C4324|'*typ*': struktura byl vyplní důsledku specifikátor zarovnání
C4325|atributy pro standardní oddíl '*popis*' ignorovat
C4326|Návratový typ se*název*by měla být*typ*, místo provedení'*typ*.
C4327|'*výraz*': zarovnání indirection LHS (*číslo*) je větší než RHS (*číslo*)
C4328|'*popis*': zarovnání indirection formální parametr *číslo* (*číslo*) je větší než skutečná argument zarovnání (*číslo*)
C4329|Zarovnání specifikátor je na výčtu ignorována.
C4336|Import knihovny typů referencí '*knihovny*'před importem'*popis*.
C4337|knihovny typů referencí '*knihovny*'v'*popis*, se automaticky importují
C4338|#pragma *popis*: standardní oddíl '*části*' se používá
C4339|'*typ*': použití nedefinované typu zjistil v CLR nebo WinRT meta-data - použití tohoto typu může vést k výjimku modulu runtime
C4353|nestandardní rozšíření používané: Konstanta 0 jako výraz funkce.  Místo toho použijte '__noop' – vnitřní funkce
C4370|'*deklarace*': z předchozí verze kompilátoru kvůli lepší okolních došlo ke změně rozložení – třída
C4371|'*deklarace*': mohlo dojít ke změně rozložení třídy z předchozí verze kompilátoru kvůli lepší okolních člena '*člen*.
C4373|'*typ*': virtuální funkce přepsání*deklarace*', předchozí verze kompilátoru přepsat při parametry pouze podle const nebo volatile kvalifikátory lišil.
C4387|'*popis*': byla považována za
C4389|'*výraz*': Neshoda podepsané nepodepsaných
C4391|'*deklarace*': nesprávné návratový typ pro vnitřní, byla očekávána funkce '*typu*.
C4392|'*deklarace*': nesprávný počet argumentů pro vnitřní, byla očekávána funkce '*číslo*' argumenty
C4407|CAST. mezi různé ukazatel na člena reprezentace kompilátoru generovat nesprávný kód
C4420|'*název*': operátor není k dispozici, pomocí '*název*' místo toho; kontrola běhu může dojít k ohrožení
C4440|volání metody konvence předefinování z '*popis*'do'*popis*' ignorovat
C4442|vložený null ukončovací __annotation argument.  Hodnota bude zkrácen.
C4444|'*název*': '__unaligned' nejvyšší úrovně není implementována v tomto kontextu
C4526|'*typ*': statické členské funkce nelze přepsat virtuální funkce '*deklarace*' přepsání ignorovány, bude skrytá virtuální funkce
C4531|Zpracování výjimek jazyka C++ není k dispozici na systém Windows CE. Použít strukturované zpracování výjimek
C4532|'*popis*': přejít z *nakonec* bloku má undefined chování při ukončení zpracování
C4533|Inicializace se*deklarace*' je vynecháno, goto *deklarace*.
C4534|'*deklarace*, nebude pro výchozí konstruktor *– třída* '*typ*' z důvodu argument výchozí
C4535|volání _set_se_translator() vyžaduje/EHa
C4536|'*popis*': název typu překračuje limit meta-data "*číslo*' znaků
C4537|'*deklarace*': '.' u jiných UDT typu
C4542|Přeskočení generování sloučené vložený text souboru nelze zapisovat *typ* souboru: "*filename*': *chyba*
C4543|Vložit text Potlačené podle atributu "žádné\_injected_text.
C4555|výraz nemá žádný vliv; očekávaný výraz s vedlejším účinkem
C4557|'__assume' obsahuje vliv '*vliv*.
C4558|Hodnota operand '*číslo*"je mimo rozsah"*číslo* - *číslo*.
C4561|'__fastcall' není kompatibilní s ' nebo clr' možnost: převod '__stdcall.
C4562|jsou požadovány s plně deklaraci funkce ' nebo clr' možnost: převádění (')' do '(void).
C4564|Metoda '*název*' z *– třída* '*typ*'Definuje nepodporované výchozí parametr'*parametr*.
C4584|'*typ*': základní třídy*deklarace*'je již základní třídy z'*deklarace*.
C4608|Inicializace více členů sjednocení: '*typ*'a'*typu*.
C4619|#pragma – upozornění: neexistuje číslo upozornění "*číslo*.
C4623|'*typ*': výchozí konstruktor byl implicitně definován jako odstranit
C4624|'*typ*': destruktor byl implicitně definován jako odstranit
C4625|'*typ*': kopírovacího konstruktoru byl implicitně definován jako odstranit
C4626|'*typ*': operátor přiřazení byl implicitně definován jako odstranit
C4645|funkce deklarovat s 'noreturn' má příkaz return
C4646|funkce deklarovat s 'noreturn' má návratový typ není void
C4659|#pragma '*popis*': používat vyhrazené segmentu '*název*' má undefined chování, použijte #pragma komentář (linker,...)
C4667|'*deklarace*': žádné funkce šablony definovaný, která odpovídá vynutit vytváření instancí
C4668|'*název*'není definován jako makro preprocesoru, nahraďte '0' pro'*hodnotu*.
C4669|'*výraz*': unsafe převod: '*typ*' je spravovaná/WinRT typu objektu
C4674|'*název*' musí být deklarován "statická" a mít přesně jeden parametr
C4680|'*typ*': Třída typu coclass neurčuje výchozí rozhraní
C4681|'*typ*': Třída typu coclass neurčuje výchozí rozhraní, která je zdroje událostí
C4682|'*typ*': atribut směrovou parametr zadán, jako výchozí bude použit [v]
C4683|'*deklarace*': má zdroj události k výstupnímu-parametr; cvičení opatrní při zapojování více obslužných rutin událostí
C4684|'*popis*': upozornění!! atribut může způsobit, že generace neplatný kód: používejte opatrně
C4685|Očekává se >> ' nalezen ' >>, při analýze parametry šablony
C4700|Neinicializovaný místní proměnné '*název*se používá
C4701|potenciálně Neinicializovaný místní proměnné '*název*se používá
C4702|Nedosažitelný kódu
C4711|Funkce '*název*' vybrané pro automatické vložené rozšíření
C4714|Funkce '*deklarace*' označen jako __forceinline není vložená
C4715|'*funkce*': Ne všechny cesty řízení vrátit hodnotu
C4716|'*funkce*': musí vrátit hodnotu
C4717|'*funkce*': rekurzivní u všech cest řízení funkce způsobí přetečení zásobníku modul runtime
C4718|'*funkce*': rekurzivní volání nemá žádné vedlejší účinky odstranění
C4719|Dvojité konstanta najít na požádání Qfast - použití f jako příponu udávajících jednoduchou přesností
C4723|potenciální dělení hodnotou 0
C4724|potenciální mod hodnotou 0
C4725|instrukce mohou být nepřesné na některé Pentiums
C4757|dolní index je velké hodnoty bez znaménka, hodláte záporné konstanta?
C4772|#import odkazuje typ z chybějící knihovny typů; '*popis*se používá jako zástupný znak
C4792|Funkce '*funkce*' deklarované pomocí import systému a odkazované z nativního kódu; knihovny importu vyžaduje, aby propojení
C4794|segment proměnné místní úložiště vláken '*název*'se změnil z'*segment*'do'*segment*.
C4798|nativní kód generovaný pro funkci p kód '*název*' s obslužná rutina výjimky nebo unwind sémantiku
C4799|Funkce '*název*' nemá žádný EMMS instrukcí
C4803|'*deklarace*': metoda pro vyvolání obsahuje třídu jiného úložiště od události, se*deklarace*.
C4810|Hodnota – Direktiva pragma pack(show) == *číslo*
C4811|Hodnota – Direktiva pragma odpovídat (forScope, zobrazit) == *hodnota*
C4820|'*typ*': '*číslo*' bajtů odsazení přidat po *typ* '*typu*.
C4905|široké řetězcový literál přetypovat '*typu*.
C4906|řetězcový literál přetypovat '*typu*.
C4912|'*atribut*': atribut má undefined chování na vnořené UDT
C4916|aby bylo možné používat dispid '*typ*': je nutné zavést pomocí rozhraní
C4917|'*typ*': identifikátor GUID může být přidružen pouze třídy, rozhraní nebo obor názvů
C4918|'*znak*': neplatný znak v seznamu optimalizace – Direktiva pragma
C4920|výčet *název* člen *název*=*číslo* již projevuje ve výčtu *název* jako *název* = *číslo*
C4921|'*název*': hodnota atributu '*hodnotu*' by neměl být určen násobkem
C4925|'*deklarace*': dispinterface metodu nelze volat ze skriptu
C4926|'*deklarace*': symbol je již definován: atributy ignorovat
C4927|Neplatný převod; implicitně použilo více než jeden uživatelem definovaný převod
C4928|nelegální inicializace kopírování; implicitně použit více než jeden uživatelem definovaný převod
C4929|'*popis*': knihovny typů obsahuje sjednocení; ignoruje kvalifikátor 'embedded_idl –.
C4930|'*deklarace*': deklaraci není volaná funkce (byl definici proměnné určené?)
C4931|Nemůžeme se za předpokladu, že byl sestaven knihovny typů pro *číslo*-bit ukazatele
C4932|__identifier (*popis*) a __identifier (*popis*) jsou
C4934|'__delegate(multicast)' je zastaralý, použijte '__delegate' místo toho
C4935|specifikátor přístupu sestavení změnil z '*popis*.
C4944|'*název*': nelze importovat symbol '*zdroj*': jako*deklarace*' již existuje v aktuálním oboru
C4945|'*název*': nelze importovat symbol '*zdroj*': jako*deklarace*'již byla naimportována ze sestavení'*zdroj*.
C4946|reinterpret_cast – používá se mezi související třídy: '*deklarace*'a'*deklarace*.
C4995|'*název*': název byl označen jako zastaralý #pragma
C4996|'*problém*': *popis*
C4997|'*typ*': Třída typu coclass neimplementuje rozhraní modelu COM nebo pseudorozhraní
C4998|OČEKÁVÁ se nezdařilo: *popis*(*číslo*)

## <a name="see-also"></a>Viz také
[– Možnost kompilátoru /WV](../../build/reference/compiler-option-warning-level.md)
[upozornění kompilátoru, která jsou ve výchozím nastavení vypnuté](../../preprocessor/compiler-warnings-that-are-off-by-default.md)
[upozornění](../../preprocessor/warning.md)
