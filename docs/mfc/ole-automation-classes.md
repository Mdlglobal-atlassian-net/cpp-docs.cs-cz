---
title: OLE – třídy automatizace
ms.date: 11/04/2016
helpviewer_keywords:
- Automation, classes
- Automation classes [MFC], OLE classes
- OLE Automation [MFC], classes
- Automation classes [MFC]
- OLE Automation [MFC]
ms.assetid: 96e5372b-ff8a-4da1-933b-4d9bbf4dceb3
ms.openlocfilehash: 644a4930eb55636ba6e87b949ed610b725334661
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447680"
---
# <a name="ole-automation-classes"></a>OLE – třídy automatizace

Tyto třídy podporují klienty automatizace (aplikace, které ovládají jiné aplikace). Automatizační servery (aplikace, které je možné ovládat jinými aplikacemi), jsou podporované prostřednictvím [map pro odesílání](../mfc/reference/dispatch-maps.md).

[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)<br/>
Slouží k volání automatizačních serverů z vašeho klienta automatizace. Při přidávání třídy se tato třída používá k vytvoření typově bezpečných tříd pro automatizační servery, které poskytují knihovnu typů.

[COleDispatchException](../mfc/reference/coledispatchexception-class.md)<br/>
Výjimka vyplývající z chyby při automatizaci OLE. Automatizační servery vyvolají výjimky služby Automation a zachycují je prostřednictvím klientů automatizace.

## <a name="see-also"></a>Viz také

[Přehled třídy](../mfc/class-library-overview.md)
