---
title: Přidání třídy knihovny MFC z knihovny typů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 349d06d7fecb82af64fbf2d3b2ebe54689b3b292
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
  
 Průvodce vytvoří třídy knihovny MFC odvozené od [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md), u každého rozhraní přidáte z knihovny vybraného typu. `COleDispatchDriver` Implementuje OLE – automatizace na straně klienta.  
  
## <a name="see-also"></a>Viz také  
 [Klienti automatizace](../../mfc/automation-clients.md)   
 [Klienti automatizace: Použití knihoven typů](../../mfc/automation-clients-using-type-libraries.md)

