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
ms.openlocfilehash: 9a0199577ea46520c2eadc308812de8a1ce4b514
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "71685808"
---
# <a name="dialog-data-exchange"></a>Výměna dat dialogových oken

Použijete-li mechanismus DDX, nastavíte počáteční hodnoty členských proměnných objektu dialogového okna, obvykle v obslužné rutině `OnInitDialog` nebo v konstruktoru dialogového okna. Bezprostředně před zobrazením dialogu, DDX mechanismus rozhraní přenáší hodnoty členských proměnných do ovládacích prvků v dialogovém okně, kde se zobrazí, když se dialogové okno zobrazí jako odpověď na `DoModal` nebo `Create`. Výchozí implementace `OnInitDialog` v `CDialog` volá `UpdateData` členskou funkci třídy `CWnd` pro inicializaci ovládacích prvků v dialogovém okně.

Stejný mechanismus přenáší hodnoty z ovládacích prvků na členské proměnné, když uživatel klikne na tlačítko OK (nebo pokaždé, když zavoláte `UpdateData` členskou funkci s argumentem **true**). Mechanismus ověřování dat dialogového okna ověřuje všechny datové položky, pro které jste určili pravidla ověřování.

Následující obrázek znázorňuje výměnu dialogových dat.

![Výměna dat dialogových oken](../mfc/media/vc379d1.gif "Výměna dat dialogových oken") <br/>
Výměna dat dialogových oken

`UpdateData` funguje v obou směrech, jak je uvedeno v parametru **bool** , který je předaný do něj. Chcete-li provést výměnu, `UpdateData` nastaví objekt `CDataExchange` a zavolá přepsanou třídu `DoDataExchange` členské funkce `CDialog`. `DoDataExchange` přebírá argument typu `CDataExchange`. Objekt `CDataExchange` předaný do `UpdateData` představuje kontext výměny, který tyto informace definuje jako směr výměny.

Když jste (nebo průvodce kódem) přepsali `DoDataExchange`, zadáte volání jedné funkce DDX na datový člen (ovládací prvek). Každá funkce DDX ví, jak vyměňovat data v obou směrech na základě kontextu zadaného argumentem `CDataExchange` předaného do vašeho `DoDataExchange` pomocí `UpdateData`.

Knihovna MFC poskytuje mnoho funkcí DDX pro různé druhy systému Exchange. Následující příklad ukazuje `DoDataExchange` přepsání, ve kterém jsou volány dvě funkce DDX a jedna funkce DDV:

[!code-cpp[NVC_MFCControlLadenDialog#49](../mfc/codesnippet/cpp/dialog-data-exchange_1.cpp)]

Řádky `DDX_` a `DDV_` představují datovou mapu. Zobrazí se ukázková funkce DDX a DDV pro ovládací prvek zaškrtávací políčko a ovládací prvek pro úpravy v uvedeném pořadí.

Pokud uživatel zruší modální dialogové okno, `OnCancel` členská funkce ukončí dialogové okno a `DoModal` vrátí hodnotu **IDCANCEL**. V takovém případě mezi dialogovým oknem a objektem dialogového okna nejsou vyměňována žádná data.

## <a name="see-also"></a>Viz také:

[Výměna a ověřování dat dialogových oken](../mfc/dialog-data-exchange-and-validation.md)<br/>
[Práce s dialogovými okny v MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Ověřování dat dialogového okna](../mfc/dialog-data-validation.md)
