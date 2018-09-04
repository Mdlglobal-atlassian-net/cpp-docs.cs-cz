---
title: Přidání třídy knihovny MFC z knihovny typů | Dokumentace Microsoftu
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
ms.openlocfilehash: c79409ae6e4c7447050c26246768c0074c4e4e92
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43677192"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>Přidání třídy knihovny MFC z knihovny typů
Tohoto průvodce použijte k vytvoření třídy knihovny MFC z rozhraní dostupné knihovny typů. Můžete přidat do třídy knihovny MFC [aplikace knihovny MFC](../../mfc/reference/creating-an-mfc-application.md), [knihovny MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md), nebo [ovládací prvek ActiveX knihovny MFC](../../mfc/reference/creating-an-mfc-activex-control.md).  
  
> [!NOTE]
>  Není nutné k vytvoření projektu knihovny MFC s podporou pro přidání třídy z knihovny typů automatizace.  
  
 Knihovna typů obsahuje binární popis rozhraní vystavené komponentou, definování metody společně s jejich parametry a návratové typy. Knihovna typů musí být zaregistrovaný, aby se zobrazí v **dostupné knihovny typů** seznamu v přidání třídy z Průvodce knihovnou typů. Viz "Uvnitř Distributed COM: typ a jazyk integrace knihoven" v knihovně MSDN pro další informace.  
  
### <a name="to-add-an-mfc-class-from-a-type-library"></a>Přidání třídy knihovny MFC z knihovny typů  
  
1.  V jednom **Průzkumníka řešení** nebo [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code), klikněte pravým tlačítkem na název projektu, ke kterému chcete přidat třídu.  
  
2.  V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **přidat třídu**.  
  
3.  V [přidat třídu](../../ide/add-class-dialog-box.md) dialogové okno, v podokně šablon, klikněte na tlačítko **třída knihovny MFC z Typelib**a potom klikněte na tlačítko **otevřít** zobrazíte [přidat třídu z Průvodce knihovnou typů ](../../mfc/reference/add-class-from-typelib-wizard.md).  
  
 V průvodci můžete přidat více než jedna třída v knihovně typů. Podobně přidáním tříd z více než jeden typ knihovny v rámci jedné relace průvodce.  
  
 Průvodce vytvoří třídy knihovny MFC, odvozený z [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md), pro každé rozhraní, kterou přidáte z vybrané knihovny typů. `COleDispatchDriver` implementuje na straně klienta automatizaci OLE.  
  
## <a name="see-also"></a>Viz také  
 [Klienti automatizace](../../mfc/automation-clients.md)   
 [Klienti automatizace: Použití knihoven typů](../../mfc/automation-clients-using-type-libraries.md)

