---
title: Upozornění kompilátoru podle verze kompilátoru
ms.date: 10/24/2018
helpviewer_keywords:
- warnings, by compiler version
- cl.exe compiler, setting warning options
ms.openlocfilehash: ae5d1957694abe09d1e04fba5ccfd2cd87d36940
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530179"
---
# <a name="compiler-warnings-by-compiler-version"></a>Upozornění kompilátoru podle verze kompilátoru

Kompilátor může potlačit upozornění, která byla zavedená po verzi určíte pomocí [/WV:](../../build/reference/compiler-option-warning-level.md) – možnost kompilátoru. To je užitečné při správě procesu sestavení při zavedení nové verze sady nástrojů a chcete dočasně potlačení nové upozornění. Tato možnost nepotlačuje nové chybové zprávy. Nedoporučujeme, potlačí všechna nová upozornění trvale! Doporučujeme vždy kompilaci na nejvyšší úrovni regulární upozornění __/W4__a odeberte __/WV:__ možnost ve vašem buildu co nejdříve.

Tyto verze kompilátoru zavedená nová upozornění:

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
| Visual C++ 2017 RTM | 19.10.25017.0 |
| Visual C++ 2017 verze 15.3 | 19.11.25506.0 |
| Visual C++ 2017 verze 15.5 | 19.12.25830.0 |
| Visual C++ 2017 verze 15.6 | 19.13.26128.0 |
| Visual C++ 2017 verze 15.7 | 19.14.26428.0 |
| Visual C++ 2017 verze 15.8 | 19.15.26726.0 |

Můžete zadat pouze hlavní číslo, číslo hlavní a dílčí nebo hlavní, vedlejší verzi a čísla do sestavení __/WV:__ možnost. Kompilátor oznámí všechna upozornění, které odpovídají verze, které začínat zadaným číslem a potlačí všechna upozornění pro větší než zadané číslo verze. Například __/Wv:17__ sestavy všech upozornění zavedená v rámci nebo před jakoukoli verzi nástroje Visual Studio 2012 a potlačí všechny upozornění zavedená jakékoli kompilátorem z Visual Studio 2013 (verzi 18) nebo novější. Potlačit upozornění zavedená v sadě Visual Studio 2015 update 2 a novější, je možné použít __/Wv:19.00.23506__. Použití __/Wv:19.11__ hlášení všechna upozornění zavedená v libovolné verzi sady Visual Studio před Visual Studio 2017 verze 15.5, ale potlačí upozornění zavedená v sadě Visual Studio 2017 verze 15.5 nebo novější.

V následujících oddílech najdete seznam upozornění zavedená ve všech verzích Visual C++, který můžete potlačit pomocí __/WV:__ – možnost kompilátoru. __/WV:__ možnost nelze potlačit upozornění, které nejsou uvedené, které jsou staršího data než zadanou verzí kompilátoru.

## <a name="warnings-introduced-in-visual-c-2017-version-158-compiler-version-1915267260"></a>Upozornění zavedená ve Visual C++ 2017 verze 15.8 (verze kompilátoru 19.15.26726.0)

Tato upozornění a všechna upozornění v pozdějších verzích jsou potlačeny pomocí možnosti kompilátoru __/Wv:19.14__.

|||
|-|-|
C5046|"*funkce*': typ zahrnující s vnitřním propojením není definovaný Symbol|

## <a name="warnings-introduced-in-visual-c-2017-version-157-compiler-version-1914264280"></a>Upozornění zavedená v sadě Visual C++ 2017 verze 15.7 (verze kompilátoru 19.14.26428.0)

Tato upozornění a všechna upozornění v pozdějších verzích jsou potlačeny pomocí možnosti kompilátoru __/Wv:19.13__.

|||
|-|-|
C4642|"*problém*': nelze importovat omezení pro obecný parametr"*parametr*.
C5045|Kompilátor vloží zmírnění hrozby Spectre pro zatížení paměti, pokud přepínač/qspectre zadané

## <a name="warnings-introduced-in-visual-c-2017-version-156-compiler-version-1913261280"></a>Upozornění zavedená v sadě Visual C++ 2017 verze 15.6 (verze kompilátoru 19.13.26128.0)

Tato upozornění a všechna upozornění v pozdějších verzích jsou potlačeny pomocí možnosti kompilátoru __/Wv:19.12__.

|||
|-|-|
C5044|Argument pro možnost příkazového řádku *možnost* odkazuje na cestu "*cesta*", která neexistuje

## <a name="warnings-introduced-in-visual-c-2017-version-155-compiler-version-1912258300"></a>Upozornění zavedená v sadě Visual C++ 2017 verze 15.5 (verze kompilátoru 19.12.25830.0)

Tato upozornění a všechna upozornění v pozdějších verzích jsou potlačeny pomocí možnosti kompilátoru __/Wv:19.11__.

|||
|-|-|
C4843|"*type1*': Obslužná rutina výjimky odkazu na pole nebo typ funkce není dostupná, použijte '*type2*' místo toho
C4844|"export module *module_name*;" je teď preferovanou syntaxí pro deklaraci rozhraní modulu
C5039|"*funkce*': ukazatel nebo odkaz na potenciální vyvolávací funkci předán do funkce extern C v - EHc. Pokud tato funkce vyvolá výjimku, může dojít k nedefinovanému chování.
C5040|Specifikace dynamických výjimek jsou platné jenom v C ++ 14 a dřívějších verzích; zpracuje jako noexcept(false).
C5041|"*definice*': definice mimo řádek pro statický datový člen constexpr nevyžaduje a je zastaralé v C ++ 17
C5042|"*deklarace*': deklarace funkcí v blokovém rozsahu nemůže být zadané"vložené"ve standardním jazyce C++; odeberte specifikátor inline.
C5043|"*specifikace*': specifikace výjimky se neshoduje s předchozí deklarací.

## <a name="warnings-introduced-in-visual-c-2017-version-153-compiler-version-1911255060"></a>Upozornění zavedená v sadě Visual C++ 2017 verze 15.3 (verze kompilátoru 19.11.25506.0)

Tato upozornění a všechna upozornění v pozdějších verzích jsou potlačeny pomocí možnosti kompilátoru __/Wv:19.10__.

|||
|-|-|
C4597|nedefinované chování: *popis*
C4604|"*typ*': předání argumentů hodnotou mezi nativním a spravovaným kódem vyžaduje platný kopírovací konstruktor. V opačném případě nedefinované chování za běhu
C4749|podmíněně podporováno: *popis*
C4768|atributy __declspec před specifikací propojení se ignorují.
C4834|zahazuje se návratová hodnota funkce s atributem nodiscard.
C4841|nestandardní rozšíření: *rozšíření*
C4842|není zaručeno, že výsledek offsetof použitý pro typ pomocí vícenásobného dědění bude konzistentní napříč verzemi kompilátoru.
C4869|'nodiscard' jde použít jenom pro třídy, výčty a funkcí s neprázdným návratovým typem
C5033|"*třídy úložiště*' již není podporovanou třídou úložiště.
C5034|použití vnitřních "*vnitřní*" způsobí, že funkce *funkce* se zkompiluje jako kód hosta.
C5035|použití funkce '*funkce*"způsobí, že funkce *funkce* se zkompiluje jako kód hosta.
C5036|převod ukazatele funkci VarArgs při kompilování x86arm64 "*type1*"do"*type2*.
C5037|"*členské funkce*': definice mimo řádek člena šablony třídy nemůže mít výchozí argumenty
C5038|datový člen "*member1*'bude inicializován po datovém členu'*člen2*.

