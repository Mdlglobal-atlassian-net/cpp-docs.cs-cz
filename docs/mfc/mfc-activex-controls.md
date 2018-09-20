---
title: MFC – ovládací prvky ActiveX | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MFC ActiveX Controls (MFC)
dev_langs:
- C++
helpviewer_keywords:
- COleControl class [MFC], MFC ActiveX controls
- ActiveX controls [MFC], MFC
- containers [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], serializing
- MFC ActiveX controls [MFC], containers
- serialization [MFC], MFC ActiveX controls
- dispatch maps [MFC], for MFC ActiveX controls
- MFC ActiveX controls [MFC], active/inactive state
- events [MFC], ActiveX controls
- MFC ActiveX controls [MFC]
ms.assetid: c911fb74-3afc-4bf3-a0f5-7922b14d9a1b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b94172d57bc21e7f747a5d0986ef28dbfb80e481
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428639"
---
# <a name="mfc-activex-controls"></a>MFC – ovládací prvky ActiveX

Ovládací prvek ActiveX je opakovaně použitelná softwarová komponenta založená na modelu COM (Component Object), který podporuje širokou škálu funkcí OLE a lze je přizpůsobit podle potřeb mnoha softwaru.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace najdete v tématu [ovládací prvky ActiveX](activex-controls.md).

Ovládací prvky ActiveX jsou navrženy pro použití v běžných kontejnerech ovládacího prvku ActiveX a v Internetu na webových stránkách. Můžete vytvořit ovládací prvky ActiveX, buď pomocí rozhraní MFC popsaného zde, nebo pomocí [aktivní šablony knihovny (ATL)](../atl/active-template-library-atl-concepts.md).

Ovládací prvek ActiveX se dokáže vykreslit do vlastního okna, reagovat na události (například kliknutí myší) a lze jej spravovat pomocí rozhraní zahrnujícího vlastnosti a metody podobné těm, které obsahují automatizační objekty.

Tyto ovládací prvky lze vyvíjet pro mnoho účelů, jako je například přístup do databáze, monitorování dat nebo vykreslování do grafu. Kromě jejich přenositelnosti podporují ovládací prvky ActiveX funkce, které byly prvkům ActiveX dříve nedostupné, například kompatibilitu s existujícími kontejnery OLE a schopnost integrovat své nabídky do nabídek těchto kontejnerů. Ovládací prvky ActiveX plně podporují automatizaci, která umožňuje prvku vystavit vlastnosti pro čtení a zápis a sadu metod, které lze volat jeho uživatelem.

Lze vytvořit ovládací prvky ActiveX bez oken či prvky, které po své aktivaci okno pouze vytvoří. Ovládací prvky bez okna urychlují zobrazení aplikace a umožňují existenci průhledných a neobdélníkových prvků. Vlastnosti ovládacího prvku ActiveX lze načíst také asynchronně.

Ovládací prvek ActiveX je implementován jako server uvnitř procesu (obvykle malý objekt), který lze použít v libovolném kontejneru OLE. Povšimněte si, že všechny funkce ovládacího prvku ActiveX jsou dostupné pouze v případě, že je použit uvnitř kontejneru OLE navrženého pro komunikaci s prvky ActiveX. Zobrazit [přenos ovládacích prvků ActiveX do jiných aplikací](../mfc/containers-for-activex-controls.md) seznam kontejnerů podporujících ovládací prvky ActiveX. Tento typ kontejneru, dále jen „kontejner ovládacího prvku“, dokáže pracovat s ovládacím prvkem ActiveX pomocí jeho vlastností a metod a přijímá od něj oznámení ve formě událostí. Následující obrázek znázorňuje tuto interakci.

![Mezi kontejnerem ovládacího prvku ActiveX a ovládací prvek](../mfc/media/vc37221.gif "vc37221") interakce mezi kontejneru ovládacího prvku ActiveX a ovládacím prvku ActiveX

Některé aktuální informace o optimalizaci ovládacích prvků ActiveX naleznete v tématu [knihovny MFC – ovládací prvky ActiveX: optimalizace](../mfc/mfc-activex-controls-optimization.md).

