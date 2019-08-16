---
title: Upozornění kompilátoru, která jsou ve výchozím natavení vypnuta.
ms.date: 05/30/2018
helpviewer_keywords:
- warnings, compiler
- cl.exe compiler, setting options
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
ms.openlocfilehash: 1a95153f3cefd2bcfcae6ebb297a7c6b52944f82
ms.sourcegitcommit: d3829ae0c3db909f96057755a80665f5ea4896ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/16/2019
ms.locfileid: "69550476"
---
# <a name="compiler-warnings-that-are-off-by-default"></a>Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá

Kompilátor podporuje upozornění, která jsou ve výchozím nastavení vypnuta, protože většina vývojářů je nenalezne. V některých případech upozorňují na stylistickou volbu nebo na běžné idiomy ve starším kódu. Další upozornění se týkají použití rozšíření společnosti Microsoft pro jazyk. V ostatních případech označuje oblast, kde programátor často provádí nesprávné předpoklady, což může vést k neočekávanému nebo nedefinovanému chování. Pokud je povoleno, některá z těchto upozornění se mohou v hlavičkách knihovny zobrazit mnohokrát. Běhové knihovny jazyka C a C++ standardní knihovny jsou určeny k vygenerování žádného upozornění na úrovni upozornění [/W4](../build/reference/compiler-option-warning-level.md).

## <a name="enable-warnings-that-are-off-by-default"></a>Povolit upozornění, která jsou ve výchozím nastavení vypnutá

Pomocí jedné z následujících možností můžete povolit upozornění, která jsou ve výchozím nastavení standardně vypnutá:

- **#pragma upozornění (výchozí:** *warning_number* **)**

   Zadané upozornění (*warning_number*) je povoleno na výchozí úrovni. Dokumentace pro upozornění obsahuje výchozí úroveň upozornění.

- **upozornění #pragma (** *warning_level* **:** *warning_number* **)**

   Zadané upozornění (*warning_number*) je povoleno na zadané úrovni (*warning_level*).

- [/Wall](../build/reference/compiler-option-warning-level.md)

   `/Wall`povolí všechna upozornění, která jsou ve výchozím nastavení vypnutá. Pokud použijete tuto možnost, můžete jednotlivá upozornění vypnout pomocí možnosti [/WD](../build/reference/compiler-option-warning-level.md) .

- [/w*Lnnnn*](../build/reference/compiler-option-warning-level.md)

   Tato možnost povolí upozornění *nnnn* na úrovni *L*.

## <a name="warnings-that-are-off-by-default"></a>Upozornění, která jsou ve výchozím nastavení vypnutá

Následující upozornění jsou ve výchozím nastavení vypnuta v aplikaci Visual Studio 2015 a novějších verzích:

