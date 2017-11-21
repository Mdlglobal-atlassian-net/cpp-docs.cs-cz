---
title: "Hostování Windows Forms uživatelský ovládací prvek jako zobrazení MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms controls [C++], hosting as an MFC view
- hosting Windows Forms control [C++]
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4a8ee337c6e647f88fc4ef8730f100681c37a170
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="hosting-a-windows-forms-user-control-as-an-mfc-view"></a>Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC
MFC používá třídu CWinFormsView pro hostování uživatelského ovládacího prvku Windows Forms v MFC zobrazení. Jsou zobrazení MFC Windows Forms – ovládací prvky ActiveX. Uživatelský ovládací prvek je umístěn jako podřízený nativní zobrazení a zabírá celého klienta nativní zobrazení.  
  
 Konečný výsledek se podobá modelu používaný [třídy CFormView](../mfc/reference/cformview-class.md). Díky tomu můžete využívat výhod Návrhář formulářů Windows a runtime a vytvářet bohaté zobrazení založené na formulářích.  
  
 Protože zobrazení MFC Windows Forms – ovládací prvky ActiveX, nemají stejné `hwnd` jako zobrazení MFC. Také je nelze předat jako ukazatel [CView](../mfc/reference/cview-class.md) zobrazení. Obecně platí pomocí metod rozhraní .NET Framework pracovat se zobrazeními Windows Forms a využívá méně Win32.  
  
 Ukázkové aplikace, která ukazuje použití MFC modelu Windows Forms, najdete v části [integrace produktů Windows Forms a MFC](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: vytvoření uživatelského ovládacího prvku a hostitelské poskytování zobrazení MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)  
  
 [Postupy: Přidání příkaz prvku směrování do ovládacího prvku Windows Forms](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)  
  
 [Postupy: řízení vlastnosti volání a metody modelu Windows Forms](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)  
  
## <a name="see-also"></a>Viz také  
 [Použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Postupy: vytváření složených ovládacích prvků](/dotnet/framework/winforms/controls/how-to-author-composite-controls)