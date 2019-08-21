---
title: Upozornění kompilátoru C4800 až C5999
ms.date: 04/21/2019
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
ms.openlocfilehash: ae73d4ba503dfbbc27f91040c31beb91da3b7e54
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631541"
---
# <a name="compiler-warnings-c4800-through-c5999"></a>Upozornění kompilátoru C4800 až C5999

Články v této části dokumentace vysvětlují podmnožinu upozornění, která jsou generována kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Varovné zprávy

|Upozornění|Message|
|-------------|------------|
|[Upozornění kompilátoru (úroveň 4) C4800](compiler-warning-level-3-c4800.md)| Implicitní převod z*typu*na bool Možné ztráty informací |
|[Upozornění kompilátoru (úroveň 1) C4803](compiler-warning-level-1-c4803.md)|'*Method*': Metoda vyvolání má jinou třídu úložiště než událost, '*Event*'|
|[Upozornění kompilátoru (úroveň 1) C4804](compiler-warning-level-1-c4804.md)|'*Operation*': nebezpečné použití typu ' bool ' v operaci|
|[Upozornění kompilátoru (úroveň 1) C4805](compiler-warning-level-1-c4805.md)|'*Operation*': potenciálně nebezpečné kombinace typu*typ1*a typu '*typ2*' v operaci|
|[Upozornění kompilátoru (úroveň 1) C4806](compiler-warning-level-1-c4806.md)|'*Operation*': nebezpečná operace: žádná hodnota typu*typ1*povýšená na typ '*typ2*' se může rovnat dané konstantě.|
|[Upozornění kompilátoru (úroveň 1) C4807](compiler-warning-level-1-c4807.md)|'*Operation*': potenciálně nebezpečné kombinace typu*typ1*a podepsaného bitového pole typu '*typ2*'|
|Upozornění kompilátoru (úroveň 1) C4808|*hodnota*Case není platná hodnota pro podmínku Switch typu bool.|
|Upozornění kompilátoru (úroveň 1) C4809|příkaz switch má redundantní jmenovku default; jsou zadané všechny možné jmenovky Case.|
|[Upozornění kompilátoru (úroveň 1) C4810](compiler-warning-level-1-c4810.md)|Hodnota direktivy pragma pack (show) = = n|
|[Upozornění kompilátoru (úroveň 1) C4811](compiler-warning-level-1-c4811.md)|Hodnota direktivy pragma shody (forScope, show) = = Value|
|[Upozornění kompilátoru (úroveň 1) C4812](compiler-warning-level-1-c4812.md)|zastaralý styl deklarace: místo toho prosím použijte '*new_syntax*'.|
|[Upozornění kompilátoru (úroveň 1) C4813](compiler-warning-level-1-c4813.md)|'*Function*': funkce Friend lokální třídy musí být dřív deklarovaná.|
|[Upozornění kompilátoru (úroveň 4) C4816](compiler-warning-level-4-c4816.md)|*param*: parametr má pole s nulovou velikostí, které se zkrátí (Pokud není objekt předaný odkazem).|
|[Upozornění kompilátoru (úroveň 1) C4817](compiler-warning-level-1-c4817.md)|'*Member*': Neplatné použití '. ' pro přístup k tomuto členu; Kompilátor nahradil znakem->.|
|[Upozornění kompilátoru (úroveň 1) C4819](compiler-warning-level-1-c4819.md)|Soubor obsahuje znak, který nemůže být reprezentovaný v aktuální znakové stránce (číslo). Uložte soubor ve formátu Unicode, aby nedošlo ke ztrátě dat.|
|[Upozornění kompilátoru (úroveň 4) C4820](compiler-warning-level-4-c4820.md)|odsazeníbajtů, které se přidalo po sestavení '*MEMBER_NAME*'|
|[Upozornění kompilátoru (úroveň 1) C4821](compiler-warning-level-1-c4821.md)|Nejde určit typ kódování Unicode, uložte prosím soubor s signaturou (BOM).|
|[Upozornění kompilátoru (úroveň 1) C4822](compiler-warning-level-1-c4822.md)|' Member Function ': členská funkce lokální třídy nemá tělo|
|[Upozornění kompilátoru (úroveň 3) C4823](compiler-warning-level-3-c4823.md)|'*Function*': používá ukazatele připnutí, ale není povolena sémantika unwind. Zvažte použití/EHa|
|Upozornění kompilátoru (úroveň 2) C4826|Převod z '*typ1*' na '*typ2*' je rozšířen o znaménko. To může způsobit neočekávané chování modulu runtime.|
|Upozornění kompilátoru (úroveň 3) C4827|Metoda Public ToString s 0 parametry by se měla označit jako Virtual a override.|
|[Upozornění kompilátoru (úroveň 1) C4829](compiler-warning-level-1-c4829.md)|Pravděpodobně nesprávné parametry pro funkci main. Zvažte možnost int Main (Platform:: array\<Platform:: String ^ > ^ argv).|
|[Upozornění kompilátoru (úroveň 1) C4835](compiler-warning-level-1-c4835.md)|'*Variable*': inicializátor pro exportovaná data se nespustí, dokud se spravovaný kód poprvé nespustí v sestavení hostitele.|
|Upozornění kompilátoru (úroveň 4) C4837|zjistil se trigraph:?? *znak*nahrazen*znakem*|
|[Upozornění kompilátoru (úroveň 1) C4838](compiler-warning-level-1-c4838.md)|převod z '*type_1*' na '*type_2*' vyžaduje zužující převod|
|[Upozornění kompilátoru (úroveň 3) C4839](compiler-warning-level-3-c4839.md)|nestandardní použití třídy*Type*jako argumentu funkce variadické|
|[Upozornění kompilátoru (úroveň 4) C4840](compiler-warning-level-4-c4840.md)|nepřenosné použití třídy*Type*jako argumentu funkce variadické|
|Upozornění kompilátoru (úroveň 4) C4841|používá se nestandardní rozšíření: označení složeného člena se používá v OffsetOf.|
|Upozornění kompilátoru (úroveň 4) C4842|výsledek OffsetOf aplikovaný na typ s použitím vícenásobné dědičnosti není zaručený, aby byl mezi verzemi kompilátoru konzistentní.|
|Upozornění kompilátoru C4843|'*typ1*': Obslužná rutina výjimky odkazu na typ pole nebo funkce je nedostupná, místo toho použijte možnost*typ2*.|
|Upozornění kompilátoru C4844|' export Module *module_name*; je teď upřednostňovanou syntaxí pro deklaraci rozhraní modulu.|
| Upozornění kompilátoru (úroveň 4) C4845 | '\_\|\|\|\[declspec (No\_initAll)'jeignorováno,pokudnapříkazovémřádkunebylzadán'/d1initall0123]'\_\_ |
| Upozornění kompilátoru (úroveň 4) C4846 | *hodnota Value*není platným argumentem pro '/d1initall ': příznak příkazového řádku se ignoruje. |
| Upozornění kompilátoru (úroveň 4) C4847 | '\_declspec\_(žádné\_init\_All) ' lze použít pouze pro funkci, typ třídy nebo místní proměnnou: ignorováno |
| Upozornění kompilátoru (úroveň 1) C4848 | Podpora pro standardní atribut "žádná\_jedinečná\_adresa" v c++ 17 a starších verzích je rozšířením dodavatele. |
|[Upozornění kompilátoru (úroveň 4) C4866](c4866.md)| Kompilátor nemůže pro volání *operator_name* vyhovět pořadí vyhodnocování zleva doprava.|
|[Upozornění kompilátoru (chyba) C4867](compiler-warning-c4867.md)|'*Function*': ve volání funkce chybí seznam argumentů; Chcete-li vytvořit ukazatel na člena, použijte*volání ' Call*'|
|[Upozornění kompilátoru (úroveň 4) C4868](compiler-warning-c4868.md)|Kompilátor '_File_(*Line_Number*) ' nemůže v seznamu inicializace v závorkách vyhovět pořadí vyhodnocování zleva doprava.|
|Upozornění kompilátoru (úroveň 2) C4872|Při kompilování grafu volání pro: concurrency::p arallel_for_each v*umístění*se zjistilo dělení nulou (desetinné čárky).|
|Upozornění kompilátoru (úroveň 1) C4880|přetypování z ' const *type_1*' na '*type_2*': odtypování vzdálenosti volna z ukazatele nebo odkazu může způsobit nedefinované chování ve funkci s omezením amp|
|Upozornění kompilátoru (úroveň 4) C4881|konstruktor nebo destruktor se nebudou volat pro proměnnou tile_static '*Variable*'.|
|Upozornění kompilátoru (úroveň 1) C4882|předávání funktory s operátory volání non-const do concurrency::p arallel_for_each je zastaralé.|
|[Upozornění kompilátoru C4900](compiler-warning-level-1-c4900.md)|Il – Neshoda mezi '*tool1*' verze '*version1*' a '*Tool2*' verze '*Version2*'|
|[Upozornění kompilátoru (úroveň 1) C4905](compiler-warning-level-1-c4905.md)|široký řetězcový literál přetypován na 'LPSTR'|
|[Upozornění kompilátoru (úroveň 1) C4906](compiler-warning-level-1-c4906.md)|řetězcový literál přetypován na 'LPWSTR'|
|[Upozornění kompilátoru (úroveň 1) C4910](compiler-warning-level-1-c4910.md)|'\<identifikátor >: __declspec (dllexport) ' a ' extern ' jsou nekompatibilní pro explicitní vytváření instancí.|
|[Upozornění kompilátoru (úroveň 1) C4912](compiler-warning-level-1-c4912.md)|*atribut ' Attribute*': atribut má nedefinované chování pro vnořené UDT|
|[Upozornění kompilátoru (úroveň 4) C4913](compiler-warning-level-4-c4913.md)|uživatelsky definovaný binární operátor ', ' existuje, ale žádné přetížení by nemohlo převést všechny operandy, použil se výchozí předdefinovaný binární operátor ', '.|
|Upozornění kompilátoru (úroveň 1) C4916|aby bylo možné mít DISPID, "*Description*" musí být zavedený rozhraním.|
|[Upozornění kompilátoru (úroveň 1) C4917](compiler-warning-level-1-c4917.md)|'*deklarátor*': identifikátor GUID lze přidružit pouze k třídě, rozhraní nebo oboru názvů.|
|[Upozornění kompilátoru (úroveň 4) C4918](compiler-warning-level-4-c4918.md)|'*Character*': neplatný znak v seznamu optimalizací pragma|
|[Upozornění kompilátoru (úroveň 1) C4920](compiler-warning-level-1-c4920.md)|Enum enum member member_1 = value_1 se už zobrazil ve výčtu výčtu jako member_2 = value_2.|
|Upozornění kompilátoru (úroveň 3) C4921|'*Description*': hodnota atributu '*attribute*' nesmí být určena pro násobení|
|[Upozornění kompilátoru (úroveň 1) C4925](compiler-warning-level-1-c4925.md)|*Metoda*: metodu IDispatch nejde volat ze skriptu.|
|[Upozornění kompilátoru (úroveň 1) C4926](compiler-warning-level-1-c4926.md)|*identifikátor*: symbol je už definovaný: atributy se ignorují.|
|[Upozornění kompilátoru (úroveň 1) C4927](compiler-warning-level-1-c4927.md)|Neplatný převod; implicitně se používá víc než jeden uživatelsky definovaný převod.|
|[Upozornění kompilátoru (úroveň 1) C4928](compiler-warning-level-1-c4928.md)|nelegální inicializace kopírování; implicitně použit více než jeden uživatelem definovaný převod|
|[Upozornění kompilátoru (úroveň 1) C4929](compiler-warning-level-1-c4929.md)|'*File*': knihovny typů obsahuje sjednocení; ignoruje se kvalifikátor embedded_idl.|
|[Upozornění kompilátoru (úroveň 1) C4930](compiler-warning-level-1-c4930.md)|'*prototyp*': nebyla volána prototypovaná funkce (byla určena definice proměnné?)|
|[Upozornění kompilátoru (úroveň 4) C4931](compiler-warning-level-4-c4931.md)|Předpokládáme, že knihovna typů byla sestavena pro ukazatele počtu bitů.|
|[Upozornění kompilátoru (úroveň 4) C4932](compiler-warning-level-4-c4932.md)|__identifier (*identifikátor*) a \__identifier (*Identifier*) nejde odlišit.|
|Upozornění kompilátoru (úroveň 1) C4934|' __delegate (vícesměrové vysílání) ' je zastaralé, místo toho\_použijte ' _Delegate '|
|[Upozornění kompilátoru (úroveň 1) C4935](compiler-warning-level-1-c4935.md)|specifikátor přístupu k sestavení se změnil z:*Access*.|
|[Upozornění kompilátoru (úroveň 1, chyba) C4936](compiler-warning-c4936.md)|Tato __declspec je podporovaná jenom při kompilaci s možností/CLR nebo/CLR: Pure.|
|[Upozornění kompilátoru (úroveň 4) C4937](compiler-warning-level-4-c4937.md)|*Text1*a*Text2*nejde odlišit jako argumenty*direktivy*.|
|[Upozornění kompilátoru (úroveň 4) C4938](compiler-warning-level-4-c4938.md)|*var*: Proměnná omezení plovoucí desetinné čárky může způsobit nekonzistentní výsledky v/FP: Strict nebo #pragma fenv_access.|
|[Upozornění kompilátoru C4939](compiler-warning-level-1-c4939.md)|#pragma vtordisp je zastaralá a v budoucí verzi vizuálu se odebere.C++|
|[Upozornění kompilátoru (úroveň 1) C4944](compiler-warning-level-1-c4944.md)|'*symbol*': nejde importovat symbol z '*assembly1*': protože '*symbol*' již v aktuálním oboru existuje.|
|[Upozornění kompilátoru (úroveň 1) C4945](compiler-warning-level-1-c4945.md)|'*symbol*': nelze importovat symbol z '*assembly1*': '*symbol*' již byl importován z jiného sestavení '*Assembly2*'|
|[Upozornění kompilátoru (úroveň 1) C4946](compiler-warning-level-1-c4946.md)|reinterpret_cast používá se mezi souvisejícími třídami: '*Class1*' a '*Class2*'|
|[Upozornění kompilátoru (úroveň 1) C4947](compiler-warning-level-1-c4947.md)|'*type_or_member*': označeno jako zastaralé|
|[Upozornění kompilátoru (úroveň 2) C4948](compiler-warning-level-2-c4948.md)|návratový typ '*přistupující*třídy ' neodpovídá typu posledního parametru odpovídající metody setter|
|[Upozornění kompilátoru (úroveň 1 a úroveň 4) C4949](compiler-warning-level-1-and-level-4-c4949.md)|direktivy pragma managed a unmanaged mají smysl, jenom když se zkompiluje s možností/CLR [: Option].|
|[Upozornění kompilátoru (úroveň 1, chyba) C4950](compiler-warning-c4950.md)|'*type_or_member*': označeno jako zastaralé|
|[Upozornění kompilátoru (úroveň 1) C4951](compiler-warning-level-1-c4951.md)|'*Function*' se od shromáždění dat profilu upravovala; data profilu funkce se nepoužijí.|
|[Upozornění kompilátoru (úroveň 1) C4952](compiler-warning-level-1-c4952.md)|'*Function*': v databázi programu '*pgd_file*' nebyla nalezena žádná data profilu|
|[Upozornění kompilátoru (úroveň 1) C4953](compiler-warning-level-1-c4953.md)|Inlineing*Function*se od shromáždění dat profilu upravovala. data profilu se nepoužijí.|
|Upozornění kompilátoru C4954|'*Function*': není profilované (obsahuje výraz přepínače __int64)|
|Upozornění kompilátoru C4955|'*import2*': import se ignoruje; již importováno z '*import1*'|
|[Upozornění kompilátoru (úroveň 1, chyba) C4956](compiler-warning-c4956.md)|*typ*: Tento typ nejde ověřit.|
|[Upozornění kompilátoru (úroveň 1, chyba) C4957](compiler-warning-c4957.md)|'*cast*': explicitní přetypování z '*cast_from*' na '*cast_to*' nelze ověřit|
|[Upozornění kompilátoru (úroveň 1, chyba) C4958](compiler-warning-c4958.md)|'*Operation*': aritmetický ukazatel nelze ověřit|
|[Upozornění kompilátoru (úroveň 1, chyba) C4959](compiler-warning-c4959.md)|nejde definovat nespravovaný typtypu v/CLR: safe, protože přístup k jeho členům poskytuje neověřitelný kód.|
|[Upozornění kompilátoru (úroveň 4) C4960](compiler-warning-level-4-c4960.md)|*funkce ' function*' je příliš velká pro profilaci|
|[Upozornění kompilátoru (úroveň 1) C4961](compiler-warning-c4961.md)|Žádná data profilu se nesloučila do souboru. PGD, optimalizace na základě profilu jsou zakázané.|
|[Upozornění kompilátoru (úroveň 4) C4962](compiler-warning-c4962.md)|'*Function*': Optimalizace na základě profilu jsou zakázané, protože optimalizace způsobily nekonzistenci dat profilu.|
|Upozornění kompilátoru (úroveň 1) C4963|'*Description*': nebyla nalezena žádná data profilu; v instrumentované buildu se použily různé možnosti kompilátoru.|
|[Upozornění kompilátoru (úroveň 1) C4964](compiler-warning-level-1-c4964.md)|Nebyly zadány žádné možnosti optimalizace; informace o profilu nebudou shromažďovány.|
|[Upozornění kompilátoru (úroveň 1) C4965](compiler-warning-level-1-c4965.md)|implicitní pole typu Integer 0; použít nullptr nebo explicitní přetypování|
|Upozornění kompilátoru (úroveň 1) C4966|klíčové slovo*Function*má __code_seg anotaci s nepodporovaným názvem segmentu, Poznámka se ignoruje.|
|Upozornění kompilátoru C4970|konstruktor Delegate: cílový objekt se ignoruje, protože*typ*je statický.|
|Upozornění kompilátoru (úroveň 1) C4971|Pořadí argumentů: \<> cílového objektu, \<> cílové funkce pro konstruktor Delegate je zastaralé, použijte \<cílovou funkci >, \<cílový objekt = "" >|
|[Upozornění kompilátoru (úroveň 1, chyba) C4972](compiler-warning-c4972.md)|Přímá úprava nebo zpracování výsledku operace unbox, protože l-hodnotu nelze ověřit|
|Upozornění kompilátoru (úroveň 1) C4973|*symbol*: označený jako zastaralý|
|Upozornění kompilátoru (úroveň 1) C4974|*symbol*: označený jako zastaralý|
|Upozornění kompilátoru (úroveň 3) C4981|Warbird: funkce Functions označená jako __forceinline není vložená, protože obsahuje sémantiku výjimky.|
|[Upozornění kompilátoru C4984](compiler-warning-c4984.md)|If constexpr je rozšíření jazyka C++ 17.|
|Upozornění kompilátoru (úroveň 3) C4985|'*symbol_name*': atributy nejsou přítomny u předchozí deklarace.|
|[Upozornění kompilátoru C4986](compiler-warning-c4986.md)|*deklarace*: specifikace výjimky neodpovídá předchozí deklaraci.|
|Upozornění kompilátoru (úroveň 4) C4987|použito nestandardní rozšíření: 'throw (...)'|
|Upozornění kompilátoru (úroveň 4) C4988|'*Variable*': proměnná je deklarována mimo obor třídy/funkce|
|Upozornění kompilátoru (úroveň 4) C4989|'*Type*': typ má konfliktní definice.|
|Upozornění kompilátoru (úroveň 3) C4990|Warbird: *zpráva*|
|Upozornění kompilátoru (úroveň 3) C4991|Warbird: funkce*Functions*označená jako __forceinline není vložená, protože úroveň ochrany pro inlineing je větší než nadřazená úroveň.|
|Upozornění kompilátoru (úroveň 3) C4992|Warbird: funkce '*Function*' označená jako __forceinline není vložená, protože obsahuje vložené sestavení, které nelze chránit|
|[Upozornění kompilátoru (úroveň 3) C4995](compiler-warning-level-3-c4995.md)|'*Function*': název byl označen jako zastaralý #pragma|
|[Upozornění kompilátoru (úroveň 3) C4996](compiler-warning-level-3-c4996.md)|"*zastaralé-deklarace*": vyřazení *-zpráva* (nebo "byla deklarována jako zastaralá")|
|[Upozornění kompilátoru (úroveň 1) C4997](compiler-warning-level-1-c4997.md)|*Class: Třída typu coclass*neimplementuje rozhraní COM nebo pseudo rozhraní.|
|Upozornění kompilátoru (úroveň 1) C4998|OČEKÁVANÉ selhání: *očekáváno*(*hodnota*)|
|[Upozornění kompilátoru C4999](compiler-warning-level-1-c4999.md)|NEZNÁMÉ upozornění, zvolte prosím příkaz technická podpora v nabídce Visual C++ Help, nebo otevřete soubor s podporou technické podpory, kde najdete další informace.|
|Upozornění kompilátoru C5022|*Type*: je zadaných víc konstruktorů Move.|
|Upozornění kompilátoru C5023|'*Type*': zadáno více operátorů přiřazení přesunutí|
|Upozornění kompilátoru (úroveň 4) C5024|*Type*: konstruktor Move byl implicitně definovaný jako odstraněný.|
|Upozornění kompilátoru (úroveň 4) C5025|*Type*: operátor Move Assignment byl implicitně definovaný jako odstraněný.|
|Upozornění kompilátoru (úroveň 1 a úroveň 4) C5026|*Type*: konstruktor Move byl implicitně definovaný jako odstraněný.|
|Upozornění kompilátoru (úroveň 1 a úroveň 4) C5027|*Type*: operátor Move Assignment byl implicitně definovaný jako odstraněný.|
|Upozornění kompilátoru (úroveň 1) C5028|*název*: Zarovnání zadané v předchozí deklaraci (*Number*) není v definici zadané.|
|Upozornění kompilátoru (úroveň 4) C5029|používá se nestandardní rozšíření: atributy zarovnání C++ v se použijí jenom na proměnné, datové členy a typy značek.|
|Upozornění kompilátoru (úroveň 3) C5030|atribut Attributese nerozpoznal.|
|Upozornění kompilátoru (úroveň 4) C5031|upozornění #pragma (pop): pravděpodobně neshoda, stav upozornění na vyjímání stavu vloženého do jiného souboru|
|Upozornění kompilátoru (úroveň 4) C5032|zjištěné upozornění #pragma (push) bez odpovídajícího #pragma upozornění (pop)|
|Upozornění kompilátoru (úroveň 1) C5033|Třída*úložiště*už není podporovanou třídou úložiště.|
|Upozornění kompilátoru C5034|Použití vnitřních vnitřních objektůzpůsobí, že *funkce* Function se zkompiluje jako kód hosta.|
|Upozornění kompilátoru C5035|použití funkce Function způsobí, že *funkce* Function se zkompiluje jako kód hosta.|
|Upozornění kompilátoru (úroveň 1) C5036|při kompilaci s/Hybrid: x86arm64 '*typ1*' do '*typ2*' se převádí ukazatel na funkci VarArgs.|
|Upozornění kompilátoru (chyba) C5037|*Member-Function*: mimo řádek definice člena šablony třídy nemůže mít výchozí argumenty.|
|[Upozornění kompilátoru (úroveň 4) C5038](c5038.md)|datový člen*člen1*se inicializuje po datovém členu '*member2*'.|
|Upozornění kompilátoru (úroveň 4) C5039|'*Function*': ukazatel nebo odkaz na potenciálně vyvolání funkce předaný do extern funkce jazyka C v rámci-EHC. Pokud tato funkce vyvolá výjimku, může dojít k nedefinovanému chování.|
|Upozornění kompilátoru (úroveň 3) C5040|specifikace dynamických výjimek jsou platné jenom v C++ 14 a dřívějších verzích; zpracovává se jako s výjimkou (false).|
|Upozornění kompilátoru (úroveň 1) C5041|'*definition*': definice mimo řádek pro statický datový člen constexpr není potřebná a je v c++ 17 zastaralá.|
|Upozornění kompilátoru (úroveň 3) C5042|'*deklarace*': deklarace funkcí v oboru bloku nelze zadat ' inline ' na standard C++; odebrat specifikátor inline|
|Upozornění kompilátoru (úroveň 2) C5043|*specifikace*: specifikace výjimky neodpovídá předchozí deklaraci.|
|Upozornění kompilátoru (úroveň 4) C5044|Argument pro možnost příkazového řádku odkazuje na cestu "*cesta*", která neexistuje.|
|[Upozornění kompilátoru C5045](c5045.md)|Kompilátor vloží Spectre zmírnění paměti, pokud je zadán přepínač/Qspectre|
|[Upozornění kompilátoru (úroveň 2) C5046](c5046.md)|'*Function*': Symbol zahrnující typ s interní vazbou není definovaný.|
| Upozornění kompilátoru (úroveň 1) C5047 | nestandardní \_ \_použití, pokud\_existuje, s moduly se nepodporuje. |
| Upozornění kompilátoru (úroveň 1) C5048 | Použití makra '*název_makra*' může mít za následek Nedeterministický výstup |
| Upozornění kompilátoru (úroveň 1) C5049 | *řetězec*: Vložení úplné cesty může mít za následek výstup závislý na počítači. |
| Upozornění kompilátoru (úroveň 1) C5050 | Možné nekompatibilní prostředí při importování modulu*module_name*: *problém* |
| Upozornění kompilátoru (úroveň 1) C5100 | \_\_Argumenty\_VAjsouvyhrazené\_ pro použití v makrech variadické.\_ |
| Upozornění kompilátoru (úroveň 1) C5101 | použití direktivy preprocesoru v seznamu argumentů makra jako funkce je nedefinované chování. |
| Upozornění kompilátoru (úroveň 1) C5102 | ignoruje se neplatná definice makra příkazového řádku*Value*. |
| Upozornění kompilátoru (úroveň 1) C5103 | vložením '*token1*' a '*token2*' není výsledkem platný token předzpracování |
| Upozornění kompilátoru (úroveň 1) C5104 | Našla se hodnota "*řetězec1*#*řetězec2*" v seznamu nahrazení makra. měli jste na mysli "*řetězec1*" "#*řetězec2*"? |
| Upozornění kompilátoru (úroveň 1) C5105 | rozšíření makra produkující definované má nedefinované chování. |
| Upozornění kompilátoru (úroveň 1) C5106 | makro se předefinovalo s jinými názvy parametrů. |
| Upozornění kompilátoru (úroveň 1) C5107 | chybí ukončovací znak*char*. |

## <a name="see-also"></a>Viz také:

[Chyby aC++ upozornění pro nástroje C/kompilátor a sestavení](../compiler-errors-1/c-cpp-build-errors.md) \
[Upozornění kompilátoru C4000-C5999](compiler-warnings-c4000-c5999.md)