## <a name="warnings-introduced-in-visual-c-2017-rtm-compiler-version-1910250170"></a>Upozornění zavedená ve Visual C++ 2017 RTM (verze kompilátoru 19.10.25017.0)

Tato upozornění a všechna upozornění v pozdějších verzích jsou potlačeny pomocí možnosti kompilátoru __/Wv:19.00__.

|||
|-|-|
C4468|'fallthrough': atribut musí následovat popisek případu nebo výchozí popisek.
C4698|"*funkce*" je pro účely vyhodnocení pouze a může změnit v budoucích aktualizacích nebo odebrání.
C4839|nestandardní použití třídy*třídy*"jako argumentu variadické funkce
C4840|nepřenositelné použití třídy*třídy*"jako argumentu variadické funkce

## <a name="warnings-introduced-in-visual-c-2015-update-3-compiler-version-1900242151"></a>Upozornění zavedená ve Visual C++ 2015 Update 3 (verze kompilátoru 19.00.24215.1)

Tato upozornění a všechna upozornění v pozdějších verzích jsou potlačeny pomocí možnosti kompilátoru __/Wv:19.00.23918__.

|||
|-|-|
C4467|používání atributů ATL je zastaralé.
C4596|"*název*': Neplatný kvalifikovaný název v deklaraci člena
C4598|"#include \< *záhlaví*\>': číslo hlavičky *číslo* v *zdroje* neodpovídá *zdroj* v daném okamžiku pozice
C4599|"*argument*': *zdroj* číslo argumentu *číslo* neodpovídá *zdroje*

## <a name="warnings-introduced-in-visual-c-2015-update-2-compiler-version-1900239180"></a>Upozornění zavedená ve Visual C++ 2015 Update 2 (verze kompilátoru 19.00.23918.0)

Tato upozornění a všechna upozornění v pozdějších verzích jsou potlačeny pomocí možnosti kompilátoru __/Wv:19.00.23506__.

|||
|-|-|
C4466|Nebylo možné provést elizi haldy
C4595|"*třídy*': bez operátoru new nebo delete funkce nemůže být deklarovaná jako inline.
C4828|Tento soubor obsahuje znak začínající na posunu 0 x*hodnotu* , který je v aktuální zdrojové znakové sadě neplatný (znaková stránka *číslo*).
C4868|Kompilátor nemůže vynutit pořadí vyhodnocování zleva doprava v seznamu inicializátorů v závorkách

## <a name="warnings-introduced-in-visual-c-2015-update-1-compiler-version-1900235060"></a>Upozornění zavedená ve Visual C++ 2015 Update 1 (verze kompilátoru 19.00.23506.0)

Tato upozornění a všechna upozornění v pozdějších verzích jsou potlačeny pomocí možnosti kompilátoru __/Wv:19.00.23026__.

|||
|-|-|
C4426|příznaky optimalizace se po včetně záhlaví, může být #pragma optimize().
C4654|Kód umístěný před vložení předkompilované hlavičky řádku budou ignorovány. Přidejte kód do předkompilované hlavičky.
C5031|#pragma warning(pop): pravděpodobně o neshodu, stav automaticky otevíraného upozornění vložil do jiného souboru
C5032|zjištěna #pragma warning(push) bez odpovídajícího příkazu #pragma warning(pop)

## <a name="warnings-introduced-in-visual-c-2015-rtm-compiler-version-1900230260"></a>Upozornění zavedená ve Visual C++ 2015 RTM (verze kompilátoru 19.00.23026.0)

Tato upozornění a všechna upozornění v pozdějších verzích jsou potlačeny pomocí možnosti kompilátoru __/WV: 18__.

|||
|-|-|
C4427|"*chyba*': přetečení v dělení konstantou; nedefinované chování
C4438|"*typ*': nejde volat bezpečně / await: clrcompat režimu. Pokud se*typ*"volání do modulu CLR může způsobit poškození hlavičky CLR
C4455|' operator *název*': identifikátory přípon literálů, které nezačínají podtržítkem jsou vyhrazené.
C4456|deklarace "*název*' skryje předchozí místní deklaraci
C4457|deklarace "*název*' skryje parametr funkce
C4458|deklarace "*název*' skryje člen třídy
C4459|deklarace "*název*' skryje globální deklaraci
C4462|"*typ*': Nelze určit identifikátor GUID typu. Program může při běhu selhat.
C4463|přetečení; přiřazení *hodnotu* bitové pole, které můžou ukládat jenom hodnoty z *hodnotu* k *hodnota*
C4473|"*funkce*': není dostatečný počet argumentů předaný pro formátovací řetězec
C4474|"*funkce*': předáno příliš mnoho argumentů pro formátovací řetězec
C4475|"*funkce*': modifikátor délky '*modifikátor*'nelze použít se znakem pole typů'*znak*" ve specifikátoru formátu
C4476|"*funkce*': Neznámý znak pole typů '*znak*" ve specifikátoru formátu
C4477|"*funkce*': řetězec formátu"*řetězec*"vyžaduje argument typu"*typ*", ale variadický argument *číslo* má typ"*typ*.
C4478|"*funkce*': nejde směšovat poziční a nepoziční zástupné symboly ve stejném formátovacím řetězci
C4494|"*typ*': __declspec(Allocator) se ignoruje protože návratový typ funkce není ukazatel nebo odkaz
C4495|používá se nestandardní rozšíření: __super: nahraďte explicitním názvem základní třídy
C4496|používá se nestandardní rozšíření 'for each' používá: nahraďte rozsahové pro příkaz
C4497|používá se nestandardní rozšíření 'sealed': nahraďte hodnotou final.
C4498|používá se nestandardní rozšíření: '*rozšíření*.
C4499|"*specializace*': explicitní specializace nemůže mít třídu úložiště (ignorováno)
C4576|Typ v uvozovkách následovaný seznamem inicializátorů je nestandardní explicitní syntaxe převodu typu
C4577|použít bez výjimky režimu; zpracování noexcept ukončení při výjimce není zaručena. Zadejte/EHsc
C4578|'abs': převod z '*typ*"do"*typ*", může dojít ke ztrátě dat (chtěli jste volat"*název*"nebo #include \<cmath >?)
C4582|"*typ*': konstruktor se nevolá implicitně
C4583|"*typ*': destructor se nevolá implicitně
C4587|"*typ*': Změna chování: konstruktor se nevolá implicitně už
C4588|"*typ*': Změna chování: destruktor je už nevolá implicitně
C4589|Konstruktor abstraktní třídy*typ*"ignoruje inicializátor virtuální základní třídy"*typ*.
C4591|'constexpr' se limit hloubky volání *číslo* překročena (/ constexpr: Depth\<číslo >)
C4592|"*typ*': symbol se dynamicky inicializuje (omezení implementace)
C4593|"*typ*': limit kroků vyhodnocení volání 'constexpr' z *hodnotu* překročil; použijte steps\<číslo > o zvýšení limitu
C4647|Změna chování: __is_pod (*typ*) má jinou hodnotu v předchozích verzích
C4648|standardní atribut "carries_dependency" se ignoruje.
C4649|atributy se ignorují. v tomto kontextu
C4753|Nejde najít hranice pro ukazatel; Vnitřní funkce MPX se ignoruje
C4771|Hranice musí být vytvořené pomocí jednoduchého ukazatele; Vnitřní funkce MPX se ignoruje
C4774|"*popis*': formátovací řetězec očekávaný v argumentu *číslo* není řetězcový literál
C4775|používá se nestandardní rozšíření použité ve formátovacím řetězci "*řetězec*"funkce"*funkce*.
C4776|' %*znak*"není povolena ve formátovacím řetězci funkce"*funkce*.
C4777|"*popis*': řetězec formátu"*řetězec*"vyžaduje argument typu"*typ*", ale variadický argument *číslo* má typ"*typ*.
C4778|"*popis*': neukončený formátovací řetězec"*řetězec*.
C4838|Převod z '*typ*"do"*typ*' vyžaduje zúžení převodu
C5022|"*typ*': zadaných víc konstruktorů move
C5023|"*typ*': zadaných víc operátorů přiřazení přesunutí
C5024|"*deklarace*': přesunout konstruktor byl implicitně definovaný jako odstraněný
C5025|"*deklarace*': Přesuňte operátor přiřazení je implicitně definovaný jako odstraněný
C5026|"*typ*': přesunout konstruktor byl implicitně definovaný jako odstraněný
C5027|"*typ*': Přesuňte operátor přiřazení je implicitně definovaný jako odstraněný
C5028|"*název*': zarovnání zadané před deklarací (*číslo*) není zadané v definici
C5029|používá se nestandardní rozšíření: atributy zarovnání v C++ použít pro proměnné, datové členy a pouze typy značek
C5030|atribut '*atribut*' nebyla rozpoznána

