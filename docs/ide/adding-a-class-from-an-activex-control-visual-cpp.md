---
title: Přidání třídy z ovládacího prvku ActiveX
ms.date: 11/08/2018
f1_keywords:
- vc.codewiz.class.axcontrol
helpviewer_keywords:
- ActiveX controls [C++], adding classes
- classes [C++], creating
- ActiveX Control Wizard
- add class from ActiveX control wizard [C++]
ms.assetid: 729fcb37-54b8-44d5-9b4e-50bb16e0eea4
ms.openlocfilehash: 1d91d98082a5c5d6d45bfa31e81c59e8925aa2c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386266"
---
# <a name="add-a-class-from-an-activex-control"></a>Přidání třídy z ovládacího prvku ActiveX

Tohoto průvodce použijte k vytvoření třídy knihovny MFC z rozhraní v ovládacím prvku ActiveX k dispozici. Můžete přidat do třídy knihovny MFC [aplikace knihovny MFC](../mfc/reference/creating-an-mfc-application.md), [knihovny MFC DLL](../mfc/reference/creating-an-mfc-dll-project.md), nebo [ovládací prvek ActiveX knihovny MFC](../mfc/reference/creating-an-mfc-activex-control.md).

> [!WARNING]
> V sadě Visual Studio 2017 verze 15.9 Microsoft nepoužívá tato Průvodce kódem a bude ho neodebereme v budoucí verzi systému Visual Studio. Tento průvodce je používána zřídka. Obecné podpory knihovny ATL a MFC nemá žádný vliv, odebráním tohoto průvodce. Pokud chcete sdílet svůj názor na toto vyřazení, dokončete [tento průzkum](https://www.surveymonkey.com/r/QDWKKCN). Vaše zpětná vazba záleží na nás.
<!-- Blank comment here to separate the warning and note. -->
> [!NOTE]
> Není nutné k vytvoření projektu knihovny MFC s podporou pro přidání třídy z ovládacího prvku ActiveX automatizace.

Ovládací prvek ActiveX je opakovaně použitelná softwarová komponenta založená na modelu COM (Component Object), který podporuje širokou škálu funkcí OLE. Je možné přizpůsobit podle potřeb mnoha softwaru. Ovládací prvky ActiveX v běžných kontejnerech ovládacího prvku ActiveX nebo na Internetu můžete použít v webové stránky.

**Přidání třídy knihovny MFC z ovládacího prvku ActiveX:**

1. V jednom **Průzkumníka řešení** nebo [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code), klikněte pravým tlačítkem na název projektu, ke kterému chcete přidat třídu ovládacího prvku ActiveX.

1. V místní nabídce zvolte **přidat**a klikněte na tlačítko **přidat třídu**.

1. V [přidat třídu](../ide/add-class-dialog-box.md) v dialogu **šablony** podokně zvolte **třída knihovny MFC z ovládacího prvku ActiveX**a klikněte na tlačítko **otevřít** zobrazíte [přidání třídy z Průvodce ovládacím prvkem ActiveX](#add-class-from-activex-control-wizard).

V průvodci můžete přidat více než jedno rozhraní v ovládacím prvku ActiveX. Můžete také vytvořit třídy z více než jeden ovládací prvek ActiveX v rámci jedné relace průvodce.

Můžete taky přidat třídy z registrovaných v systému – ovládací prvky ActiveX nebo třídy lze přidat z ovládacích prvků ActiveX, které jsou umístěny v souborech knihovny typů (.tlb, .olb, .dll, .ocx nebo .exe) i bez jejich první registrace v systému. Další informace o registraci ovládacích prvků ActiveX naleznete v tématu [řídí registrace OLE](../mfc/reference/registering-ole-controls.md).

Průvodce vytvoří třídy knihovny MFC, odvozený z [CWnd](../mfc/reference/cwnd-class.md) nebo z [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md), pro každé rozhraní, kterou přidáte z vybraného ovládacího prvku ActiveX.

## <a name="in-this-section"></a>V tomto oddílu

- [Přidání třídy z Průvodce ovládacím prvkem ActiveX](#add-class-from-activex-control-wizard)

## <a name="add-class-from-activex-control-wizard"></a>Přidání třídy z Průvodce ovládacím prvkem ActiveX

Tohoto průvodce použijte k přidání třídy knihovny MFC z ovládacího prvku ActiveX k dispozici. Průvodce vytvoří třídu pro každé rozhraní, kterou přidáte z vybraného ovládacího prvku ActiveX.

- **Přidat třídu Z:**

  Určuje umístění knihovny typů, ze kterého se vytvoří třídu.

  |Možnost|Popis|
  |------------|-----------------|
  |**Registru**|Knihovna typů je registrován v systému. Zaregistrované knihovny typů jsou uvedeny v **dostupné ovládací prvky ActiveX**.|
  |**File**|Knihovna typů není nutně registrován v systému, ale je uložen v souboru. Zadejte umístění souboru v **umístění**.|

- **Dostupné ovládací prvky ActiveX**

  Určuje ovládací prvky ActiveX, které jsou aktuálně registrované v systému. Vyberte ze seznamu zobrazíte jeho rozhraní v ovládacím prvku ActiveX **rozhraní** seznamu. Zobrazit [– ovládací prvky ActiveX knihovny MFC: Distribuce ovládacích prvků ActiveX](../mfc/mfc-activex-controls-distributing-activex-controls.md) Další informace o registraci komponenty – ovládací prvky ActiveX.

  Pokud vyberete **souboru** pod **přidat třídu z**, toto pole je k dispozici pro změnu.

- **Poloha**

  Určuje umístění ovládacího prvku ActiveX. Pokud vyberete **souboru** pod **přidat třídu z**, můžete uvést umístění souboru, který má knihovnu typů. Přejděte do umístění souboru, vyberte tlačítko se třemi tečkami.

  Pokud vyberete **registru** pod **přidat třídu z**, toto pole je k dispozici pro změnu.

- **Rozhraní**

  Určuje rozhraní v ovládacím prvku ActiveX. Průvodce používá rozhraní z aktuálního výběru v **dostupné ovládací prvky ActiveX**, nebo použije rozhraní ze zadané v souboru knihovny typů **umístění**.

  |Tlačítka převodu|Popis|
  |---------------------|-----------------|
  |**>**|Přidá rozhraní vybrané v **rozhraní** seznamu. Tato možnost je k dispozici, pokud není vybrané žádné rozhraní.|
  |**>>**|Přidá všechna rozhraní v ovládacím prvku ActiveX. Průvodce používá rozhraní z aktuálního výběru v **dostupné ovládací prvky ActiveX**, nebo použije rozhraní ze zadané v souboru knihovny typů **umístění**.|
  |**\<**|Odebere aktuálně vybranou v třídu **generované třídy** seznamu. Není k dispozici, pokud není žádná třída aktuálně vybraný **generované třídy** seznamu.|
  |**\<\<**|Odebere všechny třídy v **generované třídy** seznamu. Pokud není k dispozici **generované třídy** seznam je prázdný.|

- **Generované třídy**

  Určuje názvy tříd, které mají být vygenerovány z rozhraní přidaných pomocí **>** nebo **>>** tlačítko. Toto políčko vyberte třídu, použijte nahoru nebo dolů procházejte seznam klíčů. Když vyberete **Dokončit**, může zobrazit každý název generované třídy v **třídy** pole a každý generovaný název souboru v **souboru .h** pole. V tomto poli můžete vybrat pouze jednu třídu najednou.

  Třídu lze odebrat tak, že ji vyberete v tomto seznamu a vyberete **<**. Nemusíte vybrat třídu v **generované třídy** pole odebrat všechny třídy. Výběrem **<<**, odeberte všechny třídy v **generované třídy** pole.

- **Třída**

   Určuje název třídy vybraný v **generované třídy** pole, které průvodce přidá při výběru **Dokončit**. Můžete upravit název v **třídy** pole.

- **.h file**

  Nastaví název hlavičkového souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na názvu je zadat v **generované třídy**. Vyberte tlačítko se třemi tečkami uložení názvu souboru do umístění podle vaší volby, nebo připojit k existujícímu souboru deklaraci třídy. Pokud zvolíte existující soubor, Průvodce neuloží se do vybraného umístění dokud vyberte **Dokončit** v průvodci.

  Průvodce nepřepíše souboru. Pokud vyberte název existující soubor a pak vyberte **Dokončit**, Průvodce vás vyzve k označení, zda se má připojit k deklaraci třídy do obsahu souboru. Vyberte **Ano** pro připojení k souboru; vyberte **ne** pro návrat do průvodce a zadejte jiný název souboru.

- **soubor .cpp**

  Nastaví název implementačního souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na názvu je zadat v **generované třídy**. Vyberte tlačítko se třemi tečkami uložit název souboru do umístění podle vaší volby. Soubor se neukládá do vybraného umístění, dokud nevyberete **Dokončit** v průvodci.

  Průvodce nepřepíše souboru. Pokud vyberte název existující soubor a pak vyberte **Dokončit**, Průvodce vás vyzve k označení, zda se má připojit implementace třídy do obsahu souboru. Vyberte **Ano** pro připojení k souboru; vyberte **ne** pro návrat do průvodce a zadejte jiný název souboru.
