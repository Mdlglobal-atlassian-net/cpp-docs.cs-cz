---
title: "C4600 upozornění kompilátoru prostřednictvím C4799 | Microsoft Docs"
ms.date: 10/25/2017
ms.technology: cpp-tools
ms.topic: error-reference
f1_keywords:
- C4602
- C4603
- C4609
- C4612
- C4613
- C4620
- C4622
- C4629
- C4631
- C4634
- C4635
- C4636
- C4637
- C4638
- C4645
- C4646
- C4655
- C4657
- C4658
- C4662
- C4670
- C4671
- C4672
- C4674
- C4676
- C4678
- C4681
- C4682
- C4685
- C4688
- C4689
- C4690
- C4693
- C4694
- C4695
- C4696
- C4718
- C4719
- C4720
- C4721
- C4722
- C4724
- C4725
- C4728
- C4729
- C4732
- C4739
- C4750
- C4751
- C4752
- C4754
- C4755
- C4757
- C4764
- C4767
- C4770
- C4792
- C4794
dev_langs: C++
ms.assetid: 22bd4392-f3be-445c-9f23-6126aebac901
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 456d35247f25d20684e8b6957d61428a2b113ca0
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2017
---
# <a name="compiler-warnings-c4600-through-c4799"></a>C4600 upozornění kompilátoru prostřednictvím C4799

Články v této části dokumentace obsahovat informace o podmnožinu upozornění kompilátoru Visual C++. Dostanete zde uvedené informace, nebo v okně výstupu v sadě Visual Studio, můžete vybrat číslo chyby a potom stiskněte klávesu F1.

