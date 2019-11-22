---
title: Framework (MFC)
ms.date: 09/17/2019
helpviewer_keywords:
- encapsulation [MFC], Win32 API
- MFC, application framework
- wrapper classes [MFC], explained
- Win32 [MFC], API encapsulation by MFC
- application framework [MFC], about MFC application framework
- APIs [MFC], encapsulation by MFC Win32
- encapsulation [MFC]
- Windows API [MFC], encapsulation by MFC
- encapsulated Win32 API [MFC]
ms.assetid: 3be0fec8-9843-4119-ae42-ece993ef500b
ms.openlocfilehash: 387f53e3123b6863fcf218da39c7c5e356eb8219
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303409"
---
# <a name="framework-mfc"></a>Framework (MFC)

Vaše práce s rozhraním knihovny MFC (Microsoft Foundation Class) je převážně založena na několika hlavních třídách a několika vizuálních C++ nástrojích. Některé třídy zapouzdřují velkou část rozhraní API (Application Programming Interface) Win32. Jiné třídy zapouzdřují koncepty aplikace, jako jsou dokumenty, zobrazení a aplikace samotné. I ostatní zapouzdřují funkce OLE a funkce pro přístup k datům rozhraní ODBC a rozhraní DAO.  (Rozhraní DAO je podporováno prostřednictvím sady Office 2013. Rozhraní DAO 3,6 je finální verze a je považována za zastaralou.)

Například Win32's koncept okna je zapouzdřeno třídou MFC `CWnd`. To znamená, že C++ třída s názvem `CWnd` zapouzdřuje nebo "zabalí" `HWND` popisovač, který představuje okno systému Windows. Stejně tak `CDialog` třídy zapouzdřují dialogová okna Win32.

Zapouzdření znamená, že C++ třída `CWnd`například obsahuje členskou proměnnou typu `HWND`a členské funkce třídy zapouzdřují volání funkcí Win32, které přebírají `HWND` jako parametr. Členské funkce třídy obvykle mají stejný název jako funkce Win32, které zapouzdřují.

## <a name="in-this-section"></a>V tomto oddílu

[Rozhraní SDI a knihovna MDI](../mfc/sdi-and-mdi.md)

[Dokumenty, zobrazení a framework](../mfc/documents-views-and-the-framework.md)

[Průvodci a editory prostředků](../mfc/wizards-and-the-resource-editors.md)

## <a name="in-related-sections"></a>V souvisejících oddílech

[Sestavení na základě rozhraní .NET Framework](../mfc/building-on-the-framework.md)

[Jakým způsobem volá framework váš kód](../mfc/how-the-framework-calls-your-code.md)

[CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)

[Šablony dokumentů a proces vytváření dokumentů/zobrazení](../mfc/document-templates-and-the-document-view-creation-process.md)

[Zpracování a mapování zpráv](../mfc/message-handling-and-mapping.md)

[Objekty oken](../mfc/window-objects.md)

## <a name="see-also"></a>Viz také:

[Použití tříd pro psaní aplikací pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
