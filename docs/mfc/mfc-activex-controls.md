---
title: MFC – ovládací prvky ActiveX
ms.date: 11/19/2018
f1_keywords:
- MFC ActiveX Controls (MFC)
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
ms.openlocfilehash: e9cc38eebed0b1f8e0932e89ef1452261aefd7dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365440"
---
# <a name="mfc-activex-controls"></a>MFC – ovládací prvky ActiveX

Ovládací prvek ActiveX je opakovaně použitelná softwarová součást založená na modelu COM (Com), která podporuje širokou škálu funkcí OLE a lze ji přizpůsobit tak, aby vyhovovala mnoha softwarovým potřebám.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být použita pro nový vývoj. Další informace naleznete [v tématu ActiveX Controls](activex-controls.md).

Ovládací prvky ActiveX jsou navrženy pro použití v běžných kontejnerech ovládacího prvku ActiveX a v Internetu na webových stránkách. Ovládací prvky ActiveX můžete vytvořit buď pomocí knihovny MFC, popsané zde, nebo pomocí [knihovny active template Library (ATL).](../atl/active-template-library-atl-concepts.md)

Ovládací prvek ActiveX se dokáže vykreslit do vlastního okna, reagovat na události (například kliknutí myší) a lze jej spravovat pomocí rozhraní zahrnujícího vlastnosti a metody podobné těm, které obsahují automatizační objekty.

Tyto ovládací prvky lze vyvíjet pro mnoho účelů, jako je například přístup do databáze, monitorování dat nebo vykreslování do grafu. Kromě jejich přenositelnosti podporují ovládací prvky ActiveX funkce, které byly prvkům ActiveX dříve nedostupné, například kompatibilitu s existujícími kontejnery OLE a schopnost integrovat své nabídky do nabídek těchto kontejnerů. Ovládací prvky ActiveX plně podporují automatizaci, která umožňuje prvku vystavit vlastnosti pro čtení a zápis a sadu metod, které lze volat jeho uživatelem.

Lze vytvořit ovládací prvky ActiveX bez oken či prvky, které po své aktivaci okno pouze vytvoří. Ovládací prvky bez okna urychlují zobrazení aplikace a umožňují existenci průhledných a neobdélníkových prvků. Vlastnosti ovládacího prvku ActiveX lze načíst také asynchronně.

Ovládací prvek ActiveX je implementován jako server uvnitř procesu (obvykle malý objekt), který lze použít v libovolném kontejneru OLE. Povšimněte si, že všechny funkce ovládacího prvku ActiveX jsou dostupné pouze v případě, že je použit uvnitř kontejneru OLE navrženého pro komunikaci s prvky ActiveX. Seznam kontejnerů, které podporují ovládací prvky ActiveX, naleznete v tématu [Port ActiveX Controls to Other Applications.](../mfc/containers-for-activex-controls.md) Tento typ kontejneru, dále jen „kontejner ovládacího prvku“, dokáže pracovat s ovládacím prvkem ActiveX pomocí jeho vlastností a metod a přijímá od něj oznámení ve formě událostí. Následující obrázek znázorňuje tuto interakci.

![Souhra řídicího kontejneru activex a ovládacího prvku](../mfc/media/vc37221.gif "Souhra řídicího kontejneru activex a ovládacího prvku") <br/>
Interakce mezi kontejnerem ovládacího prvku ActiveX a ovládacím prvkem ActiveX v okně

Některé nedávné informace o optimalizaci ovládacích prvků ActiveX naleznete v tématu [Ovládací prvky ActiveX knihovny MFC: Optimalizace](../mfc/mfc-activex-controls-optimization.md).

Pokud chcete vytvořit ovládací prvek ActiveX knihovny MFC, přečtěte si informace [o vytvoření projektu ovládacího prvku ActiveX](../mfc/reference/mfc-activex-control-wizard.md).

Další informace naleznete v tématu:

- [ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)

- [Aktivní dokumenty](../mfc/active-documents.md)

- [Principy ovládacích prvků ActiveX](/windows/win32/com/activex-controls)

- [Upgrade existujícího ovládacího prvku ActiveX pro použití v Síti Internet](../mfc/upgrading-an-existing-activex-control.md)

