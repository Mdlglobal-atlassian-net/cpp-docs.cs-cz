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
- C4728
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
- C4728
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
ms.assetid: 22bd4392-f3be-445c-9f23-6126aebac901
ms.openlocfilehash: 638af32b27f8d66086f3a39b74ecd46fdbb4649d
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438169"
---
# <a name="compiler-warnings-c4600-through-c4799"></a>Upozornění kompilátoru C4600 až C4799

Články v této části dokumentace vysvětlují podmnožinu upozornění, která jsou generována kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Varovné zprávy

|Upozornění|Zpráva|
|-------------|-------------|
|[Upozornění kompilátoru (úroveň 1) C4600](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma ' název makra ': očekával se platný neprázdný řetězec.|
|[Upozornění kompilátoru (úroveň 1) C4602](compiler-warning-level-1-c4602.md)|#pragma pop_macro: pro tento identifikátor není push_macro žádný předchozí #pragma.|
|[Upozornění kompilátoru (úroveň 1) C4603](compiler-warning-level-1-c4603.md)|'*Identifier*': makro není definováno nebo je definice jiné po použití předkompilovaných hlaviček|
|Upozornění kompilátoru (úroveň 1) C4604|*typ*: předání argumentu hodnotou napříč nativním a spravovaným ohraničením vyžaduje platný kopírovací konstruktor. V opačném případě není chování modulu runtime definováno|
|Upozornění kompilátoru (úroveň 1) C4605|/D*makro*je zadané na aktuálním příkazovém řádku, ale při sestavení předkompilované hlavičky se nezadalo.|
|[Upozornění kompilátoru (úroveň 1) C4606](../../error-messages/compiler-warnings/compiler-warning-level-1-c4606.md)|#pragma upozornění: upozornění číslo se ignoruje; Upozornění analýzy kódu nejsou přidružená k úrovním upozornění|
|[Upozornění kompilátoru (úroveň 3) C4608](../../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|' union_member ' již byl inicializován jiným členem Union v seznamu inicializátorů ' union_member '|
|Upozornění kompilátoru (úroveň 3, chyba) C4609|'*typ1*' je odvozen z výchozího rozhraní '*Interface*' na typu '*typ2*'. Pro typ*typ1*použijte jiné výchozí rozhraní nebo přerušit vztah Base/odvozeného.|
|[Upozornění kompilátoru (úroveň 4) C4610](../../error-messages/compiler-warnings/compiler-warning-level-4-c4610.md)|u objektu Class se nedá vytvořit instance – je potřeba definovat uživatelsky definovaný konstruktor.|
|[Upozornění kompilátoru (úroveň 4) C4611](../../error-messages/compiler-warnings/compiler-warning-level-4-c4611.md)|interakce mezi funkcí a C++ zničením objektu není typu Portable.|
|[Upozornění kompilátoru (úroveň 1) C4612](compiler-warning-level-1-c4612.md)|Chyba v souboru include filename|
|[Upozornění kompilátoru (úroveň 1) C4613](compiler-warning-level-1-c4613.md)|'*symbol*': třída segmentu nemůže být změněna|
|[Upozornění kompilátoru (úroveň 1) C4615](../../error-messages/compiler-warnings/compiler-warning-level-1-c4615.md)|upozornění #pragma: Neznámý typ upozornění uživatele|
|[Upozornění kompilátoru (úroveň 1) C4616](../../error-messages/compiler-warnings/compiler-warning-level-1-c4616.md)|#pragma upozornění: číslo upozornění ' Number ' není platné upozornění kompilátoru|
|[Upozornění kompilátoru (úroveň 1) C4618](../../error-messages/compiler-warnings/compiler-warning-level-1-c4618.md)|parametry pragma zahrnovaly prázdný řetězec; Direktiva pragma se ignoruje.|
|[Upozornění kompilátoru (úroveň 3) C4619](../../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)|#pragma warning: neexistuje číslo upozornění 'number'|
|[Upozornění kompilátoru (úroveň 1) C4620](compiler-warning-level-1-c4620.md)|pro typ Type se nenašla žádná přípona operator + + s použitím formuláře s předponou.|
|[Upozornění kompilátoru (úroveň 1) C4621](../../error-messages/compiler-warnings/compiler-warning-level-1-c4621.md)|nebyla nalezena žádná přípona operátoru ' operator--' pro typ ' type ' s použitím formuláře předpony|
|[Upozornění kompilátoru (úroveň 3) C4622](compiler-warning-level-3-c4622.md)|přepisují se ladicí informace vytvořené při vytváření předkompilované hlavičky v souboru objektů: ' file '|
|[Upozornění kompilátoru (úroveň 4) C4623](../../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)|' odvozené třídy ': výchozí konstruktor byl implicitně definován jako odstraněný, protože výchozí konstruktor základní třídy je nepřístupný nebo odstraněný.|
|[Upozornění kompilátoru (úroveň 1) C4624](../../error-messages/compiler-warnings/compiler-warning-level-1-c4624.md)|' odvozené třídy ': destruktor byl implicitně definován jako odstraněný, protože destruktor základní třídy je nepřístupný nebo odstraněný.|
|[Upozornění kompilátoru (úroveň 4) C4625](../../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)|odvozená třída: konstruktor Copy byl implicitně definovaný jako odstraněný, protože konstruktor kopie základní třídy je nedostupný nebo odstraněný.|
|[Upozornění kompilátoru (úroveň 4) C4626](../../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)|odvozená třída: operátor přiřazení byl implicitně definovaný jako odstraněný, protože operátor přiřazení základní třídy je nedostupný nebo odstraněný.|
|[Upozornění kompilátoru (úroveň 1) C4627](../../error-messages/compiler-warnings/compiler-warning-level-1-c4627.md)|'\<> identifikátoru ': přeskočeno při hledání použití předkompilované hlavičky|
|[Upozornění kompilátoru (úroveň 1) C4628](../../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)|spřežky nejsou podporovány se -Ze. Sekvence znaků ' graf ' není interpretována jako alternativní token pro '% s '|
|[Upozornění kompilátoru (úroveň 4) C4629](compiler-warning-level-4-c4629.md)|používá se graf, znaková sekvence ' degraf ' interpretována jako token ' char ' (pokud to není to, co jste zamýšleli, vložte mezeru mezi tyto dva znaky)|
|[Upozornění kompilátoru (úroveň 1) C4630](../../error-messages/compiler-warnings/compiler-warning-level-1-c4630.md)|' symbol ': specifikátor třídy úložiště ' extern ' není pro definici členu platný|
|Upozornění kompilátoru (úroveň 2) C4631|Služba MSXML nebo XPath není k dispozici, komentáře k dokumentu XML nebudou zpracovány. reason|
|[Upozornění kompilátoru (úroveň 1) C4632](../../error-messages/compiler-warnings/compiler-warning-level-1-c4632.md)|Komentář k dokumentu XML: přístup k souboru byl odepřen: důvod|
|[Upozornění kompilátoru (úroveň 3) C4633](../../error-messages/compiler-warnings/compiler-warning-level-3-c4633.md)|Cíl komentáře dokumentu XML: Chyba: důvod|
|[Upozornění kompilátoru (úroveň 4) C4634](compiler-warning-level-4-c4634.md)|Cíl komentáře dokumentu XML: nejde použít: důvod.|
|[Upozornění kompilátoru (úroveň 3) C4635](compiler-warning-level-3-c4635.md)|Cíl komentáře k dokumentu XML: chybně vytvořený kód XML: důvod|
|[Upozornění kompilátoru (úroveň 3) C4636](compiler-warning-level-3-c4636.md)|Komentář k dokumentu XML aplikovaný na konstrukci: tag vyžaduje atribut Attribute, který není prázdný.|
|[Upozornění kompilátoru (Level 3 a Level 4) C4637](compiler-warning-level-3-c4637.md)|Cíl komentáře k dokumentu XML: \<zahrnout zahozenou > značku. Důvod|
|[Upozornění kompilátoru (úroveň 3) C4638](compiler-warning-level-3-c4638.md)|Cíl komentáře dokumentu XML: odkaz na neznámý symbol symbol.|
|[Upozornění kompilátoru (úroveň 4) C4639](../../error-messages/compiler-warnings/compiler-warning-level-4-c4639.md)|Chyba MSXML: komentáře k dokumentu XML nebudou zpracovány. Důvod|
|[Upozornění kompilátoru (úroveň 3) C4640 týkajícího](../../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)|'instance': stavba místního statického objektu není bezpečná pro přístup z více vláken|
|[Upozornění kompilátoru (úroveň 3) C4641](../../error-messages/compiler-warnings/compiler-warning-level-3-c4641.md)|Komentář k dokumentu XML má nejednoznačný zaměřovací odkaz:|
|[Upozornění kompilátoru (úroveň 3) C4645](compiler-warning-level-3-c4645.md)|funkce deklarovaná pomocí __declspec (Return) obsahuje příkaz return.|
|[Upozornění kompilátoru (úroveň 3) C4646](compiler-warning-level-3-c4646.md)|funkce deklarovaná pomocí __declspec (Return) má návratový typ, který není void.|
|Upozornění kompilátoru (úroveň 3) C4647|Změna chování: __is_pod (*typ*) má jinou hodnotu v předchozích verzích.|
|Upozornění kompilátoru (úroveň 3) C4648|standardní atribut carries_dependency se ignoruje.|
|Upozornění kompilátoru (úroveň 3) C4649|atributy se v tomto kontextu ignorují.|
|[Upozornění kompilátoru (úroveň 1) C4650](../../error-messages/compiler-warnings/compiler-warning-level-1-c4650.md)|informace o ladění nejsou v předkompilované hlavičce; k dispozici jsou jenom globální symboly z hlavičky.|
|[Upozornění kompilátoru (úroveň 1) C4651](../../error-messages/compiler-warnings/compiler-warning-level-1-c4651.md)|' definice ' zadaná pro předkompilovanou hlavičku, ale ne pro aktuální kompilaci|
|[Upozornění kompilátoru (úroveň 1) C4652](../../error-messages/compiler-warnings/compiler-warning-level-1-c4652.md)|možnost kompilátoru Option je nekonzistentní s předkompilovanou hlavičkou. aktuální možnost příkazového řádku přepíše, která je definována v předkompilované hlavičce.|
|[Upozornění kompilátoru (úroveň 2) C4653](../../error-messages/compiler-warnings/compiler-warning-level-2-c4653.md)|možnost kompilátoru Option je nekonzistentní s předkompilovanou hlavičkou. aktuální možnost příkazového řádku se ignoruje.|
|Upozornění kompilátoru (úroveň 4) C4654|Kód, který je umístěn před zahrnutím předkompilovaných hlaviček, bude ignorován. Přidejte kód do předkompilované hlavičky.|
|[Upozornění kompilátoru (úroveň 1) C4655](compiler-warning-level-1-c4655.md)|' symbol ': typ proměnné je nový od posledního sestavení nebo je jinak definován jinde|
|[Upozornění kompilátoru (úroveň 1) C4656](../../error-messages/compiler-warnings/compiler-warning-level-1-c4656.md)|' symbol ': datový typ je nový nebo se od posledního sestavení změnil, nebo je jinak definován jinde|
|[Upozornění kompilátoru (úroveň 1) C4657](compiler-warning-level-1-c4657.md)|výraz zahrnuje datový typ, který je nový od posledního buildu.|
|Upozornění kompilátoru (úroveň 1) C4658|' function ': prototyp funkce je nový od posledního sestavení nebo je deklarován jinak jinde|
|[Upozornění kompilátoru (úroveň 1) C4659](../../error-messages/compiler-warnings/compiler-warning-level-1-c4659.md)|#pragma ' pragma ': použití rezervovaného segmentu ' segment ' má nedefinované chování, použijte #pragma komentář (linker,...)|
|[Upozornění kompilátoru (úroveň 1) C4661](../../error-messages/compiler-warnings/compiler-warning-level-1-c4661.md)|' identifier ': není poskytnuta vhodná definice pro explicitní požadavek na vytvoření instance šablony|
|[Upozornění kompilátoru (úroveň 1) C4662](compiler-warning-level-1-c4662.md)|explicitní vytváření instancí; Šablona třídy ' identifier1 ' nemá žádnou definici, ze které by bylo možné specializovat ' identifier2 '|
|[Upozornění kompilátoru (úroveň 1) C4667](../../error-messages/compiler-warnings/compiler-warning-level-1-c4667.md)|' function ': není definována žádná šablona funkcí, která by odpovídala vynucenému vytváření instancí|
|[Upozornění kompilátoru (úroveň 4) C4668](../../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)|klíčové slovo ' symbol ' není definováno jako preprocesorové makro, nahrazuje se ' 0 ' pro ' direktivu '|
|[Upozornění kompilátoru (úroveň 1) C4669](../../error-messages/compiler-warnings/compiler-warning-level-1-c4669.md)|cast: nebezpečný převod: Class je objekt spravovaného typu.|
|[Upozornění kompilátoru (úroveň 4) C4670](compiler-warning-level-4-c4670.md)|' identifier ': Tato základní třída je nepřístupná|
|Upozornění kompilátoru (úroveň 4) C4671|' identifier ': konstruktor Copy je nepřístupný|
|[Upozornění kompilátoru (úroveň 4) C4672](compiler-warning-level-4-c4672.md)|' identifier1 ': dvojznačný. Poprvé se zobrazilo jako ' identifier2 '|
|[Upozornění kompilátoru (úroveň 4) C4673](../../error-messages/compiler-warnings/compiler-warning-level-4-c4673.md)|throw ' identifikátor ' následující typy se nebudou brát v úvahu na webu catch.|
|[Upozornění kompilátoru (úroveň 1) C4674](compiler-warning-level-1-c4674.md)|pro metodu by měla být použita deklarace static a musí obsahovat přesně jeden parametr.|
|Upozornění kompilátoru (úroveň 4) C4676|% s: destruktor je nepřístupný.|
|[Upozornění kompilátoru (úroveň 1) C4677](../../error-messages/compiler-warnings/compiler-warning-level-1-c4677.md)|' function ': podpis neprivátního členu obsahuje typ sestavení Private ' private_type '|
|[Upozornění kompilátoru (úroveň 1) C4678](compiler-warning-level-1-c4678.md)|základní třída base_type je míň dostupná než hodnota derived_type.|
|[Upozornění kompilátoru (úroveň 1) C4679](../../error-messages/compiler-warnings/compiler-warning-level-1-c4679.md)|člen: nešlo importovat člen.|
|[Upozornění kompilátoru (úroveň 4) C4680](../../error-messages/compiler-warnings/compiler-warning-level-4-c4680.md)|Class: Třída typu coclass nespecifikuje výchozí rozhraní.|
|[Upozornění kompilátoru (úroveň 4) C4681](compiler-warning-level-4-c4681.md)|Class: Třída typu coclass nespecifikuje výchozí rozhraní, které je zdrojem událostí.|
|[Upozornění kompilátoru (úroveň 4) C4682](compiler-warning-level-4-c4682.md)|' parametr ': nebyl zadán atribut směrového parametru, je použita výchozí hodnota [in]|
|[Upozornění kompilátoru (úroveň 1) C4683](../../error-messages/compiler-warnings/compiler-warning-level-1-c4683.md)|' function ': zdroj události má parametr ' out'-Parameter; cvičení opatrnosti při zapojení více obslužných rutin událostí|
|[Upozornění kompilátoru (úroveň 1) C4684](../../error-messages/compiler-warnings/compiler-warning-level-1-c4684.md)|' Attribute ': upozornění!! atribut může způsobit neplatnou generaci kódu: Používejte s opatrností.|
|[Upozornění kompilátoru (úroveň 1) C4685](compiler-warning-level-1-c4685.md)|při analýze parametrů šablony se očekávala hodnota > > našla > >.|
|[Upozornění kompilátoru (úroveň 3) C4686](../../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)|'user-defined type': možné změny v chování, změna ve vrácení konvence volání uživatelem definovaného typu|
|[Upozornění kompilátoru (chyba) C4687](../../error-messages/compiler-warnings/compiler-warning-c4687.md)|' class ': zapečetěná abstraktní třída nemůže implementovat rozhraní ' Interface '|
|[Upozornění kompilátoru (úroveň 1) C4688](../../error-messages/compiler-warnings/compiler-warning-level-1-c4688.md)|omezení: seznam omezení obsahuje typ sestavení Private.|
|Upozornění kompilátoru (úroveň 1) C4689|% c: nepodporovaný znak v #pragma detect_mismatch; #pragma se ignoruje.|
|[Upozornění kompilátoru (úroveň 4) C4690](../../error-messages/compiler-warnings/compiler-warning-level-4-c4690.md)|\[ emitidl (pop)]: více bodů POP než push|
|[Upozornění kompilátoru (úroveň 1) C4691](../../error-messages/compiler-warnings/compiler-warning-level-1-c4691.md)|Typ: odkazovaný typ se očekával v neodkazovaném sestavení ' file ', typ definovaný v aktuální jednotce překladu se místo toho použil.|
|[Upozornění kompilátoru (úroveň 1) C4692](../../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)|'function': podpis nesoukromého členu obsahuje sestavení privátního nativního typu 'native_type'|
|[Upozornění kompilátoru (úroveň 1, chyba) C4693](../../error-messages/compiler-warnings/compiler-warning-c4693.md)|' class ': zapečetěná abstraktní třída nemůže mít žádné členy instance ' člen instance '|
|[Upozornění kompilátoru (úroveň 1, chyba) C4694](../../error-messages/compiler-warnings/compiler-warning-c4694.md)|' class ': zapečetěná abstraktní třída nemůže mít základní třídu ' base_class '|
|Upozornění kompilátoru (úroveň 1) C4695|#pragma execution_character_set: znaková sada není podporovaný argument: aktuálně je podporovaná jenom znaková sada UTF-8.|
|Upozornění kompilátoru (úroveň 1) C4696|Možnost/ZBvalue1 je mimo rozsah; Předpokládá se ' hodnota2 '|
|[Upozornění kompilátoru (úroveň 1 a úroveň 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|použila se neinicializovaná lokální proměnná Name.|
|[Upozornění kompilátoru (úroveň 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)|používá se potenciálně neinicializovaná lokální proměnná Name.|
|[Upozornění kompilátoru (úroveň 4) C4702](../../error-messages/compiler-warnings/compiler-warning-level-4-c4702.md)|nedosažitelný kód|
|[Upozornění kompilátoru (úroveň 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|používá se potenciálně neinicializovaná lokální proměnná ukazatele% s.|
|[Upozornění kompilátoru (úroveň 4) C4706](../../error-messages/compiler-warnings/compiler-warning-level-4-c4706.md)|přiřazení v rámci podmíněného výrazu|
|[Upozornění kompilátoru (úroveň 4) C4709](../../error-messages/compiler-warnings/compiler-warning-level-4-c4709.md)|operátor čárka v rámci výrazu indexu pole|
|[Upozornění kompilátoru (úroveň 4) C4710](../../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)|'function': funkce není vložena|
|[Upozornění kompilátoru (úroveň 1) C4711](../../error-messages/compiler-warnings/compiler-warning-level-1-c4711.md)|funkce Function je vybraná pro automatické vložené rozšíření.|
|[Upozornění kompilátoru (úroveň 4) C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)|funkce Functions označená jako __forceinline není vložená.|
|[Upozornění kompilátoru (úroveň 1) C4715](../../error-messages/compiler-warnings/compiler-warning-level-1-c4715.md)|' function ': ne všechny cesty k ovládacím prvkům vrací hodnotu|
|[Upozornění kompilátoru (úroveň 1, chyba) C4716](../../error-messages/compiler-warnings/compiler-warning-level-1-c4716.md)|' function ': musí vracet hodnotu|
|[Upozornění kompilátoru (úroveň 1) C4717](../../error-messages/compiler-warnings/compiler-warning-level-1-c4717.md)|' function ': rekurzivní pro všechny cesty ovládacích prvků, funkce způsobí přetečení zásobníku za běhu.|
|[Upozornění kompilátoru (úroveň 4) C4718](compiler-warning-level-4-c4718.md)|volání funkce: rekurzivní volání nemá žádné vedlejší efekty, odstraňuje se|
|Upozornění kompilátoru (úroveň 1) C4719|Při zadání Qfast se našla dvojitá konstanta – použijte f jako příponu k označení jednoduché přesnosti.|
|Upozornění kompilátoru (úroveň 2) C4720|sestavy assembleru vloženého objektu: Message|
|Upozornění kompilátoru (úroveň 1) C4721|' function ': není k dispozici jako vnitřní|
|[Upozornění kompilátoru (úroveň 1) C4722](compiler-warning-level-1-c4722.md)|' function ': destruktor se nikdy nevrátí, potenciální nevrácená paměť|
|[Upozornění kompilátoru (úroveň 3) C4723](../../error-messages/compiler-warnings/compiler-warning-level-3-c4723.md)|potenciální dělení nulou|
|[Upozornění kompilátoru (úroveň 3) C4724](compiler-warning-level-3-c4724.md)|potenciální mod do 0|
|Upozornění kompilátoru (úroveň 3) C4725|instrukce můžou být u některých procesorů Pentium nepřesné.|
|[Upozornění kompilátoru (úroveň 1) C4727](../../error-messages/compiler-warnings/compiler-warning-level-1-c4727.md)|Soubor PCH s názvem pch_file se stejným časovým razítkem byl nalezen v obj_file_1 a obj_file_2.  Použití prvního souboru PCH.|
|Upozornění kompilátoru (úroveň 1) C4728|Možnost parametr/yl-se ignoruje, protože je povinný odkaz PCH.|
|Upozornění kompilátoru (úroveň 4) C4729|funkce je moc velká pro upozornění založená na grafu toku.|
|[Upozornění kompilátoru (úroveň 1) C4730](../../error-messages/compiler-warnings/compiler-warning-level-1-c4730.md) Upozornění kompilátoru (úroveň 1) C4730|' Main ': kombinování _m64 a výrazů s plovoucí desetinnou čárkou může mít za následek nesprávný kód|
|[Upozornění kompilátoru (úroveň 1) C4731](../../error-messages/compiler-warnings/compiler-warning-level-1-c4731.md)|' pointer ': registr ukazatele rámce ' register ' změněn pomocí vloženého kódu sestavení|
|Upozornění kompilátoru (úroveň 1) C4732|vnitřní% s není v této architektuře podporovaný.|
|[Upozornění kompilátoru (úroveň 1) C4733](../../error-messages/compiler-warnings/compiler-warning-level-1-c4733.md)|Vložené ASM přiřadí se k FS: 0: obslužná rutina není zaregistrovaná jako bezpečná obslužná rutina.|
|[Upozornění kompilátoru (úroveň 3) C4738](../../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)|ukládání 32bitového plovoucího výsledku do paměti, možná ztráta|
|[Upozornění kompilátoru (úroveň 1) C4739](compiler-warning-level-1-c4739.md)|odkaz na proměnnou var překračuje její prostor úložiště.|
|[Upozornění kompilátoru (úroveň 4) C4740](../../error-messages/compiler-warnings/compiler-warning-level-4-c4740.md)|tok ve vloženém kódu ASM nebo z něj potlačuje globální optimalizaci.|
|[Upozornění kompilátoru (úroveň 1) C4742](../../error-messages/compiler-warnings/compiler-warning-level-1-c4742.md)|klíčové slovo var má jiné zarovnání v Soubor1 a soubor2: číslo a číslo.|
|[Upozornění kompilátoru (úroveň 1) C4743](../../error-messages/compiler-warnings/compiler-warning-level-1-c4743.md)|typ má odlišnou velikost v ' Soubor1 ' a ' soubor2 ': Number a Number bytes|
|[Upozornění kompilátoru (úroveň 1) C4744](../../error-messages/compiler-warnings/compiler-warning-level-1-c4744.md)|klíčové slovo var má odlišný typ v ' Soubor1 ' a ' soubor2 ': ' typ1 ' a ' typ2 '|
|[Upozornění kompilátoru C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)|nestálý přístup k*výrazu*podléhá/volatile:\<iso&#124;MS > nastavení; Zvažte použití vnitřních funkcí __iso_volatile_load/Store|
|[Upozornění kompilátoru (úroveň 1) C4747](../../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)|Volání spravovaného vstupního bodu: spravovaný kód nesmí běžet pod zámkem zavaděče, včetně vstupního bodu knihovny DLL a volání z příchozího vstupního bodu knihovny DLL.|
|Upozornění kompilátoru (úroveň 4) C4749|podmíněně podporováno: OffsetOf použito*pro typ,* který není standard-layout|
|[Upozornění kompilátoru (úroveň 1) C4750](compiler-warning-level-1-c4750.md)|' identifier ': funkce s _alloca () je vložena do smyčky|
|Upozornění kompilátoru (úroveň 4) C4751|/arch: AVX se nevztahuje na procesory Intel (R) Streaming SIMD Extensions, které jsou v rámci vloženého kódu ASM.|
|Upozornění kompilátoru (úroveň 4) C4752|našli jsme rozšířená rozšíření vektoru Intel (R); Zvažte použití/arch: AVX|
|[Upozornění kompilátoru (úroveň 4) C4754](compiler-warning-level-4-c4754.md)|Pravidla převodu pro aritmetické operace v porovnání v:% s (% d) znamenají, že jednu větev nelze provést. Přetypování% s na% s (nebo podobný typ% d bajtů).|
|Upozornění kompilátoru C4755|Pravidla převodu pro aritmetické operace v porovnání v:% s (% d) znamenají, že jednu větev nejde spustit v vložené funkci. Přetypování% s na% s (nebo podobný typ% d bajtů).|
|[Upozornění kompilátoru (úroveň 2) C4756](../../error-messages/compiler-warnings/compiler-warning-level-2-c4756.md)|přetečení v konstantní aritmetické konstantě|
|Upozornění kompilátoru (úroveň 4) C4757|dolní index je velká hodnota bez znaménka. měli jste v úmyslu zápornou konstantu?|
|[Upozornění kompilátoru (úroveň 4) C4764](compiler-warning-level-4-c4764.md)|Objekty catch se nedají zarovnávat na víc než 16 bajtů.|
|Upozornění kompilátoru (úroveň 4) C4767|název oddílu% s je delší než 8 znaků a linker ho bude zkrátit.|
|Upozornění kompilátoru (úroveň 3) C4768|atributy __declspec před specifikací propojení se ignorují.|
|Upozornění kompilátoru C4770|částečně ověřený výčet*Name*se používá jako index.|
|Upozornění kompilátoru C4771|Hranice musí být vytvořené pomocí jednoduchého ukazatele; Vnitřní funkce MPX se ignoruje.|
|[Upozornění kompilátoru (úroveň 1, chyba) C4772](../../error-messages/compiler-warnings/compiler-warning-level-1-c4772.md)|#import odkazovalo na typ z chybějící knihovny typů; ' missing_type ' použit jako zástupný text|
|Upozornění kompilátoru (úroveň 4) C4774|'*String*': formátovací řetězec očekávaný v *čísle* argumentu není řetězcový literál.|
|Upozornění kompilátoru (úroveň 3) C4775|nestandardní rozšíření použité ve formátovacím řetězci*String*funkce*Function*|
|Upozornění kompilátoru (úroveň 1) C4776|znak%*Character*není ve formátovacím řetězci funkce Function povolený *.*|
|Upozornění kompilátoru (úroveň 4) C4777|'*Function*': formátovací řetězec '*řetězec*' vyžaduje argument typu '*typ1*', ale *číslo* argumentu variadické má typ '*typ2*'|
|Upozornění kompilátoru (úroveň 3) C4778|'*Function*': neukončený formátovací řetězec '*String*'|
|[Upozornění kompilátoru (úroveň 1) C4788](../../error-messages/compiler-warnings/compiler-warning-level-1-c4788.md)|' identifier ': identifikátor byl zkrácen na ' Number ' znaků|
|[Upozornění kompilátoru (úroveň 1) C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|vyrovnávací paměť ' identifikátor ' velikosti N bajtů bude přetečení. M bajtů se zapíše s posunem L.|
|Upozornění kompilátoru (úroveň 2) C4792|funkce% s deklarovaná pomocí: sysimport a odkazovaná z nativního kódu; Knihovna importu požadovaná pro propojení|
|[Upozornění kompilátoru (úroveň 1 a 3) C4793](../../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)|' function ': funkce kompilována jako nativní: \ n\t ' důvod '|
|[Upozornění kompilátoru (úroveň 1) C4794](compiler-warning-level-1-c4794.md)|segment thread local úložné proměnné% s se změnil z:% s na:% s.|
|[Upozornění kompilátoru (úroveň 1) C4799](../../error-messages/compiler-warnings/compiler-warning-level-1-c4799.md)|funkce Function nemá žádnou instrukci žádnou EMMS.|

## <a name="see-also"></a>Viz také

[Chyby aC++ upozornění pro nástroje C/kompilátor a Build](../compiler-errors-1/c-cpp-build-errors.md) a \
[Upozornění kompilátoru C4000-C5999](compiler-warnings-c4000-c5999.md)
