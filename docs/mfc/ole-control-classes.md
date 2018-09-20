---
title: OLE – třídy ovládacích prvků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.ole
dev_langs:
- C++
helpviewer_keywords:
- ActiveX classes [MFC]
- custom controls [MFC], classes
- ActiveX controls [MFC], OLE control classes
- ActiveX control classes [MFC]
- OLE controls [MFC], classes
- OLE control classes [MFC]
- reusable component classes [MFC]
ms.assetid: 96495ec3-319e-4163-b839-1af0428ed9dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ad9ab489506964266b28a38563c366db2b0d54fa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439078"
---
# <a name="ole-control-classes"></a>OLE – třídy ovládacích prvků

Jedná se o primární třídy, které chcete použít při vytváření ovládacích prvků OLE. `COleControlModule` Třída v modulu OLE ovládací prvek je třeba [CWinApp](../mfc/reference/cwinapp-class.md) třídu v aplikaci. Každý modul implementuje jednu nebo více ovládacích prvků OLE; Tyto ovládací prvky jsou reprezentovány `COleControl` objekty. Tyto ovládací prvky komunikovat s jejich kontejnery pomocí `CConnectionPoint` objekty.

`CPictureHolder` a `CFontHolder` zapouzdřují rozhraní modelu COM pro obrázky a písma, zatímco `COlePropertyPage` a `CPropExchange` třídy vám pomůže implementovat stránky vlastností a vlastností persistence pro ovládací prvek.

[COleControlModule](../mfc/reference/colecontrolmodule-class.md)<br/>
Nahrazuje `CWinApp` třída pro ovládací prvek modulu OLE. Odvozovat `COleControlModule` třídy pro vývoj objektu OLE ovládacího modulu. Inicializace modulu OLE ovládacího prvku poskytuje členské funkce.

[COleControl –](../mfc/reference/colecontrol-class.md)<br/>
Odvozovat `COleControl` třídy pro vývoj ovládacího prvku OLE. Odvozené od `CWnd`, této třídy dědí všechny funkce objekt okna Windows a další funkce specifické pro OLE, jako je například spouštění událostí a možnosti pro podporu metod a vlastností.

[Cconnectionpoint –](../mfc/reference/cconnectionpoint-class.md)<br/>
`CConnectionPoint` Třída definuje speciální typ rozhraní, které slouží ke komunikaci s dalšími objekty OLE, volá se bod připojení. Spojovací bod implementuje odchozí rozhraní, které je možné spustit na jiných objektech, jako je například vyvolává události akcí a upozornění na změnu.

[Cpictureholder –](../mfc/reference/cpictureholder-class.md)<br/>
Zapouzdřuje funkce objektu obrázek Windows a `IPicture` COM rozhraní; používaný k implementaci vlastní vlastnost obrázek ovládacího prvku OLE.

[Cfontholder –](../mfc/reference/cfontholder-class.md)<br/>
Zapouzdřuje funkce objektu písma Windows a `IFont` COM rozhraní; používaný k implementaci ovládacího prvku OLE vlastnost běžného písma.

[COlePropertyPage –](../mfc/reference/colepropertypage-class.md)<br/>
Zobrazí vlastnosti OLE řízení v grafickém rozhraní, podobnému dialogovému oknu.

[Cpropexchange –](../mfc/reference/cpropexchange-class.md)<br/>
Podporuje implementaci persistence vlastnost pro ovládací prvky OLE. Obdobná [cdataexchange –](../mfc/reference/cdataexchange-class.md) pro dialogová okna.

[Cmonikerfile –](../mfc/reference/cmonikerfile-class.md)<br/>
Moniker nebo reprezentaci řetězce, který může odesílat do monikeru a sváže synchronně do datového proudu, pro kterou je moniker je název.

[Casyncmonikerfile –](../mfc/reference/casyncmonikerfile-class.md)<br/>
Pracuje podobně jako `CMonikerFile`, nicméně naváže monikeru asynchronně do datového proudu, pro kterou je moniker je název.

[Cdatapathproperty –](../mfc/reference/cdatapathproperty-class.md)<br/>
Implementuje ovládacího prvku OLE vlastnost, která lze načíst asynchronně.

[Ccacheddatapathproperty –](../mfc/reference/ccacheddatapathproperty-class.md)<br/>
Implementuje ovládacího prvku OLE asynchronně převedený a uložili do mezipaměti v paměti souboru vlastnost.

[Colecmdui –](../mfc/reference/colecmdui-class.md)<br/>
Umožňuje aktivní dokument přijímají příkazy, které pocházejí z příslušného kontejneru uživatelského rozhraní (například funkci FileNew, otevřít, tisk a tak dále) a kontejner pro příjem příkazy, které pocházejí z aktivního dokumentu uživatelského rozhraní.

[Colesafearray –](../mfc/reference/colesafearray-class.md)<br/>
Spolupracuje s poli libovolného typu a rozměru.

## <a name="see-also"></a>Viz také

[Přehled tříd](../mfc/class-library-overview.md)

