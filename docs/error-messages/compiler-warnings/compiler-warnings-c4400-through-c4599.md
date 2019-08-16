---
title: Upozornění kompilátoru C4400 až C4599
ms.date: 04/21/2019
f1_keywords:
- C4413
- C4415
- C4416
- C4417
- C4418
- C4419
- C4421
- C4423
- C4424
- C4425
- C4426
- C4427
- C4438
- C4442
- C4443
- C4444
- C4446
- C4447
- C4448
- C4449
- C4450
- C4452
- C4453
- C4454
- C4455
- C4472
- C4474
- C4475
- C4476
- C4478
- C4480
- C4482
- C4483
- C4491
- C4492
- C4493
- C4494
- C4495
- C4496
- C4497
- C4498
- C4499
- C4509
- C4519
- C4531
- C4542
- C4562
- C4568
- C4569
- C4573
- C4574
- C4575
- C4582
- C4583
- C4585
- C4586
- C4587
- C4588
- C4591
- C4592
- C4593
- C4594
- C4595
helpviewer_keywords:
- C4413
- C4415
- C4416
- C4417
- C4418
- C4419
- C4421
- C4423
- C4424
- C4425
- C4426
- C4427
- C4438
- C4442
- C4443
- C4444
- C4446
- C4447
- C4448
- C4449
- C4450
- C4451
- C4452
- C4453
- C4454
- C4455
- C4456
- C4457
- C4459
- C4472
- C4474
- C4475
- C4476
- C4478
- C4480
- C4482
- C4483
- C4491
- C4492
- C4493
- C4494
- C4495
- C4496
- C4497
- C4498
- C4499
- C4509
- C4519
- C4531
- C4542
- C4562
- C4568
- C4569
- C4573
- C4574
- C4575
- C4582
- C4583
- C4585
- C4586
- C4587
- C4588
- C4591
- C4592
- C4593
- C4594
- C4595
ms.assetid: b07850a5-ae89-48ea-bf9a-f0e30939f9b9
ms.openlocfilehash: 9f7886a88ebd98d5d7ab1848ea7a788967362ad7
ms.sourcegitcommit: d3829ae0c3db909f96057755a80665f5ea4896ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550439"
---
# <a name="compiler-warnings-c4400-through-c4599"></a>Upozornění kompilátoru C4400 až C4599

Články v této části dokumentace vysvětlují podmnožinu upozornění, která jsou generována kompilátorem.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Varovné zprávy

