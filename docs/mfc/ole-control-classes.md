---
title: OLE – třídy ovládacích prvků | Microsoft Docs
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
ms.openlocfilehash: 5dcbda85c33bab37babe5da861067d25cf31e32c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355350"
---
# <a name="ole-control-classes"></a>OLE – třídy ovládacích prvků
Toto jsou primární třídy, které chcete použít při zápisu ovládací prvky OLE. `COleControlModule` Třídy v modul OLE řízení je třeba [CWinApp](../mfc/reference/cwinapp-class.md) třídy v aplikaci. Každý modul implementuje jeden nebo více ovládacích prvků OLE; Tyto ovládací prvky jsou reprezentované pomocí `COleControl` objekty. Tyto ovládací prvky komunikovat s jejich kontejnery pomocí `CConnectionPoint` objekty.  
  
 `CPictureHolder` a `CFontHolder` třídy zapouzdření rozhraní COM pro obrázky a písem a při `COlePropertyPage` a `CPropExchange` třídy vám pomůže implementovat stránky vlastností a vlastnost trvalosti pro ovládací prvek.  
  
 [COleControlModule](../mfc/reference/colecontrolmodule-class.md)  
 Nahradí `CWinApp` třída pro ovládací prvek modul OLE. Odvozena od `COleControlModule` třídy pro vývoj objekt OLE řízení modulu. Členské funkce poskytuje pro inicializaci modulu OLE ovládacího prvku.  
  
 [COleControl](../mfc/reference/colecontrol-class.md)  
 Odvozena od `COleControl` třídy pro vývoj ovládacího prvku OLE. Odvozené z `CWnd`, této třídy dědí všechny funkce objektem okna v systému Windows a další funkce specifické pro OLE, například spouštění událostí a možnost podpory metod a vlastností.  
  
 [CConnectionPoint](../mfc/reference/cconnectionpoint-class.md)  
 `CConnectionPoint` Třída definuje speciální typ rozhraní používaný ke komunikaci s jinými objekty OLE, označovaný jako bod připojení. Bod připojení implementuje odchozí rozhraní, které je možné zahájit akce na jiné objekty, například na aktivaci události a upozornění na změnu.  
  
 [CPictureHolder](../mfc/reference/cpictureholder-class.md)  
 Zapouzdřuje funkce objekt obrázku Windows a `IPicture` COM rozhraní; použít k implementaci vlastnost vlastní obrázek ovládacího prvku OLE.  
  
 [CFontHolder](../mfc/reference/cfontholder-class.md)  
 Zapouzdřuje funkce Windows objektu písma a `IFont` COM rozhraní; použít k implementaci uložených vlastností písma ovládacího prvku OLE.  
  
 [COlePropertyPage](../mfc/reference/colepropertypage-class.md)  
 Zobrazí vlastnosti OLE řízení v grafickém rozhraní, podobně jako dialogové okno.  
  
 [CPropExchange](../mfc/reference/cpropexchange-class.md)  
 Podporuje provádění vlastnost trvalosti pro vaše ovládací prvky OLE. Podobá se [CDataExchange](../mfc/reference/cdataexchange-class.md) pro dialogová okna.  
  
 [CMonikerFile](../mfc/reference/cmonikerfile-class.md)  
 Trvá přezdívka nebo reprezentaci řetězce, který může odeslat do přezdívka a sváže synchronně do datového proudu, pro kterou je přezdívka název.  
  
 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)  
 Podobně jako funguje `CMonikerFile`, nicméně se váže přezdívka, asynchronně do datového proudu, pro kterou je přezdívka název.  
  
 [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)  
 Implementuje OLE řídit vlastnost, která mohou být načteny asynchronně.  
  
 [CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md)  
 Vlastnost asynchronně přenáší a uložené v mezipaměti v paměti soubor ovládacího prvku implementuje OLE.  
  
 [COleCmdUI](../mfc/reference/colecmdui-class.md)  
 Umožňuje aktivní dokument přijímají příkazy, které pocházejí z jeho kontejneru uživatelské rozhraní (například funkci FileNew, otevřete, tisku a tak dále) a umožňuje kontejner pro příjem příkazů, které pocházejí z aktivní dokument uživatelské rozhraní.  
  
 [COleSafeArray](../mfc/reference/colesafearray-class.md)  
 Funguje s poli libovolného typu a dimenze.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)

