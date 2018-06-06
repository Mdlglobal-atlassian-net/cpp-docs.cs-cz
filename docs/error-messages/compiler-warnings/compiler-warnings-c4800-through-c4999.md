---
title: Kompilátoru C4800 upozornění prostřednictvím C5999 | Microsoft Docs
ms.date: 05/30/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4806
- C4807
- C4808
- C4809
- C4810
- C4811
- C4812
- C4813
- C4816
- C4817
- C4822
- C4825
- C4827
- C4837
- C4840
- C4841
- C4842
- C4843
- C4844
- C4872
- C4880
- C4881
- C4882
- C4900
- C4910
- C4912
- C4913
- C4916
- C4918
- C4920
- C4921
- C4925
- C4926
- C4932
- C4934
- C4935
- C4936
- C4937
- C4938
- C4939
- C4944
- C4947
- C4950
- C4951
- C4952
- C4953
- C4954
- C4955
- C4956
- C4957
- C4958
- C4959
- C4960
- C4961
- C4962
- C4963
- C4966
- C4970
- C4971
- C4972
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
- C4997
- C4998
- C4999
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
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06c4d65fe7b6ab2b0238c3a4e4cd081e2dc011b5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704747"
---
# <a name="compiler-warnings-c4800-through-c5999"></a>Kompilátoru C4800 upozornění prostřednictvím C5999

Články v této části dokumentace vysvětlují podmnožinu zprávy upozornění, které jsou generované kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Zprávy upozornění