|||
|-|-|
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md) (úroveň 4)|enumerátor*Identifier*v přepínači výčtu Enum není explicitně zpracovánpopiskem Case.|
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md) (úroveň 4)|enumerátor*Identifier*v přepínači výčtu enum se nezpracovává.|
| [C4165](../error-messages/compiler-warnings/compiler-warning-level-1-c4165.md) (úroveň 1) | Hodnota HRESULT se převádí na bool; Opravdu to chcete? |
| [C4191](../error-messages/compiler-warnings/compiler-warning-level-3-c4191.md) (úroveň 3)|'*Operator*': nebezpečný převod z '*type_of_expression*' na '*type_required*'|
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) (úroveň 4)|'*Identifier*': převod z '*typ1*' na '*typ2*', možná ztráta dat|
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md) (úroveň 4)|'*Operator*': převod z '*typ1*' na '*typ2*', možná ztráta dat|
|[C4255](../error-messages/compiler-warnings/compiler-warning-level-4-c4255.md) (úroveň 4)|'*Function*': není zadaný žádný prototyp funkce: převod ' () ' na ' (void) '|
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md) (úroveň 4)|'*Function*': členská funkce nepřepisuje žádnou virtuální členskou funkci třídy Base.|
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md) (úroveň 1)|'*virtual_function*': k dispozici není přepsání pro virtuální členskou funkci ze základní*třídy ' class*'; funkce je skrytá.|
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md) (úroveň 3)|'*Class*': třída má virtuální funkce, ale destruktor není virtuální.|
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md) (úroveň 4)|'*Function*': k dispozici není přepsání pro virtuální členskou funkci ze základního*typu ' Type*'; funkce je skrytá.|
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md) (úroveň 3)|'*Operator*': Neshoda bez znaménka/záporné konstanty|
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md) (úroveň 4)|používá se nestandardní rozšíření:*var*: proměnná ovládacího prvku smyčky deklarovaná ve smyčce for-Loop se používá mimo obor smyčky for-Loop.|
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md) (úroveň 4)|'*Operator*': výraz je vždy false|
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md) (úroveň 4)|'*Type*': v metadatech CLR byl zjištěn použití nedefinovaného typu – použití tohoto typu může vést k výjimce za běhu.|
|[C4342](../error-messages/compiler-warnings/compiler-warning-level-1-c4342.md) (úroveň 1)|Změna chování: byla volána*funkce Function*, ale v předchozích verzích byl volán operátor member.|
|[C4350](../error-messages/compiler-warnings/compiler-warning-level-1-c4350.md) (úroveň 1)|Změna chování: byl volán příkaz*člen1*namísto '*member2*'.|
|[C4355](../error-messages/compiler-warnings/compiler-warning-c4355.md)|'this' : použito v inicializačním seznamu základních členů|
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md) (úroveň 4)|'*Action*': převod z '*type_1*' na '*type_2*', signed/unsigned – neshoda|
|C4370 (úroveň 3)|došlo ke změně rozložení třídy z předchozí verze kompilátoru z důvodu lepšího balení|
|[C4371](../error-messages/compiler-warnings/c4371.md) (úroveň 3)|*ClassName*: rozložení třídy se mohlo od předchozí verze kompilátoru změnit kvůli lepšímu balení člena*Member*.|
|C4388 (úroveň 4)|neshoda se znaménkem, nebo bez znaménka|
|[C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md) (úroveň 2)|'*Function*': signatura funkce obsahuje typ '*Type*'; C++ objekty nejsou bezpečné předávat mezi čistým a smíšeným nebo nativním kódem.|
|C4426 (úroveň 1)|příznaky optimalizace se změnily po zahrnutí hlavičky, můžou být z důvodu #pragma optimalizovat () <sup>14,1</sup>|
|[C4435](../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md) (úroveň 4)|'*Class1*': Rozložení objektu pod/VD2 se změní kvůli virtuálnímu základu '*Class2*'.|
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md) (úroveň 4)|přetypování dynamic_cast z virtuální základní třídy '*Class1*' na '*Class2*' by mohlo v některých kontextech selhat.|
|C4444 (úroveň 3)|v tomto kontextu není implementována nejvyšší úroveň '__unaligned'|
|[C4464](../error-messages/compiler-warnings/c4464.md) (úroveň 4)|relativní cesta zahrnutí obsahuje znak "..".|
|[C4471](../error-messages/compiler-warnings/compiler-warning-level-4-c4471.md) (úroveň 4)|Dopředná deklarace výčtu bez oboru musí mít nadřízený typ (předpokládá se int) <sup>Perm</sup> .|
|C4472 (úroveň 1)|'*Identifier*' je nativní výčet: přidejte specifikátor přístupu (Private/Public) pro deklaraci spravovaného výčtu.|
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md) (úroveň 4)|'*Function*': vložená funkce, která není odkazovaná, byla odebrána.|
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md) (úroveň 4)|' název typu ': typ-Name překračuje limit meta-dat '*limit*' znaků.|
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md) (úroveň 1)|výraz před čárkou vyhodnocuje na funkci, která nemá k dispozici seznam argumentů|
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md) (úroveň 1)|volání funkce před čárkou nemá seznamu argumentů|
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md) (úroveň 1)|'*Operator*': operátor před čárkou nemá žádný vliv; očekával se operátor s vedlejším účinkem.|
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md) (úroveň 1)|výraz před čárkou nemá žádný vliv; očekávaný výraz s vedlejším účinkem|
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md) (úroveň 1)|'*operator1*': operátor před čárkou nemá žádný vliv; Měli jste v úmyslu '*operator2*'?|
|[C4555](../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md) (úroveň 1)|výraz nemá žádný vliv; očekávaný výraz s vedlejším účinkem|
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md) (úroveň 3)|' __assume ' obsahuje efekt '*efekt*'|
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md) (úroveň 4)|informační: sémantika catch (...) se od verze C++ Visual 7,1 změnila. strukturované výjimky (SEH) už se nezachycují.|
|C4574 (úroveň 4)|'*identifikátor*' je definován jako ' 0 ': nechtěli jste použít ' #if *identifikátor*'?|
|C4577 (úroveň 1)|' s výjimkou ' se používá bez zadaného režimu zpracování výjimek; ukončení u výjimky není zaručeno. Zadat/EHsc|
|C4582 (úroveň 4)|*Type*: konstruktor se nevolá implicitně.|
|C4583 (úroveň 4)|*Type*: destruktor se nevolá implicitně.|
|C4587 (úroveň 1)|'*anonymous_structure*': Změna chování: konstruktor už se nevolá implicitně|
|C4588 (úroveň 1)|'*anonymous_structure*': Změna chování: destruktor už se nevolá implicitně|
|[C4596](../error-messages/compiler-warnings/c4596.md) (úroveň 4)|'*Identifier*': neplatný kvalifikovaný název v deklaraci člena <sup>14,3</sup> <sup>Perm</sup>|
|C4598 (úroveň 1 a úroveň 3)|' #include '*záhlaví*' ': číslo hlavičky v předkompilované hlavičce neodpovídá aktuální kompilaci na této pozici <sup>14,3</sup>|
|C4599 (úroveň 3)|'*možnost* *path*': číslo argumentu příkazového řádku neodpovídá předkompilované hlavičce <sup>14,3</sup>|
|C4605 (úroveň 1)|/D*makro*je zadané na aktuálním příkazovém řádku, ale při sestavení předkompilované hlavičky se nezadalo.|
|[C4608](../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md) (úroveň 3)|'*union_member*' již byl inicializován jiným členem Union v seznamu inicializátorů, '*union_member*' <sup>Perm</sup>|
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md) (úroveň 3)|#pragma upozornění: neexistuje žádné upozornění číslo.|
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md) (úroveň 4)|'derived class': výchozí konstruktor nelze generovat, protože výchozí konstruktor základní třídy je nedostupný|
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md) (úroveň 4)|'derived class': kopírovací konstruktor nelze generovat, protože kopírovací konstruktor základní třídy je nedostupný|
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md) (úroveň 4)|'derived class': operátor přiřazení nelze generovat, protože operátor přiřazení základní třídy je nedostupný|
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md) (úroveň 1)|spřežky nejsou podporovány se -Ze. Sekvence znaků '*graf*' není interpretována jako alternativní token pro '*char*'|
|[C4640 týkajícího](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md) (úroveň 3)|'*instance*': konstrukce lokálního statického objektu není bezpečná pro přístup z více vláken|
| C4643 (úroveň 4) | Dopředná deklarace deklarací*Identifier*v oboru názvů std není C++ standardem povolena. <sup>15.8</sup> |
|C4647 (úroveň 3)|Změna chování: __is_pod (*typ*) má jinou hodnotu v předchozích verzích.|
|C4654 (úroveň 4)|Kód, který je umístěn před zahrnutím předkompilovaných hlaviček, bude ignorován. Přidejte kód do předkompilované hlavičky. <sup>14.1</sup>|
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md) (úroveň 4)|klíčové slovo*symbol*není definované jako preprocesorové makro. nahraďte ho*direktivami*(0).|
|[C4682](../error-messages/compiler-warnings/compiler-warning-level-4-c4682.md) (úroveň 4)|'*symbol*': nebyl zadán atribut směrového parametru, je použita výchozí hodnota [in]|
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md) (úroveň 3)|'*uživatelsky definovaný typ*': možná změna chování, změna v konvenci zpětného volání UDT|
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) (úroveň 1)|'*Function*': podpis neprivátního člena obsahuje sestavení privátního nativního typu '*native_type*'|
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md) (úroveň 4)|'*Function*': funkce není vložena|
|[C4738](../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md) (úroveň 3)|ukládání 32bitového plovoucího výsledku do paměti, možná ztráta|
|[C4746](../error-messages/compiler-warnings/compiler-warning-c4746.md)|nestálý přístup k*výrazu*podléhá nastavení/volatile:\<ISO&#124;MS >; zvažte použití vnitřních funkcí __iso_volatile_load/Store.|
|C4749 (úroveň 4)|podmíněně podporováno: OffsetOf použito pro typ, který není standard-layout|
|C4767 (úroveň 4)|název oddílu '*symbol*' je delší než 8 znaků a linker bude zkrácen.|
|C4768 (úroveň 3)|atributy __declspec před specifikací propojení se ignorují.|
|C4774 (úroveň 4)|'*String*': formátovací řetězec očekávaný v *čísle* argumentu není řetězcový literál.|
|C4777 (úroveň 4)|'*Function*': formátovací řetězec '*řetězec*' vyžaduje argument typu '*typ1*', ale *číslo* argumentu variadické má typ '*typ2*'|
|C4786 (úroveň 3)|'*symbol*': název objektu byl zkrácen na znaky '*Number*' v ladicích informacích|
| [C4800](../error-messages/compiler-warnings/compiler-warning-level-3-c4800.md) (úroveň 4) | Implicitní převod z*typu*na bool Možné ztráty informací <sup>16,0</sup> |
|[C4820](../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md) (úroveň 4)|odsazeníbajtů, které se přidalo po sestavení '*MEMBER_NAME*'|
| [C4822](../error-messages/compiler-warnings/compiler-warning-level-1-c4822.md) (úroveň 1) | '*Member*': členská funkce lokální třídy nemá tělo |
|C4826 (úroveň 2)|Převod z '*typ1*' na '*typ2*' je rozšířen o znaménko. To může způsobit neočekávané chování modulu runtime.|
|C4837 (úroveň 4)|zjistil se trigraph:?? *znak*nahrazen*znakem*|
|C4841 (úroveň 4)|používá se nestandardní rozšíření: označení složeného člena se používá v OffsetOf.|
|C4842 (úroveň 4)|výsledek OffsetOf aplikovaný na typ s použitím vícenásobné dědičnosti není zaručený, aby byl mezi verzemi kompilátoru konzistentní.|
|[C4868](../error-messages/compiler-warnings/compiler-warning-c4868.md) (úroveň 4)|Kompilátor '_File_(*Line_Number*) ' nemůže v seznamu inicializace v závorkách vyhovět pořadí vyhodnocování zleva doprava.|
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md) (úroveň 1)|široký řetězcový literál přetypován na 'LPSTR'|
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md) (úroveň 1)|řetězcový literál přetypován na 'LPWSTR'|
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md) (úroveň 1)|'*deklarátor*': identifikátor GUID lze přidružit pouze k třídě, rozhraní nebo oboru názvů.|
|[C4928](../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md) (úroveň 1)|nelegální inicializace kopírování; implicitně použit více než jeden uživatelem definovaný převod|
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md) (úroveň 4)|Předpokládáme, že knihovna typů byla sestavena pro ukazatele počtu bitů.|
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md) (úroveň 1)|reinterpret_cast používá se mezi souvisejícími třídami: '*Class1*' a '*Class2*'|
|C4962|'*Function*': optimalizace na základě profilu jsou zakázané, protože optimalizace způsobily nekonzistenci dat profilu.|
|[C4986](../error-messages/compiler-warnings/compiler-warning-c4986.md) (úroveň 4)|'*symbol*': specifikace výjimky neodpovídá předchozí deklaraci|
|C4987 (úroveň 4)|použito nestandardní rozšíření: 'throw (...)'|
|C4988 (úroveň 4)|'*symbol*': proměnná je deklarována mimo obor třídy/funkce|
|C5022|*Type*: je zadaných víc konstruktorů Move.|
|C5023|'*Type*': zadáno více operátorů přiřazení přesunutí|
|C5024 (úroveň 4)|*Type*: konstruktor Move byl implicitně definovaný jako odstraněný.|
|C5025 (úroveň 4)|*Type*: operátor Move Assignment byl implicitně definovaný jako odstraněný.|
|C5026 (úroveň 1 a úroveň 4)|*Type*: konstruktor Move byl implicitně definovaný jako odstraněný.|
|C5027 (úroveň 1 a úroveň 4)|*Type*: operátor Move Assignment byl implicitně definovaný jako odstraněný.|
|C5029 (úroveň 4)|používá se nestandardní rozšíření: atributy zarovnání C++ v se použijí jenom na proměnné, datové členy a typy značek.|
|C5031 (úroveň 4)|upozornění #pragma (pop): pravděpodobně neshoda, stav upozornění na vyjímání stavu vloženo v jiném souboru <sup>14,1</sup>|
|C5032 (úroveň 4)|zjištěno upozornění #pragma (push) bez odpovídajícího #pragma upozornění (pop) <sup>14,1</sup>|
|C5034|Použití vnitřních vnitřních objektůzpůsobí, že *funkce* Function se zkompiluje jako kód hosta <sup>15,3</sup> .|
|C5035|použití funkce Function způsobí, že funkce Function se zkompiluje jako kód hosta <sup>15,3</sup> .|
|C5036 (úroveň 1)|při kompilaci s/Hybrid: x86arm64 '*typ1*' do '*typ2*' <sup>15,3</sup> ' – převod ukazatele na funkci vararg|
|[C5038](../error-messages/compiler-warnings/c5038.md) (úroveň 4)|datový člen*člen1*se inicializuje po datovém členu '*member2*' <sup>15,3</sup>|
|C5039 (úroveň 4)|'*Function*': ukazatel nebo odkaz na potenciálně vyvolání funkce předaný do extern funkce jazyka C v rámci-EHC. Pokud tato funkce vyvolá výjimku, může dojít k nedefinovanému chování. <sup>15.5</sup>|
|C5042 (úroveň 3)|'*Function*': deklarace funkcí v oboru bloku nelze zadat ' inline ' na standard C++; odebrat specifikátor inline <sup>15,5</sup>|
|[C5045](../error-messages/compiler-warnings/c5045.md)|Kompilátor vloží Spectre zmírnění paměti, pokud je zadaný přepínač/Qspectre <sup>15,7</sup>|