|Upozornění|Message|
|-------------|-------------|
|[Upozornění kompilátoru (úroveň 1) C4600](compiler-warning-level-1-c4600.md)|#pragma '*název makra*': očekával se platný neprázdný řetězec.|
|[Upozornění kompilátoru (úroveň 4) C4400](../../error-messages/compiler-warnings/compiler-warning-level-4-c4400.md)|*typ*: kvalifikátory const/volatile pro tento typ nejsou podporované.|
|[Upozornění kompilátoru (úroveň 1) C4401](../../error-messages/compiler-warnings/compiler-warning-level-1-c4401.md)|'*bitového pole*': člen je bitové pole|
|[Upozornění kompilátoru (úroveň 1) C4402](../../error-messages/compiler-warnings/compiler-warning-level-1-c4402.md)|musí používat operátor PTR|
|[Upozornění kompilátoru (úroveň 1) C4403](../../error-messages/compiler-warnings/compiler-warning-level-1-c4403.md)|Neplatný operátor PTR|
|[Upozornění kompilátoru (úroveň 3) C4404](../../error-messages/compiler-warnings/compiler-warning-level-3-c4404.md)|tečka v direktivě se ignoruje.|
|[Upozornění kompilátoru (úroveň 1) C4405](../../error-messages/compiler-warnings/compiler-warning-level-1-c4405.md)|'*Identifier*': identifikátor je vyhrazené slovo|
|[Upozornění kompilátoru (úroveň 1) C4406](../../error-messages/compiler-warnings/compiler-warning-level-1-c4406.md)|operand v direktivě se ignoruje.|
|[Upozornění kompilátoru (úroveň 1) C4407](../../error-messages/compiler-warnings/compiler-warning-level-1-c4407.md)|přetypování mezi různými ukazateli na reprezentace členů, kompilátor může generovat nesprávný kód.|
|[Upozornění kompilátoru (úroveň 4) C4408](../../error-messages/compiler-warnings/compiler-warning-level-4-c4408.md)|anonymní struktura&#124;Union nedeklarovala žádné datové členy.|
|[Upozornění kompilátoru (úroveň 1) C4409](../../error-messages/compiler-warnings/compiler-warning-level-1-c4409.md)|Neplatná velikost instrukce|
|[Upozornění kompilátoru (úroveň 1) C4410](../../error-messages/compiler-warnings/compiler-warning-level-1-c4410.md)|Neplatná velikost pro operand|
|[Upozornění kompilátoru (úroveň 1) C4411](../../error-messages/compiler-warnings/compiler-warning-level-1-c4411.md)|'*Identifier*': symbol se překládá na registr posunutí|
|[Upozornění kompilátoru (úroveň 2) C4412](../../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)|'*Function*': signatura funkce obsahuje typ '*Type*'; C++ objekty nejsou bezpečné předávat mezi čistým a smíšeným nebo nativním kódem.|
|Upozornění kompilátoru C4413|ClassName:: member: referenční člen je inicializovaný jako dočasný člen, který se po ukončení konstruktoru neuloží.|
|[Upozornění kompilátoru (úroveň 3) C4414](../../error-messages/compiler-warnings/compiler-warning-level-3-c4414.md)|'*Function*': krátký skok na funkci převedený na Near|
|Upozornění kompilátoru (úroveň 1) C4415|duplicate __declspec(code_seg('*name*'))|
|Upozornění kompilátoru (úroveň 1) C4416|__declspec (code_seg (...)) obsahuje prázdný řetězec: ignoruje se.|
|Upozornění kompilátoru (úroveň 1) C4417|explicitní vytváření instancí šablon nemůže mít __declspec (code_seg (...)): ignoruje se.|
|Upozornění kompilátoru (úroveň 1) C4418|__declspec (code_seg (...)) se u výčtu ignoruje.|
|Upozornění kompilátoru (úroveň 3) C4419|klíčové slovo '*symbol*' není nijak ovlivněno při použití na soukromou referenční třídu '*Class*'.|
|[Upozornění kompilátoru (úroveň 1) C4420](../../error-messages/compiler-warnings/compiler-warning-level-1-c4420.md)|'*checked_operator*': operátor není k dispozici, místo toho použijte*operátor ' operator*'; může dojít k ohrožení zabezpečení při kontrole za běhu.|
|Upozornění kompilátoru (úroveň 3) C4421|*parametr*: parametr odkazu u obnovitelné funkce je potenciálně nebezpečný.|
|Upozornění kompilátoru (úroveň 3) C4423|std:: bad_alloc: bude zachyceno třídou (*Type*) na řádku *číslo* .|
|Upozornění kompilátoru (úroveň 3) C4424|zachytit pro "*typ1*" před "*typ2*" na řádku *číslo*; Pokud je vyvolána výjimka std:: bad_alloc, může být výsledkem nepředvídatelné chování.|
|Upozornění kompilátoru (úroveň 1) C4425|Anotaci SAL nelze použít pro...|
|Upozornění kompilátoru (úroveň 1) C4426|příznaky optimalizace se změnily po zahrnutí hlavičky, můžou být z důvodu #pragma optimalizovat ().|
|Upozornění kompilátoru (úroveň 1) C4427|'*Operator*': přetečení v konstantním dělení, nedefinované chování|
|[Upozornění kompilátoru (úroveň 4) C4429](../../error-messages/compiler-warnings/compiler-warning-level-4-c4429.md)|název Universal-Character-Name může být neúplný nebo nesprávně vytvořený.|
|[Upozornění kompilátoru (chyba) C4430](../../error-messages/compiler-warnings/compiler-warning-c4430.md)|chybějící specifikátor typu: předpokládá se int Poznámka: C++nepodporuje default-int.|
|[Upozornění kompilátoru (úroveň 4) C4431](../../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md)|chybějící specifikátor typu: předpokládá se int Poznámka: Jazyk C už nepodporuje výchozí int.|
|[Upozornění kompilátoru (úroveň 4) C4434](../../error-messages/compiler-warnings/compiler-warning-level-4-c4434.md)|statický konstruktor musí mít privátní přístupnost; Změna na privátní přístup|
|[Upozornění kompilátoru (úroveň 4) C4435](../../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md)|'*Derived_Class*': Rozložení objektu pod/VD2 se změní kvůli virtuálnímu základu '*BASE_CLASS*'.|
|[Upozornění kompilátoru (úroveň 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)|dynamické\_přetypování z Virtual Base '*BASE_CLASS*' na '*Derived_Class*' v konstruktoru nebo destruktoru by mohlo selhat s částečně vytvořeným objektem|
|[Upozornění kompilátoru (úroveň 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)|dynamické\_přetypování z virtuální základní třídy '*BASE_CLASS*' na '*Derived_Class*' může v některých kontextech selhat.|
|Upozornění kompilátoru C4438|'*Function*': nelze jej vyvolat bezpečně v režimu/await: clrcompat. Pokud*funkce Functions*do CLR zavolá, může dojít k poškození HLAVí CLR.|
|[Upozornění kompilátoru (chyba) C4439](../../error-messages/compiler-warnings/compiler-warning-c4439.md)|'*Function*': definice funkce se spravovaným typem v podpisu musí mít konvenci volání __clrcall|
|[Upozornění kompilátoru (úroveň 1) C4440](../../error-messages/compiler-warnings/compiler-warning-level-1-c4440.md)|předefinování konvence volání z '*calling_convention1*' na '*calling_convenction2*' se ignoruje.|
|[Upozornění kompilátoru (úroveň 1) C4441](../../error-messages/compiler-warnings/compiler-warning-level-1-c4441.md)|konvence volání '*calling_convention1*' ignorována; místo toho se použila možnost*calling_convention2*.|
|Upozornění kompilátoru (úroveň 1) C4442|vložený ukončovací znak null v argumentu __annotation  Hodnota se zkrátí.|
|Upozornění kompilátoru (úroveň 1) C4443|očekávalo se, že parametr pragma bude mít hodnotu 0, 1 nebo 2.|
|Upozornění kompilátoru (úroveň 3) C4444|'*Identifier*': nejvyšší úroveň ' __unaligned ' není v tomto kontextu implementována|
|[Upozornění kompilátoru (úroveň 1) C4445](../../error-messages/compiler-warnings/compiler-warning-level-1-c4445.md)|'*Function*': virtuální metoda v typu&#124;' WinRT Managed ' nemůže být privátní|
|Upozornění kompilátoru (úroveň 1) C4446|*Type*: člen '*název1*' nejde mapovat na tento typ, protože je v konfliktu s názvem typu. Metoda se přejmenovala na*název2*.|
|Upozornění kompilátoru (úroveň 1) C4447|byl nalezen podpis Main bez modelu vláken. Zvažte použití operátoru int Main (Platform::\<Array Platform:: String ^ > ^ args).|
|Upozornění kompilátoru C4448|*typ*1 nemá výchozí rozhraní zadané v metadatech. Vybírání: "*typ2*", což může při běhu selhat.|
|Upozornění kompilátoru C4449|*typ*nezapečetěný typ by měl být označený jako [WebHostHidden].|
|Upozornění kompilátoru C4450|hodnota*typ1*by měla být označená jako [WebHostHidden], protože je odvozená od '*typ2*'.|
|Upozornění kompilátoru (úroveň 4) C4451|' classname1:: member ': Použití třídy ref class ' classname2:: member ' uvnitř tohoto kontextu může vést k neplatnému zařazování objektu napříč kontexty.|
|Upozornění kompilátoru (úroveň 1) C4452|'*Identifier*': veřejný typ nemůže být v globálním oboru. Musí být v oboru názvů, který je podřízeným názvem výstupního souboru. winmd.|
|Upozornění kompilátoru (úroveň 1) C4453|*typ*: Typ [WebHostHidden] by se neměl používat na publikované ploše typu public, který není [WebHostHidden].|
|Upozornění kompilátoru (úroveň 1) C4454|klíčové slovo*Function*je přetížené více než počtem vstupních parametrů, aniž by byl zadán parametr [DefaultOverload]. Vybírá se*deklarace*jako výchozí přetížení.|
|Upozornění kompilátoru (úroveň 1) C4455|operátor operator: identifikátory přípon literálů, které nezačínají podtržítkem, jsou vyhrazené.|
|[Upozornění kompilátoru (úroveň 4) C4456](compiler-warning-level-4-c4456.md)|deklarace '*Identifier*' skrývá předchozí místní deklaraci|
|[Upozornění kompilátoru (úroveň 4) C4457](compiler-warning-level-4-c4457.md)|deklarace '*Identifier*' skrývá parametr funkce|
|[Upozornění kompilátoru (úroveň 4) C4458](compiler-warning-level-4-c4458.md)|deklarace '*Identifier*' skrývá člena třídy|
|[Upozornění kompilátoru (úroveň 4) C4459](compiler-warning-level-4-c4459.md)|deklarace '*Identifier*' skrývá globální deklaraci|
|[Upozornění kompilátoru (úroveň 4) C4460](../../error-messages/compiler-warnings/compiler-warning-level-4-c4460.md)|Operátor "&#124;WinRT Managed" operator", má parametr předaný odkazem. Operátor {0}&#124;spravovaného WinRT máodlišnou sémantiku od C++ operátoru*cpp_operator*, chtěli jste ho předat hodnotou?|
|[Upozornění kompilátoru (úroveň 1) C4461](../../error-messages/compiler-warnings/compiler-warning-level-1-c4461.md)|*ClassName*: Tato třída má finalizační metodu! *finalizační*metoda, ale nemá žádný destruktor ~*dtor*|
|[Upozornění kompilátoru (úroveň 1, chyba) C4462](../../error-messages/compiler-warnings/compiler-warning-level-1-c4462.md)|'*Type*': nelze určit identifikátor GUID typu. Program může při běhu selhat.|
|[Upozornění kompilátoru (úroveň 4) C4463](compiler-warning-level-4-c4463.md)|plně přiřazení*hodnoty*k bitovému poli, které může uchovávat jenom hodnoty z '*MIN_VALUE*' na '*MAX_VALUE*'|
|[Upozornění kompilátoru (úroveň 4) C4464](../../error-messages/compiler-warnings/c4464.md)|relativní cesta zahrnutí obsahuje znak "..".|
|[Upozornění kompilátoru (úroveň 1) C4470](../../error-messages/compiler-warnings/compiler-warning-level-1-c4470.md)|direktivy pragma ovládacího prvku s plovoucí desetinnou čárkou se ignorují v/CLR|
|[Upozornění kompilátoru (úroveň 4) C4471](compiler-warning-level-4-c4471.md)|'*Enumeration*': Dopředná deklarace výčtu bez oboru musí mít podkladový typ (předpokládá se int).|
|Upozornění kompilátoru (úroveň 1) C4472|'*Identifier*' je nativní výčet: přidejte specifikátor přístupu (Private/Public) k deklaraci výčtu spravovaného WinRT&#124;.|
|[Upozornění kompilátoru (úroveň 1) C4473](c4473.md)|'*Function*': pro formátovací řetězec není předán dostatečný počet argumentů|
|Upozornění kompilátoru (úroveň 3) C4474|'*Function*': pro formátovací řetězec bylo předáno příliš mnoho argumentů|
|Upozornění kompilátoru (úroveň 3) C4475|'*Function*': modifikátor délky '*Modifikátor*' nelze použít se znakem pole typu '*znak*' ve specifikátoru formátu|
|Upozornění kompilátoru (úroveň 3) C4476|'*Function*': Neznámý znak pole typu '*Character*' ve specifikátoru formátu|
|[Upozornění kompilátoru (úroveň 1) C4477](c4477.md)|'*Function*': formátovací řetězec '*řetězec*' vyžaduje argument typu '*Type*', ale *číslo* argumentu variadické je typu '*Type*'|
|Upozornění kompilátoru (úroveň 1) C4478|'*Function*': poziční a Nepoziční zástupné symboly nelze kombinovat ve stejném formátovacím řetězci|
|Upozornění kompilátoru (chyba) C4480|používá se nestandardní rozšíření: zadání podkladového typupro výčet Enum.|
|[Upozornění kompilátoru (úroveň 4) C4481](../../error-messages/compiler-warnings/compiler-warning-level-4-c4481.md)|používá se nestandardní rozšíření: specifikátor override "*klíčové slovo*"|
|Upozornění kompilátoru C4482|používá se nestandardní rozšíření: vkvalifikovaném názvu se používá výčet Enum.|
|Upozornění kompilátoru (úroveň 1, chyba) C4483|Chyba syntaxe: očekávalo C++ se klíčové slovo.|
|[Upozornění kompilátoru (chyba) C4484](../../error-messages/compiler-warnings/compiler-warning-c4484.md)|'*override_function*': odpovídá metodě Base ref class '*base_class_function*', ale není označeno jako ' Virtual ', ' New ' nebo ' override '; Předpokládá se klíčové slovo New (a ne Virtual).|
|[Upozornění kompilátoru (chyba) C4485](../../error-messages/compiler-warnings/compiler-warning-c4485.md)|'*override_function*': odpovídá metodě Base ref class '*base_class_function*', ale není označeno jako ' New ' nebo ' override '; Předpokládá se klíčové slovo New (a Virtual).|
|[Upozornění kompilátoru (úroveň 1) C4486](../../error-messages/compiler-warnings/compiler-warning-level-1-c4486.md)|'*Function*': soukromá virtuální metoda třídy ref class nebo value class by měla být označena jako Sealed|
|[Upozornění kompilátoru (úroveň 4) C4487](../../error-messages/compiler-warnings/compiler-warning-level-4-c4487.md)|'*derived_class_function*': shoduje se se zděděnou nevirtuální metodou '*base_class_function*', ale není explicitně označena jako ' New '|
|[Upozornění kompilátoru (úroveň 1) C4488](../../error-messages/compiler-warnings/compiler-warning-level-1-c4488.md)|'*Function*': vyžaduje klíčové slovo '*klíčové*slovo ' pro implementaci metody rozhraní '*interface_method*'|
|[Upozornění kompilátoru (úroveň 1) C4489](../../error-messages/compiler-warnings/compiler-warning-level-1-c4489.md)|'*specifikátor*': není povoleno pro metodu rozhraní '*Method*'; Specifikátory přepsání jsou povolené jenom pro metody třídy ref class a value class.|
|[Upozornění kompilátoru (úroveň 1) C4490](../../error-messages/compiler-warnings/compiler-warning-level-1-c4490.md)|override: nesprávné použití specifikátoru override; klíčové slovo*Function*se neshoduje s metodou Base ref class.|
|Upozornění kompilátoru (úroveň 1) C4491|*název*: má neplatný formát verze IDL.|
|Upozornění kompilátoru (úroveň 1, chyba) C4492|'*Function1*': odpovídá metodě Base ref class '*function2*', ale není označeno ' override '|
|Upozornění kompilátoru (úroveň 3, chyba) C4493|výraz DELETE nemá žádný vliv, protože destruktor*typu*nemá přístupnost Public.|
|Upozornění kompilátoru (úroveň 1) C4494|'*Function*': Ignoruje se __declspec (Alokátor), protože návratový typ funkce není ukazatel nebo odkaz.|
|Upozornění kompilátoru C4495|používá se nestandardní rozšíření __super: Nahraďte explicitním názvem základní třídy.|
|Upozornění kompilátoru C4496|nestandardní rozšíření for each použito: Nahraďte ho příkazem ranged-for.|
|Upozornění kompilátoru C4497|používá se nestandardní rozšíření Sealed: Nahraďte ho ' Final '.|
|Upozornění kompilátoru C4498|používá se nestandardní rozšíření: '*Extension*'|
|Upozornění kompilátoru (úroveň 4) C4499|'*Function*': explicitní specializace nemůže mít třídu úložiště (ignorováno).|
|[Upozornění kompilátoru (úroveň 1) C4502](../../error-messages/compiler-warnings/compiler-warning-level-1-c4502.md)|*specifikace propojení*vyžaduje použití klíčového slova extern a musí předcházet všem ostatním specifikátorům.|
|[Upozornění kompilátoru (úroveň 1) C4503](../../error-messages/compiler-warnings/compiler-warning-level-1-c4503.md)|'*Identifier*': překročila se délka názvu dekorované, název byl zkrácen.|
|[Upozornění kompilátoru (úroveň 4) C4505](../../error-messages/compiler-warnings/compiler-warning-level-4-c4505.md)|'*Function*': došlo k odebrání neodkazované místní funkce|
|[Upozornění kompilátoru (úroveň 1) C4506](../../error-messages/compiler-warnings/compiler-warning-level-1-c4506.md)|žádná definice pro vloženou funkciFunction|
|[Upozornění kompilátoru (úroveň 1) C4508](../../error-messages/compiler-warnings/compiler-warning-level-1-c4508.md)|'*Function*': funkce by měla vracet hodnotu; Předpokládá se návratový typ void.|
|Upozornění kompilátoru C4509|používá se nestandardní rozšíření:*Function*používá SEH a*objekt*má destruktor.|
|[Upozornění kompilátoru (úroveň 4) C4510](../../error-messages/compiler-warnings/compiler-warning-level-4-c4510.md)|*Class*: výchozí konstruktor byl implicitně definovaný jako odstraněný.|
|[Upozornění kompilátoru (úroveň 3) C4511](../../error-messages/compiler-warnings/compiler-warning-level-3-c4511.md)|*Class*: konstruktor Copy byl implicitně definovaný jako odstraněný.|
|[Upozornění kompilátoru (úroveň 4) C4512](../../error-messages/compiler-warnings/compiler-warning-level-4-c4512.md)|'*Class*': operátor přiřazení byl implicitně definován jako odstraněný.|
|[Upozornění kompilátoru (úroveň 4) C4513](../../error-messages/compiler-warnings/compiler-warning-level-4-c4513.md)|*Class*: destruktor byl implicitně definovaný jako odstraněný.|
|[Upozornění kompilátoru (úroveň 4) C4514](../../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md)|'*Function*': vložená funkce, která není odkazovaná, byla odebrána.|
|[Upozornění kompilátoru (úroveň 4) C4515](../../error-messages/compiler-warnings/compiler-warning-level-4-c4515.md)|'*Namespace*': obor názvů používá sám sebe|
|[Upozornění kompilátoru (úroveň 4) C4516](../../error-messages/compiler-warnings/compiler-warning-level-4-c4516.md)|' class:: symbol ': deklarace Access-Declarations jsou zastaralé; použití deklarace členů poskytuje lepší alternativu.|
|[Upozornění kompilátoru (úroveň 4) C4517](../../error-messages/compiler-warnings/compiler-warning-level-4-c4517.md)|deklarace Access-Declarations jsou zastaralé; použití deklarace členů poskytuje lepší alternativu.|
|[Upozornění kompilátoru (úroveň 1) C4518](../../error-messages/compiler-warnings/compiler-warning-level-1-c4518.md)|*specifikátor*: třídy úložiště nebo specifikátory typu se tady neočekávají; přeskočen|
|Upozornění kompilátoru (chyba) C4519|výchozí argumenty šablony jsou povolené jenom pro šablonu třídy.|
|[Upozornění kompilátoru (úroveň 3) C4521](../../error-messages/compiler-warnings/compiler-warning-level-3-c4521.md)|'*Class*': bylo zadáno více kopírovacích konstruktorů|
|[Upozornění kompilátoru (úroveň 3) C4522](../../error-messages/compiler-warnings/compiler-warning-level-3-c4522.md)|*Class*: je zadaných víc operátorů přiřazení.|
|[Upozornění kompilátoru (úroveň 3) C4523](../../error-messages/compiler-warnings/compiler-warning-level-3-c4523.md)|'*Class*': bylo zadáno více destruktorů|
|[Upozornění kompilátoru (úroveň 1) C4526](../../error-messages/compiler-warnings/compiler-warning-level-1-c4526.md)|'*Function*': statická členská funkce nemůže přepsat přepsání virtuálnífunkce virtuální funkce se ignoruje, virtuální funkce bude skrytá.|
|[Upozornění kompilátoru (úroveň 1) C4530](../../error-messages/compiler-warnings/compiler-warning-level-1-c4530.md)|C++použila se obslužná rutina výjimky, ale není povolená sémantika unwind. Zadat/EHsc|
|Upozornění kompilátoru (úroveň 1) C4531|C++zpracování výjimek není v systém Windows CE k dispozici. Použití strukturovaného zpracování výjimek|
|[Upozornění kompilátoru (úroveň 1) C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|' Continue ': skok mimo blok ' __finally/finally ' má během zpracování ukončení nedefinované chování|
|[Upozornění kompilátoru (úroveň 1) C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|Inicializace*proměnné*se přeskočila příkazem*goto Label*.|
|[Upozornění kompilátoru (úroveň 3) C4534](../../error-messages/compiler-warnings/compiler-warning-level-3-c4534.md)|*konstruktor*nebude výchozím konstruktorem pro Class/struct*identifikátor*z důvodu výchozího argumentu.|
|[Upozornění kompilátoru (úroveň 3) C4535](../../error-messages/compiler-warnings/compiler-warning-level-3-c4535.md)|volání _set_se_translator () vyžaduje/EHa.|
|[Upozornění kompilátoru (úroveň 4) C4536](../../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md)|'*TypeName*': typ-Name překračuje limit meta-dat '*character_limit*' znaků.|
|[Upozornění kompilátoru (úroveň 1) C4537](../../error-messages/compiler-warnings/compiler-warning-level-1-c4537.md)|'*Object*': '. ' se aplikuje na typ, který není typu UDT|
|[Upozornění kompilátoru (úroveň 3) C4538](../../error-messages/compiler-warnings/compiler-warning-level-3-c4538.md)|*typ*: kvalifikátory const/volatile pro tento typ nejsou podporované.|
|[Upozornění kompilátoru (úroveň 1) C4540](../../error-messages/compiler-warnings/compiler-warning-level-1-c4540.md)|dynamic_cast použité pro převod na nedostupný nebo nejednoznačný základ; test za běhu se nezdařil ("*typ1*" na "*typ2*")|
|[Upozornění kompilátoru (úroveň 1) C4541](../../error-messages/compiler-warnings/compiler-warning-level-1-c4541.md)|'*Identifier*' použitý u polymorfního typu '*Type*' s/gr-; může dojít k nepředvídatelnému chování.|
|Upozornění kompilátoru (úroveň 1) C4542|Přeskakuje se generování sloučeného vloženého textového souboru, nejde zapisovat do souboru *typ_souboru* : "*problém*": *zpráva*|
|[Upozornění kompilátoru (úroveň 3) C4543](../../error-messages/compiler-warnings/compiler-warning-level-3-c4543.md)|Vložený text potlačený atributem No\_injected_text|
|[Upozornění kompilátoru (úroveň 1) C4544](../../error-messages/compiler-warnings/compiler-warning-level-1-c4544.md)|*deklarace*: výchozí argument šablony se pro tuto deklaraci šablony ignoruje.|
|[Upozornění kompilátoru (úroveň 1) C4545](../../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md)|výraz před čárkou vyhodnocuje na funkci, která nemá k dispozici seznam argumentů|
|[Upozornění kompilátoru (úroveň 1) C4546](../../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md)|volání funkce před čárkou nemá seznamu argumentů|
|[Upozornění kompilátoru (úroveň 1) C4547](../../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md)|'*Operator*': operátor před čárkou nemá žádný vliv; očekával se operátor s vedlejším účinkem.|
|[Upozornění kompilátoru (úroveň 1) C4548](../../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md)|výraz před čárkou nemá žádný vliv; očekávaný výraz s vedlejším účinkem|
|[Upozornění kompilátoru (úroveň 1) C4549](../../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md)|'*Operator*': operátor před čárkou nemá žádný vliv; Měli jste v úmyslu '*Operator*'?|
|[Upozornění kompilátoru (úroveň 1) C4550](../../error-messages/compiler-warnings/compiler-warning-level-1-c4550.md)|výraz se vyhodnocuje jako funkce, ve které chybí seznam argumentů.|
|[Upozornění kompilátoru (úroveň 1) C4551](../../error-messages/compiler-warnings/compiler-warning-level-1-c4551.md)|v volání funkce chybí seznam argumentů.|
|[Upozornění kompilátoru (úroveň 1) C4552](../../error-messages/compiler-warnings/compiler-warning-level-1-c4552.md)|'*Operator*': operátor nemá žádný vliv; očekával se operátor s vedlejším účinkem.|
|[Upozornění kompilátoru (úroveň 1) C4553](../../error-messages/compiler-warnings/compiler-warning-level-1-c4553.md)|'*Operator*': operátor nemá žádný vliv; Měli jste v úmyslu použít operátora?|
|[Upozornění kompilátoru (úroveň 3) C4554](../../error-messages/compiler-warnings/compiler-warning-level-3-c4554.md) C4554|'*Operator*': Ověřte, zda není priorita operátorů možná chyba; použití závorek k upřesnění priority|
|[Upozornění kompilátoru (úroveň 1) C4555](../../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md)|výraz nemá žádný vliv; očekávaný výraz s vedlejším účinkem|
|[Upozornění kompilátoru (úroveň 1) C4556](../../error-messages/compiler-warnings/compiler-warning-level-1-c4556.md)|hodnota vnitřního argumentu Immediate '*Value*' je mimo rozsah '*lower_bound* - *Upper_bound*'|
|[Upozornění kompilátoru (úroveň 3) C4557](../../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md)|' __assume ' obsahuje efekt '*efekt*'|
|[Upozornění kompilátoru (úroveň 1) C4558](../../error-messages/compiler-warnings/compiler-warning-level-1-c4558.md)|hodnota operandu '*Value*' je mimo rozsah '*lower_bound* - *Upper_bound*'|
|[Upozornění kompilátoru (úroveň 4) C4559](../../error-messages/compiler-warnings/compiler-warning-level-4-c4559.md)|'*Function*': předefinování; funkce získává __declspec (modifikátor).|
|[Upozornění kompilátoru (úroveň 1) C4561](../../error-messages/compiler-warnings/compiler-warning-level-1-c4561.md)|' __fastcall ' není kompatibilní s možností '/CLR ': Probíhá převod na ' __stdcall '|
|Upozornění kompilátoru (úroveň 4) C4562|s možností/CLR se vyžadují plně prototypované funkce: () se převádí na: (void).|
|[Upozornění kompilátoru (úroveň 4) C4564](../../error-messages/compiler-warnings/compiler-warning-level-4-c4564.md)|Metoda "*Method*" třídy "*ClassName*" definuje nepodporovaný výchozí parametr '*Parameter*'|
|[Upozornění kompilátoru (úroveň 4) C4565](../../error-messages/compiler-warnings/compiler-warning-level-4-c4565.md)|'*Function*': předefinování; symbol byl dřív deklarovaný pomocí __declspec (modifikátor).|
|[Upozornění kompilátoru (úroveň 1) C4566](../../error-messages/compiler-warnings/compiler-warning-level-1-c4566.md)|znak reprezentovaný symbolem Universal-Character-Name nemůže být reprezentovaný v aktuální znakové stránce (*Number*).|
|Upozornění kompilátoru (úroveň 1) C4568|'*Function*': podpis explicitního přepsání neodpovídá žádnému členu.|
|Upozornění kompilátoru (úroveň 3) C4569|'*Function*': podpis explicitního přepsání neodpovídá žádnému členu.|
|[Upozornění kompilátoru (úroveň 3) C4570](../../error-messages/compiler-warnings/compiler-warning-level-3-c4570.md)|*Type*: není explicitně deklarované jako abstraktní, ale má abstraktní funkce.|
|[Upozornění kompilátoru (úroveň 4) C4571](../../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md)|Informační: sémantika catch (...) se od verze C++ Visual 7,1 změnila. strukturované výjimky (SEH) už se nezachycují.|
|[Upozornění kompilátoru (úroveň 1) C4572](../../error-messages/compiler-warnings/compiler-warning-level-1-c4572.md)|Atribut [ParamArray] je zastaralý v rámci/CLR, použijte... takové|
|Upozornění kompilátoru (úroveň 1) C4573|použití*funkce lambda Function*vyžaduje, aby kompilátor zachytí this, ale aktuální výchozí režim sběru nepovoluje.|
|Upozornění kompilátoru (úroveň 4) C4574|'*Identifikátor*' je definován jako ' 0 ': nechtěli jste použít ' #if identifikátor '?|
|Upozornění kompilátoru (úroveň 1) C4575|' __vectorcall ' není kompatibilní s možností '/CLR ': Probíhá převod na ' __stdcall '|
|Upozornění kompilátoru (úroveň 1, chyba) C4576|typ v závorce následovaný seznamem inicializátorů je nestandardní explicitní syntaxe převodu typu.|
|Upozornění kompilátoru (úroveň 1, vypnuto) C4577|' s výjimkou ' se používá bez zadaného režimu zpracování výjimek; ukončení u výjimky není zaručeno. Zadat/EHsc|
|Upozornění kompilátoru (úroveň 1, chyba) C4578|' ABS ': převod z '*typ1*' na '*typ2*', možná ztráta dat (nechtěli jste volat '*Function*' nebo #include \<cmath >?)|
|[Upozornění kompilátoru (úroveň 3) C4580](../../error-messages/compiler-warnings/compiler-warning-level-3-c4580.md)|[Attribute] je zastaralá; místo toho zadejte System:: Attribute nebo Platform:: metadata jako základní (Base) třídu.|
|[Upozornění kompilátoru (úroveň 1) C4581](../../error-messages/compiler-warnings/compiler-warning-level-1-c4581.md)|zastaralé chování:*řetězec*byl nahrazen řetězcem '*String*' pro zpracování atributu|
|Upozornění kompilátoru (úroveň 4) C4582|*Type*: konstruktor se nevolá implicitně.|
|Upozornění kompilátoru (úroveň 4) C4583|*Type*: destruktor se nevolá implicitně.|
|[Upozornění kompilátoru (úroveň 1) C4584](../../error-messages/compiler-warnings/compiler-warning-level-1-c4584.md)|'*Class1*': základní třída '*Class2*' je již základní třídou '*class3*'|
|Upozornění kompilátoru (úroveň 1, chyba) C4585|'*Class*': Třída Public ref class WinRT musí být buď zapečetěná, nebo musí být odvozená od existující nezapečetěné třídy.|
|Upozornění kompilátoru (úroveň 1, chyba) C4586|*typ*: Veřejný typ se nedá deklarovat v oboru názvů nejvyšší úrovně s názvem Windows.|
|Upozornění kompilátoru (úroveň 1) C4587|'*anonymous_structure*': Změna chování: konstruktor už se nevolá implicitně|
|Upozornění kompilátoru (úroveň 1) C4588|'*anonymous_structure*': Změna chování: destruktor už se nevolá implicitně|
|Upozornění kompilátoru (úroveň 1) C4591|překročil se limit hloubky volání constexpr pro *číslo* (/constexpr: Depth\<číslo >).|
|Upozornění kompilátoru (úroveň 3) C4592|'*Function*': vyhodnocení volání constexpr se nezdařilo; funkce bude volána v době běhu.|
|Upozornění kompilátoru (úroveň 1) C4593|'*Function*': limit kroku vyhodnocení volání constexpr '*limit*' byl překročen; k navýšení\<limitu použijte/constexpr: Number Steps >.|
|Upozornění kompilátoru (úroveň 3) C4594|*typ*: destruktor se implicitně nevolá, pokud je vyvolána výjimka.|
|Upozornění kompilátoru (úroveň 1) C4595|'*Type*': Změna chování: destruktor již nebude implicitně volán, pokud je vyvolána výjimka|
|[Upozornění kompilátoru (úroveň 4) C4596](../../error-messages/compiler-warnings/c4596.md)|'*Identifier*': neplatný kvalifikovaný název v deklaraci členu|
|Upozornění kompilátoru (chyba) C4597|nedefinované chování: OffsetOf se aplikuje na člen virtuální základny.|
|Upozornění kompilátoru (úroveň 1 a úroveň 3) C4598|' #include '*záhlaví*' ': číslo hlavičky v předkompilované hlavičce neodpovídá aktuální kompilaci na této pozici|
|Upozornění kompilátoru (úroveň 3) C4599|'*příznak* *cesty*': číslo argumentu příkazového řádku neodpovídá předkompilované hlavičce|

## <a name="see-also"></a>Viz také:

[Chyby aC++ upozornění pro nástroje C/kompilátor a sestavení](../compiler-errors-1/c-cpp-build-errors.md) \
[Upozornění kompilátoru C4000-C5999](compiler-warnings-c4000-c5999.md)
