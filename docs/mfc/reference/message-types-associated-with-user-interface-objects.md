---
title: Typy přidružených k objektům uživatelského rozhraní zpráv | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.uiobject.msgs
dev_langs:
- C++
helpviewer_keywords:
- message types and user interface objects [MFC]
ms.assetid: 681ee1a7-f6e6-4ea0-9fc6-1fb53a35516e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd89f19547eef8ade9d23a6176ea74cb49586857
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860287"
---
# <a name="message-types-associated-with-user-interface-objects"></a>Typy zpráv přidružených k objektům uživatelského rozhraní

V následující tabulce jsou uvedeny typy objektů, se kterými pracujete a typy zpráv přidružených k jejich.

### <a name="user-interface-objects-and-associated-messages"></a>Objekty uživatelského rozhraní a přidružených zpráv

|ID objektu|Zprávy|
|---------------|--------------|
|Název třídy, představující obsahujícího okna|Zprávy Windows [CWnd](../../mfc/reference/cwnd-class.md)-odvozené třídy: dialogové okno, okna, podřízené okno, podřízené okno MDI nebo nejvyššího rámce okna.|
|Identifikátor nabídky nebo akcelerátoru|– Zpráva příkaz (spustí program funkce).<br />-UPDATE_COMMAND_UI zpráva (dynamicky aktualizuje položku nabídky).|
|Identifikátor ovládacího prvku|Zpráv s oznámením ovládacího prvku pro vybraný typ ovládacího prvku.|

## <a name="see-also"></a>Viz také

[Mapování zpráv na funkce](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Přidání členské funkce](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Přidání členské proměnné](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Přepisování virtuální funkce](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Popisovače zpráv knihovny MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navigace strukturou třídy](../../ide/navigating-the-class-structure-visual-cpp.md)
