---
title: Odvozené třídy oken
ms.date: 11/04/2016
helpviewer_keywords:
- window class hierarchy
- hierarchies, window classes
- classes [MFC], derived
- CWnd class [MFC], classes derived from
- derived classes [MFC], window classes
- window classes [MFC], derived
ms.assetid: 6f7e437e-fbde-4a06-bfab-72d9dbf05292
ms.openlocfilehash: e86ca139b8470dce614564f0c0134a611adeda2c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153371"
---
# <a name="derived-window-classes"></a>Odvozené třídy oken

Můžete vytvářet okna přímo z [CWnd](../mfc/reference/cwnd-class.md), nebo odvozovat nové třídy okna z `CWnd`. Toto je takto obvykle vytváříte vlastní okna. Většina oken v rámci programu jsou však místo toho vytvářeny z jednoho z `CWnd`-odvozené třídy oken s rámečkem dodávané knihovnou MFC.

## <a name="frame-window-classes"></a>Třídy oken s rámečkem

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
Používá se pro rámce windows SDI, která ohraničují jeden dokument a jeho zobrazení. Okno rámce je hlavní okno rámce aplikace i okno rámce aktuálního dokumentu.

[CMDIFrameWnd –](../mfc/reference/cmdiframewnd-class.md)<br/>
Použít jako hlavní okno rámce pro aplikace MDI. Hlavní okno rámce je kontejner pro všechna okna dokumentu MDI a sdílí s nimi jeho nabídky panelu. Okna rámce MDI je okno nejvyšší úrovně, který se zobrazí na ploše.

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
Používá se pro jednotlivé dokumenty otevřené v okna hlavního rámce MDI. Každý dokument a jeho zobrazení jsou orámovány podřízeným oknem rámce MDI obsažených hlavním okně rámce MDI. Podřízené okno MDI vypadá podobně jako typické okno rámce, ale je obsaženo uvnitř okna rámce MDI namísto na ploše. Podřízené okno MDI však nemá vlastní panel nabídek a musí sdílet panel nabídek okna rámce MDI, který jej obsahuje.

Další informace najdete v tématu [rámce Windows](../mfc/frame-windows.md).

## <a name="other-window-classes-derived-from-cwnd"></a>Další třídy Window odvozené z CWnd

Kromě oken rámce jsou několik dalších hlavních kategorií oken odvozeno `CWnd`:

*Zobrazení*<br/>
Zobrazení jsou vytvářena pomocí `CWnd`-odvozené třídy [CView](../mfc/reference/cview-class.md) (nebo některé z odvozených tříd). Zobrazení je připojené k dokumentu a funguje jako prostředník mezi dokumentem a uživatelem. Zobrazení je podřízené okno (není podřízený formulář MDI), které obvykle vyplní klientské oblasti okna rámce aplikace SDI nebo okna podřízeného rámce MDI (nebo část oblasti klienta se nevztahuje panel nástrojů nebo stavového řádku).

*Dialogová okna*<br/>
Dialogová okna jsou vytvářena pomocí `CWnd`-odvozené třídy [CDialog](../mfc/reference/cdialog-class.md).

*Formuláře*<br/>
Zobrazení formuláře založená na dialogovém okně prostředky, jako například dialogová okna, jsou vytvořena pomocí tříd [CFormView](../mfc/reference/cformview-class.md), [CRecordView](../mfc/reference/crecordview-class.md), nebo [CDaoRecordView](../mfc/reference/cdaorecordview-class.md).

*Ovládací prvky*<br/>
Ovládací prvky jako tlačítka, seznamy a pole se seznamem jsou vytvořeny pomocí ostatních tříd odvozených z `CWnd`. Zobrazit [řídit témata](../mfc/controls-mfc.md).

*Ovládací pruhy*<br/>
Podřízená okna obsahující ovládací prvky. Příklady zahrnují panely nástrojů a stavové řádky. Zobrazit [ovládací pruhy](../mfc/control-bars.md).

## <a name="window-class-hierarchy"></a>Hierarchie tříd oken

Odkazovat [graf hierarchie MFC](../mfc/hierarchy-chart.md) v *odkaz knihovny MFC*. Zobrazení jsou vysvětlena v [architekturu Document/View](../mfc/document-view-architecture.md). Dialogová okna jsou vysvětlené v [dialogových oknech](../mfc/dialog-boxes.md).

## <a name="creating-your-own-special-purpose-window-classes"></a>Vytvoření vlastní třídy oken se speciálním účelem

Kromě tříd oken poskytovaných knihovnou tříd budete potřebovat speciální podřízená okna. Chcete-li vytvořit takové okno, vytvořte vlastní [CWnd](../mfc/reference/cwnd-class.md)-odvozené třídy a nastavte ji na podřízené okno snímku nebo zobrazení. Berte v úvahu, že rozhraní spravuje rozsah klientské oblasti okna rámce dokumentu. Většina klientské oblasti je spravována zobrazením, ale ostatní okna, jako jsou například ovládací panely nebo vlastní okna, mohou sdílet prostor se zobrazením. Možná budete muset pracovat s mechanismy ve třídách [CView](../mfc/reference/cview-class.md) a [ccontrolbar –](../mfc/reference/ccontrolbar-class.md) pro umístění podřízených oken v klientské oblasti okna rámce.

[Vytvoření Windows](../mfc/creating-windows.md) popisuje vytvoření vytvoření objektů oken a oken, která spravují.

## <a name="see-also"></a>Viz také:

[Objekty oken](../mfc/window-objects.md)