## <a name="basic-components-of-an-activex-control"></a><a name="_core_basic_components_of_an_activex_control"></a>Základní součásti ovládacího prvku ActiveX

Ovládací prvek ActiveX používá několik programových prvků, kterými efektivně komunikuje s kontejnerem ovládacího prvku a s uživatelem. Jedná se o třídu [COleControl](../mfc/reference/colecontrol-class.md), sadu funkcí spouštění událostí a mapování odeslání.

Každý vyvinutý objekt ovládacího prvku ActiveX dědí výkonnou sadu funkcí ze své základní třídy knihovny MFC, třídy `COleControl`. Mezi tyto funkce patří aktivace na místě a automatizační logika. Třída `COleControl` může objektu ovládacího prvku poskytnout stejné funkce jako objekt okna MFC a navíc schopnost vyvolat události. `COleControl`může také poskytnout [ovládací prvky bez oken](../mfc/providing-windowless-activation.md), které spoléhají na jejich kontejner u některých funkcí, které okno poskytuje (zachycení myši, fokus klávesnice, posouvání), ale nabízejí mnohem rychlejší zobrazení.

Jelikož třída ovládacího prvku je odvozena z třídy `COleControl`, dědí schopnost posílat (tzv. „vyvolat“) kontejneru ovládacího prvku zprávy (tzv. události) v případě, že jsou splněny určité podmínky. Tyto události se používají pro oznámení kontejneru ovládacího prvku, že se v ovládacím prvku stalo něco důležitého. Přidáním parametrů k události lze kontejneru ovládacího prvku zaslat dodatečné informace o události. Další informace o událostech ovládacího prvku ActiveX naleznete v článku [Ovládací prvky ActiveX knihovny MFC: Události](../mfc/mfc-activex-controls-events.md).

Posledním prvkem je mapa odeslání, která se používá k vystavení sady funkcí (zvaných metody) a atributů (zvaných vlastnosti) uživateli ovládacího prvku. Vlastnosti umožňují kontejneru ovládacího prvku nebo uživateli manipulovat s prvkem různými způsoby. Uživatel může změnit vzhled ovládacího prvku, změnit určité jeho hodnoty nebo vznést na prvek požadavky, například na přístup k určitým datům, které ovládací prvek udržuje. Toto rozhraní je určeno vývojářem ovládacího prvku a je definováno pomocí **zobrazení třídy**. Další informace o metodách a vlastnostech ovládacího prvku ActiveX naleznete v článcích [Ovládací prvky ActiveX knihovny MFC: Metody](../mfc/mfc-activex-controls-methods.md) a [vlastnosti](../mfc/mfc-activex-controls-properties.md).

## <a name="interaction-between-controls-with-windows-and-activex-control-containers"></a><a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a>Interakce mezi ovládacími prvky se systémem Windows a kontejnery ovládacího prvku ActiveX

Je-li ovládací prvek použit uvnitř kontejneru ovládacího prvku, používá pro komunikaci dva mechanismy: vystavuje vlastnosti a metody a vyvolává události. Následující obrázek ukazuje, jak jsou tyto dva mechanismy implementovány.

![Ovládací prvek ActiveX komunikuje se svým kontejnerem](../mfc/media/vc37222.gif "Ovládací prvek ActiveX komunikuje se svým kontejnerem") <br/>
Komunikace mezi kontejnerem ovládacího prvku ActiveX a prvkem samotným

Předchozí obrázek znázorňuje také způsob, jakým ovládací prvek zpracovává jiná rozhraní OLE (kromě automatizace a událostí).

Veškerou komunikaci ovládacího prvku s kontejnerem zajišťuje třída `COleControl`. Chcete-li zpracovat některé požadavky `COleControl` kontejneru, bude volat členské funkce, které jsou implementovány ve třídě ovládacího prvku. Tímto způsobem jsou zpracovány všechny metody a některé vlastnosti. Třída ovládacího prvku může také započít komunikaci s kontejnerem zavoláním členských funkcí třídy `COleControl`. Tímto způsobem jsou vyvolávány události.