|Upozornění|Zpráva|
|-------------|-------------|
|[Upozornění kompilátoru (úroveň 3) C4800](compiler-warning-level-3-c4800.md)|'*typ*': vynucení hodnoty bool: true, nebo "Nepravda" (upozornění výkonu)|
|[Upozornění kompilátoru (úroveň 1) C4803](compiler-warning-level-1-c4803.md)|'*metoda*': metoda pro vyvolání obsahuje třídu jiného úložiště od události, se*událostí*'|
|[Upozornění kompilátoru (úroveň 1) C4804](compiler-warning-level-1-c4804.md)|'*operace*': unsafe použití typu, bool, v operaci|
|[Upozornění kompilátoru (úroveň 1) C4805](compiler-warning-level-1-c4805.md)|'*operace*': unsafe kombinaci typu '*type1*"a typ"*type2*' v operaci|
|Upozornění kompilátoru (úroveň 1) C4806|'*operace*': nebezpečné operace: žádná hodnota typu '*type1*"propagovaných na typ"*type2*se může rovnat dané konstanta|
|Upozornění kompilátoru (úroveň 1) C4807|'*operace*': unsafe kombinaci typu '*type1*'a podepsaný bitová pole typu'*type2*.|
|Upozornění kompilátoru (úroveň 1) C4808|případ '*hodnotu*' není platná hodnota pro podmínku přepínač typu 'bool.|
|Upozornění kompilátoru (úroveň 1) C4809|příkaz Switch má popisek redundantní "default"; jsou uvedeny všechny možné 'případu, popisky|
|Upozornění kompilátoru (úroveň 1) C4810|Hodnota – Direktiva pragma pack(show) == n|
|Upozornění kompilátoru (úroveň 1) C4811|Hodnota – Direktiva pragma odpovídat (forScope, zobrazit) == – hodnota|
|Upozornění kompilátoru (úroveň 1) C4812|zastaralé deklarace styl: použijte '*new_syntax*' místo toho|
|Upozornění kompilátoru (úroveň 1) C4813|'*funkce*': funkce friend místní třídy musí mít bylo dříve deklarované|
|Upozornění kompilátoru (úroveň 4) C4816|'*param*': parametr má nulovou velikostí pole, která bude zkrácen (Pokud je objekt předán odkazem)|
|Upozornění kompilátoru (úroveň 1) C4817|'*člen*': Neplatné použití '.' pro přístup k tomuto členu; kompilátoru nahradí '->.|
|[Upozornění kompilátoru (úroveň 1) C4819](compiler-warning-level-1-c4819.md)|Tento soubor obsahuje znak, který není možné vyjádřit v aktuální znakové stránky (number). Uložte soubor ve formátu Unicode, aby se zabránilo ztrátě dat.|
|[Upozornění kompilátoru (úroveň 4) C4820](compiler-warning-level-4-c4820.md)|'*bajtů*'bajtů odsazení přidat po konstrukce'*member_name*.|
|[Upozornění kompilátoru (úroveň 1) C4821](compiler-warning-level-1-c4821.md)|Nelze určit typ kódování Unicode, uložte soubor s podpisem (BOM)|
|Upozornění kompilátoru (úroveň 1) C4822|'člen function': místní třídy – členská funkce nemá text|
|[Upozornění kompilátoru (úroveň 3) C4823](compiler-warning-level-3-c4823.md)|'*funkce*': používá přídavných ukazatelů ale unwind sémantiku nejsou povoleny. Zvažte použití/EHa|
|Upozornění kompilátoru (úroveň 2) C4826|Převod z '*type1*'do'*type2*' je rozšířeny. To může způsobit neočekávané modul runtime chování.|
|Upozornění kompilátoru (úroveň 3) C4827|Veřejná metoda 'ToString' s 0 parametry by měl být označen jako virtuální a přepsání|
|[Upozornění kompilátoru (úroveň 1) C4829](compiler-warning-level-1-c4829.md)|Může být nesprávné parametry hlavní funkce. Vezměte v úvahu, int hlavní (Platform::Array\<Platform::String ^ > ^ argv –).|
|[Upozornění kompilátoru (úroveň 1) C4835](compiler-warning-level-1-c4835.md)|'*proměnná*': inicializátoru pro exportovaná data se nespustí, dokud spravovaný kód je nejdřív provést v sestavení hostitele|
|Upozornění kompilátoru (úroveň 4) C4837|trigraph zjistil: '?? *znak*"nahradit"*znak*.|
|[Upozornění kompilátoru (úroveň 1) C4838](compiler-warning-level-1-c4838.md)|Převod z '*type_1*'do'*type_2*se vyžaduje zužující převod|
|[Upozornění kompilátoru (úroveň 3) C4839](compiler-warning-level-3-c4839.md)|nestandardní použití třídy se*typu*' jako argument funkce variadická|
|Upozornění kompilátoru (úroveň 4) C4840|Použijte jiný přenositelností třídy '*typu*' jako argument funkce variadická|
|Upozornění kompilátoru (úroveň 4) C4841|nestandardní rozšíření používané: označení složené člen použít v offsetof –|
|Upozornění kompilátoru (úroveň 4) C4842|výsledek offsetof "–", které se použijí k typu pomocí vícenásobná dědičnost nemusí být konzistentní mezi verzemi kompilátoru|
|Upozornění C4843 kompilátoru|'*type1*': Obslužná rutina výjimky z odkazu na typ pole nebo funkce nedostupný, použijte '*type2*' místo toho|
|Upozornění C4844 kompilátoru|"export modulu *module_name*;' je nyní upřednostňované syntaxe deklarace rozhraní modulu|
|[C4867 kompilátoru upozornění (chyba)](compiler-warning-c4867.md)|'*funkce*': chybí seznam argumentů volání funkce, pomocí '*volání*, vytvořte ukazatel na člena|
|[C4868 kompilátoru upozornění (úroveň 4)](compiler-warning-c4868.md)|'_soubor_(*line_number*), kompilátor nemusí vynutit pořadí vyhodnocení zleva doprava v seznamu braced inicializace|
|Upozornění kompilátoru (úroveň 2) C4872|plovoucí bodu dělení nulou zjistil při kompilování graf volání pro concurrency::parallel_for_each v: '*umístění*.|
|Upozornění kompilátoru (úroveň 1) C4880|přetypování z ' const *type_1*'do'*type_2*': přetypování rychle constness z ukazatel nebo odkaz může vést k nedefinované chování v amp omezený funkci|
|Upozornění kompilátoru (úroveň 4) C4881|v konstruktoru nebo destruktoru nebude možné volat pro proměnnou tile_static '*proměnná*.|
|Upozornění kompilátoru (úroveň 1) C4882|předání functors s operátory volání bez const concurrency::parallel_for_each je zastaralý.|
|Upozornění C4900 kompilátoru|IL neshody mezi '*tool1*'version'*version1*'a'*tool2*'version'*version2*.|
|[Upozornění kompilátoru (úroveň 1) C4905](compiler-warning-level-1-c4905.md)|široký řetězcový literál přetypován na 'LPSTR'|
|[Upozornění kompilátoru (úroveň 1) C4906](compiler-warning-level-1-c4906.md)|řetězcový literál přetypován na 'LPWSTR'|
|Upozornění kompilátoru (úroveň 1) C4910|'\<identifikátor >: '__declspec(dllexport)' a 'extern, jsou nekompatibilní na explicitní vytvoření instance|
|Upozornění kompilátoru (úroveň 1) C4912|'*atribut*': atribut má undefined chování na vnořené UDT|
|Upozornění kompilátoru (úroveň 4) C4913|uživatel definované binární operátor ',' existuje, ale žádné přetížení může převést všechny operandy, výchozí integrovanou binární operátor ',' použité|
|Upozornění kompilátoru (úroveň 1) C4916|aby bylo možné používat dispid '*popis*': je nutné zavést pomocí rozhraní|
|[Upozornění kompilátoru (úroveň 1) C4917](compiler-warning-level-1-c4917.md)|'*deklarátor*': identifikátor GUID může být přidružen pouze třídy, rozhraní nebo obor názvů|
|Upozornění kompilátoru (úroveň 4) C4918|'*znak*': neplatný znak v seznamu optimalizace – Direktiva pragma|
|Upozornění kompilátoru (úroveň 1) C4920|member_1 člen výčtu výčtového typu = value_1 ve výčtu výčtu již považovat za member_2 = value_2|
|Upozornění kompilátoru (úroveň 3) C4921|'*popis*': hodnota atributu '*atribut*' by neměl být určen násobkem|
|Upozornění kompilátoru (úroveň 1) C4925|'*metoda*': dispinterface metodu nelze volat ze skriptu|
|Upozornění kompilátoru (úroveň 1) C4926|'*identifikátor*': symbol je již definován: atributy ignorovat|
|[Upozornění kompilátoru (úroveň 1) C4927](compiler-warning-level-1-c4927.md)|Neplatný převod; implicitně použilo více než jeden uživatelem definovaný převod|
|[Upozornění kompilátoru (úroveň 1) C4928](compiler-warning-level-1-c4928.md)|nelegální inicializace kopírování; implicitně použit více než jeden uživatelem definovaný převod|
|[Upozornění kompilátoru (úroveň 1) C4929](compiler-warning-level-1-c4929.md)|'*souboru*': knihovny typů obsahuje sjednocení; ignoruje kvalifikátor 'embedded_idl –.|
|[Upozornění kompilátoru (úroveň 1) C4930](compiler-warning-level-1-c4930.md)|'*prototypu*': deklaraci není volaná funkce (byl definici proměnné určené?)|
|[Upozornění kompilátoru (úroveň 4) C4931](compiler-warning-level-4-c4931.md)|Předpokládáme, že knihovna typů byla sestavena pro ukazatele počtu bitů.|
|Upozornění kompilátoru (úroveň 4) C4932|__identifier (*identifikátor*) a \__identifier (*identifikátor*) jsou|
|Upozornění kompilátoru (úroveň 1) C4934|'__delegate(multicast)' je zastaralý, použijte '\__delegate' místo toho|
|Upozornění kompilátoru (úroveň 1) C4935|specifikátor přístupu sestavení změnil z '*přístup*.|
|Upozornění kompilátoru (úroveň 1, chyba) C4936|Tato __declspec je podporována pouze, když kompilujete s/CLR nebo/CLR: pure|
|Upozornění kompilátoru (úroveň 4) C4937|'*text1*'a'*text2*se neodlišuje jako argumenty pro *– direktiva*.|
|Upozornění kompilátoru (úroveň 4) C4938|'*var*': plovoucí redukční proměnnou bod může způsobit nekonzistentní výsledky v rámci /fp: striktní nebo fenv_access – #pragma|
|Upozornění C4939 kompilátoru|#pragma vtordisp je zastaralá a budou odebrány v budoucí verzi Visual C++|
|Upozornění kompilátoru (úroveň 1) C4944|'*symbol*': nelze importovat symbol '*assembly1*': jako*symbol*' již existuje v aktuálním oboru|
|[Upozornění kompilátoru (úroveň 1) C4945](compiler-warning-level-1-c4945.md)|'*symbol*': nelze importovat symbol '*assembly1*': jako*symbol*'již byla naimportována ze sestavení'*assembly2* '|
|[Upozornění kompilátoru (úroveň 1) C4946](compiler-warning-level-1-c4946.md)|reinterpret_cast – používá se mezi související třídy: '*class1*'a'*class2*.|
|Upozornění kompilátoru (úroveň 1) C4947|'*typ nebo člen*': označené jako zastaralé|
|[Upozornění kompilátoru (úroveň 2) C4948](compiler-warning-level-2-c4948.md)|Návratový typ se*přistupujícího objektu*' neodpovídá poslední parametr typ odpovídající nastavovací metoda|
|[Upozornění kompilátoru (úrovně 1 a 4) C4949](compiler-warning-level-1-and-level-4-c4949.md)|direktivy 'spravované' a 'nespravované, dávat smysl jenom v případě, že kompilovat s ' / clr [: možnost].|
|Upozornění kompilátoru (úroveň 1, chyba) C4950|'*typ nebo člen*': označené jako zastaralé|
|Upozornění kompilátoru (úroveň 1) C4951|'*funkce*' bylo upraveno od data nebyla shromážděna, profil nepoužívá data profilu – funkce|
|Upozornění kompilátoru (úroveň 1) C4952|'*funkce*': v databázi programu nalezena žádná data profilu se*pgd_file*.|
|Upozornění kompilátoru (úroveň 1) C4953|Inlinee '*funkce*' bylo upraveno od data nebyla shromážděna, profil data profilu nepoužívá|
|Upozornění C4954 kompilátoru|'*funkce*': není profilovaným (obsahuje výraz přepínače __int64)|
|Upozornění C4955 kompilátoru|'*import2*': import ignorován; již byla naimportována ze '*import1*.|
|Upozornění kompilátoru (úroveň 1, chyba) C4956|'*typ*': Tento typ není ověřitelný|
|Upozornění kompilátoru (úroveň 1, chyba) C4957|'*přetypování*': explicitní přetypování z '*cast_from*'do'*cast_to*' není ověřitelný|
|Upozornění kompilátoru (úroveň 1, chyba) C4958|'*operace*': není ověřitelný aritmetika ukazatele|
|Upozornění kompilátoru (úroveň 1, chyba) C4959|nelze definovat nespravovaný typ '*typu*, v/CLR: safe vzhledem k tomu, že přístup k jeho členy vypočítá neověřitelný kód|
|Upozornění kompilátoru (úroveň 4) C4960|'*funkce*' je příliš dlouhý pro být vytvořený profil|
|Upozornění kompilátoru (úroveň 1) C4961|Žádná data profilu se sloučí .pgd souboru, zakázat optimalizace na základě profilu|
|Upozornění kompilátoru (úroveň 4) C4962|'*funkce*': optimalizace na základě profilu zakázán, protože optimalizace způsobily nekonzistenci dat profilu|
|Upozornění kompilátoru (úroveň 1) C4963|'*popis*': nalezena žádná data profilu; kompilátoru různé možnosti, které byly používány v instrumentovaného sestavení|
|[Upozornění kompilátoru (úroveň 1) C4964](compiler-warning-level-1-c4964.md)|Nebyly zadány žádné možnosti optimalizace; informace o profilu nebudou shromažďovány.|
|[Upozornění kompilátoru (úroveň 1) C4965](compiler-warning-level-1-c4965.md)|implicitní pole celé číslo 0; použít nullptr nebo explicitní přetypování|
|Upozornění kompilátoru (úroveň 1) C4966|'*funkce*' má anotaci __code_seg s názvem nepodporované segmentu, poznámky ignorovat|
|Upozornění C4970 kompilátoru|Delegovat konstruktor: cílový objekt ignorován, protože se*typ*' je statický|
|Upozornění kompilátoru (úroveň 1) C4971|Argument pořadí: \<cílový objekt >, \<cíle funkce > pro konstruktor delegáta je zastaralý, pomocí \<cíle funkce >, \<cílový objekt = "" >|
|Upozornění kompilátoru (úroveň 1, chyba) C4972|Přímo změnou nebo práce výsledek operace unbox jako lvalue neověřitelný|
|Upozornění kompilátoru (úroveň 1) C4973|'*symbol*': označené jako zastaralé|
|Upozornění kompilátoru (úroveň 1) C4974|'*symbol*': označené jako zastaralé|
|Upozornění kompilátoru (úroveň 3) C4981|Warbird: funkce '*funkce*' označen jako __forceinline není vložená protože obsahuje sémantiku výjimky|
|Upozornění kompilátoru (úroveň 3) C4985|Název symbolu ": atributy není k dispozici na předchozí deklarace.|
|[Upozornění kompilátoru C4986](compiler-warning-c4986.md)|'*deklarace*': specifikace výjimek neodpovídá předchozí deklarace|
|Upozornění kompilátoru (úroveň 4) C4987|použito nestandardní rozšíření: 'throw (...)'|
|Upozornění kompilátoru (úroveň 4) C4988|'*proměnná*': proměnná deklarována mimo rozsah třídy nebo funkce|
|Upozornění kompilátoru (úroveň 4) C4989|'*typ*': typ má konfliktní definice.|
|Upozornění kompilátoru (úroveň 3) C4990|Warbird: *zpráv*|
|Upozornění kompilátoru (úroveň 3) C4991|Warbird: funkce '*funkce*' označen jako __forceinline není vložená protože je větší než nadřazené úrovně ochrany inlinee|
|Upozornění kompilátoru (úroveň 3) C4992|Warbird: funkce '*funkce*' označen jako __forceinline není vložená protože obsahuje vložené sestavení, které nelze chránit|
|[Upozornění kompilátoru (úroveň 3) C4995](compiler-warning-level-3-c4995.md)|'*funkce*': název byl označen jako zastaralý #pragma|
|[Upozornění kompilátoru (úroveň 3) C4996](compiler-warning-level-3-c4996.md)|'*popis*': *zpráv*|
|Upozornění kompilátoru (úroveň 1) C4997|'*třída*': Třída typu coclass neimplementuje rozhraní modelu COM nebo pseudorozhraní|
|Upozornění kompilátoru (úroveň 1) C4998|OČEKÁVÁ se nezdařilo: *očekávání*(*hodnotu*)|
|Upozornění C4999 kompilátoru|Neznámý upozornění Zvolte prosím příkaz se na technickou podporu v nabídce Nápověda Visual C++, nebo otevřít soubor nápovědy se na technickou podporu pro další informace|
|Upozornění C5022 kompilátoru|'*typ*': více přesunutí konstruktory zadaný|
|Upozornění C5023 kompilátoru|'*typ*': více operátory přiřazení pro přesunutí zadaný|
|Upozornění kompilátoru (úroveň 4) C5024|'*typ*': přesunout konstruktor byl implicitně definován jako odstranit|
|Upozornění kompilátoru (úroveň 4) C5025|'*typ*': přesunout operátor přiřazení byl implicitně definován jako odstranit|
|Upozornění kompilátoru (úroveň 1 a 4) C5026|'*typ*': přesunout konstruktor byl implicitně definován jako odstranit|
|Upozornění kompilátoru (úroveň 1 a 4) C5027|'*typ*': přesunout operátor přiřazení byl implicitně definován jako odstranit|
|Upozornění kompilátoru (úroveň 1) C5028|'*název*': zarovnání zadaný v deklaraci předchozích (*číslo*) nebyly zadány v definici|
|Upozornění kompilátoru (úroveň 4) C5029|nestandardní rozšíření používané: zarovnání atributy v jazyce C++ vztahuje na proměnné, datové členy a pouze typy značek|
|Upozornění kompilátoru (úroveň 3) C5030|atribut '*atribut*' nebyla rozpoznána|
|Upozornění kompilátoru (úroveň 4) C5031|#pragma warning(pop): pravděpodobně neshoda, odebrání nabídnutých v jiném souboru stavu upozornění|
|Upozornění kompilátoru (úroveň 4) C5032|zjištěna #pragma warning(push) se žádné odpovídající warning(pop) #pragma|
|Upozornění kompilátoru (úroveň 1) C5033|'*třídy úložiště*' je již třída podporované úložiště|
|Upozornění C5034 kompilátoru|použití vnitřní '*vnitřní*' způsobí, že funkce *funkce* sestavují jako kód hosta|
|Upozornění C5035 kompilátoru|pomocí funkce '*funkce*' způsobí, že funkce *funkce* sestavují jako kód hosta|
|Upozornění kompilátoru (úroveň 1) C5036|vararg funkce Převod ukazatele, když kompilujete s /hybrid:x86arm64 '*type1*'do'*type2*.|
|Upozornění kompilátoru (chyba) C5037|'*– členská funkce*': definici z přesahujících člena třídy šablony nemůže mít výchozí argumenty|
|[Upozornění kompilátoru (úroveň 4) C5038](c5038.md)|– datový člen '*člen1*'bude inicializován po – datový člen'*člen2*.|
|Upozornění kompilátoru (úroveň 4) C5039|'*funkce*': ukazatel nebo odkaz na potenciálně vyvolání funkce předaný funkci extern C v části - EHc. Nedefinované chování může dojít, pokud je tato funkce vyvolá výjimku.|
|Upozornění kompilátoru (úroveň 3) C5040|specifikace výjimek dynamické jsou platné pouze v C ++ 14 a starší; práce jako s noexcept(false)|
|Upozornění kompilátoru (úroveň 1) C5041|'*definice*':--line definice pro constexpr statických dat člena není potřebné a je zastaralý součástí C ++ 17|
|Upozornění kompilátoru (úroveň 3) C5042|'*deklarace*': deklarace funkcí v oboru bloku nemůže být zadaný, vložené' ve standardní C++; odeberte specifikátor 'vložené.|
|Upozornění kompilátoru (úroveň 2) C5043|'*specifikace*': specifikace výjimek neodpovídá předchozí deklarace|
|Upozornění kompilátoru (úroveň 4) C5044|Argument pro možnost příkazového řádku *možnost* odkazuje na cestu, '*cesta*, který neexistuje|
