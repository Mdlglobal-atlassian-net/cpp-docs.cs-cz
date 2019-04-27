---
title: Výměna dat dialogových oken
ms.date: 11/19/2018
helpviewer_keywords:
- initializing dialog boxes
- canceling data exchange
- dialog box data, retrieving
- DDX (dialog data exchange), data exchange mechanism
- dialog boxes [MFC], initializing
- dialog boxes [MFC], retrieving user input using DDX
- dialog box data
- dialog boxes [MFC], data exchange
- CDataExchange class [MFC], using DDX
- DoDataExchange method [MFC]
- user input [MFC], retrieving from MFC dialog boxes
- capturing user input [MFC]
- transferring dialog box data
- DDX (dialog data exchange), canceling
- UpdateData method [MFC]
- retrieving dialog box data [MFC]
ms.assetid: 4675f63b-41d2-45ed-b6c3-235ad8ab924b
ms.openlocfilehash: 338630aef358d9490461179288d5c45a2d3b821c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348790"
---
# <a name="dialog-data-exchange"></a>Výměna dat dialogových oken

Pokud použijete mechanismus DDX, nastavíte počáteční hodnoty dialogového okna proměnné členů objektu, obvykle v vaše `OnInitDialog` obslužné rutiny nebo konstruktor dialogového okna. Bezprostředně před zobrazením dialogového okna, je v rámci DDX Frameworku přenese hodnoty proměnné členů k ovládacím prvkům v dialogovém okně, ve kterém se zobrazují při samotné se zobrazí dialogové okno v reakci na `DoModal` nebo `Create`. Výchozí implementace `OnInitDialog` v `CDialog` volání `UpdateData` členské funkce třídy `CWnd` inicializovat ovládací prvky v dialogovém okně.

Stejný mechanismus přenáší hodnoty z ovládacích prvků do proměnné členů když uživatel klikne na tlačítko OK (nebo když voláte `UpdateData` členskou funkci s argumentem **TRUE**). Mechanismus ověřování dat dialogového okna ověří všechny datové položky, pro které jste zadali ověřovací pravidla.

Následující obrázek znázorňuje výměna dat dialogových oken.

![Výměna dat dialogových oken pole](../mfc/media/vc379d1.gif "výměna dat dialogových oken pole") <br/>
Výměna dat dialogových oken

`UpdateData` funguje v obou směrech, jak jsou určené **BOOL** předán parametr. K provedení výměny `UpdateData` nastaví `CDataExchange` objektu a volání vlastní třídy dialogového okna přepsání `CDialog`společnosti `DoDataExchange` členskou funkci. `DoDataExchange` přebírá argument typu `CDataExchange`. `CDataExchange` Předán objekt `UpdateData` představuje místní exchange, definování takové informace jako směr exchange.

Když jste (nebo Průvodce kódem) přepsat `DoDataExchange`, zadáte volání funkce jedné DDX na datový člen (řízení). Každá funkce DDX ví, jak vyměňovat data v obou směrech na základě kontextu poskytnutých `CDataExchange` argument předaný do vaší `DoDataExchange` podle `UpdateData`.

Knihovna MFC poskytuje mnoho funkcí DDX pro různé druhy exchange. Následující příklad ukazuje `DoDataExchange` přepsání, ve které dvě DDX jsou volány funkce a DDV funkce:

[!code-cpp[NVC_MFCControlLadenDialog#49](../mfc/codesnippet/cpp/dialog-data-exchange_1.cpp)]

`DDX_` a `DDV_` řádky jsou data mapování. Ukázka DDX a DDV funkce uvedené jsou pro ovládací prvek zaškrtávací políčko a ovládací prvek textové pole.

Pokud uživatel zruší modální dialogové okno, `OnCancel` členskou funkci ukončí dialogové okno a `DoModal` vrátí hodnotu **IDCANCEL**. V takovém případě žádná data se vyměňují mezi dialogových oken a objektu dialogového okna.

## <a name="see-also"></a>Viz také:

[Výměna a ověřování dat dialogových oken](../mfc/dialog-data-exchange-and-validation.md)<br/>
[Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Ověřování dat dialogového okna](../mfc/dialog-data-validation.md)
