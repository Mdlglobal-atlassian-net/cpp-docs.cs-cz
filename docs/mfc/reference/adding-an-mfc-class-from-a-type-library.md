---
title: "Přidání třídy knihovny MFC z knihovny typů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1efc61e097d7e1136fdb7b6ef740dc00342077e4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>Přidání třídy knihovny MFC z knihovny typů
Pomocí tohoto průvodce k vytvoření třídy knihovny MFC z rozhraní dostupných knihoven typů. Můžete přidat do třídy knihovny MFC [aplikace knihovny MFC](../../mfc/reference/creating-an-mfc-application.md), [MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md), nebo [ovládacího prvku ActiveX knihovny MFC](../../mfc/reference/creating-an-mfc-activex-control.md).  
  
> [!NOTE]
>  Není nutné k vytvoření projektu knihovny MFC s podporou pro přidání třídy z knihovny typů automatizace.  
  
 Knihovny typů obsahuje binární popis rozhraní vystavených komponentou, definování metody spolu s jejich parametry a návratové typy. Knihovna typů musí být registrována pro zobrazí v **dostupné knihovny typů** v přidat třídu z Průvodce Typelib v seznamu. Najdete v části "Uvnitř Distributed COM: typ knihovny a jazyk integrace" v knihovně MSDN Další informace.  
  
### <a name="to-add-an-mfc-class-from-a-type-library"></a>Přidání třídy knihovny MFC z knihovny typů  
  
1.  Buď **Průzkumníku řešení** nebo [zobrazení tříd](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), klikněte pravým tlačítkem na název projektu, do které chcete přidat třídu.  
  
2.  V místní nabídce klikněte na **přidat**a potom klikněte na **přidat třídu**.  
  
3.  V [přidat třídu](../../ide/add-class-dialog-box.md) kliknutím na dialogové okno, v podokně šablon **třída knihovny MFC z knihovny Typelib**a potom klikněte na **otevřete** zobrazíte [přidat třídu z Průvodce Typelib ](../../mfc/reference/add-class-from-typelib-wizard.md).  
  
 V průvodci můžete přidat více než jednu třídu v knihovny typů. Podobně můžete přidat třídy z více než jeden knihovny typů v rámci jedné relace průvodce.  
  
 Průvodce vytvoří třídy knihovny MFC odvozené od [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md), u každého rozhraní přidáte z knihovny vybraného typu. `COleDispatchDriver`implementuje OLE – automatizace na straně klienta.  
  
## <a name="see-also"></a>Viz také  
 [Klienti automatizace](../../mfc/automation-clients.md)   
 [Klienti automatizace: Použití knihoven typů](../../mfc/automation-clients-using-type-libraries.md)

