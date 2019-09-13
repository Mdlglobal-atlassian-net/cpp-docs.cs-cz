---
title: Použití uživatelského ovládacího prvku Windows Form v prostředí MFC
ms.date: 01/08/2018
helpviewer_keywords:
- MFC [C++], Windows Forms support
- interoperability [C++], Windows Forms in MFC
- interoperability [C++], MFC
- interop [C++], Windows Forms in MFC
- interop [C++], MFC
- Windows Forms [C++], MFC support
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
ms.openlocfilehash: efabbf84778d925ec1de03f5f4ea0ca09185bd81
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926058"
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>Použití uživatelského ovládacího prvku Windows Form v prostředí MFC

Pomocí model Windows Forms třídy podpory knihovny MFC můžete hostovat model Windows Forms ovládací prvky v rámci svých aplikací knihovny MFC jako ovládací prvek ActiveX v dialogových oknech knihovny MFC nebo zobrazeních. Kromě toho mohou být model Windows Forms formuláře hostovány jako dialogová okna knihovny MFC.

Následující části popisují, jak:

- Hostování ovládacího prvku model Windows Forms v dialogovém okně knihovny MFC.

- Hostování uživatelského ovládacího prvku model Windows Forms jako zobrazení MFC.

- Hostování formuláře model Windows Forms jako dialogového okna knihovny MFC.

> [!NOTE]
> Knihovna MFC model Windows Forms Integration funguje pouze v projektech, které jsou propojeny dynamicky s `_AFXDLL` knihovnou MFC (projekty, ve kterých je definována).

> [!NOTE]
> Při sestavování aplikace pomocí soukromé (upravené) kopie knihovny DLL model Windows Forms rozhraní knihovny MFC (mfcmifc80. dll), nebude možné ji nainstalovat do mezipaměti GAC, pokud nenahradíte klíč společnosti Microsoft vlastním klíčem dodavatele. Další informace o podepisování sestavení naleznete v tématu [programování se sestaveními](/dotnet/framework/app-domains/programming-with-assemblies) a [sestavení se silným názvem (podepisováníC++sestavení) (/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

Pokud vaše aplikace MFC používá model Windows Forms, je nutné znovu distribuovat mfcmifc80. dll s vaší aplikací. Další informace naleznete v tématu [Redistribuce knihovny MFC](../windows/redistributing-the-mfc-library.md).

## <a name="in-this-section"></a>V tomto oddílu

[Hostitelské poskytování uživatelského rozhraní Windows Form v dialogovém okně knihovny MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)

[Hostitelské poskytování uživatelského ovládacího prvku Windows Forms jako zobrazení MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)

[Hostitelské poskytování uživatelského ovládacího prvku modelu Windows Form jako dialogového okna knihovny MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)

## <a name="reference"></a>Reference

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

[Prvky uživatelského rozhraní](../mfc/user-interface-elements-mfc.md)<br/>
[Zobrazení formulářů](../mfc/form-views-mfc.md)