## <a name="warnings-introduced-in-visual-c-2013-compiler-version-1800210051"></a>Upozornění zavedená v aplikaci Visual C++ 2013 (verzi kompilátoru 18.00.21005.1)

Tato upozornění a všechna upozornění v pozdějších verzích jsou potlačeny pomocí možnosti kompilátoru __/Wv:17__.

|||
|-|-|
C4301|"*typ*': přepisující virtuální funkce jenom se liší od"*deklarace*"v kvalifikátoru const/volatile
C4316|"*typ*': objekt přidělený do haldy nemusí být zarovnáním *číslo*
C4380|"*typ*': konstruktor default nemůže být zastaralý.
C4388|"*token*': podepsané/unsigned – neshoda
C4423|'std::bad_alloc': zachytí se třídou ("*typ*") na řádku *číslo*
C4424|zachycení pro "*typ*"před"*typ*' na řádku *číslo*; nepředvídatelné chování může dojít, pokud" předcházelo:
C4425|Poznámku SAL nejde použít u '...'
C4464|relativní cestu zahrnutí obsahuje '..'
C4575|"__vectorcall" kompatibilní s "/ clr' možnost: převod na: __stdcall.
C4609|"*typ*"odvozuje od výchozího rozhraní"*typ*'na typ'*typ*". Použít jiné výchozí rozhraní pro "*typ*", nebo zrušit vztah základní/odvozené.
C4754|Pravidla převodu pro aritmetické operace v porovnání v: *popis*(*číslo*) znamená, že jednu větev nejde provést. Přetypování "*typ*"do"*typ*" (nebo podobný typ o *číslo* bajtů).
C4755|Pravidla převodu pro aritmetické operace v porovnání v: *popis*(*číslo*) znamená, že jednu větev nejde provést ve vložené funkci. Přetypování "*typ*"do"*typ*" (nebo podobný typ o *číslo* bajtů).
C4767|Název oddílu "*název*" je delší než 8 znaků a bude zkrácen linkerem.
C4770|částečně ověřený výčet "*název*se používá jako index.
C4827|Veřejné metody "ToString" 0 parametrů by měla být označena jako virtuální a přepsání
C4882|předání funktory s operátory volání nekonstantní do: concurrency::parallel_for_each je zastaralé.
C4973|"*typ*': označené jako zastaralé
C4974|"*typ*': označené jako zastaralé
C4981|Warbird: funkce '*deklarace*"označená jako __forceinline není vložená, protože obsahuje sémantiku výjimky.
C4990|Warbird: *zprávy*
C4991|Warbird: funkce '*deklarace*"označená jako __forceinline není vložená, protože úroveň ochrany inlinee je vyšší než nadřazené
C4992|Warbird: funkce '*deklarace*"označená jako __forceinline není vložená, protože obsahuje vložené sestavení, které nejde chránit.

## <a name="warnings-introduced-in-visual-c-2012-compiler-version-1700511061"></a>Upozornění zavedená v aplikaci Visual C++ 2012 (verze kompilátoru 17.00.51106.1)

Tato upozornění a všechna upozornění v pozdějších verzích jsou potlačeny pomocí možnosti kompilátoru __/Wv:16__.

|||
|-|-|
C4330|atribut '*atribut*"pro oddíl'*části*" ignorováno
C4415|duplicate __declspec(code_seg('*name*'))
C4416|__declspec(code_seg(...)) obsahuje prázdný řetězec: ignoruje
C4417|explicitní vytváření instancí šablon nemůže mít __declspec(code_seg(...)): ignoruje
C4418|__declspec(code_seg(...)) se pro výčet ignoruje.
C4419|"*název*'nemá žádný vliv při použití u privátního ref class'*typ*".
C4435|"*typ*': rozložení objektu pod: / vd2 se změní z důvodu virtuální base '*typ*.
C4436|přetypování dynamic_cast z virtuální base '*typ*"do"*typ*"v konstruktoru nebo destruktoru by mohlo selhat s částečně vytvořeným objektem.
C4437|přetypování dynamic_cast z virtuální base '*typ*"do"*typ*' může v některých kontextech selhat
C4443|Parametr očekávané pragma bude mít '0', '1' nebo '2'
C4446|"*typ*': nelze mapovat člen"*název*"na tento typ, z důvodu konfliktu s názvem typu. Tato metoda se přejmenovala na "*název*.
C4447|"hlavní" podpis nalezen bez model vláken. Zvažte použití ' int main (Platform::Array\<Platform::String ^ > ^ args) ".
C4448|"*typ*' nemá v metadatech zadané výchozí rozhraní. Vybere: "*typ*", která může při běhu selhat.
C4449|"*typ*" nezapečetěný typ musí být označené jako [WebHostHidden].
C4450|"*typ*"musí být označené jako [WebHostHidden]' protože se odvozuje od"*typ*.
C4451|"*typ*': použití třídy ref class*typ*" uvnitř tohoto kontextu může vést k neplatnému zařazování objektu napříč kontexty
C4452|"*typ*': typ public nemůže být v globálním oboru. Musí být v oboru názvů, který je podřízený názvu výstupního souboru .winmd.
C4453|"*typ*': Typ [WebHostHidden] by neměl používat na publikované ploše typu public, který není [WebHostHidden].
C4454|"*typ*" je přetížené o větší než počet vstupních parametrů bez nastavení [defaultoverload] zadaná. Výběr "*deklarace*' jako výchozí přetížení
C4471|"*název*': Dopředná deklarace výčtu bez oboru musí mít základní typ (předpokládá se int)
C4472|"*název*' je nativní výčet: přidejte specifikátor přístupu (private/public) Chcete-li deklarovat výčet spravované/WinRT
C4492|"*typ*': odpovídá metodě base ref class '*typ*", ale není označené jako override.
C4493|odstranit výraz nemá žádný účinek, jako je destruktor "*typ*' nemá přístupnost public.
C4585|"*typ*': A WinRT musí být buď zapečetěná třída public ref class nebo odvozovat od existující nezapečetěné třídy
C4586|"*typ*': veřejný typ nemůže být deklarovaný v nejvyšší úrovni obor názvů s názvem"Windows"
C4695|#pragma execution_character_set: "*argument*' není podporovaný argument: momentálně se podporuje jenom"UTF-8' je podporován.
C4703|potenciálně neinicializovaná lokální proměnná ukazatele "*název*" použít
C4728|/ Yl-se ignoruje, protože je vyžadován odkaz na soubor PCH
C4745|přístup typu "*název*" nelze kvůli jeho velikosti dodržet.
C4746|přístup typu "*název*' / volatile:\<iso\|ms > nastavení; zvažte použití vnitřních funkcí Using __iso_volatile_load/store
C4872|číslo s plovoucí čárkou bodu dělení nulou zjistil při kompilování grafu volání pro: concurrency::parallel_for_each: "*popis*.
C4880|přetypování z "*typ*"do"*typ*': přetypování konstantnosti z ukazatele nebo odkazu může vést k nedefinovanému chování ve funkci s omezením pomocí specifikátoru amp
C4881|konstruktor nebo destruktor se nebudou volat pro proměnnou tile_static "*typ*.
C4966|"*popis*' má poznámku __code_seg s nepodporovaným názvem segmentu, ignorovat poznámky
C4988|"*typ*': proměnná deklarována mimo rozsah třídy a funkce
C4989|"*popis*': typ má konfliktní definice.

