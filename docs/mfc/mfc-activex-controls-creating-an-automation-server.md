---
title: 'MFC – ovládací prvky ActiveX: Vytvoření serveru automatizace'
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers [MFC], MFC ActiveX controls
- ActiveX controls [MFC], Automation server
- MFC ActiveX controls [MFC], Automation server
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
ms.openlocfilehash: 6861d8b0798ece957c84f52a15032052aa83b9c7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448123"
---
# <a name="mfc-activex-controls-creating-an-automation-server"></a>MFC – ovládací prvky ActiveX: Vytvoření serveru automatizace

Ovládací prvek ActiveX knihovny MFC můžete vyvíjet jako automatizační server za účelem programově vložení ovládacího prvku v jiné aplikaci a volání metod v ovládacím prvku z aplikace. Takový ovládací prvek bude stále k dispozici zajistit také jejich hostování v kontejneru ovládacího prvku ActiveX.

### <a name="to-create-a-control-as-an-automation-server"></a>Vytvoření ovládacího prvku jako automatizační server

1. [Vytvoření](../mfc/reference/mfc-activex-control-wizard.md) ovládacího prvku.

1. [Přidejte metody](../mfc/mfc-activex-controls-methods.md).

1. Přepsat [IsInvokeAllowed](../mfc/reference/colecontrol-class.md#isinvokeallowed).

1. Vytvoření ovládacího prvku.

### <a name="to-programmatically-access-the-methods-in-an-automation-server"></a>Chcete-li programově přístup k metodám v serveru automatizace

1. Vytvoření aplikace, například, [MFC exe](../mfc/reference/mfc-application-wizard.md).

1. Na začátku `InitInstance` funkci, přidejte následující řádek:

   [!code-cpp[NVC_MFC_AxCont#17](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_1.cpp)]

1. V zobrazení tříd klikněte pravým tlačítkem myši na uzel projektu a vyberte **přidáním tříd z knihovny typů** Import knihovny typů.

   Soubory s .cpp a .h přípony názvu souboru se přidá do projektu.

1. V souboru hlaviček třídy, ve kterém bude volat jeden nebo více metod v ovládacím prvku ActiveX, přidejte následující řádek: `#include filename.h`, kde název_souboru je název souboru hlaviček, který byl vytvořen při importu knihovny typů.

1. Ve funkci, ve kterém bude provedeno volání metody v ovládacím prvku ActiveX přidejte kód, který vytvoří objekt ovládacího obálkovou třídu a vytvořit objekt ActiveX. Například následující kód knihovny MFC vytvoří `CCirc` ovládacího prvku, získá vlastnost Caption a výsledek se zobrazí po kliknutí na tlačítko OK v dialogovém okně:

   [!code-cpp[NVC_MFC_AxCont#18](../mfc/codesnippet/cpp/mfc-activex-controls-creating-an-automation-server_2.cpp)]

Pokud chcete přidat metody do ovládacího prvku ActiveX po použití v aplikaci, můžete začít používat nejnovější verzi ovládacího prvku v aplikaci tak, že odstraníte soubory, které se vytvořily při importu knihovny typů. Importujte knihovny typů znovu.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

