---
title: Upozornění kompilátoru C4600 až C4799
ms.date: 04/21/2019
f1_keywords:
- C4609
- C4658
- C4671
- C4676
- C4689
- C4695
- C4696
- C4719
- C4720
- C4721
- C4728"
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
helpviewer_keywords:
- C4609
- C4658
- C4671
- C4676
- C4689
- C4695
- C4696
- C4719
- C4720
- C4721
- C4728"
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
ms.assetid: 22bd4392-f3be-445c-9f23-6126aebac901
ms.openlocfilehash: 3df17b115797f4d68621854d072c41aca14a0fd8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227028"
---
# <a name="compiler-warnings-c4600-through-c4799"></a>Upozornění kompilátoru C4600 až C4799

Články v této části dokumentace vysvětlují podmnožinu varovné zprávy, které jsou generovány kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Zprávy upozornění

|Upozornění|Zpráva|
|-------------|-------------|
|[Upozornění kompilátoru (úroveň 1) C4600](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma "– makro name": očekával se platný neprázdný řetězec|
|[Upozornění kompilátoru (úroveň 1) C4602](compiler-warning-level-1-c4602.md)|#pragma pop_macro: 'název makra' žádné předchozí #pragma push_macro pro tento identifikátor|
|[Upozornění kompilátoru (úroveň 1) C4603](compiler-warning-level-1-c4603.md)|"*identifikátor*': Makro není definované nebo se definice liší od použití předkompilované hlavičky|
|Upozornění kompilátoru (úroveň 1) C4604|"*typ*': předání argumentů hodnotou mezi nativním a spravovaným kódem vyžaduje platný kopírovací konstruktor. V opačném případě nedefinované chování za běhu|
|Upozornění kompilátoru (úroveň 1) C4605|! /D *– makro*"zadaný na aktuálním příkazovém řádku, ale nebyl zadán, kdy byla vytvořena předkompilované hlavičky|
|[Upozornění kompilátoru (úroveň 1) C4606](../../error-messages/compiler-warnings/compiler-warning-level-1-c4606.md)|#pragma warning: "číslo upozornění' ignorovány; Upozornění analýzy kódu nejsou přidružená k úrovním upozornění|
|[Upozornění kompilátoru (úroveň 3) C4608](../../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|'union_member' již byl inicializován jiným členem Unie v seznamu inicializátorů, 'union_member.|
|Upozornění kompilátoru (úroveň 3, chyby) C4609|"*type1*"odvozuje od výchozího rozhraní"*rozhraní*'na typ'*type2*". Použít jiné výchozí rozhraní pro "*type1*", nebo zrušit vztah základní/odvozené.|
|[Upozornění kompilátoru (úroveň 4) C4610](../../error-messages/compiler-warnings/compiler-warning-level-4-c4610.md)|objekt 'class' možné nikdy instancovat - uživatelem definovaný konstruktor. vyžaduje|
|[Upozornění kompilátoru (úroveň 4) C4611](../../error-messages/compiler-warnings/compiler-warning-level-4-c4611.md)|interakce mezi 'function' a destrukcí objektu C++ není typu portable.|
|[Upozornění kompilátoru (úroveň 1) C4612](compiler-warning-level-1-c4612.md)|Chyba v názvu vloženého souboru|
|[Upozornění kompilátoru (úroveň 1) C4613](compiler-warning-level-1-c4613.md)|"*symbol*': nelze změnit třídu segmentu|
|[Upozornění kompilátoru (úroveň 1) C4615](../../error-messages/compiler-warnings/compiler-warning-level-1-c4615.md)|#pragma warning: Neznámý typ uživatelského upozornění|
|[Upozornění kompilátoru (úroveň 1) C4616](../../error-messages/compiler-warnings/compiler-warning-level-1-c4616.md)|#pragma warning: číslo upozornění 'number' není platné upozornění kompilátoru|
|[Upozornění kompilátoru (úroveň 1) C4618](../../error-messages/compiler-warnings/compiler-warning-level-1-c4618.md)|v parametrech direktivy pragma zahrnuté prázdný řetězec; pragma se ignoruje|
|[Upozornění kompilátoru (úroveň 3) C4619](../../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)|#pragma warning: neexistuje číslo upozornění 'number'|
|[Upozornění kompilátoru (úroveň 1) C4620](compiler-warning-level-1-c4620.md)|postfixová podoba ' operator ++' nalezen pro typ 'type', používá se prefixová podoba|
|[Upozornění kompilátoru (úroveň 1) C4621](../../error-messages/compiler-warnings/compiler-warning-level-1-c4621.md)|'operator--' pro typ 'type', používá se prefixová podoba se nenašla postfixová podoba|
|[Upozornění kompilátoru (úroveň 3) C4622](compiler-warning-level-3-c4622.md)|přepisují se ladicí informace vytvořené při vytváření předkompilované hlavičky v souboru objektů: 'file'|
|[Upozornění kompilátoru (úroveň 4) C4623](../../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)|'derived class': výchozí konstruktor byl implicitně definovaný jako odstranit, protože výchozí konstruktor základní třídy je nedostupné nebo odstraněné|
|[Upozornění kompilátoru (úroveň 1) C4624](../../error-messages/compiler-warnings/compiler-warning-level-1-c4624.md)|'derived class': destruktor byl implicitně definovaný jako odstranit, protože destruktor základní třídy je nedostupné nebo odstraněné|
|[Upozornění kompilátoru (úroveň 4) C4625](../../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)|'derived class': kopírovací konstuktor byl implicitně definovaný jako odstranit, protože kopírovací konstruktor základní třídy je nedostupné nebo odstraněné|
|[Upozornění kompilátoru (úroveň 4) C4626](../../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)|'derived class': operátor přiřazení je implicitně definovaný jako odstranit, protože operátor přiřazení základní třídy je nedostupné nebo odstraněné|
|[Upozornění kompilátoru (úroveň 1) C4627](../../error-messages/compiler-warnings/compiler-warning-level-1-c4627.md)|"\<identifikátor >': při hledání použití předkompilované hlavičky přeskočen|
|[Upozornění kompilátoru (úroveň 1) C4628](../../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)|spřežky nejsou podporovány se -Ze. Sekvence znaků 'digraph' není interpretována jako alternativní token pro '%s'|
|[Upozornění kompilátoru (úroveň 4) C4629](compiler-warning-level-4-c4629.md)|použít digraph, sekvence znaků 'digraph' interpretován jako token 'char' (vložení mezery mezi dvěma znaky. Pokud ne, co jste zamýšleli)|
|[Upozornění kompilátoru (úroveň 1) C4630](../../error-messages/compiler-warnings/compiler-warning-level-1-c4630.md)|'symbol': specifikátor storage-class "externí" neplatné v definici člena|
|Upozornění kompilátoru (úroveň 2) C4631|MSXML nebo XPath není k dispozici, dokument XML, který nezpracují se komentáře. Důvod|
|[Upozornění kompilátoru (úroveň 1) C4632](../../error-messages/compiler-warnings/compiler-warning-level-1-c4632.md)|Komentář k dokumentu XML: soubor – přístup odepřen: důvod|
|[Upozornění kompilátoru (úroveň 3) C4633](../../error-messages/compiler-warnings/compiler-warning-level-3-c4633.md)|Cíl komentáře dokumentu XML: Chyba: z důvodu|
|[Upozornění kompilátoru (úroveň 4) C4634](compiler-warning-level-4-c4634.md)|Cíl komentáře dokumentu XML: nelze použít: důvod|
|[Upozornění kompilátoru (úroveň 3) C4635](compiler-warning-level-3-c4635.md)|Cíl komentáře dokumentu XML: chybně vytvořený kód XML: důvod|
|[Upozornění kompilátoru (úroveň 3) C4636](compiler-warning-level-3-c4636.md)|Komentář k dokumentu XML použitý k sestavení kompletních: značka vyžaduje neprázdný atribut ' attribute '.|
|[Upozornění kompilátoru (úroveň 3 a 4) C4637](compiler-warning-level-3-c4637.md)|Cíl komentáře dokumentu XML: \<zahrnout > značky zahozeny. Důvod|
|[Upozornění kompilátoru (úroveň 3) C4638](compiler-warning-level-3-c4638.md)|Cíl komentáře dokumentu XML: odkaz na neznámý symbol 'symbol'.|
|[Upozornění kompilátoru (úroveň 4) C4639](../../error-messages/compiler-warnings/compiler-warning-level-4-c4639.md)|Chyba MSXML; dokumentu XML, který nezpracují se komentáře. Důvod|
|[Upozornění kompilátoru (úroveň 3) c4640 týkajícího](../../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)|'instance': stavba místního statického objektu není bezpečná pro přístup z více vláken|
|[Upozornění kompilátoru (úroveň 3) C4641](../../error-messages/compiler-warnings/compiler-warning-level-3-c4641.md)|Komentář k dokumentu XML má nejednoznačný křížový odkaz:|
|[Upozornění kompilátoru (úroveň 3) C4645](compiler-warning-level-3-c4645.md)|funkce deklarovaná pomocí __declspec(noreturn) má návratový příkaz|
|[Upozornění kompilátoru (úroveň 3) C4646](compiler-warning-level-3-c4646.md)|funkce deklarovaná pomocí __declspec(noreturn) má návratový typ jiný než void|
|Upozornění kompilátoru (úroveň 3) C4647|Změna chování: __is_pod (*typ*) má jinou hodnotu v předchozích verzích|
|Upozornění kompilátoru (úroveň 3) C4648|standardní atribut "carries_dependency" se ignoruje.|
|Upozornění kompilátoru (úroveň 3) C4649|atributy se ignorují. v tomto kontextu|
|[Upozornění kompilátoru (úroveň 1) C4650](../../error-messages/compiler-warnings/compiler-warning-level-1-c4650.md)|informace o ladění není v předkompilovanou hlavičkou; bude k dispozici jenom globální symboly z hlavičky|
|[Upozornění kompilátoru (úroveň 1) C4651](../../error-messages/compiler-warnings/compiler-warning-level-1-c4651.md)|zadaná pro předkompilovanou hlavičku, ale ne pro aktuální kompilaci definice|
|[Upozornění kompilátoru (úroveň 1) C4652](../../error-messages/compiler-warnings/compiler-warning-level-1-c4652.md)|"možnost" konzistentní s předkompilovanou hlavičkou; – možnost kompilátoru přepíše aktuální parametr příkazového řádku, který definovaný v předkompilované hlavičky|
|[Upozornění kompilátoru (úroveň 2) C4653](../../error-messages/compiler-warnings/compiler-warning-level-2-c4653.md)|"možnost" konzistentní s předkompilovanou hlavičkou; – možnost kompilátoru Ignorovat aktuální parametr příkazového řádku|
|Upozornění kompilátoru (úroveň 4) C4654|Kód umístěný před vložení předkompilované hlavičky řádku budou ignorovány. Přidejte kód do předkompilované hlavičky.|
|[Upozornění kompilátoru (úroveň 1) C4655](compiler-warning-level-1-c4655.md)|'symbol': typ proměnné je nový od nejnovějších sestavení, nebo je někde definovaný nějak jinak|
|[Upozornění kompilátoru (úroveň 1) C4656](../../error-messages/compiler-warnings/compiler-warning-level-1-c4656.md)|'symbol': datový typ je nový nebo se změnil od nejnovějšího buildu nebo je někde definovaný nějak jinak|
|[Upozornění kompilátoru (úroveň 1) C4657](compiler-warning-level-1-c4657.md)|součástí výrazu je datový typ, který je nový od nejnovějšího buildu|
|Upozornění kompilátoru (úroveň 1) C4658|'function': prototyp funkce je nový od nejnovějších sestavení, nebo je jinak jinde deklarovaný|
|[Upozornění kompilátoru (úroveň 1) C4659](../../error-messages/compiler-warnings/compiler-warning-level-1-c4659.md)|#pragma – direktiva "pragma": používání vyhrazeného segmentu 'segmentu' má nedefinované chování, použijte #pragma comment (linker,...)|
|[Upozornění kompilátoru (úroveň 1) C4661](../../error-messages/compiler-warnings/compiler-warning-level-1-c4661.md)|'identifier': zadaná pro šablony explicitní vytváření instancí požadavek žádná vhodná definice|
|[Upozornění kompilátoru (úroveň 1) C4662](compiler-warning-level-1-c4662.md)|explicitní vytváření instancí; Třída šablony 'identifier1' nemá žádnou definici, ze kterého chcete specializovat "identifier2.|
|[Upozornění kompilátoru (úroveň 1) C4667](../../error-messages/compiler-warnings/compiler-warning-level-1-c4667.md)|'function': definovaná žádná šablona funkcí, která odpovídá vynucenému vytváření instancí|
|[Upozornění kompilátoru (úroveň 4) C4668](../../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)|'symbol' není definován jako preprocesor makro, nahraďte '0' pro 'direktivu.|
|[Upozornění kompilátoru (úroveň 1) C4669](../../error-messages/compiler-warnings/compiler-warning-level-1-c4669.md)|'přetypovat': nebezpečný převod: "třída" je objekt spravovaného typu|
|[Upozornění kompilátoru (úroveň 4) C4670](compiler-warning-level-4-c4670.md)|'identifier': této základní třídy je nedostupný|
|Upozornění kompilátoru (úroveň 4) C4671|'identifier': kopírovací konstuktor je nedostupný|
|[Upozornění kompilátoru (úroveň 4) C4672](compiler-warning-level-4-c4672.md)|'identifier1': nejednoznačné. Poprvé zaznamenáno jako "identifier2.|
|[Upozornění kompilátoru (úroveň 4) C4673](../../error-messages/compiler-warnings/compiler-warning-level-4-c4673.md)|'identifier' vyvolání těchto typů nebude brát v lokalitě catch|
|[Upozornění kompilátoru (úroveň 1) C4674](compiler-warning-level-1-c4674.md)|"metoda" by se měl deklarovat 'static' a mít přesně jeden parametr.|
|Upozornění kompilátoru (úroveň 4) C4676|'%s': destruktor je nedostupný|
|[Upozornění kompilátoru (úroveň 1) C4677](../../error-messages/compiler-warnings/compiler-warning-level-1-c4677.md)|'function': podpis nesoukromého členu obsahuje typ sestavení private 'private_type.|
|[Upozornění kompilátoru (úroveň 1) C4678](compiler-warning-level-1-c4678.md)|Základní třída 'base_type' je méně dostupný než "derived_type"|
|[Upozornění kompilátoru (úroveň 1) C4679](../../error-messages/compiler-warnings/compiler-warning-level-1-c4679.md)|'member': nepovedlo se naimportovat člen|
|[Upozornění kompilátoru (úroveň 4) C4680](../../error-messages/compiler-warnings/compiler-warning-level-4-c4680.md)|'class': Konstrukt coclass nespecifikuje výchozí rozhraní|
|[Upozornění kompilátoru (úroveň 4) C4681](compiler-warning-level-4-c4681.md)|'class': Konstrukt coclass nespecifikuje výchozí rozhraní, který je zdrojem událostí|
|[Upozornění kompilátoru (úroveň 4) C4682](compiler-warning-level-4-c4682.md)|"parametr": žádný parametr směrového atributu zadán, výchozí [v]|
|[Upozornění kompilátoru (úroveň 1) C4683](../../error-messages/compiler-warnings/compiler-warning-level-1-c4683.md)|'function': Zdroj události má "out"-parameter; Postupujte obezřetně při připojení více obslužných rutin událostí|
|[Upozornění kompilátoru (úroveň 1) C4684](../../error-messages/compiler-warnings/compiler-warning-level-1-c4684.md)|'attribute': UPOZORNĚNÍ! atribut může způsobit vygenerování neplatného kódu: používejte opatrně,|
|[Upozornění kompilátoru (úroveň 1) C4685](compiler-warning-level-1-c4685.md)|byl očekáván ' >> ' najít ' >> "při analýze parametrů šablony|
|[Upozornění kompilátoru (úroveň 3) C4686](../../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)|'user-defined type': možné změny v chování, změna ve vrácení konvence volání uživatelem definovaného typu|
|[Kompilátor varování C4687 (chyba)](../../error-messages/compiler-warnings/compiler-warning-c4687.md)|'class': zapečetěná abstraktní třída nemůže implementovat rozhraní "rozhraní"|
|[Upozornění kompilátoru (úroveň 1) C4688](../../error-messages/compiler-warnings/compiler-warning-level-1-c4688.md)|"omezení": seznam omezení obsahuje typ sestavení private 'type'|
|Upozornění kompilátoru (úroveň 1) C4689|'%c': Nepodporovaný znak v #pragma detect_mismatch; #pragma ignorovat|
|[Upozornění kompilátoru (úroveň 4) C4690](../../error-messages/compiler-warnings/compiler-warning-level-4-c4690.md)|\[ emitidl (pop)]: Další POP než push|
|[Upozornění kompilátoru (úroveň 1) C4691](../../error-messages/compiler-warnings/compiler-warning-level-1-c4691.md)|'type': neodkazovaná sestavení 'file', typ definovaný v aktuální překladové jednotce použít místo toho se očekával odkazovaný typ|
|[Upozornění kompilátoru (úroveň 1) C4692](../../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)|'function': podpis nesoukromého členu obsahuje sestavení privátního nativního typu 'native_type'|
|[Upozornění kompilátoru (úroveň 1, chyba) C4693](../../error-messages/compiler-warnings/compiler-warning-c4693.md)|'class': zapečetěná abstraktní třída nemůže mít všechny instance členů člena instance.|
|[Upozornění kompilátoru (úroveň 1, chyba) C4694](../../error-messages/compiler-warnings/compiler-warning-c4694.md)|'class': zapečetěná abstraktní třída nemůže mít základní třídy "$base_class.|
|Upozornění kompilátoru (úroveň 1) C4695|#pragma execution_character_set: 'znaková sada' není podporovaný argument: momentálně se podporuje jenom "UTF-8' je podporován.|
|Upozornění kompilátoru (úroveň 1) C4696|/ Parametr ZBvalue1 je mimo rozsah; za předpokladu, že "hodnota2"|
|[Upozornění kompilátoru (úroveň 1 a 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|Neinicializovaná lokální proměnná "name" použít|
|[Upozornění kompilátoru (úroveň 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)|potenciální neinicializovaná lokální proměnná "name" použít|
|[Upozornění kompilátoru (úroveň 4) C4702](../../error-messages/compiler-warnings/compiler-warning-level-4-c4702.md)|Nedosažitelný kód|
|[Upozornění kompilátoru (úroveň 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|potenciálně neinicializovaná lokální proměnná ukazatele %s, který používá|
|[Upozornění kompilátoru (úroveň 4) C4706](../../error-messages/compiler-warnings/compiler-warning-level-4-c4706.md)|přiřazení podmíněného výrazu|
|[Upozornění kompilátoru (úroveň 4) C4709](../../error-messages/compiler-warnings/compiler-warning-level-4-c4709.md)|operátor čárka v rámci výrazu indexu pole|
|[Upozornění kompilátoru (úroveň 4) C4710](../../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)|'function': funkce není vložena|
|[Upozornění kompilátoru (úroveň 1) C4711](../../error-messages/compiler-warnings/compiler-warning-level-1-c4711.md)|Funkce 'function' vybraná pro automatické vložení rozšíření|
|[Upozornění kompilátoru (úroveň 4) C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)|Funkce označená jako __forceinline není vložená funkce|
|[Upozornění kompilátoru (úroveň 1) C4715](../../error-messages/compiler-warnings/compiler-warning-level-1-c4715.md)|'function': Ne všechny cesty ovládacích prvků vracet hodnotu|
|[Upozornění kompilátoru (úroveň 1, chyba) C4716](../../error-messages/compiler-warnings/compiler-warning-level-1-c4716.md)|'function': musí vracet hodnotu|
|[Upozornění kompilátoru (úroveň 1) C4717](../../error-messages/compiler-warnings/compiler-warning-level-1-c4717.md)|'function': rekurzivní pro všechny cesty ovládacích prvků, funkce způsobí za běhu přetečení zásobníku|
|[Upozornění kompilátoru (úroveň 4) C4718](compiler-warning-level-4-c4718.md)|volání funkce: rekurzivní volání nemá žádné vedlejší efekty, odstraňuje se|
|Upozornění kompilátoru (úroveň 1) C4719|Pokud Qfast - použít 'f' jako přípona pro indikaci přesnosti single se našla konstanta Double|
|Upozornění kompilátoru (úroveň 2) C4720|sestavy assembleru vloženého kódu v řádku: "zpráva"|
|Upozornění kompilátoru (úroveň 1) C4721|'function': není k dispozici jako vnitřní|
|[Upozornění kompilátoru (úroveň 1) C4722](compiler-warning-level-1-c4722.md)|'function': destruktor nikdy nevrací potenciální nevrácená paměť|
|[Upozornění kompilátoru (úroveň 3) C4723](../../error-messages/compiler-warnings/compiler-warning-level-3-c4723.md)|potenciální dělení 0|
|[Upozornění kompilátoru (úroveň 3) C4724](compiler-warning-level-3-c4724.md)|potenciální dělení se zbytkem 0|
|Upozornění kompilátoru (úroveň 3) C4725|instrukce nemusí být na některých procesorech Pentium přesná.|
|[Upozornění kompilátoru (úroveň 1) C4727](../../error-messages/compiler-warnings/compiler-warning-level-1-c4727.md)|Soubor PCH s názvem pch_file se stejným časovým razítkem se našel v obj_file_1 a obj_file_2.  Pomocí první soubor PCH.|
|Upozornění kompilátoru (úroveň 1) C4728|/ Yl-se ignoruje, protože je vyžadován odkaz na soubor PCH|
|Upozornění kompilátoru (úroveň 4) C4729|upozornění založená na funkce je moc velká pro graf toku|
|[Kompilátor varování (úroveň 1) C4730](../../error-messages/compiler-warnings/compiler-warning-level-1-c4730.md)upozornění kompilátoru (úroveň 1) C4730|"hlavní": směšování výrazů _m64 a plovoucí desetinná čárka výrazy mohou způsobit nesprávný kód|
|[Kompilátor varování (úroveň 1) C4731](../../error-messages/compiler-warnings/compiler-warning-level-1-c4731.md)|"ukazatelů": "zaregistrovat" upravil vložený kód sestavení registr ukazatelů rámců|
|Upozornění kompilátoru (úroveň 1) C4732|vnitřní '%s' není v této architektuře podporovaný.|
|[Kompilátor varování (úroveň 1) C4733](../../error-messages/compiler-warnings/compiler-warning-level-1-c4733.md)|Vložené asm přiřazení 'FS:0': není zaregistrovaný jako bezpečná obslužná rutina|
|[Kompilátor varování (úroveň 3) C4738](../../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)|ukládání 32bitového plovoucího výsledku do paměti, možná ztráta|
|[Upozornění kompilátoru (úroveň 1) C4739](compiler-warning-level-1-c4739.md)|odkaz na proměnnou 'var' překračuje její prostor úložiště.|
|[Kompilátor varování (úroveň 4) C4740](../../error-messages/compiler-warnings/compiler-warning-level-4-c4740.md)|Flow nebo z vloženého kódu asm potlačuje globální optimalizaci.|
|[Kompilátor varování (úroveň 1) C4742](../../error-messages/compiler-warnings/compiler-warning-level-1-c4742.md)|'příkaz var' má jiné zarovnání v 'file1' a 'file2': číslo a číslo|
|[Kompilátor varování (úroveň 1) C4743](../../error-messages/compiler-warnings/compiler-warning-level-1-c4743.md)|'type' má jinou velikost 'file1' a 'file2': číslo a počet bajtů|
|[Kompilátor varování (úroveň 1) C4744](../../error-messages/compiler-warnings/compiler-warning-level-1-c4744.md)|'příkaz var' má jiný typ v 'file1' a 'file2': 'type1' a 'type2'|
|[Kompilátor varování C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)|přístup typu "*výraz*' / volatile:\<iso&#124;ms > nastavení; zvažte použití vnitřních funkcí Using __iso_volatile_load/store|
|[Upozornění kompilátoru (úroveň 1) C4747](../../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)|Volání spravované 'entrypoint": Zámek zavaděče, včetně vstupního bodu DLL a volání dosáhlo ze vstupního bodu DLL se možná nespustí spravovaný kód|
|Upozornění kompilátoru (úroveň 4) C4749|podmíněně podporováno: na které se netýkají nestandardním rozložením typu se použil offsetof '*typ*.|
|[Upozornění kompilátoru (úroveň 1) C4750](compiler-warning-level-1-c4750.md)|'identifier': funkce s: _alloca() je vložená do smyčky|
|Upozornění kompilátoru (úroveň 4) C4751|/ arch: AVX se nevztahuje na Streaming SIMD Extensions Intel(R), která jsou ve vloženém kódu ASM|
|Upozornění kompilátoru (úroveň 4) C4752|Najít Intel(R) Advanced Vector Extensions; Zvažte použití/arch: AVX|
|[Upozornění kompilátoru (úroveň 4) C4754](compiler-warning-level-4-c4754.md)|Pravidla převodu pro aritmetické operace v porovnání v: %s(%d) znamenají, že jednu větev nejde provést. Přetypujte '%s' na '%s' (nebo podobný typ o %d bajtech).|
|Kompilátor varování C4755|Pravidla převodu pro aritmetické operace v porovnání v: %s(%d) znamenají, že jednu větev nejde provést ve vložené funkci. Přetypujte '%s' na '%s' (nebo podobný typ o %d bajtech).|
|[Upozornění kompilátoru (úroveň 2) C4756](../../error-messages/compiler-warnings/compiler-warning-level-2-c4756.md)|přetečení v aritmetice konstanty|
|Upozornění kompilátoru (úroveň 4) C4757|hodnota argumentu Subscript je velká hodnota bez znaménka, nechtěli jste použít zápornou konstantu?|
|[Upozornění kompilátoru (úroveň 4) C4764](compiler-warning-level-4-c4764.md)|Nelze zarovnat objekty catch na hodnotu větší než 16 bajtů.|
|Upozornění kompilátoru (úroveň 4) C4767|Název oddílu '%s' je delší než 8 znaků a bude zkrácen linkerem.|
|Upozornění kompilátoru (úroveň 3) C4768|atributy __declspec před specifikací propojení se ignorují.|
|Kompilátor varování C4770|částečně ověřený výčet "*název*se používá jako index.|
|Kompilátor varování C4771|Hranice musí být vytvořené pomocí jednoduchého ukazatele; Vnitřní funkce MPX se ignoruje|
|[Upozornění kompilátoru (úroveň 1, chyba) C4772](../../error-messages/compiler-warnings/compiler-warning-level-1-c4772.md)|#import odkazovala na typ z chybějící knihovny typů; používá jako zástupný symbol missing_type|
|Upozornění kompilátoru (úroveň 4) C4774|"*řetězec*': formátovací řetězec očekávaný v argumentu *číslo* není řetězcový literál|
|Upozornění kompilátoru (úroveň 3) C4775|používá se nestandardní rozšíření použité ve formátovacím řetězci "*řetězec*"funkce"*funkce*.|
|Upozornění kompilátoru (úroveň 1) C4776|' %*znak*"není povolena ve formátovacím řetězci funkce"*funkce*.|
|Upozornění kompilátoru (úroveň 4) C4777|"*funkce*': řetězec formátu"*řetězec*"vyžaduje argument typu"*type1*", ale variadický argument *číslo* má typ"*type2*.|
|Upozornění kompilátoru (úroveň 3) C4778|"*funkce*': neukončený formátovací řetězec"*řetězec*.|
|[Kompilátor varování (úroveň 1) C4788](../../error-messages/compiler-warnings/compiler-warning-level-1-c4788.md)|'identifier': identifikátor se zkrátil na znaků 'number'|
|[Kompilátor varování (úroveň 1) C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|'identifier' bajtů N velikost vyrovnávací paměti bude mít přeběhnutí; M bajtů se zapíše s posunem L|
|Upozornění kompilátoru (úroveň 2) C4792|Funkce '%s' deklarovaná pomocí: sysimport a odkazuje z nativního kódu; naimportujte knihovnu požadovanou pro propojení.|
|[Upozornění kompilátoru (úroveň 1 a 3) C4793](../../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)|'function': funkci zkompilovat jako nativní: \n\t'reason.|
|[Upozornění kompilátoru (úroveň 1) C4794](compiler-warning-level-1-c4794.md)|Segment úložiště thread local proměnné '%s' změněn z '%s' na '%s'|
|[Upozornění kompilátoru (úroveň 1) C4799](../../error-messages/compiler-warnings/compiler-warning-level-1-c4799.md)|Funkce 'function' nemá žádnou instrukci EMMS.|

## <a name="see-also"></a>Viz také:

[C /C++ nástroje chyby a upozornění kompilátoru a sestavení](../compiler-errors-1/c-cpp-build-errors.md) \
[Upozornění kompilátoru C4000 - C5999](compiler-warnings-c4000-c5999.md)