## <a name="warnings-introduced-in-visual-c-2010-compiler-version-16004021901"></a>Upozornění zavedená ve Visual C++ 2010 (verze kompilátoru 16.00.40219.01)

Tato upozornění a všechna upozornění v pozdějších verzích jsou potlačeny pomocí možnosti kompilátoru __/Wv:15__.

|||
|-|-|
C4352|"*název*': vnitřní funkce už je definovaná
C4573|použití "*typ*' vyžaduje, aby kompilátor zachytil 'this' ale aktuální výchozí režim zachycování to neumožňuje
C4574|"*název*'je definován jako ' 0': chtěli jste použít ' #if *název*"?
C4689|"*znak*': v #pragma detect_mismatch je nepodporovaný znak; ignoruje #pragma
C4751|/ arch AVX se nevztahuje na Streaming SIMD Extensions Intel(R), která jsou ve vloženém kódu ASM
C4752|Najít Intel(R) Advanced Vector Extensions; Zvažte možnost použít příslušný/arch AVX
C4837|zjistil se trigraph: "?? *znak*"nahrazuje"*znak*.
C4986|"*deklarace*': specifikace výjimky se neshoduje s předchozí deklarací.
C4987|použito nestandardní rozšíření: 'throw (...)'

## <a name="warnings-introduced-in-visual-c-2008-compiler-version-15002102208"></a>Upozornění zavedená ve Visual C++ 2008 (verze kompilátoru 15.00.21022.08)

Tato upozornění a všechna upozornění v pozdějších verzích jsou potlačeny pomocí možnosti kompilátoru __/Wv:14__.

|||
|-|-|
C4396|"*typ*': specifikátor inline nejde použít, když deklarace friend odkazuje na specializaci šablony funkce
C4413|"*deklarace*': referenční člen je inicializovaný jako dočasný, který se po ukončení konstruktoru nezachová
C4491|"*popis*': má neplatný formát verze IDL
C4603|"*název*': Makro není definované nebo se definice liší od použití předkompilované hlavičky
C4627|"*popis*': při hledání použití předkompilované hlavičky přeskočen
C4750|"*popis*': funkce s: _alloca() je vložená do smyčky
C4910|"*typ*": "__declspec(dllexport)" a "externí" nejsou pro explicitní vytváření instancí
C4985|"*deklarace*': neexistují atributy pro předchozí deklaraci.

## <a name="warnings-introduced-in-visual-c-2005-compiler-version-140050727762"></a>Upozornění zavedená ve Visual C++ 2005 (verze kompilátoru 14.00.50727.762)

Tato upozornění a všechna upozornění v pozdějších verzích jsou potlačeny pomocí možnosti kompilátoru __/Wv:13__.

