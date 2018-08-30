---
title: Použití Windows v prostředí MFC formuláře uživatelského ovládacího prvku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 1/08/2018
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- interoperability [C++], Windows Forms in MFC
- interoperability [C++], MFC
- interop [C++], Windows Forms in MFC
- interop [C++], MFC
- Windows Forms [C++], MFC support
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 795c16a46356eb9599e02b43b51066b603b8b9ce
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222105"
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>Použití uživatelského ovládacího prvku Windows Form v prostředí MFC

Pomocí třídy pro podporu knihovny MFC Windows Forms může hostovat ovládacích prvků Windows Forms v rámci vašich aplikací knihovny MFC jako ovládací prvek ActiveX v dialogových oknech MFC nebo zobrazení. Kromě toho je možné hostovat modelu Windows Forms jako dialogová okna knihovny MFC.

Následující části popisují, jak:

- Hostování ovládacího prvku Windows Forms v dialogovém okně knihovny MFC.

- Hostování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC.

- Hostování formuláře Windows Forms jako dialogového okna knihovny MFC.

> [!NOTE]
> Integrace formulářů Windows MFC funguje jenom v projektech, které dynamicky propojit s knihovnou MFC (projekty, ve kterém `_AFXDLL` je definována).

> [!NOTE]
> Když vytváříte aplikaci pomocí privátního (upravené) kopírování z rozhraní Windows Forms knihovny MFC DLL (mfcmifc80.dll), dojde k instalaci v mezipaměti GAC, není-li nahradit klíč Microsoftu s vlastním klíčem dodavatele. Další informace o podepisování sestavení naleznete v tématu [programování se sestaveními](/dotnet/framework/app-domains/programming-with-assemblies) a [sestavení se silným názvem (podepisování sestavení) (C + +/ CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

Pokud vaše aplikace knihovny MFC používá Windows Forms, musíte redistribuovat mfcmifc80.dll s vaší aplikací. Další informace najdete v tématu [Redistribuce knihovny MFC](../ide/redistributing-the-mfc-library.md).

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

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)

[Uicheckstate –](../mfc/reference/uicheckstate-enumeration.md)

## <a name="related-sections"></a>Související oddíly

[Windows Forms](/dotnet/framework/winforms/index)

[Windows Forms – ovládací prvky](/dotnet/framework/winforms/controls/index)

## <a name="see-also"></a>Viz také:

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)  
[Zobrazení formulářů](../mfc/form-views-mfc.md)  
