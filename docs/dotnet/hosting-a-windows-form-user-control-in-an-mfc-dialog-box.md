---
title: Hostování Windows Form uživatelského ovládacího prvku v dialogovém okně knihovny MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 291c0856e9d305e0b2b31c6bc233005b111592a9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33129434"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>Hostitelské poskytování uživatelského rozhraní Windows Form v dialogovém okně knihovny MFC
Hostitelem ovládacího prvku Windows Forms jako zvláštní druh ovládacího prvku ActiveX knihovny MFC a komunikuje pomocí ovládacího prvku pomocí vlastnosti a metody třídy a rozhraní ActiveX <xref:System.Windows.Forms.Control> třídy. Doporučujeme používat rozhraní .NET Framework vlastnosti a metody k provozu na ovládací prvek.  
  
 Ukázkové aplikace, která ukazuje použití MFC modelu Windows Forms, najdete v části [integrace produktů Windows Forms a MFC](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
> [!NOTE]
>  V aktuální verzi `CDialogBar` objektu nemůže být hostitelem ovládací prvky Windows Forms.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytvoření uživatelského ovládacího prvku a jeho hostování v dialogovém okně](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)  
  
 [Postupy: vytvoření vazby dat DDX/DDV s modelem Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)  
  
 [Postupy: Zpracování událostí modelu Windows Forms z nativních tříd jazyka C++](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)  
  
## <a name="reference"></a>Odkaz  
 [Třída CWinFormsControl](../mfc/reference/cwinformscontrol-class.md) &#124; [CDialog – třída](../mfc/reference/cdialog-class.md) &#124; [třída CWnd](../mfc/reference/cwnd-class.md)&#124; <xref:System.Windows.Forms.Control>  
  
## <a name="see-also"></a>Viz také  
 [Použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Rozdíly mezi programování prostředími Windows Forms a MFC](../dotnet/windows-forms-mfc-programming-differences.md)   
 [Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)   
 [Hostitelské poskytování uživatelského ovládacího prvku modelu Windows Form jako dialogového okna knihovny MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)