Chcete-li vytvořit ovládací prvek ActiveX knihovny MFC, naleznete v tématu [vytvoření projektu ovládacího prvku ActiveX](../mfc/reference/mfc-activex-control-wizard.md).

Další informace naleznete v tématu:

- [ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)

- [Aktivní dokumenty](../mfc/active-documents.md)

- [Principy ovládacích prvků ActiveX](/windows/desktop/com/activex-controls)

- [Upgrade existujícího ovládacího prvku ActiveX pro použití na Internetu](../mfc/upgrading-an-existing-activex-control.md)

##  <a name="_core_basic_components_of_an_activex_control"></a> Základní součásti ovládacího prvku ActiveX

Ovládací prvek ActiveX používá několik programových prvků, kterými efektivně komunikuje s kontejnerem ovládacího prvku a s uživatelem. Jedná se o třídu [COleControl](../mfc/reference/colecontrol-class.md), sada funkcí vyvolávající události a odesílání mapování.

Každý vyvinutý objekt ovládacího prvku ActiveX dědí výkonnou sadu funkcí ze své základní třídy knihovny MFC, třídy `COleControl`. Mezi tyto funkce patří aktivace na místě a automatizační logika. Třída `COleControl` může objektu ovládacího prvku poskytnout stejné funkce jako objekt okna MFC a navíc schopnost vyvolat události. `COleControl` Můžete také zadat [ovládací prvky bez oken](../mfc/providing-windowless-activation.md), které spoléhají na své kontejnery pro pomoc s funkcí okno nabízí (například zachycení myši, fokus klávesnice, posouvání), ale nabízí mnohem rychlejší zobrazení.

Jelikož třída ovládacího prvku je odvozena z třídy `COleControl`, dědí schopnost posílat (tzv. „vyvolat“) kontejneru ovládacího prvku zprávy (tzv. události) v případě, že jsou splněny určité podmínky. Tyto události se používají pro oznámení kontejneru ovládacího prvku, že se v ovládacím prvku stalo něco důležitého. Přidáním parametrů k události lze kontejneru ovládacího prvku zaslat dodatečné informace o události. Další informace o události ovládacích prvků ActiveX naleznete v článku [knihovny MFC – ovládací prvky ActiveX: události](../mfc/mfc-activex-controls-events.md).

Posledním prvkem je mapa odeslání, která se používá k vystavení sady funkcí (zvaných metody) a atributů (zvaných vlastnosti) uživateli ovládacího prvku. Vlastnosti umožňují kontejneru ovládacího prvku nebo uživateli manipulovat s prvkem různými způsoby. Uživatel může změnit vzhled ovládacího prvku, změnit určité jeho hodnoty nebo vznést na prvek požadavky, například na přístup k určitým datům, které ovládací prvek udržuje. Toto rozhraní je určeno vývojářem ovládacího prvku a je definován pomocí **zobrazení tříd**. Další informace o vlastnosti a metody ovládacího prvku ActiveX, najdete v článcích [knihovny MFC – ovládací prvky ActiveX: metody](../mfc/mfc-activex-controls-methods.md) a [vlastnosti](../mfc/mfc-activex-controls-properties.md).

##  <a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a> Interakce mezi ovládacími prvky s Windows a kontejnery ovládacích prvků ActiveX

Je-li ovládací prvek použit uvnitř kontejneru ovládacího prvku, používá pro komunikaci dva mechanismy: vystavuje vlastnosti a metody a vyvolává události. Následující obrázek ukazuje, jak jsou tyto dva mechanismy implementovány.

![Ovládací prvek ActiveX komunikuje s jejím kontejnerem](../mfc/media/vc37222.gif "vc37222") komunikace mezi kontejneru ovládacího prvku ActiveX a ovládacím prvku ActiveX

Předchozí obrázek znázorňuje také způsob, jakým ovládací prvek zpracovává jiná rozhraní OLE (kromě automatizace a událostí).

Veškerou komunikaci ovládacího prvku s kontejnerem zajišťuje třída `COleControl`. Pro zpracování některých požadavků kontejneru `COleControl` bude volat členské funkce, které jsou implementované ve třídě ovládacího prvku. Tímto způsobem jsou zpracovány všechny metody a některé vlastnosti. Třída ovládacího prvku může také započít komunikaci s kontejnerem zavoláním členských funkcí třídy `COleControl`. Tímto způsobem jsou vyvolávány události.