<sup>14,1</sup> toto upozornění je k dispozici počínaje verzí Visual Studio 2015 Update 1.<br/>
<sup>14,3</sup> toto upozornění je k dispozici od začátku v aplikaci Visual Studio 2015 Update 3.<br/>
<sup>15,3</sup> toto upozornění je k dispozici počínaje verzí Visual Studio 2017 15,3.<br/>
<sup>15,5</sup> toto upozornění je k dispozici počínaje verzí Visual Studio 2017 15,5.<br/>
<sup>15,7</sup> toto upozornění je k dispozici počínaje verzí Visual Studio 2017 15,7.<br/>
<sup>15,8</sup> toto upozornění je k dispozici počínaje verzí Visual Studio 2017 15,8.<br/>
::: moniker range=">= vs-2019"
<sup>16,0</sup> toto upozornění je dostupné od verze Visual Studio 2019 RTM.<br/>
::: moniker-end
<sup>Oprávnění</sup> Toto upozornění je vypnuté, pokud není nastavená možnost kompilátoru [/Permissive-](../build/reference/permissive-standards-conformance.md) .

## <a name="warnings-off-by-default-in-earlier-versions"></a>Upozornění vypnutá ve výchozím nastavení v dřívějších verzích

Tato upozornění byla ve výchozím nastavení ve verzích kompilátoru v rámci sady Visual Studio 2015 vypnutá:

|||
|-|-|
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md) (úroveň 2)|'*Conversion*': zkrácení z '*typ1*' na '*typ2*'|
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md) (úroveň 1)|'*Variable*': zkrácení ukazatele z '*Type*' na '*Type*'|
|[C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md) (úroveň 1)|'*Operation*': převod z '*typ1*' na '*typ2*' větší velikosti|
|[C4319](../error-messages/compiler-warnings/compiler-warning-level-1-c4319.md) (úroveň 1)|'*Operator*': nula rozšiřuje '*typ1*' na '*typ2*' o větší velikost|

Toto upozornění bylo ve výchozím nastavení ve verzích kompilátoru v rámci sady Visual Studio 2012 vypnuto:

|||
|-|-|
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md) (úroveň 4)|chybějící specifikátor typu: předpokládá se int Poznámka: Jazyk C už nepodporuje výchozí int.|

## <a name="see-also"></a>Viz také:

[warning](../preprocessor/warning.md)