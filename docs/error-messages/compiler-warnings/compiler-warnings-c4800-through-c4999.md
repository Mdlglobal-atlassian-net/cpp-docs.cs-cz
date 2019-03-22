---
title: Compiler Warnings C4800 Through C5999
ms.date: 03/14/2019
f1_keywords:
- C4808
- C4809
- C4825
- C4827
- C4837
- C4841
- C4842
- C4843
- C4844
- C4845
- C4846
- C4847
- C4848
- C4872
- C4880
- C4881
- C4882
- C4910
- C4916
- C4921
- C4934
- C4951
- C4954
- C4955
- C4963
- C4966
- C4970
- C4971
- C4973
- C4974
- C4981
- C4985
- C4987
- C4988
- C4989
- C4990
- C4991
- C4992
- C4998
- C5022
- C5023
- C5024
- C5025
- C5026
- C5027
- C5028
- C5029
- C5030
- C5031
- C5032
- C5033
- C5034
- C5035
- C5036
- C5037
- C5039
- C5040
- C5041
- C5042
- C5043
- C5044
- C5045
- C5046
- C5047
- C5048
- C5049
- C5050
- C5100
- C5101
- C5102
- C5103
- C5104
- C5105
- C5106
- C5107
helpviewer_keywords:
- C4808
- C4809
- C4825
- C4827
- C4837
- C4841
- C4842
- C4843
- C4844
- C4845
- C4846
- C4847
- C4848
- C4872
- C4880
- C4881
- C4882
- C4910
- C4916
- C4921
- C4934
- C4951
- C4954
- C4955
- C4963
- C4966
- C4970
- C4971
- C4973
- C4974
- C4981
- C4985
- C4987
- C4988
- C4989
- C4990
- C4991
- C4992
- C4998
- C5022
- C5023
- C5024
- C5025
- C5026
- C5027
- C5028
- C5029
- C5030
- C5031
- C5032
- C5033
- C5034
- C5035
- C5036
- C5037
- C5039
- C5040
- C5041
- C5042
- C5043
- C5044
- C5045
- C5046
- C5047
- C5048
- C5049
- C5050
- C5100
- C5101
- C5102
- C5103
- C5104
- C5105
- C5106
- C5107
ms.openlocfilehash: 101181e72aaf30ca8bc1d0e4191649fcc4155a64
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328340"
---
# <a name="compiler-warnings-c4800-through-c5999"></a>Compiler Warnings C4800 Through C5999

Články v této části dokumentace vysvětlují podmnožinu varovné zprávy, které jsou generovány kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Zprávy upozornění

