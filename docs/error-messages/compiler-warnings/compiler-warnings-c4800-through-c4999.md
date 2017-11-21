---
title: "Kompilátoru C4800 upozornění prostřednictvím C5999 | Microsoft Docs"
ms.date: 10/25/2017
ms.technology: cpp-tools
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
- C5038
dev_langs: C++
ms.assetid: c3182430-8b3b-4ab2-a532-5cd436707dc8
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1bf919fbb1959af6fad031a7f32262466f6f49ff
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2017
---
# <a name="compiler-warnings-c4800-through-c5999"></a>Kompilátoru C4800 upozornění prostřednictvím C5999

Články v této části dokumentace obsahovat informace o podmnožinu upozornění kompilátoru Visual C++. Dostanete zde uvedené informace, nebo v okně výstupu v sadě Visual Studio, můžete vybrat číslo chyby a potom stiskněte klávesu F1.

> [!NOTE]
> Ne každý [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] chyby nebo upozornění je popsána v MSDN. Diagnostické zprávy v mnoha případech poskytuje všechny informace, které jsou k dispozici. Pokud se domníváte, že chybovou zprávu potřebuje další vysvětlení, můžete dejte nám vědět. Můžete použít formulář zpětné vazby na této stránce, nebo přejít na panelu nabídek v sadě Visual Studio a zvolte **pomoci**, **ohlásit chybu**, nebo můžete odeslat zprávu návrhu nebo chyb na [Microsoft Connect](http://connect.microsoft.com/VisualStudio).

Chyby a upozornění na veřejných fórech MSDN můžete najít další pomoc. [Jazyka Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) fórum je pro dotazy a v diskusích o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] syntaxi a kompilátoru jazyka. [Visual C++ Obecné](http://go.microsoft.com/fwlink/?LinkId=158194) fórum je pro dotazy o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] které nejsou popsané v dalších fóra. Můžete také zjistit nápovědu k nástroji chyby a upozornění na [Stack Overflow](http://stackoverflow.com/).

## <a name="in-this-section"></a>V tomto oddílu

|Upozornění|Zpráva|
|-------------|-------------|
|[Upozornění (úroveň 3) kompilátoru C4800](compiler-warning-level-3-c4800.md)|'type': vynucení hodnoty bool: true, nebo "Nepravda" (upozornění výkonu)|
|[C4803 kompilátoru upozornění (úroveň 1)](compiler-warning-level-1-c4803.md)|"metody": metoda pro vyvolání obsahuje třídu jiného úložiště od události, 'událost'|
|[C4804 kompilátoru upozornění (úroveň 1)](compiler-warning-level-1-c4804.md)|'operace': unsafe použití typu, bool, v operaci|
|[C4805 kompilátoru upozornění (úroveň 1)](compiler-warning-level-1-c4805.md)|'operace': unsafe směs typu "typ" a typu "typ" v operaci|
|Upozornění kompilátoru (úroveň 1) C4806|'operace': nebezpečné operace: žádná hodnota typu "typ" povýšit na typ "typ" může rovnat dané konstanta|
|Upozornění kompilátoru (úroveň 1) C4807|'operace': unsafe směs typu "typ" a podepsaný bitová pole typu "typ"|
|Upozornění kompilátoru (úroveň 1) C4808|případ 'Hodnota' není platná hodnota pro podmínku přepínač typu 'bool.|
|Upozornění kompilátoru (úroveň 1) C4809|příkaz Switch má popisek redundantní "default"; jsou uvedeny všechny možné 'případu, popisky|
|Upozornění kompilátoru (úroveň 1) C4810|Hodnota – Direktiva pragma pack(show) == n|
|Upozornění kompilátoru (úroveň 1) C4811|Hodnota – Direktiva pragma odpovídat (forScope, zobrazit) == – hodnota|
|Upozornění kompilátoru (úroveň 1) C4812|zastaralé deklarace styl: místo toho použijte 'new_syntax.|
|Upozornění kompilátoru (úroveň 1) C4813|'function': funkce friend místní třídy musí mít bylo dříve deklarované|
|Upozornění kompilátoru (úroveň 4) C4816|'param': parametr má nulovou velikostí pole, která bude zkrácen (Pokud je objekt předán odkazem)|
|Upozornění kompilátoru (úroveň 1) C4817|"člen": Neplatné použití '.' pro přístup k tomuto členu; nahradí kompilátoru '->.|
|[C4819 kompilátoru upozornění (úroveň 1)](compiler-warning-level-1-c4819.md)|Tento soubor obsahuje znak, který není možné vyjádřit v aktuální znakové stránky (number). Uložte soubor ve formátu Unicode, aby se zabránilo ztrátě dat.|
|[C4820 kompilátoru upozornění (úroveň 4)](compiler-warning-level-4-c4820.md)|odsazení 'bytes' bajtů přidáno po vytvoření 'member_name'|
|[C4821 kompilátoru upozornění (úroveň 1)](compiler-warning-level-1-c4821.md)|Nelze určit typ kódování Unicode, uložte soubor s podpisem (BOM)|
|Upozornění kompilátoru (úroveň 1) C4822|'člen function': místní třídy – členská funkce nemá text|
|[C4823 kompilátoru upozornění (úroveň 3)](compiler-warning-level-3-c4823.md)|'function': používá přídavných ukazatelů ale unwind sémantiku nejsou povoleny. Zvažte použití/EHa|
|Upozornění kompilátoru (úroveň 2) C4826|Převod z '*type1*'do'*type2*' je rozšířeny. To může způsobit neočekávané modul runtime chování.|
|Upozornění kompilátoru (úroveň 3) C4827|Veřejná metoda 'ToString' s 0 parametry by měl být označen jako virtuální a přepsání|
|[C4829 kompilátoru upozornění (úroveň 1)](compiler-warning-level-1-c4829.md)|Může být nesprávné parametry hlavní funkce. Vezměte v úvahu, int hlavní (Platform::Array\<Platform::String ^ > ^ argv –).|
|[C4835 kompilátoru upozornění (úroveň 1)](compiler-warning-level-1-c4835.md)|"proměnné": inicializátoru pro exportovaná data se nespustí, dokud spravovaný kód je nejdřív provést v sestavení hostitele|
|Upozornění kompilátoru (úroveň 4) C4837|trigraph zjistil: '?? *znak*"nahradit"*znak*.|
|[C4838 kompilátoru upozornění (úroveň 1)](compiler-warning-level-1-c4838.md)|Převod z 'type_1' do 'type_2' vyžaduje zužující převod|
|[Upozornění kompilátoru (úroveň 3) C4839](compiler-warning-level-3-c4839.md)|nestandardní použití třídy se*typu*' jako argument funkce variadická|
|Upozornění kompilátoru (úroveň 4) C4840|Použijte jiný přenositelností třídy '*typu*' jako argument funkce variadická|
|Upozornění kompilátoru (úroveň 4) C4841|nestandardní rozšíření používané: označení složené člen použít v offsetof –|
|Upozornění kompilátoru (úroveň 4) C4842|výsledek offsetof "–", které se použijí k typu pomocí vícenásobná dědičnost nemusí být konzistentní mezi verzemi kompilátoru|
|[C4867 kompilátoru upozornění (chyba)](compiler-warning-c4867.md)|'function': volání funkce chybí seznam argumentů; Vytvořte ukazatel na člena pomocí 'volání.|
|[C4868 kompilátoru upozornění (úroveň 4)](compiler-warning-c4868.md)|'_soubor_(*line_number*), kompilátor nemusí vynutit pořadí vyhodnocení zleva doprava v seznamu braced inicializace|
|Upozornění kompilátoru (úroveň 2) C4872|plovoucí bodu dělení nulou zjistil při kompilování graf volání pro concurrency::parallel_for_each v: '*umístění*.|
|Upozornění kompilátoru (úroveň 1) C4880|přetypování z 'const type_1' do 'type_2': přetypování rychle constness z ukazatel nebo odkaz může vést k nedefinované chování v amp omezený funkci|
|Upozornění kompilátoru (úroveň 4) C4881|v konstruktoru nebo destruktoru nebude možné volat pro proměnnou tile_static "proměnné"|
|Upozornění kompilátoru (úroveň 1) C4882|předání functors s operátory volání bez const concurrency::parallel_for_each je zastaralý.|
|Upozornění C4900 kompilátoru|IL neshody mezi 'tool1' verze 'version1' a 'tool2' verze 'version2.|
|[C4905 kompilátoru upozornění (úroveň 1)](compiler-warning-level-1-c4905.md)|široký řetězcový literál přetypován na 'LPSTR'|
|[C4906 kompilátoru upozornění (úroveň 1)](compiler-warning-level-1-c4906.md)|řetězcový literál přetypován na 'LPWSTR'|
|Upozornění kompilátoru (úroveň 1) C4910|'\<identifikátor >: '__declspec(dllexport)' a 'extern, jsou nekompatibilní na explicitní vytvoření instance|
|Upozornění kompilátoru (úroveň 1) C4912|'atribut': atribut má undefined chování na vnořené UDT|
|Upozornění kompilátoru (úroveň 4) C4913|uživatel definované binární operátor ',' existuje, ale žádné přetížení může převést všechny operandy, výchozí integrovanou binární operátor ',' použité|
|Upozornění kompilátoru (úroveň 1) C4916|aby bylo možné používat dispid '*popis*': je nutné zavést pomocí rozhraní|
|[C4917 kompilátoru upozornění (úroveň 1)](compiler-warning-level-1-c4917.md)|'deklarátor': identifikátor GUID může být přidružen pouze třídy, rozhraní nebo obor názvů|
|Upozornění kompilátoru (úroveň 4) C4918|'znak': neplatný znak v seznamu optimalizace – Direktiva pragma|
|Upozornění kompilátoru (úroveň 1) C4920|member_1 člen výčtu výčtového typu = value_1 ve výčtu výčtu již považovat za member_2 = value_2|
|Upozornění kompilátoru (úroveň 3) C4921|'*popis*': hodnota atributu '*atribut*' by neměl být určen násobkem|
|Upozornění kompilátoru (úroveň 1) C4925|"metody": dispinterface metodu nelze volat ze skriptu|
|Upozornění kompilátoru (úroveň 1) C4926|"identifikátor": symbol je již definován: atributy ignorovat|
|[C4927 kompilátoru upozornění (úroveň 1)](compiler-warning-level-1-c4927.md)|Neplatný převod; implicitně použilo více než jeden uživatelem definovaný převod|
|[C4928 kompilátoru upozornění (úroveň 1)](compiler-warning-level-1-c4928.md)|nelegální inicializace kopírování; implicitně použit více než jeden uživatelem definovaný převod|
|[C4929 kompilátoru upozornění (úroveň 1)](compiler-warning-level-1-c4929.md)|'file': knihovny typů obsahuje sjednocení; ignoruje kvalifikátor 'embedded_idl –.|
|[C4930 kompilátoru upozornění (úroveň 1)](compiler-warning-level-1-c4930.md)|'prototypu': deklaraci není volaná funkce (byl definici proměnné určené?)|
|[C4931 kompilátoru upozornění (úroveň 4)](compiler-warning-level-4-c4931.md)|Předpokládáme, že knihovna typů byla sestavena pro ukazatele počtu bitů.|
|Upozornění kompilátoru (úroveň 4) C4932|__identifier (*identifikátor*) a \__identifier (*identifikátor*) jsou|
|Upozornění kompilátoru (úroveň 1) C4934|'__delegate(multicast)' je zastaralý, použijte '\__delegate' místo toho|
|Upozornění kompilátoru (úroveň 1) C4935|specifikátor přístupu sestavení změnil z 'přístup.|
|Upozornění kompilátoru (úroveň 1, chyba) C4936|Tato __declspec je podporována pouze, když kompilujete s/CLR nebo/CLR: pure|
|Upozornění kompilátoru (úroveň 4) C4937|'text1' a 'text2, jsou jako argumenty pro "směrnice"|
|Upozornění kompilátoru (úroveň 4) C4938|'příkaz var': plovoucí redukční proměnnou bod může způsobit nekonzistentní výsledky v rámci /fp: striktní nebo fenv_access – #pragma|
|Upozornění C4939 kompilátoru|#pragma vtordisp je zastaralá a budou odebrány v budoucí verzi Visual C++|
|Upozornění kompilátoru (úroveň 1) C4944|'symbol': nelze importovat symbol 'assembly1': jako 'symbol' již existuje v aktuálním oboru|
|[C4945 kompilátoru upozornění (úroveň 1)](compiler-warning-level-1-c4945.md)|'symbol': nelze importovat symbol 'assembly1': jako 'symbol' již byla naimportována ze sestavení 'assembly2'|
|[C4946 kompilátoru upozornění (úroveň 1)](compiler-warning-level-1-c4946.md)|reinterpret_cast použito mezi souvisejícími třídami: 'class1' a 'class2'|
|Upozornění kompilátoru (úroveň 1) C4947|'typ nebo člen': označené jako zastaralé|
|[C4948 kompilátoru upozornění (úroveň 2)](compiler-warning-level-2-c4948.md)|Návratový typ "objekt" neodpovídá poslední parametr typ odpovídající nastavovací metoda|
|[C4949 kompilátoru upozornění (úroveň 1 a 4)](compiler-warning-level-1-and-level-4-c4949.md)|direktivy 'spravované' a 'nespravované, dávat smysl jenom v případě, že kompilovat s ' / clr [: možnost].|
|Upozornění kompilátoru (úroveň 1, chyba) C4950|'typ nebo člen': označené jako zastaralé|
|Upozornění kompilátoru (úroveň 1) C4951|Po profil, který data nebyla shromážděna, data profilu funkce nepoužívá upraven 'function'.|
|Upozornění kompilátoru (úroveň 1) C4952|'function': v programu databáze 'pgd_file' nalezena žádná data profilu|
|Upozornění kompilátoru (úroveň 1) C4953|Po profil, který data nebyla shromážděna, data profilu nepoužívá upraven Inlinee 'function'.|
|Upozornění C4954 kompilátoru|'function': není profilovaným (obsahuje výraz přepínače __int64)|
|Upozornění C4955 kompilátoru|'import2': import ignorován; již byla naimportována ze 'import1.|
|Upozornění kompilátoru (úroveň 1, chyba) C4956|'type': Tento typ není ověřitelný|
|Upozornění kompilátoru (úroveň 1, chyba) C4957|'přetypovat': explicitní přetypování z 'přetypování z' do 'cast_to' není ověřitelný|
|Upozornění kompilátoru (úroveň 1, chyba) C4958|'operace': není ověřitelný aritmetika ukazatele|
|Upozornění kompilátoru (úroveň 1, chyba) C4959|v/CLR: safe nemůže definovat nespravované typu "typ", protože přístup k jeho členy vypočítá neověřitelný kód|
|Upozornění kompilátoru (úroveň 4) C4960|'function' je příliš dlouhý pro být vytvořený profil|
|Upozornění kompilátoru (úroveň 1) C4961|Žádná data profilu se sloučí .pgd souboru, zakázat optimalizace na základě profilu|
|Upozornění kompilátoru (úroveň 4) C4962|'function': optimalizace na základě profilu zakázán, protože optimalizace způsobily nekonzistenci dat profilu|
|Upozornění kompilátoru (úroveň 1) C4963|'*popis*': nalezena žádná data profilu; kompilátoru různé možnosti, které byly používány v instrumentovaného sestavení|
|[C4964 kompilátoru upozornění (úroveň 1)](compiler-warning-level-1-c4964.md)|Nebyly zadány žádné možnosti optimalizace; informace o profilu nebudou shromažďovány.|
|[C4965 kompilátoru upozornění (úroveň 1)](compiler-warning-level-1-c4965.md)|implicitní pole celé číslo 0; použít nullptr nebo explicitní přetypování|
|Upozornění kompilátoru (úroveň 1) C4966|'*funkce*' má anotaci __code_seg s názvem nepodporované segmentu, poznámky ignorovat|
|Upozornění C4970 kompilátoru|Delegovat konstruktor: cílový objekt ignorován, protože se*typ*' je statický|
|Upozornění kompilátoru (úroveň 1) C4971|Argument pořadí: \<cílový objekt >, \<cíle funkce > pro konstruktor delegáta je zastaralý, pomocí \<cíle funkce >, \<cílový objekt = "" >|
|Upozornění kompilátoru (úroveň 1, chyba) C4972|Přímo změnou nebo práce výsledek operace unbox jako lvalue neověřitelný|
|Upozornění kompilátoru (úroveň 1) C4973|'*symbol*': označené jako zastaralé|
|Upozornění kompilátoru (úroveň 1) C4974|'*symbol*': označené jako zastaralé|
|Upozornění kompilátoru (úroveň 3) C4981|Warbird: funkce '*funkce*' označen jako __forceinline není vložená protože obsahuje sémantiku výjimky|
|Upozornění kompilátoru (úroveň 3) C4985|Název symbolu ": atributy není k dispozici na předchozí deklarace.|
|[C4986 upozornění kompilátoru](compiler-warning-c4986.md)|'*deklarace*': specifikace výjimek neodpovídá předchozí deklarace|
|Upozornění kompilátoru (úroveň 4) C4987|použito nestandardní rozšíření: 'throw (...)'|
|Upozornění kompilátoru (úroveň 4) C4988|'*proměnná*': proměnná deklarována mimo rozsah třídy nebo funkce|
|Upozornění kompilátoru (úroveň 4) C4989|'*typ*': typ má konfliktní definice.|
|Upozornění kompilátoru (úroveň 3) C4990|Warbird: *zpráv*|
|Upozornění kompilátoru (úroveň 3) C4991|Warbird: funkce '*funkce*' označen jako __forceinline není vložená protože je větší než nadřazené úrovně ochrany inlinee|
|Upozornění kompilátoru (úroveň 3) C4992|Warbird: funkce '*funkce*' označen jako __forceinline není vložená protože obsahuje vložené sestavení, které nelze chránit|
|[C4995 kompilátoru upozornění (úroveň 3)](compiler-warning-level-3-c4995.md)|'function': název byl označen jako zastaralý #pragma|
|[C4996 kompilátoru upozornění (úroveň 3)](compiler-warning-level-3-c4996.md)|'*popis*': *zpráv*|
|Upozornění kompilátoru (úroveň 1) C4997|'class': Třída typu coclass neimplementuje rozhraní modelu COM nebo pseudorozhraní|
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
