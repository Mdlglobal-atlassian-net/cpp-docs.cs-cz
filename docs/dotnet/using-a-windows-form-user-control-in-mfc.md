---
title: "Uživatelský ovládací prvek pomocí Windows Form v prostředí MFC | Microsoft Docs"
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
- interoperability [C++], Windows Forms in MFC
- interoperability [C++], MFC
- interop [C++], Windows Forms in MFC
- interop [C++], MFC
- Windows Forms [C++], MFC support
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 59b4d974a6b25b896067bce0042d9a5ff9221cc2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>Použití uživatelského ovládacího prvku Windows Form v prostředí MFC
Použití tříd MFC Windows Forms podpory, můžete hostovat ovládací prvky Windows Forms v aplikacích MFC jako ovládací prvek ActiveX v dialogových oknech MFC nebo zobrazení. Kromě toho může být hostovaný modelu Windows Forms jako dialogových oken MFC.  
  
 Následující části popisují postup:  
  
-   Hostování ovládacího prvku Windows Forms v dialogovém okně knihovny MFC.  
  
-   Hostování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC.  
  
-   Hostitel Windows Forms formuláře jako dialogového okna knihovny MFC.  
  
> [!NOTE]
>  MFC Windows Forms integrace funguje jenom v projektech, které jsou dynamicky propojené s knihovnou MFC (projekty, ve kterých je definován AFXDLL).  
  
> [!NOTE]
>  Když vytvoříte aplikaci pomocí privátního (upravené) kopie rozhraní MFC Windows Forms DLL (mfcmifc80.dll), se nezdaří instalace v mezipaměti GAC, pokud je klíč Microsoft nahradit klíč dodavatele. Další informace o podepisování sestavení najdete v tématu [programování se sestaveními](/dotnet/framework/app-domains/programming-with-assemblies) a [sestavení se silným názvem (podepisování sestavení) (C + +/ CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).  
  
 Ukázkové aplikace pomocí Windows Forms, najdete v části [BirthdayPicker Sample: ukazuje rozhraní .NET Framework prostředky s Windows Forms](http://msdn.microsoft.com/en-us/ac932aed-5502-4667-be29-709bca435317), [ukázka kalkulačku: Windows Forms Pocket Calculator](http://msdn.microsoft.com/en-us/2283b516-3b7e-45f2-80c4-fdcfb366ce25)a [ Ukázka Scribble: MDI kreslení aplikace](http://msdn.microsoft.com/en-us/f025da3e-659b-4222-b991-554a1b8b2358).  
  
 Ukázkové aplikace, která ukazuje použití MFC modelu Windows Forms, najdete v části [integrace produktů Windows Forms a MFC](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
 Pokud vaše aplikace MFC používá Windows Forms, budete muset znovu distribuovat mfcmifc90.dll s vaší aplikací. Další informace najdete v tématu [Redistribuce knihovny MFC](../ide/redistributing-the-mfc-library.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Hostitelské poskytování uživatelského rozhraní Windows Form v dialogovém okně knihovny MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)  
  
 [Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)  
  
 [Hostitelské poskytování uživatelského ovládacího prvku modelu Windows Form jako dialogového okna knihovny MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)  
  
## <a name="reference"></a>Odkaz  
 [CWinFormsControl – třída](../mfc/reference/cwinformscontrol-class.md)  
  
 [CWinFormsDialog – třída](../mfc/reference/cwinformsdialog-class.md)  
  
 [CWinFormsView – třída](../mfc/reference/cwinformsview-class.md)  
  
 [ICommandSource – rozhraní](../mfc/reference/icommandsource-interface.md)  
  
 [ICommandTarget – rozhraní](../mfc/reference/icommandtarget-interface.md)  
  
 [ICommandUI – rozhraní](../mfc/reference/icommandui-interface.md)  
  
 [IView – rozhraní](../mfc/reference/iview-interface.md)  
  
 [CommandHandler](../atl/commandhandler.md)  
  
 [DDX_ManagedControl –](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)  
  
 [UICheckState](../mfc/reference/uicheckstate-enumeration.md)  
  
## <a name="related-sections"></a>Související oddíly  
 [Windows Forms](/dotnet/framework/winforms/index)  
  
 [Windows Forms – ovládací prvky](/dotnet/framework/winforms/controls/index)  
  
## <a name="see-also"></a>Viz také  
 [Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)   
 [Zobrazení formulářů](../mfc/form-views-mfc.md)