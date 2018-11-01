---
title: Definování členských proměnných pro ovládací prvky dialogového okna (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- member variables, defining for controls
- variables, dialog box control member variables
- controls [C++], member variables
- Dialog Editor [C++], defining member variables for controls
ms.assetid: 84347c63-c33c-4b04-91f5-6d008c45ba58
ms.openlocfilehash: 56a7d01d26656c8cf9def3bf09e3ccb18fb436fd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449451"
---
# <a name="defining-member-variables-for-dialog-controls-c"></a>Definování členských proměnných pro ovládací prvky dialogového okna (C++)

Chcete-li definovat členské proměnné pro libovolný ovládací prvek pole dialogové okno s výjimkou tlačítka, můžete použít následující metody.

> [!NOTE]
> Tento článek se týká pouze ovládací prvky dialogového okna v rámci projektu knihovny MFC. Projekty knihovny ATL používejte **nové zprávy Windows a obslužné rutiny událostí** dialogové okno.

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>Chcete-li definovat členské proměnné pro ovládací prvek dialogového okna (jiné tlačítko)

1. V [editoru dialogového okna](../windows/dialog-editor.md), zvolte ovládací prvek.

2. Při stisknutí **Ctrl** klíče, poklepejte na ovládací prvek pole dialogového okna.

   [Přidat členskou proměnnou průvodce](../ide/add-member-variable-wizard.md) se zobrazí.

3. Zadejte příslušné informace **přidat členskou proměnnou** průvodce. Další informace najdete v tématu [výměna dat dialogových oken](../mfc/dialog-data-exchange.md).

4. Klikněte na tlačítko **OK** se vrátíte **dialogové okno** editoru.

   > [!TIP]
   > Pokud chcete přejít ze libovolný ovládací prvek dialogového okna na jeho existující obslužné rutiny, poklepejte na ovládací prvek.

Můžete také použít **členské proměnné** kartu **Průvodce třídami MFC** přidáte nové proměnné členů pro zadanou třídu a zobrazíte ty, které jsou již definovány.

## <a name="requirements"></a>Požadavky

MFC

## <a name="see-also"></a>Viz také

[Mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)<br/>
[Přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Průvodce třídou MFC](../mfc/reference/mfc-class-wizard.md)<br/>
[Přidání třídy](../ide/adding-a-class-visual-cpp.md)<br/>
[Přidání členské funkce](../ide/adding-a-member-function-visual-cpp.md)<br/>
[Přidání členské proměnné](../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Přepisování virtuální funkce](../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Popisovače zpráv knihovny MFC](../mfc/reference/adding-an-mfc-message-handler.md)