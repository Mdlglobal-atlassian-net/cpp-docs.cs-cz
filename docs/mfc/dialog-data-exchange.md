---
title: Výměna dat dialogových oken | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2385efcef9949eab60b1542b2039e3ff2ac80e38
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930856"
---
# <a name="dialog-data-exchange"></a>Výměna dat dialogových oken
Pokud chcete použít tento mechanismus DDX, nastavíte počáteční hodnoty dialogového okna objektu členské proměnné, obvykle v vaší `OnInitDialog` obslužná rutina nebo konstruktor dialogové okno. Okamžitě předtím, než se zobrazí dialogové okno, v rámci DDX Frameworku přenese hodnoty členské proměnné ovládacích prvků v dialogovém okně jejich umístění při samotné se zobrazí dialogové okno v reakci na `DoModal` nebo `Create`. Výchozí implementaci `OnInitDialog` v `CDialog` volání `UpdateData` funkce člena třídy `CWnd` k chybě při inicializaci ovládacích prvků v dialogovém okně.  
  
 Shodný mechanismus přenosu hodnoty z ovládacích prvků do proměnné členů když uživatel klikne na tlačítko OK (nebo vždy, když zavoláte `UpdateData` – členská funkce s argumentem **TRUE**). Mechanismus ověřování dat dialogu ověří všechny datové položky, pro které jste zadali ověřovacích pravidel.  
  
 Následující obrázek ukazuje výměna dat dialogových oken.  
  
 ![Výměna dat dialogových oken pole](../mfc/media/vc379d1.gif "vc379d1")  
Výměna dat dialogových oken  
  
 `UpdateData` funguje v obou směrech podle specifikace **BOOL** předán parametr. K provedení systému exchange, `UpdateData` nastaví `CDataExchange` objekt a volání vlastní třídy dialogového okna přepsat z `CDialog`na `DoDataExchange` – členská funkce. `DoDataExchange` argument typu trvá `CDataExchange`. `CDataExchange` Byl předán objekt `UpdateData` představuje kontext systému exchange, které definujete takové informace jako směr exchange.  
  
 Při přepsání vy (nebo kód průvodce) `DoDataExchange`, zadejte volání funkce jedné DDX na každého člena dat (řízení). Jednotlivé funkce DDX umí vyměňovat data v obou směrech na základě kontextu poskytl `CDataExchange` argument předaný vaší `DoDataExchange` podle `UpdateData`.  
  
 MFC poskytuje mnoho funkcí DDX pro různé druhy exchange. Následující příklad ukazuje `DoDataExchange` přepsání, ve které dvě DDX se nazývají funkce a jednu funkci DDV:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#49](../mfc/codesnippet/cpp/dialog-data-exchange_1.cpp)]  
  
 `DDX_` a `DDV_` mapování dat jsou řádky. Ukázka DDX a DDV funkce zobrazí jsou pro ovládací prvek zaškrtávací políčko a ovládací prvek textové pole, v uvedeném pořadí.  
  
 Pokud uživatel zruší modální dialogové `OnCancel` – členská funkce ukončí dialogové okno a `DoModal` vrátí hodnotu **IDCANCEL**. V takovém případě žádná data se vyměňují mezi dialogové okno a objektu dialogového okna.  
  
## <a name="see-also"></a>Viz také  
 [Dialogové okno Data výměna a ověřování](../mfc/dialog-data-exchange-and-validation.md)   
 [Životní cyklus dialogového okna](../mfc/life-cycle-of-a-dialog-box.md)   
 [Ověřování dat dialogového okna](../mfc/dialog-data-validation.md)