##  <a name="_core_active_and_inactive_states_of_an_activex_control"></a> Aktivní a neaktivní stavy ovládacího prvku ActiveX

Ovládací prvek má dva základní stavy: aktivní a neaktivní. Dříve bylo zvykem, že tyto stavy byly rozlišeny skutečností, zda ovládací prvek má okno. Aktivní ovládací prvek okno měl, neaktivní nikoli. Se zavedením aktivace bez oken není již toto rozlišení univerzální, ale pro mnoho ovládacích prvků je stále platné.

Když [ovládací prvek bez oken](../mfc/providing-windowless-activation.md) své aktivaci vyvolá zachycení myši, fokus klávesnice, posouvání a jiné služby okna ze svého kontejneru. Můžete také [poskytnout interakce myší neaktivním ovládacím prvkům](../mfc/providing-mouse-interaction-while-inactive.md), stejně jako vytvoření ovládacích prvků [čekají na aktivaci vytvořit okno](../mfc/turning-off-the-activate-when-visible-option.md).

Ovládací prvek s oknem je po své aktivaci schopen plně spolupracovat s kontejnerem ovládacího prvku, uživatelem a systémem Windows. Obrázek níže ukazuje komunikační kanály mezi ovládacím prvkem ActiveX, kontejnerem ovládacího prvku a operačním systémem.

![Zpráva zpracování v aktivním ovládacím prvku ActiveX](../mfc/media/vc37223.gif "vc37223") Windows zpracování zprávy v ovládacím prvku ActiveX (Pokud aktivní)

##  <a name="_core_serializing_activex_elements"></a> Serializace

Schopnost serializovat data, někdy označovaná také jako trvalost, umožňuje ovládacímu prvku zapisovat hodnoty svých vlastností do trvalého úložiště. Ovládací prvky lze znovu vytvořit přečtením stavu objektu z úložiště.

Ovládací prvek není odpovědný za získání přístupu k paměťovému médiu. Namísto toho je kontejner ovládacího prvku odpovědný za poskytnutí paměťových médií ovládacímu prvku ve vhodných chvílích. Další informace o serializaci naleznete v článku [knihovny MFC – ovládací prvky ActiveX: serializace](../mfc/mfc-activex-controls-serializing.md). Informace o optimalizaci serializace naleznete v tématu [optimalizace trvalosti a inicializace](../mfc/optimizing-persistence-and-initialization.md) v ovládacích prvcích ActiveX: optimalizace.

##  <a name="_core_installing_activex_control_classes_and_tools"></a> Instalace nástroje a třídy ovládacích prvků ActiveX

Po instalaci jazyka Visual C++ jsou třídy ovládacích prvků ActiveX knihovny MFC a konečné a ladicí DLL knihovny runtime ovládacích prvků ActiveX automaticky nainstalovány, pokud byly v instalačním programu zvoleny Ovládací prvky ActiveX (ve výchozím nastavení zvoleny jsou).

Ve výchozím nastavení třídy ovládacích prvků ActiveX a nástroje jsou nainstalovány v následujících podadresářích pod \Program Files\Microsoft sady Visual Studio .NET:

- **\Common7\Tools**

     Obsahuje soubory testovacího kontejneru (TstCon32.exe a jeho soubory nápovědy)

- **\Vc7\atlmfc\include**

     Obsahuje vložené soubory potřebné k vývoji ovládacích prvků ActiveX pomocí knihovny MFC

- **\Vc7\atlmfc\src\mfc**

     Obsahuje zdrojové kódy určitých tříd ovládacích prvků ActiveX v knihovně MFC

- **\Vc7\atlmfc\lib**

     Obsahuje knihovny potřebné k vývoji ovládacích prvků ActiveX pomocí knihovny MFC

Obsahuje také ukázky ovládacích prvků ActiveX knihovny MFC. Další informace o těchto ukázkách najdete v tématu [ukázky ovládacích prvků: ovládací prvky ActiveX](../visual-cpp-samples.md)

## <a name="see-also"></a>Viz také

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)