> [!NOTE]
> Ne každý [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] chyby nebo upozornění je popsána v MSDN. Diagnostické zprávy v mnoha případech poskytuje všechny informace, které jsou k dispozici. Pokud se domníváte, že chybovou zprávu potřebuje další vysvětlení, můžete dejte nám vědět. Můžete použít formulář zpětné vazby na této stránce, nebo přejít na panelu nabídek v sadě Visual Studio a zvolte **pomoci**, **ohlásit chybu**, nebo můžete odeslat zprávu návrhu nebo chyb na [Microsoft Connect](http://connect.microsoft.com/VisualStudio).

Chyby a upozornění na veřejných fórech MSDN můžete najít další pomoc. [Jazyka Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) fórum je pro dotazy a v diskusích o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] syntaxi a kompilátoru jazyka. [Visual C++ Obecné](http://go.microsoft.com/fwlink/?LinkId=158194) fórum je pro dotazy o [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] které nejsou popsané v dalších fóra. Můžete také zjistit nápovědu k nástroji chyby a upozornění na [Stack Overflow](http://stackoverflow.com/).

## <a name="in-this-section"></a>V tomto oddílu

|Upozornění|Zpráva|
|-------------|-------------|
|[C4600 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma "makro název": očekáván platný neprázdný řetězec|
|Upozornění kompilátoru (úroveň 1) C4602|pop_macro – #pragma: "makro název" žádné předchozí push_macro – #pragma tohoto identifikátoru|
|Upozornění kompilátoru (úroveň 1) C4603|'*identifikátor*': Makro není definováno nebo ho definici se liší po použití předkompilovaných hlaviček|
|Upozornění kompilátoru (úroveň 1) C4604|'*typ*': předání argumentů hodnotou mezi nativní a spravovaná hranic vyžaduje platný kopírovacího konstruktoru. Jinak není definován chování za běhu|
|Upozornění kompilátoru (úroveň 1) C4605|' /D*makro*' zadaný u aktuálního příkazového řádku, ale nebyl zadán, pokud byl vytvořený předkompilovaných hlaviček|
|[C4606 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4606.md)|#pragma – upozornění: upozornění číslo ignorován; Upozornění analýzy kódu nejsou přidružené úrovně varování|
|[Kompilátoru upozornění (úroveň 3) C4608](../../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|'union_member' již byl inicializován jiný union člen v seznamu inicializátor 'union_member.|
|Upozornění kompilátoru (úroveň 3, chyba) C4609|'*type1*'je odvozena z výchozí rozhraní'*rozhraní*'na typ"*type2*'. Použijte jiný výchozí rozhraní pro '*type1*", nebo zrušit základní nebo odvozené.|
|[C4610 kompilátoru upozornění (úroveň 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4610.md)|objekt 'class' může být vytvořena nikdy – konstruktor požadované definované uživatelem|
|[C4611 kompilátoru upozornění (úroveň 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4611.md)|interakce mezi 'function' a odstraňování objektů C++ je jiný přenositelností|
|Upozornění kompilátoru (úroveň 1) C4612|došlo k chybě v patří název souboru|
|Upozornění kompilátoru (úroveň 1) C4613|'*symbol*': Třída segmentu nelze změnit.|
|[C4615 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4615.md)|#pragma – upozornění: Neznámé uživatelské typ upozornění|
|[C4616 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4616.md)|#pragma – upozornění: upozornění číslo, číslo' není platný kompilátoru upozornění|
|[C4618 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4618.md)|Parametry – Direktiva pragma zahrnuté prázdný řetězec; Ignorovat – Direktiva pragma|
|[C4619 kompilátoru upozornění (úroveň 3)](../../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)|#pragma warning: neexistuje číslo upozornění 'number'|
|Upozornění kompilátoru (úroveň 1) C4620|žádné operátory formu ' operátor ++' nebyla nalezena pro typ "typ" pomocí předpony formuláře|
|[C4621 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4621.md)|žádný formulář operátory operátoru' –' nebyla nalezena pro typ "typ" pomocí předpony formuláře|
|Upozornění kompilátoru (úroveň 3) C4622|Informace o ladění přepsal vytvořen během vytváření předkompilovaných hlaviček v souboru objektu: 'file'|
|[C4623 kompilátoru upozornění (úroveň 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)|odvozené třídy': výchozí konstruktor byl implicitně definován jako odstranit, protože základní třída výchozí konstruktor je nedostupný, nebo odstraněné|
|[C4624 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4624.md)|odvozené třídy': destruktor byl implicitně definován jako odstranit, protože základní třída destruktor je nedostupný, nebo odstraněné|
|[C4625 kompilátoru upozornění (úroveň 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)|odvozené třídy': kopírovacího konstruktoru byl implicitně definován jako odstranit, protože základní třída kopírovacího konstruktoru je nedostupný, nebo odstraněné|
|[C4626 kompilátoru upozornění (úroveň 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)|odvozené třídy': operátor přiřazení byl implicitně definován jako odstranit, protože operátor přiřazení základní třída je nedostupný, nebo odstraněné|
|[C4627 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4627.md)|'\<identifikátor >': při vyhledávání předkompilované hlavičky použití přeskočen|
|[C4628 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)|spřežky nejsou podporovány se -Ze. Posloupnost znaků spřežka není interpretovat jako alternativní token pro '%s'|
|Upozornění kompilátoru (úroveň 4) C4629|použít spřežka posloupnost znaků spřežka interpretovat jako token "char" (Vložit mezery mezi dvěma znaky. Pokud se jedná, není to v pořádku)|
|[C4630 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4630.md)|'symbol': 'extern' – specifikátor třídy úložiště neplatný na definice člena|
|Upozornění kompilátoru (úroveň 2) C4631|MSXML nebo není k dispozici, XPath dokumentu XML, který komentáře nebude zpracováno. Důvod|
|[C4632 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4632.md)|Komentář dokumentu XML: soubor – přístup byl odepřen: důvod|
|[C4633 kompilátoru upozornění (úroveň 3)](../../error-messages/compiler-warnings/compiler-warning-level-3-c4633.md)|Cíl komentář dokumentu XML: Chyba: důvod|
|Upozornění kompilátoru (úroveň 4) C4634|Cíl komentář dokumentu XML: nelze použít: důvod|
|Upozornění kompilátoru (úroveň 3) C4635|Cíl komentář dokumentu XML: chybně formátovanou XML: důvod|
|Upozornění kompilátoru (úroveň 3) C4636|Použít k vytvoření komentáře dokumentu XML: značka vyžaduje neprázdný atribut ' attribute '.|
|Upozornění kompilátoru (úroveň 3 a 4) C4637|Cíl komentář dokumentu XML: \<zahrnují > Značka zahozeny. Důvod|
|Upozornění kompilátoru (úroveň 3) C4638|Cíl komentář dokumentu XML: odkaz na neznámé symbol "značkou".|
|[C4639 kompilátoru upozornění (úroveň 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4639.md)|Chyba MSXML, dokument XML, který komentáře nebude zpracováno. Důvod|
|[C4640 kompilátoru upozornění (úroveň 3)](../../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)|'instance': stavba místního statického objektu není bezpečná pro přístup z více vláken|
|[C4641 kompilátoru upozornění (úroveň 3)](../../error-messages/compiler-warnings/compiler-warning-level-3-c4641.md)|Komentář dokumentu XML má nejednoznačný křížových odkazů:|
|Upozornění kompilátoru (úroveň 3) C4645|funkce deklarovat s __declspec(noreturn) má příkaz return|
|Upozornění kompilátoru (úroveň 3) C4646|funkce deklarovat s __declspec(noreturn) má návratový typ není void|
|Upozornění kompilátoru (úroveň 3) C4647|Změna v chování: __is_pod (*typu*) má jinou hodnotu v předchozích verzích|
|Upozornění kompilátoru (úroveň 3) C4648|standardní atribut 'carries_dependency' je ignorován|
|Upozornění kompilátoru (úroveň 3) C4649|v tomto kontextu jsou ignorovány atributy|
|[C4650 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4650.md)|informace o ladění není v předkompilovaných hlaviček; pouze globální symboly z hlavičky bude k dispozici|
|[C4651 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4651.md)|definice zadány pro předkompilovaných hlaviček, ale ne pro aktuální kompilace|
|[C4652 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4652.md)|možnost kompilátoru "možnost" konzistentní s předkompilovaných hlaviček; Aktuální možnost příkazového řádku se přepíše která definována v předkompilovaných hlaviček|
|[C4653 kompilátoru upozornění (úroveň 2)](../../error-messages/compiler-warnings/compiler-warning-level-2-c4653.md)|možnost kompilátoru "možnost" konzistentní s předkompilovaných hlaviček; Ignorovat aktuální možnost příkazového řádku|
|Upozornění kompilátoru (úroveň 4) C4654|Kód umístěna před patří předkompilovaných hlaviček řádek bude ignorován. Přidávání kódu do předkompilovaných hlaviček.|
|Upozornění kompilátoru (úroveň 1) C4655|'symbol': typ proměnné je nového od poslední sestavení nebo je definován jinak jinde|
|[Kompilátoru (úroveň 1) upozornění C4656](../../error-messages/compiler-warnings/compiler-warning-level-1-c4656.md)|'symbol': datový typ je nové nebo došlo ke změně od poslední sestavení nebo je definován jinak jinde|
|Upozornění kompilátoru (úroveň 1) C4657|výraz zahrnuje datový typ, který je nového od poslední sestavení|
|Upozornění kompilátoru (úroveň 1) C4658|'function': prototyp funkce je nového od poslední sestavení nebo je deklarovaná jinak jinde|
|[C4659 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4659.md)|#pragma '– Direktiva pragma': použití vyhrazené segment 'segmentu, má undefined chování, použijte komentář #pragma (linker,...)|
|[C4661 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4661.md)|"identifikátor": zadaná pro žádost o vytvoření instance šablony explicitní žádný vhodný definice|
|Upozornění kompilátoru (úroveň 1) C4662|Explicitní vytvoření instance; šablony třídy 'identifier1' neobsahuje žádnou definici ze kterého se specializují 'identifier2.|
|[C4667 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4667.md)|'function': žádné funkce šablony definovaný, která odpovídá vynutit vytváření instancí|
|[C4668 kompilátoru upozornění (úroveň 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)|'symbol' není definován jako makro preprocesoru, nahraďte "0" pro "směrnice"|
|[C4669 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4669.md)|'přetypovat': unsafe převod: 'class' je objekt spravovaného typu|
|Upozornění kompilátoru (úroveň 4) C4670|"identifikátor": Tato základní třída je nedostupná|
|Upozornění kompilátoru (úroveň 4) C4671|"identifikátor": konstruktor copy je nedostupná|
|Upozornění kompilátoru (úroveň 4) C4672|'identifier1': nejednoznačný. První považovat za 'identifier2.|
|[C4673 kompilátoru upozornění (úroveň 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4673.md)|vyvolání "identifikátor" následující typy nebude se zvažovat v lokalitě catch|
|Upozornění kompilátoru (úroveň 1) C4674|"metody" musí být deklarován "statická" a mít přesně jeden parametr|
|Upozornění kompilátoru (úroveň 4) C4676|'%s': destruktoru je nedostupná|
|[C4677 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4677.md)|'function': podpis privátního člena obsahuje privátní typ sestavení 'private_type.|
|Upozornění kompilátoru (úroveň 1) C4678|Základní třída 'base_type' je méně přístupný než 'derived_type.|
|[C4679 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4679.md)|"člen": nelze importovat člena|
|[C4680 kompilátoru upozornění (úroveň 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4680.md)|'class': Třída typu coclass neurčuje výchozí rozhraní|
|Upozornění kompilátoru (úroveň 4) C4681|'class': Třída typu coclass neurčuje výchozí rozhraní, která je zdroje událostí|
|Upozornění kompilátoru (úroveň 4) C4682|"parametr": atribut směrovou parametr zadán, jako výchozí bude použit [v]|
|[C4683 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4683.md)|'function': 'out' má zdroj události-parametr; postupujte opatrně při zapojování více obslužných rutin událostí|
|[C4684 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4684.md)|'atribut': upozornění!! atribut může způsobit, že generace neplatný kód: používejte opatrně|
|Upozornění kompilátoru (úroveň 1) C4685|Očekává se >> ' nalezen ' >>, při analýze parametry šablony|
|[C4686 kompilátoru upozornění (úroveň 3)](../../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)|'user-defined type': možné změny v chování, změna ve vrácení konvence volání uživatelem definovaného typu|
|[C4687 kompilátoru upozornění (chyba)](../../error-messages/compiler-warnings/compiler-warning-c4687.md)|'class': zapečetěné abstraktní třídy nelze implementovat rozhraní 'rozhraní.|
|Upozornění kompilátoru (úroveň 1) C4688|'omezení': omezení seznam obsahuje sestavení privátního typu "typ"|
|Upozornění kompilátoru (úroveň 1) C4689|'%c': Nepodporovaný znak v #pragma detect_mismatch; #pragma ignorovat|
|Upozornění kompilátoru (úroveň 4) C4690|[emitidl – (pop)]: více bodů POP než nabízených oznámení|
|[C4691 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4691.md)|'type': v neregistrované sestavení 'file' typem definovaným v aktuální jednotku překlad místo toho použít byl očekáván typ odkazuje|
|[C4692 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)|'function': podpis nesoukromého členu obsahuje sestavení privátního nativního typu 'native_type'|
|[Upozornění kompilátoru (úroveň 1, chyba) C4693](../../error-messages/compiler-warnings/compiler-warning-c4693.md)|'class': zapečetěné abstraktní třídy nemůže mít žádné instance členy člen instance.|
|[Upozornění kompilátoru (úroveň 1, chyba) C4694](../../error-messages/compiler-warnings/compiler-warning-c4694.md)|'class': zapečetěné abstraktní třídy nemůže mít základní třídy, base_class.|
|Upozornění kompilátoru (úroveň 1) C4695|#pragma execution_character_set: 'znaková sada, není podporované argument: je podporována aktuálně jedinou 'UTF-8.|
|Upozornění kompilátoru (úroveň 1) C4696|/ Možnost ZBvalue1 mimo rozsah; za předpokladu, že 'hodnota2'|
|[Kompilátoru upozornění (úroveň 1 a 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|místní proměnné Neinicializovaný použít název|
|[C4701 kompilátoru upozornění (úroveň 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)|Potenciálně Neinicializovaný místní proměnné použít název|
|[C4702 kompilátoru upozornění (úroveň 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4702.md)|Nedosažitelný kódu|
|[C4703 kompilátoru upozornění (úroveň 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|proměnné potenciálně Neinicializovaný místní ukazatele '%s' použít|
|[C4706 kompilátoru upozornění (úroveň 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4706.md)|přiřazení v rámci podmíněného výrazu|
|[C4709 kompilátoru upozornění (úroveň 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4709.md)|Operátor čárky v rámci výraz index pole|
|[C4710 kompilátoru upozornění (úroveň 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)|'function': funkce není vložena|
|[C4711 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4711.md)|funkce vybrané pro rozšíření automatické vložené funkce|
|[C4714 kompilátoru upozornění (úroveň 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)|Funkce označen jako __forceinline není vložená funkce|
|[C4715 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4715.md)|'function': Ne všechny cesty řízení vrátit hodnotu|
|[C4716 kompilátoru upozornění (úroveň 1, chyba)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4716.md)|'function': musí vrátit hodnotu|
|[C4717 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4717.md)|'function': rekurzivní u všech cest řízení funkce způsobí přetečení zásobníku modul runtime|
|Upozornění kompilátoru (úroveň 4) C4718|volání funkce: rekurzivní volání nemá žádné vedlejší účinky odstranění|
|Upozornění kompilátoru (úroveň 1) C4719|Dvojité konstanta najít na požádání Qfast - použití f jako příponu udávajících jednoduchou přesností|
|Upozornění kompilátoru (úroveň 2) C4720|řádek assembleru sestavy: 'zprávy.|
|Upozornění kompilátoru (úroveň 1) C4721|'function': není k dispozici jako vnitřní funkce|
|Upozornění kompilátoru (úroveň 1) C4722|'function': destruktor nikdy vrátí, potenciální nevracení paměti|
|[C4723 kompilátoru upozornění (úroveň 3)](../../error-messages/compiler-warnings/compiler-warning-level-3-c4723.md)|potenciální dělení hodnotou 0|
|Upozornění kompilátoru (úroveň 3) C4724|potenciální mod hodnotou 0|
|Upozornění kompilátoru (úroveň 3) C4725|instrukce mohou být nepřesné na některé Pentiums|
|[C4727 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4727.md)|PCH s názvem pch_file se stejnou časové razítko v obj_file_1 a obj_file_2 nalezen.  Pomocí prvního PCH.|
|Upozornění kompilátoru (úroveň 1) C4728|/ Yi – možnost ignorován, protože se vyžaduje odkaz na PCH|
|Upozornění kompilátoru (úroveň 4) C4729|Funkce, které jsou příliš dlouhé pro graf toku na základě upozornění|
|[Kompilátoru upozornění (úroveň 1) C4730](../../error-messages/compiler-warnings/compiler-warning-level-1-c4730.md)upozornění kompilátoru (úroveň 1) C4730|"hlavní": kombinování _m64 a plovoucí bodu výrazy může vést k nesprávným kódem|
|[C4731 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4731.md)|'ukazatel': registr ukazatele 'zaregistrovat, upravit kód vnořeného sestavení s rámečkem|
|Upozornění kompilátoru (úroveň 1) C4732|vnitřní funkce '%s' není podporován v této architektuře|
|[C4733 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4733.md)|Vložené asm přiřazení k 'FS:0': není registrován jako bezpečné obslužné rutiny obslužná rutina|
|[C4738 kompilátoru upozornění (úroveň 3)](../../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)|ukládání 32bitového plovoucího výsledku do paměti, možná ztráta|
|Upozornění kompilátoru (úroveň 1) C4739|odkaz na proměnnou 'var' překračuje jeho prostorem úložiště|
|[C4740 kompilátoru upozornění (úroveň 4)](../../error-messages/compiler-warnings/compiler-warning-level-4-c4740.md)|tok nebo zrušení vloženého kódu asm potlačí globální optimalizace|
|[C4742 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4742.md)|'příkaz var' má jiné zarovnání v 'file1' a 'file2': číslo a číslo|
|[C4743 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4743.md)|"typ" má jinou velikost v 'file1' a 'file2': číslo a počet bajtů|
|[C4744 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4744.md)|'příkaz var' má jiný typ v 'file1' a 'file2': 'type1' a 'type2'.|
|[C4746 upozornění kompilátoru](../../error-messages/compiler-warnings/compiler-warning-c4746.md)|volatile přístup '*výraz*' podléhá/volatile:\<iso &#124; ms > nastavení; zvažte použití __iso_volatile_load/úložiště vnitřní funkce|
|[C4747 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)|Volání metody spravované 'entrypoint': spravovaného kódu nemusí být možné spustit v zavaděči, včetně vstupní bod knihovny DLL a volání z vstupní bod knihovny DLL|
|Upozornění kompilátoru (úroveň 4) C4749|podmíněná podporována: offsetof – použít u typu standard non-rozložení '*typ*.|
|Upozornění kompilátoru (úroveň 1) C4750|"identifikátor": funkce s _alloca() vložená do smyčky|
|Upozornění kompilátoru (úroveň 4) C4751|/arch:AVX se nevztahuje na Streaming SIMD Extensions Intel(R), která jsou v rámci vložené ASM|
|Upozornění kompilátoru (úroveň 4) C4752|Najít Intel(R) Advanced vektoru rozšíření; Zvažte použití /arch:AVX|
|Upozornění kompilátoru (úroveň 4) C4754|Převod pravidel pro aritmetické operace porovnání v %s(%d) to znamenat, že tento jeden větve nelze provést. Přetypování '%s' do '%s' (nebo podobné typu %d bajtů).|
|Upozornění C4755 kompilátoru|Převod pravidel pro aritmetické operace porovnání v %s(%d) to znamenat, že tento jeden větve nelze provést v vložená funkce. Přetypování '%s' do '%s' (nebo podobné typu %d bajtů).|
|[C4756 kompilátoru upozornění (úroveň 2)](../../error-messages/compiler-warnings/compiler-warning-level-2-c4756.md)|v konstantní aritmetické přetečení|
|Upozornění kompilátoru (úroveň 4) C4757|dolní index je velké hodnoty bez znaménka, hodláte záporné konstanta?|
|Upozornění kompilátoru (úroveň 4) C4764|Nelze zarovnat catch objektů na větší než 16 bajtů|
|Upozornění kompilátoru (úroveň 4) C4767|Název oddílu '%s' je delší než 8 znaků a bude zkrácen podle linkeru|
|Upozornění kompilátoru (úroveň 3) C4768|atributy __declspec před specifikaci propojení se ignorují.|
|Upozornění C4770 kompilátoru|částečně ověřit výčtu '*název*se používá jako index|
|Upozornění C4771 kompilátoru|Rozsah musí být vytvořen pomocí jednoduchého ukazatel; Vnitřní funkce MPX ignorovat|
|[C4772 kompilátoru upozornění (úroveň 1, chyba)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4772.md)|#import odkazuje typ z chybějící knihovny typů; missing_type použít jako zástupný znak|
|Upozornění kompilátoru (úroveň 4) C4774|'*řetězec*': v argument byl očekáván řetězec formátu *číslo* není řetězec literálu|
|Upozornění kompilátoru (úroveň 3) C4775|nestandardní rozšíření používané ve formátovacím řetězci '*řetězec*"funkce"*funkce*.|
|Upozornění kompilátoru (úroveň 1) C4776|' %*znak*není povolená, ve formátovacím řetězci funkce'*funkce*.|
|Upozornění kompilátoru (úroveň 4) C4777|'*funkce*': řetězec formátu,*řetězec*, vyžaduje argument typu'*type1*', ale argument variadická *číslo* má typ '*type2*.|
|Upozornění kompilátoru (úroveň 3) C4778|'*funkce*': neukončený řetězec formátu,*řetězec*.|
|[C4788 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4788.md)|"identifikátor": identifikátor byl zkrácen na "číslo" znaků|
|[C4789 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|bude přetečení vyrovnávací paměti identifikátor N velikost v bajtech; M bajtů se zapíšou začínající na posunu L|
|Upozornění kompilátoru (úroveň 2) C4792|Funkce '%s' deklarováno s použitím import systému a na něj odkazovat z nativního kódu; Importovat knihovny potřebné k propojení|
|[Upozornění (úroveň 1 a 3) C4793 kompilátoru](../../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)|'function': funkce kompilovány jako nativní: \n\t'reason.|
|Upozornění kompilátoru (úroveň 1) C4794|Segment úložiště thread local proměnné '%s' změnil z '%s' do '%s'|
|[C4799 kompilátoru upozornění (úroveň 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4799.md)|Funkce 'function' nemá žádný EMMS instrukcí|