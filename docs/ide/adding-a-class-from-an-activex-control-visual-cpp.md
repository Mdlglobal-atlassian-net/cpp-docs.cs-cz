---
title: Přidání třídy z ovládacího prvku ActiveX (Visual C++)
ms.date: 09/07/2018
helpviewer_keywords:
- ActiveX controls [C++], adding classes
- classes [C++], creating
ms.assetid: 729fcb37-54b8-44d5-9b4e-50bb16e0eea4
ms.openlocfilehash: c78919aeee2d2577cd7371952d95c57c17b1e5ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466622"
---
# <a name="adding-a-class-from-an-activex-control-visual-c"></a>Přidání třídy z ovládacího prvku ActiveX (Visual C++)

Tohoto průvodce použijte k vytvoření třídy knihovny MFC z rozhraní v ovládacím prvku ActiveX k dispozici. Můžete přidat do třídy knihovny MFC [aplikace knihovny MFC](../mfc/reference/creating-an-mfc-application.md), [knihovny MFC DLL](../mfc/reference/creating-an-mfc-dll-project.md), nebo [ovládací prvek ActiveX knihovny MFC](../mfc/reference/creating-an-mfc-activex-control.md).

> [!WARNING]
> V sadě Visual Studio 2017 verze 15.9 průvodce tento kód je zastaralá a v budoucí verzi systému Visual Studio se odebere. Tento průvodce je používána zřídka. Obecné podpory knihovny ATL a MFC nemá žádný vliv, odebráním tohoto průvodce. Pokud chcete sdílet svůj názor na toto vyřazení, vyplňte prosím [tento průzkum](https://www.surveymonkey.com/r/QDWKKCN). Vaše zpětná vazba záleží na nás.

> [!NOTE]
>  Není nutné k vytvoření projektu knihovny MFC s podporou pro přidání třídy z ovládacího prvku ActiveX automatizace.

Ovládací prvek ActiveX je opakovaně použitelná softwarová komponenta založená na modelu COM (Component Object), který podporuje širokou škálu funkcí OLE a lze je přizpůsobit podle potřeb mnoha softwaru. Ovládací prvky ActiveX jsou navrženy pro použití v běžných kontejnerech ovládacího prvku ActiveX a na Internetu v webové stránky.

### <a name="to-add-an-mfc-class-from-an-activex-control"></a>Přidání třídy knihovny MFC z ovládacího prvku ActiveX

1. V jednom **Průzkumníka řešení** nebo [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code), klikněte pravým tlačítkem na název projektu, ke kterému chcete přidat třídu ovládacího prvku ActiveX.

1. V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **přidat třídu**.

1. V [přidat třídu](../ide/add-class-dialog-box.md) dialogové okno, v podokně šablon, klikněte na tlačítko **třída knihovny MFC z ovládacího prvku ActiveX**a potom klikněte na tlačítko **otevřít** zobrazíte [přidat třídu z ActiveX Ovládací prvek Průvodce](../ide/add-class-from-activex-control-wizard.md).

V průvodci můžete přidat více než jedno rozhraní v ovládacím prvku ActiveX. Podobně můžete vytvořit třídy z více než jeden ovládací prvek ActiveX v rámci jedné relace průvodce.

Můžete taky přidat třídy z registrovaných v systému – ovládací prvky ActiveX nebo třídy lze přidat z ovládacích prvků ActiveX, které jsou umístěny v souborech knihovny typů (.tlb, .olb, .dll, .ocx nebo .exe) i bez jejich první registrace v systému. Zobrazit [registrace ovládacích prvků OLE](../mfc/reference/registering-ole-controls.md) Další informace o registraci ovládacích prvků ActiveX.

Průvodce vytvoří třídy knihovny MFC, odvozený z [CWnd](../mfc/reference/cwnd-class.md) nebo z [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md), pro každé rozhraní, kterou přidáte z vybraného ovládacího prvku ActiveX.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br>
[Úvod do modelu COM a knihovny ATL](../atl/introduction-to-com-and-atl.md)