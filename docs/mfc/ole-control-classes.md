---
title: OLE – třídy ovládacích prvků
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- custom controls [MFC], classes
- ActiveX controls [MFC], OLE control classes
- ActiveX control classes [MFC]
- OLE controls [MFC], classes
- OLE control classes [MFC]
- reusable component classes [MFC]
ms.assetid: 96495ec3-319e-4163-b839-1af0428ed9dd
ms.openlocfilehash: 47c28520d592c4bd49ab6cb40edbb2f5ddf59846
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447644"
---
# <a name="ole-control-classes"></a>OLE – třídy ovládacích prvků

Jedná se o primární třídy, které používáte při psaní ovládacích prvků OLE. Třída `COleControlModule` v modulu ovládacího prvku OLE je podobná třídě [CWinApp](../mfc/reference/cwinapp-class.md) v aplikaci. Každý modul implementuje jeden nebo více ovládacích prvků OLE; Tyto ovládací prvky jsou reprezentovány `COleControl` objekty. Tyto ovládací prvky komunikují s kontejnery pomocí `CConnectionPoint` objektů.

Třídy `CPictureHolder` a `CFontHolder` zapouzdřují rozhraní COM pro obrázky a písma, zatímco třídy `COlePropertyPage` a `CPropExchange` vám pomůžou implementovat stránky vlastností a trvalost vlastností ovládacího prvku.

[COleControlModule](../mfc/reference/colecontrolmodule-class.md)<br/>
Nahrazuje třídu `CWinApp` pro modul ovládacího prvku OLE. Je odvozena od třídy `COleControlModule` pro vývoj objektu modulu ovládacího prvku OLE. Poskytuje členské funkce pro inicializaci modulu ovládacího prvku OLE.

[COleControl –](../mfc/reference/colecontrol-class.md)<br/>
Je odvozena od třídy `COleControl` pro vývoj ovládacího prvku OLE. Tato třída je odvozena od `CWnd`dědí všechny funkce objektu Window systému Windows a další funkce specifické pro OLE, jako je například vypálení událostí a schopnost podporovat metody a vlastnosti.

[CConnectionPoint](../mfc/reference/cconnectionpoint-class.md)<br/>
Třída `CConnectionPoint` definuje speciální typ rozhraní, které se používá ke komunikaci s jinými objekty OLE, označované jako bod připojení. Bod připojení implementuje odchozí rozhraní, které může iniciovat akce na jiných objektech, jako je například Vyvolávání událostí a oznámení o změně.

[CPictureHolder](../mfc/reference/cpictureholder-class.md)<br/>
Zapouzdřuje funkce objektu s obrázkem Windows a rozhraní `IPicture` COM. slouží k implementaci vlastnosti vlastního obrázku ovládacího prvku OLE.

[CFontHolder](../mfc/reference/cfontholder-class.md)<br/>
Zapouzdřuje funkce objektu písma Windows a rozhraní `IFont` COM. slouží k implementaci vlastnosti burzovního písma ovládacího prvku OLE.

[COlePropertyPage –](../mfc/reference/colepropertypage-class.md)<br/>
Zobrazí vlastnosti ovládacího prvku OLE v grafickém rozhraní, podobně jako v dialogovém okně.

[CPropExchange](../mfc/reference/cpropexchange-class.md)<br/>
Podporuje implementaci trvalosti vlastností pro ovládací prvky OLE. Analogické k [CDataExchange –](../mfc/reference/cdataexchange-class.md) pro dialogová okna.

[CMonikerFile](../mfc/reference/cmonikerfile-class.md)<br/>
Přebírá moniker nebo řetězcové vyjádření, které může vytvořit do monikeru, a váže jej synchronně na datový proud, pro který je moniker název.

[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)<br/>
Funguje podobně jako `CMonikerFile`; Nicméně sváže moniker asynchronně s datovým proudem, pro který je moniker název.

[CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)<br/>
Implementuje vlastnost ovládacího prvku OLE, která může být načtena asynchronně.

[CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md)<br/>
Implementuje vlastnost ovládacího prvku OLE převedenou asynchronně a uloženou v mezipaměti v souboru paměti.

[COleCmdUI](../mfc/reference/colecmdui-class.md)<br/>
Umožňuje aktivnímu dokumentu přijímat příkazy, které pocházejí z uživatelského rozhraní kontejneru (například FileNew, otevřít, vytisknout a tak dále), a umožňuje kontejneru přijímat příkazy, které pocházejí z uživatelského rozhraní aktivního dokumentu.

[COleSafeArray](../mfc/reference/colesafearray-class.md)<br/>
Pracuje s poli libovolného typu a rozměru.

## <a name="see-also"></a>Viz také

[Přehled třídy](../mfc/class-library-overview.md)