|||
|-|-|
C4000|NEZNÁMÉ upozornění Zvolte prosím příkaz technická podpora v nabídce Nápověda pro Visual C++, nebo otevřete soubor nápovědy technické podpory pro další informace
C4272|"*typ*": je označené jako __declspec(dllimport); při importu funkce musí specifikovat nativní konvence volání.
C4333|"*výraz*': posunutí doprava o moc velkou hodnotu, ztráta dat
C4334|"*výraz*': výsledek 32bitového posunu se implicitně převedl na 64 bitů (byl 64bitový posun určený?)
C4335|Zjistil se formát souborů Mac: převeďte prosím zdrojový soubor do formátu DOS nebo UNIX
C4342|Změna chování: "*typ*" volá se, ale operátor členu byl zavolán v předchozích verzích
C4350|Změna chování: "*deklarace*"volá namísto"*deklarace*.
C4357|Param array argument nalezena v seznamu formálních argumentů pro delegáta '*deklarace*"ignoruje při generování"*typ*.
C4358|"*výraz*': návratový typ kombinovaných delegátů není"void"; vrácená hodnota není definována
C4359|"*typ*': specifikátor zarovnání je menší než skutečné zarovnání (*číslo*) a budou ignorovány.
C4362|"*typ*': modul CLR nepodporuje zarovnání větší než 8 bajtů.
C4364|#using pro sestavení '*název*"dřív zjištěné v: *popis*(*číslo*) bez atributu as_friend; atribut as_friend Nepoužito
C4365|"*výraz*': převod z '*typ*"do"*typ*", podepsaný/unsigned – neshoda
C4366|Výsledek unární "*operátor*" operátor může být zarovnaný.
C4367|Převod z '*typ*"do"*typ*' může způsobit výjimku kvůli neshodě datového typu
C4368|nelze definovat '*název*'jako člen spravovaného'*typ*': smíšené typy nejsou podporovány.
C4369|"*typ*': hodnota výčtu '*číslo*"nemůže být reprezentovaná jako"*typ*', hodnota je'*číslo*"
C4374|"*deklarace*': metoda rozhraní se nebude implementovat nevirtuální metody"*deklarace*.
C4375|oprávnění neveřejné metody "*deklarace*"nepřepisuje"*deklarace*.
C4376|přístup k specifikátor "*specifikátor*:" už není podporovaná: použijte "*specifikátor*:" místo
C4377|nativní typy jsou privátní ve výchozím nastavení; -d1PrivateNativeTypes je zastaralá.
C4378|Musí se získat ukazatele funkce pro spouštění inicializačních; Vezměte v úvahu System::ModuleHandle::ResolveMethodHandle
C4379|Verze *verze* common language runtime nepodporuje tento kompilátor. Pomocí této verze může vést k neočekávaným výsledkům
C4381|"*deklarace*': metoda rozhraní se nebude implementovat neveřejnou metodu '*deklarace*.
C4382|vyvolání "*typ*': typ s destruktorem __clrcall nebo kopírovacím konstuktorem se dá zachytit jedině v/CLR: pure modulu
C4383|"*typ*': může změnit význam zrušení odkazu na popisovač, pokud uživatelem definované"*operátor*' existuje; zapište operátor jako statickou funkci k explicitnímu operand – operátor
C4384|#pragma "*směrnice*' by měla sloužit pouze u globálního rozsahu
C4393|"*typ*': const nemá žádný vliv *popis* datový člen; ignorováno
C4394|"*typ*': symbol na úrovni appdomain by neměl být označeny atributem __declspec (*hodnotu*)
C4395|"*typ*': členská funkce se bude volat pro kopii datového členu initonly"*typ*.
C4397|DefaultCharSetAttribute se ignoruje.
C4398|"*typ*': globální objekt na úrovni jednotlivého procesu nemusí fungovat správně s více objektů třídy appdomains; zvažte použití možnosti __declspec(appdomain)
C4399|"*typ*': symbol na úrovni jednotlivého procesu nesmí být označené __declspec (*hodnotu*) při kompilaci s parametrem/CLR: pure
C4400|"*typ*': kvalifikátory const/volatile pro tento typ nejsou podporované
C4412|"*deklarace*': podpis funkce obsahuje typ"*typ*'; Jsou objekty C++ není bezpečné předávat mezi čistým kódem a kombinovaným nebo nativním kódem.
C4429|je to možné neúplný nebo nesprávně vytvořený universal-character-name
C4430|chybějící specifikátor typu: předpokládá se int Poznámka: C++ nepodporuje typ default int.
C4431|chybějící specifikátor typu: předpokládá se int Poznámka: C již nepodporuje výchozí int.
C4434|Statický konstruktor musí mít přístupnost private; Změna na soukromý přístup
C4439|"*typ*': definice funkce se spravovaným typem v podpisu musí mít konvenci volání __clrcall
C4441|konvence volání '*konvence*se ignoruje; "*konvence*' místo toho použita
C4445|"*deklarace*': v typu spravované/WinRT virtuální metoda nemůže být privátní
C4460|CLR/WinRT operátor "*typ*', má parametr předaný odkazem. CLR/WinRT operátor "*operátor*"má odlišnou sémantiku než operátor C++"*operátor*", nechtěli jste předat hodnotu v?
C4461|"*typ*': Tato třída má finalizační metodu '! *typ*", ale žádný destruktor ' ~*typ*.
C4470|direktivy pragma ovládacího prvku s plovoucí desetinnou čárkou ignorovány pod parametrem/CLR
C4480|používá se nestandardní rozšíření: zadání podkladového typu pro výčet "*typ*.
C4481|používá se nestandardní rozšíření: specifikátor override '*specifikátor*.
C4482|používá se nestandardní rozšíření: výčtu '*typ*"používat v kvalifikovaném názvu
C4483|Chyba syntaxe: Očekávalo se klíčové slovo jazyka C++
C4484|"*typ*': odpovídá metodě base ref class '*typ*", není ale označené jako 'virtuální', 'new' nebo 'override'; předpokládá se 'new' (tzn. ne virtual)
C4485|"*typ*': odpovídá metodě base ref class '*typ*", ale není označené jako "nové" nebo "override"; předpokládá se 'new. (a 'virtual')
C4486|"*typ*': virtuální metoda private třídy ref class nebo value class by měla být označená jako sealed.
C4487|"*typ*': shody zděděné nevirtuální metody"*typ*", ale není explicitně označené jako"nové"
C4488|"*typ*': vyžaduje"*– klíčové slovo*'implementovat metodu rozhraní – klíčové slovo'*typ*"
C4489|"*– klíčové slovo*': není povolené pro metodu rozhraní"*název*"; přepsání specifikátory jsou povolené jenom pro metody třídy ref class a value
C4490|"*– klíčové slovo*': nesprávné použití specifikátoru přepsání; "*typ*' neodpovídá metodě base ref class
C4538|"*typ*': kvalifikátory const/volatile pro tento typ nejsou podporované
C4559|"*typ*': předefinování; zisky __declspec – funkce (*hodnotu*)
C4565|"*typ*': předefinování; symbol se předtím deklaroval s: __declspec (*hodnotu*)
C4566|znak reprezentován universal-character-name "*znak*' nemůže být reprezentovaný v aktuální znakové stránce (*číslo*)
C4568|"*typ*': podpisu explicitního přepsání neodpovídají žádné členy
C4569|"*typ*': podpisu explicitního přepsání neodpovídají žádné členy
C4570|"*typ*': není explicitně deklarované jako abstraktní, ale má abstraktní funkce
C4571|Informační: sémantika catch(...) se od verze Visual C++ 7.1; změnila strukturované výjimky (SEH) už se nezachycují.
C4572|Atribut [ParamArray] je zastaralá pod parametrem/CLR, použijte tři tečky. místo toho
C4580|[attribute] je zastaralá; Místo toho zadejte *zadané*atribut jako základní třída
C4581|zastaralé chování: ' "*název*" "nahradit"*název*"atributu procesu
C4606|#pragma warning: "*číslo*se ignoruje; Upozornění analýzy kódu nejsou přidružená k úrovním upozornění
C4631|MSXML nebo XPath není k dispozici, dokument XML, který nezpracují se komentáře. *Popis*
C4632|Komentář k dokumentu XML: *popis* -přístup byl odepřen: *popis*
C4633|Komentář k dokumentu XML*popis*: Chyba: *popis*
C4634|Komentář k dokumentu XML*popis*: nelze použít: *popis*
C4635|Komentář k dokumentu XML*popis*: chybně vytvořený kód XML: *popis*
C4636|Komentář k dokumentu XML*popis*: značka vyžaduje neprázdný "*popis*" atribut.
C4637|Komentář k dokumentu XML*popis*: \<zahrnout > značky zahozeny. *Popis*
C4638|Komentář k dokumentu XML*popis*: odkaz na neznámý symbol "*popis*".
C4639|Chyba MSXML; dokumentu XML, který nezpracují se komentáře. *Popis*
C4641|Komentář k dokumentu XML má nejednoznačný křížový odkaz:
C4678|Základní třída*deklarace*'je méně dostupný než'*název*.
C4679|"*popis*': nepovedlo se naimportovat člen
C4687|"*typ*': zapečetěná abstraktní třída nemůže implementovat rozhraní"*typ*.
C4688|"*název*': seznam omezení obsahuje typ sestavení private '*deklarace*.
C4690|\[ emitidl (pop)]: Další POP než push
C4691|"*typ*': se očekával odkazovaný typ v bez odkazů *modulu* "*popis*', typ definovaný v aktuální překladové jednotce místo toho použita
C4692|"*název*': podpis nesoukromého členu obsahuje sestavení privátního nativního typu '*deklarace*.
C4693|"*typ*': zapečetěná abstraktní třída nemůže mít žádné členy instancí*název*.
C4694|"*typ*': zapečetěná abstraktní třída nemůže mít je třídou base*typ*.
C4720|sestavy assembleru vloženého kódu v řádku: '*popis*.
C4721|"*popis*': není k dispozici jako vnitřní
C4722|"*popis*': destruktor nikdy nevrací potenciální nevrácená paměť
C4726|ARM arch4/4T podporuje jenom "\<cpsr_f > nebo \<spsr_f >' s okamžitou hodnotou
C4727|Soubor PCH s názvem *název* se stejným časovým razítkem se našel v *název* a *název*.  Pomocí první soubor PCH.
C4729|upozornění založená na funkce je moc velká pro graf toku
C4730|"*popis*': směšování výrazů _m64 a plovoucí desetinná čárka výrazy mohou způsobit nesprávný kód
C4731|"*popis*': registr ukazatelů rámců"*zaregistrovat*"upravil kód vloženého sestavení
C4732|vnitřní "*vnitřní*" není v této architektuře podporovaný.
C4733|Vložené asm přiřazení 'FS:0': není zaregistrovaný jako bezpečná obslužná rutina
C4734|Více než 64 kB čísla řádků COFF ladění oddíl informací o; Zastavte emitování čísel řádků ladění COFF pro modul '*modulu*.
C4738|ukládání 32bitového plovoucího výsledku do paměti, možná ztráta
C4739|odkaz na proměnnou "*proměnnou*' překračuje její prostor úložiště.
C4740|Flow nebo z vloženého kódu asm potlačuje globální optimalizaci.
C4742|"*proměnnou*"má jiné zarovnání v"*umístění*"a"*umístění*': *číslo* a *číslo*
C4743|"*název*"má jinou velikost v"*umístění*"a"*umístění*': *číslo* a *číslo* bajtů
C4744|"*název*"má jiný typ v"*umístění*"a"*umístění*": "*typ*"a"*typ*.
C4747|Volání spravované '*typ*': nastavený zámek zavaděče, včetně vstupního bodu DLL a volání dosáhlo ze vstupního bodu DLL se možná nespustí spravovaný kód
C4761|Neshoda celočíselné velikosti v argumentu; Zadaný převod.
C4764|Nelze zarovnat objekty catch na hodnotu větší než 16 bajtů.
C4788|"*identifikátor*': identifikátor se zkrátil na"*číslo*"znaky
C4789|vyrovnávací paměť "*název*" velikosti *číslo* bajtů bude mít přeběhnutí; *číslo* bajtů se zapíše s posunem *číslo*
C4801|Vrácení podle odkazu není možné ověřit: *popis*
C4819|Tento soubor obsahuje znak, který nemůže být reprezentovaný v aktuální znakové stránce (*číslo*). Uložte soubor ve formátu Unicode, aby se zabránilo ztrátě dat.
C4826|Převod z '*typ*"do"*typ*"je rozšířen o znaménko. To může způsobit neočekávané chování za běhu.
C4829|Potenciálně nesprávné parametry pro funkci main. Vezměte v úvahu "int main (Platform::Array\<Platform::String ^ > ^ argv).
C4835|"*typ*': inicializátor pro exportovaná data se nespustí, dokud se v hostitelském sestavení nejdřív nespustí spravovaný kód
C4867|"*typ*': nestandardní syntaxe; pomocí '&' vytvořte ukazatel na člena
C4936|Tato možnost __declspec je podporovaná jenom při kompilaci s parametrem/CLR nebo/CLR: pure
C4937|"*název*"a"*název*jsou nejde rozlišit jako argumenty, které mají*možnost*.
C4938|"*typ*': plovoucího bodu redukční proměnná může způsobit nekonzistentní výsledky v/FP: strict nebo #pragma fenv_access
C4939|#pragma vtordisp je zastaralá a v příští verzi Visual C++ se odebere
C4947|"*typ*': označené jako zastaralé
C4949|direktivy pragma "spravované" a 'nespravované' mají smysl jenom při kompilaci s "/ clr [: možnost]"
C4950|"*typ*': označené jako zastaralé
C4955|"*popis*': import se ignoroval; už je naimportované z:"*zdroj*.
C4956|"*typ*': Tento typ není ověřitelný
C4957|"*výraz*': explicitní přetypování z typu '*typ*"do"*typ*" nejde ověřit
C4958|"*výraz*': není možné ověřit aritmetiku ukazatele
C4959|nejde definovat *třídy* "*typ*" v/CLR: safe vzhledem k tomu, že přístup k jeho členům vrací neověřitelný kód
C4960|"*popis*" je moc velké, aby se dalo Profilovat.
C4961|Žádná data profilu se nesloučila do:*umístění*", optimalizace na základě profilu zakázáno
C4962|"*popis*': profilováním řízené optimalizace zakázány, protože optimalizace způsobily nekonzistenci dat profilu
C4963|"*popis*': nenašla se žádná data profilu; jiné parametry kompilátoru v instrumentovaném buildu
C4964|Nebyly zadány žádné možnosti optimalizace; informace o profilu se nebudou shromažďovat.
C4965|implicitní pole celé číslo 0; Použijte nullptr nebo explicitní přetypování.
C4970|Konstruktor Delegate: cílový objekt ignoruje od "*deklarace*" je statická
C4971|Pořadí argumentů: \<cílový objekt >, \<cílová funkce > pro konstruktor delegate je zastaralé, použijte \<cílová funkce >, \<cílový objekt >
C4972|Přímá úprava nebo zpracování výsledku operace unbox jako l-hodnota se nelze ověřit

