---
title: Hostování Windows Forms uživatelský ovládací prvek jako zobrazení MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms controls [C++], hosting as an MFC view
- hosting Windows Forms control [C++]
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bf9e54b3e2808a232bc13052c885a341cb51297f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="hosting-a-windows-forms-user-control-as-an-mfc-view"></a>Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC
MFC používá třídu CWinFormsView pro hostování uživatelského ovládacího prvku Windows Forms v MFC zobrazení. Jsou zobrazení MFC Windows Forms – ovládací prvky ActiveX. Uživatelský ovládací prvek je umístěn jako podřízený nativní zobrazení a zabírá celého klienta nativní zobrazení.  
  
 Konečný výsledek se podobá modelu používaný [třídy CFormView](../mfc/reference/cformview-class.md). Díky tomu můžete využívat výhod Návrhář formulářů Windows a runtime a vytvářet bohaté zobrazení založené na formulářích.  
  
 Protože zobrazení MFC Windows Forms – ovládací prvky ActiveX, nemají stejné `hwnd` jako zobrazení MFC. Také je nelze předat jako ukazatel [CView](../mfc/reference/cview-class.md) zobrazení. Obecně platí pomocí metod rozhraní .NET Framework pracovat se zobrazeními Windows Forms a využívá méně Win32.  
  
 Ukázkové aplikace, která ukazuje použití MFC modelu Windows Forms, najdete v části [integrace produktů Windows Forms a MFC](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytvoření uživatelského ovládacího prvku a hostitelské poskytování zobrazení MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)  
  
 [Postupy: Přidání směrování příkazů do ovládacího prvku Windows Forms](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)  
  
 [Postupy: Vlastnosti volání a metody ovládacího prvku modelu Windows Forms](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)  
  
## <a name="see-also"></a>Viz také  
 [Použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Postupy: Vytváření složených ovládacích prvků](/dotnet/framework/winforms/controls/how-to-author-composite-controls)