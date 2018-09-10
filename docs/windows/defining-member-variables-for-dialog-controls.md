---
title: Definování členských proměnných pro ovládací prvky dialogového okna (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- member variables, defining for controls
- variables, dialog box control member variables
- controls [C++], member variables
- Dialog Editor [C++], defining member variables for controls
ms.assetid: 84347c63-c33c-4b04-91f5-6d008c45ba58
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e6734391e56f076f247bd8887a7fdb61142b3669
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317859"
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

[Mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md)  
[Přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md)  
[Průvodce třídou MFC](../mfc/reference/mfc-class-wizard.md)  
[Přidání třídy](../ide/adding-a-class-visual-cpp.md)  
[Přidání členské funkce](../ide/adding-a-member-function-visual-cpp.md)  
[Přidání členské proměnné](../ide/adding-a-member-variable-visual-cpp.md)  
[Přepisování virtuální funkce](../ide/overriding-a-virtual-function-visual-cpp.md)  
[Popisovače zpráv knihovny MFC](../mfc/reference/adding-an-mfc-message-handler.md)