## <a name="warnings-introduced-in-visual-c-2003-compiler-version-13103077"></a>Upozornění zavedená v jazyce Visual C++ 2003 (verze kompilátoru 13.10.3077)

Tato upozornění a všechna upozornění v pozdějších verzích jsou potlačeny pomocí možnosti kompilátoru __/Wv:13.00.9466__.

|||
|-|-|
C4343|#pragma optimize (*popis*, vypnuto) přepíše/og – možnost
C4344|Změna chování: použití výsledků šablony explicitní argumenty při volání funkce "*deklarace*.
C4346|"*typ*': závislý název není typ
C4348|"*deklarace*': předefinování výchozího parametru: Parametr *číslo*
C4356|"*typ*': Statický datový člen nejde inicializovat prostřednictvím odvozené třídy
C4408|Anonymní *struktura* nedeklarovalo žádné datové členy
C4544|"*deklarace*': výchozí argument šablony pro tuto deklaraci šablony ignoruje.
C4545|výraz před čárkou vyhodnocuje na funkci, která nemá k dispozici seznam argumentů
C4546|volání funkce před čárkou nemá seznamu argumentů
C4547|"*výraz*': operátor před čárkou nemá žádný vliv; očekával se operátor s vedlejším účinkem
C4548|výraz před čárkou nemá žádný vliv; očekávaný výraz s vedlejším účinkem
C4549|"*výraz*': operátor před čárkou nemá žádný vliv; nechtěli jste použít '*výraz*"?
C4628|spřežky nejsou podporovány se -Ze. Posloupnosti znaků "*pořadí*'není interpretována jako alternativní token pro'*token*.
C4629|použít digraph, sekvence znaků '*pořadí*"interpretován jako token"*token*"(Pokud ne, co jste zamýšleli vložit mezi oba znaky mezeru)
C4671|"*popis*': kopírovací konstuktor je nedostupný
C4676|"*popis*': destruktor je nedostupný
C4677|"*název*': podpis nesoukromého členu obsahuje typ sestavení private '*deklarace*.
C4686|"*typ*': možné změny v chování, změna ve vrácení konvence volání
C4812|zastaralý styl deklarace: použijte "*typ*::*název*' místo toho
C4813|"*typ*': funkce friend lokální třídy musí mít byla deklarována
C4821|Nepovedlo se zjistit typ kódování Unicode, uložte prosím soubor s podpisem (BOM)
C4822|"*typ*': členská funkce lokální třídy nemá tělo.
C4823|"*typ*': používá ukazatele Připnutí ale unwind není povolená sémantika. Zvažte použití možnosti/EHa
C4913|uživatel definovaný binární operátor ',' existuje, ale přetížení nemohlo převést všechny operandy, předdefinovaný binární operátor ',' používá
C4948|Typ vrácené hodnoty '*deklarace*"se neshoduje s typem parametru odpovídajícího nastavovacího kódu.
C4951|"*popis*' je editován od shromáždění dat profilu data profilu funkce se nepoužijí
C4952|"*popis*': nenašla se žádná data profilu v databázi programu"*popis*.
C4953|Inlinee "*popis*' je editován od shromáždění dat profilu data profilu se nepoužívá
C4954|"*popis*': není profilované (obsahuje výraz přepínače __int64)