## <a name="active-and-inactive-states-of-an-activex-control"></a><a name="_core_active_and_inactive_states_of_an_activex_control"></a>Aktivní a neaktivní stavy ovládacího prvku ActiveX

Ovládací prvek má dva základní stavy: aktivní a neaktivní. Dříve bylo zvykem, že tyto stavy byly rozlišeny skutečností, zda ovládací prvek má okno. Aktivní ovládací prvek okno měl, neaktivní nikoli. Se zavedením aktivace bez oken není již toto rozlišení univerzální, ale pro mnoho ovládacích prvků je stále platné.

Když [ovládací prvek bez oken](../mfc/providing-windowless-activation.md) přejde aktivní, vyvolá zachycení myši, fokus klávesnice, posouvání a další služby okna z jeho kontejneru. Můžete také [poskytnout interakci myši neaktivním ovládacím prvkům](../mfc/providing-mouse-interaction-while-inactive.md)a také vytvořit ovládací prvky, které [čekají, až se aktivuje, aby se vytvořilo okno](../mfc/turning-off-the-activate-when-visible-option.md).

Ovládací prvek s oknem je po své aktivaci schopen plně spolupracovat s kontejnerem ovládacího prvku, uživatelem a systémem Windows. Obrázek níže ukazuje komunikační kanály mezi ovládacím prvkem ActiveX, kontejnerem ovládacího prvku a operačním systémem.

![Zpracování msg v aktivním ovládacím prvku ActiveX s okny](../mfc/media/vc37223.gif "Zpracování msg v aktivním ovládacím prvku ActiveX s okny") <br/>
Zpracování zpráv systému Windows v ovládacím prvku ActiveX s oknem (je-li aktivní)

## <a name="serialization"></a><a name="_core_serializing_activex_elements"></a>Serializace

Schopnost serializovat data, někdy označovaná také jako trvalost, umožňuje ovládacímu prvku zapisovat hodnoty svých vlastností do trvalého úložiště. Ovládací prvky lze znovu vytvořit přečtením stavu objektu z úložiště.

Ovládací prvek není odpovědný za získání přístupu k paměťovému médiu. Namísto toho je kontejner ovládacího prvku odpovědný za poskytnutí paměťových médií ovládacímu prvku ve vhodných chvílích. Další informace o serializaci naleznete v článku [Ovládací prvky ActiveX knihovny MFC: Serializace](../mfc/mfc-activex-controls-serializing.md). Informace o optimalizaci serializace naleznete v [tématu Optimalizace trvalostva a inicializace](../mfc/optimizing-persistence-and-initialization.md) v ovládacích prvcích ActiveX: Optimalizace.

## <a name="installing-activex-control-classes-and-tools"></a><a name="_core_installing_activex_control_classes_and_tools"></a>Instalace tříd a nástrojů ovládacího prvku ActiveX

Po instalaci jazyka Visual C++ jsou třídy ovládacích prvků ActiveX knihovny MFC a konečné a ladicí DLL knihovny runtime ovládacích prvků ActiveX automaticky nainstalovány, pokud byly v instalačním programu zvoleny Ovládací prvky ActiveX (ve výchozím nastavení zvoleny jsou).

Ve výchozím nastavení jsou třídy a nástroje ovládacího prvku ActiveX nainstalovány v následujících podadresářích v části \Program Files\Microsoft Visual Studio .NET:

- **\Common7\Nástroje**

   Obsahuje soubory testovacího kontejneru (TstCon32.exe a jeho soubory nápovědy)

- **\Vc7\atlmfc\include**

   Obsahuje vložené soubory potřebné k vývoji ovládacích prvků ActiveX pomocí knihovny MFC

- **\Vc7\atlmfc\src\mfc**

   Obsahuje zdrojové kódy určitých tříd ovládacích prvků ActiveX v knihovně MFC

- **\Vc7\atlmfc\lib**

   Obsahuje knihovny potřebné k vývoji ovládacích prvků ActiveX pomocí knihovny MFC

Obsahuje také ukázky ovládacích prvků ActiveX knihovny MFC. Další informace o těchto ukázkách naleznete [v tématu Ovládací prvky Ukázky: Ovládací prvky ActiveX založené na knihovně MFC](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Viz také

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)