|Upozornění|Zpráva|
|-------------|-------------|
|[(Úroveň 4) upozornění kompilátoru C4800](compiler-warning-level-3-c4800.md)| Implicitní převod z '*typ*' na typ bool. Ztráty informací je to možné |
|[Upozornění kompilátoru (úroveň 1) C4803](compiler-warning-level-1-c4803.md)|"*metoda*': metoda raise má jinou třídu úložiště než událost,"*události*"|
|[Upozornění kompilátoru (úroveň 1) C4804](compiler-warning-level-1-c4804.md)|"*operace*': potenciálně nebezpečné používání typu 'bool' v operaci|
|[Upozornění kompilátoru (úroveň 1) C4805](compiler-warning-level-1-c4805.md)|"*operace*': potenciálně nebezpečné směšování typu"*type1*"a typ"*type2*"v operaci|
|[Upozornění kompilátoru (úroveň 1) C4806](compiler-warning-level-1-c4806.md)|"*operace*': nebezpečná operace: žádná hodnota typu"*type1*'přesunutá na typ'*type2*"se nemůže rovnat dané konstantě|
|[Upozornění kompilátoru (úroveň 1) C4807](compiler-warning-level-1-c4807.md)|"*operace*': potenciálně nebezpečné směšování typu"*type1*"a podepsané bitové pole typu"*type2*.|
|Upozornění kompilátoru (úroveň 1) C4808|případ "*hodnotu*' je 'bool' není platnou hodnotou pro podmínku přepínače typu|
|Upozornění kompilátoru (úroveň 1) C4809|příkaz Switch má redundantní "default" popisek; jsou uvedeny všechny možné jmenovky case.|
|[Upozornění kompilátoru (úroveň 1) C4810](compiler-warning-level-1-c4810.md)|Hodnota direktivy pragma pack(show) == n|
|[Upozornění kompilátoru (úroveň 1) C4811](compiler-warning-level-1-c4811.md)|Hodnota pragma conform (forScope, show) == hodnota|
|[Upozornění kompilátoru (úroveň 1) C4812](compiler-warning-level-1-c4812.md)|zastaralý styl deklarace: použijte "*new_syntax*' místo toho|
|[Upozornění kompilátoru (úroveň 1) C4813](compiler-warning-level-1-c4813.md)|"*funkce*': funkce friend lokální třídy musí mít byla deklarována|
|[Upozornění kompilátoru (úroveň 4) C4816](compiler-warning-level-4-c4816.md)|"*param*': parametr má pole s nulovou velikostí, které se zkrátí (Pokud v odkazu nebude předaný objekt)|
|[Upozornění kompilátoru (úroveň 1) C4817](compiler-warning-level-1-c4817.md)|"*člen*': Neplatné použití". "pro přístup k tomuto členu; nahrazení kompilátoru znaky->.|
|[Upozornění kompilátoru (úroveň 1) C4819](compiler-warning-level-1-c4819.md)|Tento soubor obsahuje znak, který nemůže být reprezentovaný v aktuální znakové stránce (číslo). Uložte soubor ve formátu Unicode, aby se zabránilo ztrátě dat.|
|[Upozornění kompilátoru (úroveň 4) C4820](compiler-warning-level-4-c4820.md)|"*bajtů*"bajtů výplně se přidalo po konstrukci"*member_name*.|
|[Upozornění kompilátoru (úroveň 1) C4821](compiler-warning-level-1-c4821.md)|Nepovedlo se zjistit typ kódování Unicode, uložte prosím soubor s podpisem (BOM)|
|[Upozornění kompilátoru (úroveň 1) C4822](compiler-warning-level-1-c4822.md)|'člen function': členská funkce lokální třídy nemá tělo.|
|[Upozornění kompilátoru (úroveň 3) C4823](compiler-warning-level-3-c4823.md)|"*funkce*': používá ukazatele Připnutí ale unwind není povolená sémantika. Zvažte použití možnosti/EHa|
|Upozornění kompilátoru (úroveň 2) C4826|Převod z '*type1*"do"*type2*"je rozšířen o znaménko. To může způsobit neočekávané chování za běhu.|
|Upozornění kompilátoru (úroveň 3) C4827|Veřejné metody "ToString" 0 parametrů by měla být označena jako virtuální a přepsání|
|[Upozornění kompilátoru (úroveň 1) C4829](compiler-warning-level-1-c4829.md)|Potenciálně nesprávné parametry pro funkci main. Vezměte v úvahu "int main (Platform::Array\<Platform::String ^ > ^ argv).|
|[Upozornění kompilátoru (úroveň 1) C4835](compiler-warning-level-1-c4835.md)|"*proměnnou*': inicializátor pro exportovaná data se nespustí, dokud se v hostitelském sestavení nejdřív nespustí spravovaný kód|
|Upozornění kompilátoru (úroveň 4) C4837|zjistil se trigraph: "?? *znak*"nahrazuje"*znak*.|
|[Upozornění kompilátoru (úroveň 1) C4838](compiler-warning-level-1-c4838.md)|Převod z '*type_1*"do"*type_2*' vyžaduje zúžení převodu|
|[Upozornění kompilátoru (úroveň 3) C4839](compiler-warning-level-3-c4839.md)|nestandardní použití třídy*typ*"jako argumentu variadické funkce|
|[Upozornění kompilátoru (úroveň 4) C4840](compiler-warning-level-4-c4840.md)|nepřenositelné použití třídy*typ*"jako argumentu variadické funkce|
|Upozornění kompilátoru (úroveň 4) C4841|nestandardní rozšíření: v offsetof použilo složené označení člena|
|Upozornění kompilátoru (úroveň 4) C4842|není zaručeno, že výsledek offsetof použitý pro typ pomocí vícenásobného dědění bude konzistentní napříč verzemi kompilátoru.|
|Kompilátor varování C4843|"*type1*": Obslužná rutina výjimky odkazu na pole nebo typ funkce není dostupná, použijte '*type2*' místo toho|
|Kompilátor varování C4844|"export module *module_name*;" je teď preferovanou syntaxí pro deklaraci rozhraní modulu|
| Upozornění kompilátoru (úroveň 4) C4845 | "\_\_declspec (ne\_init\_all)" se ignoruje, pokud "/ d1initall\[0\|1\|2\|3]' nebyl zadán v příkazovém řádku |
| Upozornění kompilátoru (úroveň 4) C4846 | "*hodnotu*" není platným argumentem pro ' / d1initall': příkazového řádku příznak, ignorováno |
| Upozornění kompilátoru (úroveň 4) C4847 | "\_\_declspec (ne\_init\_all)" může používat jedině pro funkce, typ třídy nebo místní proměnná: ignoruje |
| Upozornění kompilátoru (úroveň 1) C4848 | Podpora pro standardní atribut "žádné\_jedinečný\_adres v C ++ 17 a starších verzích je rozšířením dodavatele |
|[Upozornění kompilátoru (úroveň 4) C4866](c4866.md)| Kompilátor nemůže vynutit pořadí vyhodnocování zleva doprava pro volání *operator_name*|
|[Upozornění (chyba) kompilátoru C4867](compiler-warning-c4867.md)|"*funkce*': chybí seznam argumentů volání funkce; použijte"*volání*' vytvořte ukazatel na člena|
|[Upozornění (úroveň 4) kompilátoru C4868](compiler-warning-c4868.md)|"_souboru_(*line_number*)' kompilátor nemůže vynutit pořadí vyhodnocování zleva doprava v inicializačního seznamu v závorkách|
|Upozornění kompilátoru (úroveň 2) C4872|číslo s plovoucí čárkou bodu dělení nulou zjistil při kompilování grafu volání pro: concurrency::parallel_for_each: "*umístění*.|
|Upozornění kompilátoru (úroveň 1) C4880|přetypování z ' const *type_1*"do"*type_2*': přetypování konstantnosti z ukazatele nebo odkazu může vést k nedefinovanému chování ve funkci s omezením pomocí specifikátoru amp|
|Upozornění kompilátoru (úroveň 4) C4881|konstruktor nebo destruktor se nebudou volat pro proměnnou tile_static "*proměnnou*.|
|Upozornění kompilátoru (úroveň 1) C4882|předání funktory s operátory volání nekonstantní do: concurrency::parallel_for_each je zastaralé.|
|[Kompilátor varování C4900](compiler-warning-level-1-c4900.md)|IL – Neshoda mezi "*tool1*'version'*version1*"a"*tool2*'version'*větev version2*.|
|[Upozornění kompilátoru (úroveň 1) C4905](compiler-warning-level-1-c4905.md)|široký řetězcový literál přetypován na 'LPSTR'|
|[Upozornění kompilátoru (úroveň 1) C4906](compiler-warning-level-1-c4906.md)|řetězcový literál přetypován na 'LPWSTR'|
|[Upozornění kompilátoru (úroveň 1) C4910](compiler-warning-level-1-c4910.md)|"\<identifikátor >:"__declspec(dllexport)"a"externí"nejsou pro explicitní vytváření instancí|
|[Upozornění kompilátoru (úroveň 1) C4912](compiler-warning-level-1-c4912.md)|"*atribut*': atribut má nedefinované chování pro vnořené UDT|
|[Upozornění kompilátoru (úroveň 4) C4913](compiler-warning-level-4-c4913.md)|uživatel definovaný binární operátor ',' existuje, ale přetížení nemohlo převést všechny operandy, předdefinovaný binární operátor ',' používá|
|Upozornění kompilátoru (úroveň 1) C4916|Pokud chcete mít dispid, "*popis*': musí být zavedené prostřednictvím rozhraní|
|[Upozornění kompilátoru (úroveň 1) C4917](compiler-warning-level-1-c4917.md)|"*deklarátor*': identifikátor GUID lze přidružit pouze pomocí třídy, rozhraní nebo oboru názvů|
|[Upozornění kompilátoru (úroveň 4) C4918](compiler-warning-level-4-c4918.md)|"*znak*': neplatný znak v seznamu optimalizací pragma|
|[Upozornění kompilátoru (úroveň 1) C4920](compiler-warning-level-1-c4920.md)|member_1 člen výčtu výčtového typu = value_1 už zjistil ve výčtu výčtu jako member_2 = value_2|
|Upozornění kompilátoru (úroveň 3) C4921|"*popis*': hodnota atributu '*atribut*' by neměl být zadaný vícenásobně|
|[Upozornění kompilátoru (úroveň 1) C4925](compiler-warning-level-1-c4925.md)|"*metoda*': metodu dispinterface nejde volat ze skriptu|
|[Upozornění kompilátoru (úroveň 1) C4926](compiler-warning-level-1-c4926.md)|"*identifikátor*': symbol je už definovaný: atributy se ignorují|
|[Upozornění kompilátoru (úroveň 1) C4927](compiler-warning-level-1-c4927.md)|Neplatný převod; implicitně použit více než jeden uživatelsky definovaný převod.|
|[Upozornění kompilátoru (úroveň 1) C4928](compiler-warning-level-1-c4928.md)|nelegální inicializace kopírování; implicitně použit více než jeden uživatelem definovaný převod|
|[Upozornění kompilátoru (úroveň 1) C4929](compiler-warning-level-1-c4929.md)|"*souboru*': Knihovna typů obsahuje sjednocení; ignoruje se kvalifikátor embedded_idl.|
|[Upozornění kompilátoru (úroveň 1) C4930](compiler-warning-level-1-c4930.md)|"*prototypu*': nevolá se prototypovaná funkce se nevolala (byla definice proměnné záměrná?)|
|[Upozornění kompilátoru (úroveň 4) C4931](compiler-warning-level-4-c4931.md)|Předpokládáme, že knihovna typů byla sestavena pro ukazatele počtu bitů.|
|[Upozornění kompilátoru (úroveň 4) C4932](compiler-warning-level-4-c4932.md)|__identifier (*identifikátor*) a \__identifikátor (*identifikátor*) nejde rozlišit|
|Upozornění kompilátoru (úroveň 1) C4934|'__delegate(multicast)' je zastaralý, použijte '\__delegate' místo toho|
|[Upozornění kompilátoru (úroveň 1) C4935](compiler-warning-level-1-c4935.md)|specifikátor přístupu sestavení změnit "*přístup*.|
|[Upozornění kompilátoru (úroveň 1, chyba) C4936](compiler-warning-c4936.md)|Tato možnost __declspec je podporovaná jenom při kompilaci s parametrem/CLR nebo/CLR: pure|
|[Upozornění kompilátoru (úroveň 4) C4937](compiler-warning-level-4-c4937.md)|"*text1*"a"*text2*jsou nejde rozlišit jako argumenty, které mají*směrnice*.|
|[Upozornění kompilátoru (úroveň 4) C4938](compiler-warning-level-4-c4938.md)|"*var*": Plovoucího bodu redukční proměnná může způsobit nekonzistentní výsledky v/FP: strict nebo #pragma fenv_access|
|[Kompilátor varování C4939](compiler-warning-level-1-c4939.md)|#pragma vtordisp je zastaralá a v příští verzi Visual C++ se odebere|
|[Upozornění kompilátoru (úroveň 1) C4944](compiler-warning-level-1-c4944.md)|"*symbol*': nejde naimportovat symbol z:"*assembly1*': jako*symbol*"již existuje v aktuálním rozsahu.|
|[Upozornění kompilátoru (úroveň 1) C4945](compiler-warning-level-1-c4945.md)|"*symbol*': nejde naimportovat symbol z:"*assembly1*': jako*symbol*"již byl importován z jiného sestavení"*assembly2* '|
|[Upozornění kompilátoru (úroveň 1) C4946](compiler-warning-level-1-c4946.md)|reinterpret_cast použito mezi souvisejícími třídami: '*class1*"a"*class2*.|
|[Upozornění kompilátoru (úroveň 1) C4947](compiler-warning-level-1-c4947.md)|"*typ nebo člen*': označené jako zastaralé|
|[Upozornění kompilátoru (úroveň 2) C4948](compiler-warning-level-2-c4948.md)|Typ vrácené hodnoty '*přistupující objekt*"se neshoduje s typem parametru odpovídajícího nastavovacího kódu.|
|[Upozornění kompilátoru (úrovně 1 a 4) C4949](compiler-warning-level-1-and-level-4-c4949.md)|direktivy pragma "spravované" a 'nespravované' mají smysl jenom při kompilaci s "/ clr [: možnost]"|
|[Upozornění kompilátoru (úroveň 1, chyba) C4950](compiler-warning-c4950.md)|"*typ nebo člen*': označené jako zastaralé|
|[Upozornění kompilátoru (úroveň 1) C4951](compiler-warning-level-1-c4951.md)|"*funkce*' byl upraven od shromáždění dat profilu data profilu funkce se nepoužijí|
|[Upozornění kompilátoru (úroveň 1) C4952](compiler-warning-level-1-c4952.md)|"*funkce*': nenašla se žádná data profilu v databázi programu"*pgd_file*.|
|[Upozornění kompilátoru (úroveň 1) C4953](compiler-warning-level-1-c4953.md)|Inlinee "*funkce*' byl upraven od shromáždění dat profilu data profilu se nepoužívá|
|Kompilátor varování C4954|"*funkce*': není profilované (obsahuje výraz přepínače __int64)|
|Kompilátor varování C4955|"*import2*': import se ignoroval; už je naimportované z:"*import1*.|
|[Upozornění kompilátoru (úroveň 1, chyba) C4956](compiler-warning-c4956.md)|"*typ*': Tento typ není ověřitelný|
|[Upozornění kompilátoru (úroveň 1, chyba) C4957](compiler-warning-c4957.md)|"*přetypování*': explicitní přetypování z typu '*cast_from*"do"*cast_to*" nejde ověřit|
|[Upozornění kompilátoru (úroveň 1, chyba) C4958](compiler-warning-c4958.md)|"*operace*': není možné ověřit aritmetiku ukazatele|
|[Upozornění kompilátoru (úroveň 1, chyba) C4959](compiler-warning-c4959.md)|nejde definovat nespravovaný typ "*typ*" v/CLR: safe vzhledem k tomu, že přístup k jeho členům vrací neověřitelný kód|
|[Upozornění kompilátoru (úroveň 4) C4960](compiler-warning-level-4-c4960.md)|"*funkce*" je moc velké, aby se dalo Profilovat.|
|[Upozornění kompilátoru (úroveň 1) C4961](compiler-warning-c4961.md)|Žádná data profilu se nesloučila do .pgd souboru, optimalizace na základě profilu zakázáno|
|[Upozornění kompilátoru (úroveň 4) C4962](compiler-warning-c4962.md)|"*funkce*": Optimalizace na základě profilu zakázáno, protože optimalizace způsobily nekonzistenci dat profilu|
|Upozornění kompilátoru (úroveň 1) C4963|"*popis*': nenašla se žádná data profilu; jiné parametry kompilátoru v instrumentovaném buildu|
|[Upozornění kompilátoru (úroveň 1) C4964](compiler-warning-level-1-c4964.md)|Nebyly zadány žádné možnosti optimalizace; informace o profilu se nebudou shromažďovat.|
|[Upozornění kompilátoru (úroveň 1) C4965](compiler-warning-level-1-c4965.md)|implicitní pole celé číslo 0; Použijte nullptr nebo explicitní přetypování.|
|Upozornění kompilátoru (úroveň 1) C4966|"*funkce*' má poznámku __code_seg s nepodporovaným názvem segmentu, ignorovat poznámky|
|Kompilátor varování C4970|Konstruktor Delegate: cílový objekt ignoruje od "*typ*" je statická|
|Upozornění kompilátoru (úroveň 1) C4971|Pořadí argumentů: \<cílový objekt >, \<cílová funkce > pro konstruktor delegate je zastaralé, použijte \<cílová funkce >, \<cílový objekt = "" >|
|[Upozornění kompilátoru (úroveň 1, chyba) C4972](compiler-warning-c4972.md)|Přímá úprava nebo zpracování výsledku operace unbox jako l-hodnota se nelze ověřit|
|Upozornění kompilátoru (úroveň 1) C4973|"*symbol*': označené jako zastaralé|
|Upozornění kompilátoru (úroveň 1) C4974|"*symbol*': označené jako zastaralé|
|Upozornění kompilátoru (úroveň 3) C4981|Warbird: funkce '*funkce*"označená jako __forceinline není vložená, protože obsahuje sémantiku výjimky.|
|Upozornění kompilátoru (úroveň 3) C4985|Název symbolu ': neexistují atributy pro předchozí deklaraci.|
|[Upozornění kompilátoru C4986](compiler-warning-c4986.md)|"*deklarace*': specifikace výjimky se neshoduje s předchozí deklarací.|
|Upozornění kompilátoru (úroveň 4) C4987|použito nestandardní rozšíření: 'throw (...)'|
|Upozornění kompilátoru (úroveň 4) C4988|"*proměnnou*': proměnná deklarována mimo rozsah třídy a funkce|
|Upozornění kompilátoru (úroveň 4) C4989|"*typ*': typ má konfliktní definice.|
|Upozornění kompilátoru (úroveň 3) C4990|Warbird: *zprávy*|
|Upozornění kompilátoru (úroveň 3) C4991|Warbird: funkce '*funkce*"označená jako __forceinline není vložená, protože úroveň ochrany inlinee je vyšší než nadřazené|
|Upozornění kompilátoru (úroveň 3) C4992|Warbird: funkce '*funkce*"označená jako __forceinline není vložená, protože obsahuje vložené sestavení, které nejde chránit.|
|[Upozornění kompilátoru (úroveň 3) C4995](compiler-warning-level-3-c4995.md)|"*funkce*': název byl označený jako #pragma deprecated|
|[Upozornění kompilátoru (úroveň 3) C4996](compiler-warning-level-3-c4996.md)|"*popis*': *zprávy*|
|[Upozornění kompilátoru (úroveň 1) C4997](compiler-warning-level-1-c4997.md)|"*třídy*': Konstrukt coclass neimplementuje rozhraní modelu COM nebo pseudo rozhraní|
|Upozornění kompilátoru (úroveň 1) C4998|OČEKÁVÁ se nezdařilo: *očekávání*(*hodnotu*)|
|[Kompilátor varování C4999](compiler-warning-level-1-c4999.md)|NEZNÁMÉ upozornění Zvolte prosím příkaz technická podpora v nabídce Nápověda pro Visual C++, nebo otevřete soubor nápovědy technické podpory pro další informace|
|Kompilátor varování C5022|"*typ*': zadaných víc konstruktorů move|
|Kompilátor varování C5023|"*typ*': zadaných víc operátorů přiřazení přesunutí|
|Upozornění kompilátoru (úroveň 4) C5024|"*typ*': přesunout konstruktor byl implicitně definovaný jako odstraněný|
|Upozornění kompilátoru (úroveň 4) C5025|"*typ*': Přesuňte operátor přiřazení je implicitně definovaný jako odstraněný|
|Upozornění kompilátoru (úroveň 1 a 4) C5026|"*typ*': přesunout konstruktor byl implicitně definovaný jako odstraněný|
|Upozornění kompilátoru (úroveň 1 a 4) C5027|"*typ*': Přesuňte operátor přiřazení je implicitně definovaný jako odstraněný|
|Upozornění kompilátoru (úroveň 1) C5028|"*název*": Zarovnání zadané před deklarací (*číslo*) není zadané v definici|
|Upozornění kompilátoru (úroveň 4) C5029|používá se nestandardní rozšíření: atributy zarovnání v C++ použít pro proměnné, datové členy a pouze typy značek|
|Upozornění kompilátoru (úroveň 3) C5030|atribut '*atribut*' nebyla rozpoznána|
|Upozornění kompilátoru (úroveň 4) C5031|#pragma warning(pop): pravděpodobně o neshodu, stav automaticky otevíraného upozornění vložil do jiného souboru|
|Upozornění kompilátoru (úroveň 4) C5032|zjištěna #pragma warning(push) bez odpovídajícího příkazu #pragma warning(pop)|
|Upozornění kompilátoru (úroveň 1) C5033|"*třídy úložiště*' již není podporovanou třídou úložiště.|
|Kompilátor varování C5034|použití vnitřních "*vnitřní*" způsobí, že funkce *funkce* se zkompiluje jako kód hosta.|
|Kompilátor varování C5035|použití funkce '*funkce*"způsobí, že funkce *funkce* se zkompiluje jako kód hosta.|
|Upozornění kompilátoru (úroveň 1) C5036|převod ukazatele funkci VarArgs při kompilování x86arm64 "*type1*"do"*type2*.|
|Upozornění kompilátoru (chyba) C5037|"*členské funkce*': definice mimo řádek člena šablony třídy nemůže mít výchozí argumenty|
|[Upozornění kompilátoru (úroveň 4) C5038](c5038.md)|datový člen "*member1*'bude inicializován po datovém členu'*člen2*.|
|Upozornění kompilátoru (úroveň 4) C5039|"*funkce*': ukazatel nebo odkaz na potenciální vyvolávací funkci předán do funkce extern C v - EHc. Pokud tato funkce vyvolá výjimku, může dojít k nedefinovanému chování.|
|Upozornění kompilátoru (úroveň 3) C5040|Specifikace dynamických výjimek jsou platné jenom v C ++ 14 a dřívějších verzích; zpracuje jako noexcept(false).|
|Upozornění kompilátoru (úroveň 1) C5041|"*definice*': definice mimo řádek pro statický datový člen constexpr nevyžaduje a je zastaralé v C ++ 17|
|Upozornění kompilátoru (úroveň 3) C5042|"*deklarace*': deklarace funkcí v blokovém rozsahu nemůže být zadané"vložené"ve standardním jazyce C++; odeberte specifikátor inline.|
|Upozornění kompilátoru (úroveň 2) C5043|"*specifikace*': specifikace výjimky se neshoduje s předchozí deklarací.|
|Upozornění kompilátoru (úroveň 4) C5044|Argument pro možnost příkazového řádku *možnost* odkazuje na cestu "*cesta*", která neexistuje|
|[Kompilátor varování C5045](c5045.md)|Kompilátor vloží zmírnění hrozby Spectre pro zatížení paměti, pokud přepínač/qspectre zadané|
|[Upozornění kompilátoru (úroveň 2) C5046](c5046.md)|"*funkce*": Symbol, zahrnující typ s vnitřním propojením nedefinovaná.|
| Upozornění kompilátoru (úroveň 1) C5047 | nestandardní použití \_ \_Pokud\_existuje s moduly se nepodporuje |
| Upozornění kompilátoru (úroveň 1) C5048 | Použití makra "*makro*' může způsobit nedeterministické výstupu |
| Upozornění kompilátoru (úroveň 1) C5049 | "*řetězec*": Vkládání úplnou cestu může vést k výstupu závislé na počítači |
| Upozornění kompilátoru (úroveň 1) C5050 | Je to možné kompatibilní prostředí při importování modulu '*module_name*': *problém* |
| Upozornění kompilátoru (úroveň 1) C5100 | \_\_Posouzení ohrožení zabezpečení\_ARGS\_ \_ je vyhrazená pro použití v variadická makra |
| Upozornění kompilátoru (úroveň 1) C5101 | použití direktivy preprocesoru v seznamu argumentů funkci podobnou makru je nedefinované chování |
| Upozornění kompilátoru (úroveň 1) C5102 | ignoruje se neplatná příkazového řádku definice makra "*hodnota*. |
| Upozornění kompilátoru (úroveň 1) C5103 | vkládání "*token1*"a"*token2*' nemá za následek platný token předběžného zpracování |
| Upozornění kompilátoru (úroveň 1) C5104 | nenašel se*řetězec1*#*řetězec2*'v seznamu nahrazení makra, měli jste na mysli'*řetězec1*"" #*řetězec2*"? |
| Upozornění kompilátoru (úroveň 1) C5105 | rozšíření makra vytváření "definice" má nedefinované chování |
| Upozornění kompilátoru (úroveň 1) C5106 | předefinovalo se různé názvy parametrů – makro |
| Upozornění kompilátoru (úroveň 1) C5107 | chybí ukončení "*char*" znak |