## <a name="warnings-introduced-in-visual-c-2002-compiler-version-13009466"></a>Upozornění zavedená ve Visual C++ 2002 (verze kompilátoru 13.00.9466)

Tato upozornění a všechna upozornění v pozdějších verzích jsou potlačeny pomocí možnosti kompilátoru __/Wv:12__.

|||
|-|-|
C4096|"*typ*': rozhraní není rozhraní COM; nebude se emitovat do IDL
C4097|byl očekáván parametr pragma bude mít "obnovit" nebo hodnotu off.
C4165|"HRESULT" je převáděn na 'bool'; jste si jisti, že je to, co chcete?
C4183|"*název*': chybí návratový typ; předpokládá se, že členská funkce vrátí"int"
C4199|*Popis*
C4255|"*název*': zadaný žádný prototyp funkce: převod '(') '(void).
C4256|"*deklarace*': konstruktor pro třídu s virtuálními základy má '...'; volání nemusí být kompatibilní se staršími verzemi Visual C++
C4258|"*název*': definice z for loop se ignoruje; je použita definice z nadřazeného oboru
C4263|"*deklarace*': členská funkce nepřepisuje žádnou virtuální členskou funkci základní třídy
C4264|"*deklarace*': přepsání není k dispozici pro virtuální členskou funkci ze základní"*třídy*'; funkce je skrytá.
C4265|"*typ*': třída má virtuální funkce, ale destruktor není virtuální instance této třídy nemusí být zničené správně
C4266|"*deklarace*': přepsání není k dispozici pro virtuální členskou funkci ze základní"*třídy*'; funkce je skrytá.
C4267|"*výraz*': převod z parametr size_t' k"*typ*", může dojít ke ztrátě dat.
C4274|#ident ignorovány; najdete v dokumentaci #pragma Comment (exestr, 'řetězec')
C4277|importovaná položka "*typ*::*název*' existuje jako datový člen i jako funkční člen; datový člen ignorovat
C4278|"*název*': identifikátor v knihovně typů '*popis*" už je makro; použijte kvalifikátor "přejmenovat"
C4279|"*název*': identifikátor v knihovně typů '*popis*' je klíčové slovo; použijte kvalifikátor"přejmenovat"
C4287|"*výraz*': unsigned/negative – neshoda konstanty
C4288|používá se nestandardní rozšíření: '*název*': Proměnná ovládacího prvku smyčky deklarovaná ve smyčce for-loop se používá mimo obor smyčky for-loop; je v konfliktu s deklarací ve vnějším oboru
C4289|používá se nestandardní rozšíření: '*název*': Proměnná ovládacího prvku smyčky deklarovaná ve smyčce for-loop se používá mimo obor smyčky for loop
C4293|"*výraz*': záporný nebo moc velký počet operací shift je; nedefinované chování
C4295|"*typ*': pole je příliš malá, aby zahrnují ukončujícího znaku null
C4296|"*výraz*': výraz je vždycky *hodnota*
C4297|"*typ*': funkce předpokládá, že nechcete vytvořit výjimku, ale neobsahuje
C4298|"*název*': identifikátor v knihovně typů '*popis*" už je makro; přejmenování na ' __*název*.
C4299|"*název*': identifikátor v knihovně typů '*popis*' je klíčové slovo; přejmenování na ' __*název*"
C4302|"*výraz*': zkrácení z '*typ*"do"*typ*"
C4303|*převod* z "*typ*"do"*typ*" je zastaralé, použijte přetypování static_cast, __try_cast nebo dynamic_cast.
C4314|Parametr očekávané pragma bude mít hodnotu 32, nebo hodnotu 64.
C4315|"*typ*': 'this' ukazatele pro člena '*typ*' nemusí být zarovnáním *číslo* podle očekávání tím, konstruktor
C4318|Předejte nulovou konstantou jako délka do memset.
C4319|"*výraz*': nulové rozšíření"*typ*"do"*typ*' větší velikosti
C4321|automaticky se generuje IID pro rozhraní '*typ*.
C4322|automaticky se generuje CLSID pro třídu*typ*.
C4323|opakovaně se používá zaregistrované CLSID pro třídu*typ*.
C4324|"*typ*': struktury byla, aby bylo vytvořeno z důvodu specifikátor zarovnání
C4325|atributy pro oddíl standard "*popis*se ignoruje
C4326|Typ vrácené hodnoty '*název*by měl být*typ*'namísto z'*typ*"
C4327|"*výraz*': zarovnání indirekce LHS (*číslo*) je větší než zarovnání indirekce RHS (*číslo*)
C4328|"*popis*': nepřímé zarovnání formálního parametru *číslo* (*číslo*) je větší než vlastní zarovnání argumentů (*číslo*)
C4329|specifikátor zarovnání se pro výčet ignoruje.
C4336|Import knihovny typů s křížovými odkazy "*knihovny*'před importem"*popis*.
C4337|Knihovna typů s křížovými odkazy "*knihovny*"in"*popis*" se importuje automaticky.
C4338|#pragma *popis*: oddíl standard "*části*' se používá
C4339|"*typ*': použití nedefinovaného typu zjistil v metadat CLR/WinRT – použití tohoto typu může vést k výjimce modulu runtime
C4353|používá se nestandardní rozšíření: Konstanta 0 jako výraz funkce.  Místo toho použijte vnitřní funkce "__noop.
C4370|"*deklarace*': má ke změně rozložení třídy z předchozí verze kompilátoru z důvodu lepšího balení
C4371|"*deklarace*': může mít ke změně rozložení třídy z předchozí verze kompilátoru z důvodu lepšího balení člena '*člen*.
C4373|"*typ*': virtuální funkce přepíše*deklarace*", předchozí verze kompilátoru nepřepsala, když se parametry lišily jenom podle kvalifikátory const/volatile
C4387|"*popis*': byla považována za
C4389|"*výraz*': podepsané/unsigned – neshoda
C4391|"*deklarace*': nesprávný návratový typ pro vnitřní funkci, byl očekáván '*typ*"
C4392|"*deklarace*': nesprávný počet argumentů pro vnitřní funkci, byl očekáván '*číslo*" argumenty
C4407|přetypování mezi různé reprezentacemi ukazatele na člen, kompilátor může vygenerovat nesprávný kód
C4420|"*název*': operátor není k dispozici, pomocí"*název*' místo toho; kontrolu za běhu může dojít k ohrožení
C4440|Předefinování konvence volání z: "*popis*"do"*popis*se ignoruje
C4442|vložený terminátor s hodnotou null v argumentu __annotation.  Hodnota bude zkrátila.
C4444|"*název*': v tomto kontextu není implementována nejvyšší úroveň '__unaligned'
C4526|"*typ*': statická členská funkce nemůže přepsat virtuální funkce"*deklarace*"přepsání ignorovat, virtuální funkce bude skrytá.
C4531|Zpracování výjimek jazyka C++ není k dispozici ve Windows CE. Použití strukturovaného zpracování výjimek
C4532|"*popis*': přechod z *nakonec* blok má během zpracování ukončení nedefinované chování
C4533|Inicializace "*deklarace*" je přeskočených ' goto *deklarace*.
C4534|"*deklarace*' nesmí být výchozí konstruktor pro *třídy* "*typ*"kvůli výchozího argumentu
C4535|Calling _set_se_translator() vyžaduje/EHa.
C4536|"*popis*': název typu překračuje limit metadat '*číslo*" znaky
C4537|"*deklarace*": "." u-uživatelem Definovaný typ
C4542|Přeskakuje se generování sloučeného vloženého textového souboru nelze zapisovat *typ* souboru: "*filename*': *chyba*
C4543|Vložený text se potlačil atribut "žádné\_injected_text.
C4555|výraz nemá žádný vliv; očekávaný výraz s vedlejším účinkem
C4557|'__assume' obsahuje efekt '*efekt*.
C4558|hodnota operandu "*číslo*"je mimo rozsah"*číslo* - *číslo*.
C4561|"__fastcall' nekompatibilní s" / clr' možnost: převod na: __stdcall.
C4562|používat plně prototypované funkce jsou požadovány s "/ clr' možnost: převod '(') '(void).
C4564|Metoda "*název*" z *třídy* "*typ*"definuje nepodporovaný výchozí parametr"*parametr*"
C4584|"*typ*': základní třídy*deklarace*'je již třídou base'*deklarace*"
C4608|Inicializace několika členů sjednocení: "*typ*"a"*typ*.
C4619|#pragma warning: neexistuje číslo upozornění '*číslo*.
C4623|"*typ*': výchozí konstruktor byl implicitně definovaný jako odstraněný
C4624|"*typ*': destruktor byl implicitně definovaný jako odstraněný
C4625|"*typ*': kopírovací konstuktor byl implicitně definovaný jako odstraněný
C4626|"*typ*': operátor přiřazení je implicitně definovaný jako odstraněný
C4645|funkce deklarovaná pomocí 'noreturn' má návratový příkaz
C4646|funkce deklarovaná pomocí 'noreturn' má návratový typ jiný než void
C4659|#pragma "*popis*': používání vyhrazeného segmentu"*název*' má nedefinované chování, použijte #pragma comment (linker,...)
C4667|"*deklarace*': definovaná žádná šablona funkcí, která odpovídá vynucenému vytváření instancí
C4668|"*název*'není definován jako preprocesor makro, nahraďte '0' pro'*hodnota*.
C4669|"*výraz*': nebezpečný převod:"*typ*"je objekt typu spravované/WinRT
C4674|"*název*" by se měl deklarovat 'static' a mít přesně jeden parametr.
C4680|"*typ*': Konstrukt coclass nespecifikuje výchozí rozhraní
C4681|"*typ*': Konstrukt coclass nespecifikuje výchozí rozhraní, který je zdrojem událostí
C4682|"*typ*': žádný parametr směrového atributu zadán, výchozí [v]
C4683|"*deklarace*': Zdroj události má"out"-parametr; postupujte obezřetně při připojení více obslužných rutin událostí
C4684|"*popis*': upozornění!! atribut může způsobit vygenerování neplatného kódu: používejte opatrně,
C4685|byl očekáván ' >> ' najít ' >> "při analýze parametrů šablony
C4700|Neinicializovaná lokální proměnná '*název*"použít
C4701|potenciální neinicializovaná lokální proměnná '*název*"použít
C4702|Nedosažitelný kód
C4711|funkce "*název*" vybraná pro automatické vložení rozšíření
C4714|funkce "*deklarace*" označená jako __forceinline není vložená
C4715|"*funkce*': Ne všechny cesty ovládacích prvků vracet hodnotu
C4716|"*funkce*': musí vracet hodnotu
C4717|"*funkce*': rekurzivní pro všechny cesty ovládacích prvků, funkce způsobí za běhu přetečení zásobníku
C4718|"*funkce*': rekurzivní volání nemá žádné vedlejší efekty, odstraňuje se
C4719|Pokud Qfast - použít 'f' jako přípona pro indikaci přesnosti single se našla konstanta Double
C4723|potenciální dělení 0
C4724|potenciální dělení se zbytkem 0
C4725|instrukce nemusí být na některých procesorech Pentium přesná.
C4757|hodnota argumentu Subscript je velká hodnota bez znaménka, nechtěli jste použít zápornou konstantu?
C4772|#import odkazovala na typ z chybějící knihovny typů; "*popis*se používá jako zástupný symbol
C4792|funkce "*funkce*" deklarované pomocí: sysimport a odkazované z nativního kódu; naimportujte knihovnu požadovanou pro propojení
C4794|segment proměnné úložiště místního vlákna "*název*"změněno z"*segmentu*"do"*segmentu*.
C4798|nativní kód generovaný pro funkci p-code "*název*" s obslužnou rutinou výjimky nebo sémantiku odvíjení
C4799|funkce "*název*' nemá žádnou instrukci EMMS.
C4803|"*deklarace*': metoda raise má jinou třídu úložiště než událost,"*deklarace*.
C4810|Hodnota direktivy pragma pack(show) == *číslo*
C4811|Hodnota pragma conform (forScope, show) == *hodnota*
C4820|"*typ*": "*číslo*" bajtů výplně se přidalo za *typ* "*typ*.
C4905|široký řetězcový literál přetypován na '*typ*.
C4906|řetězcový literál přetypován na '*typ*.
C4912|"*atribut*': atribut má nedefinované chování pro vnořené UDT
C4916|Pokud chcete mít dispid, "*typ*': musí být zavedené prostřednictvím rozhraní
C4917|"*typ*': identifikátor GUID lze přidružit pouze pomocí třídy, rozhraní nebo oboru názvů
C4918|"*znak*': neplatný znak v seznamu optimalizací pragma
C4920|výčet *název* člen *název*=*číslo* už zjistil ve výčtu *název* jako *název* = *číslo*
C4921|"*název*': hodnota atributu '*hodnotu*' by neměl být zadaný vícenásobně
C4925|"*deklarace*': metodu dispinterface nejde volat ze skriptu
C4926|"*deklarace*': symbol je už definovaný: atributy se ignorují
C4927|Neplatný převod; implicitně použit více než jeden uživatelsky definovaný převod.
C4928|nelegální inicializace kopírování; implicitně použit více než jeden uživatelem definovaný převod
C4929|"*popis*': Knihovna typů obsahuje sjednocení; ignoruje se kvalifikátor embedded_idl.
C4930|"*deklarace*': nevolá se prototypovaná funkce se nevolala (byla definice proměnné záměrná?)
C4931|předpokládáme, knihovna typů byla sestavena pro *číslo*-bit ukazatele
C4932|__identifier (*popis*) a __identifier (*popis*) nejde rozlišit
C4934|'__delegate(multicast)' je zastaralý, použijte '__delegate' místo toho
C4935|specifikátor přístupu sestavení změnit "*popis*.
C4944|"*název*": nejde naimportovat symbol z: "*zdroj*': jako*deklarace*" již existuje v aktuálním rozsahu.
C4945|"*název*': nejde naimportovat symbol z:"*zdroj*': jako*deklarace*'již byl importován z jiného sestavení'*zdroj*"
C4946|reinterpret_cast použito mezi souvisejícími třídami: '*deklarace*"a"*deklarace*.
C4995|"*název*': název byl označený jako #pragma deprecated
C4996|"*problém*': *popis*
C4997|"*typ*': Konstrukt coclass neimplementuje rozhraní modelu COM nebo pseudo rozhraní
C4998|OČEKÁVÁ se nezdařilo: *popis*(*číslo*)

## <a name="see-also"></a>Viz také:

- [– Možnost kompilátoru/WV:](../../build/reference/compiler-option-warning-level.md)
- [Upozornění kompilátoru, které jsou ve výchozím nastavení vypnuta](../../preprocessor/compiler-warnings-that-are-off-by-default.md)
- [warning](../../preprocessor/warning.md)
