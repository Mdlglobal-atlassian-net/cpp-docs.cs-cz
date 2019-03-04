---
title: Framework (MFC)
ms.date: 11/04/2016
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
ms.openlocfilehash: 933fcf97c24ed0903395e2c718f8c89d42473494
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269016"
---
# <a name="framework-mfc"></a>Framework (MFC)

Práce s použitím rozhraní framework knihovny Microsoft Foundation Class (MFC) je do značné míry na základě několik hlavních třídách a několik nástrojů pro Visual C++. Některé třídy zapouzdření velkou část rozhraní (API) systému Win32. Jiné třídy zapouzdření aplikace konceptů, jako jsou dokumenty, zobrazení a vlastní aplikace. Stále ostatní zapouzdření OLE funkce, ODBC a DAO přístup k datům.

Například na Win32 konceptu okna jsou zapouzdřena objektem třídy knihovny MFC `CWnd`. To znamená, že třída C++ nazývá `CWnd` zapouzdřuje nebo "zabalí" `HWND` popisovač, který představuje okno Windows. Obdobně třídy `CDialog` zapouzdřuje Win32 dialogových oknech.

Zapouzdření znamená, že třídy C++ `CWnd`, například obsahuje členskou proměnnou typu `HWND`, a členské funkce třídy zapouzdření volání Win32 funkcí, které přijímají `HWND` jako parametr. Členské funkce tříd mají obvykle stejný název jako funkce Win32, které zapouzdřují.

## <a name="in-this-section"></a>V tomto oddílu

[Rozhraní SDI a knihovna MDI](../mfc/sdi-and-mdi.md)

[Dokumenty, zobrazení a framework](../mfc/documents-views-and-the-framework.md)

[Průvodci a editory prostředků](../mfc/wizards-and-the-resource-editors.md)

## <a name="in-related-sections"></a>V související oddíly

[Sestavení na základě rozhraní .NET Framework](../mfc/building-on-the-framework.md)

[Jakým způsobem volá framework váš kód](../mfc/how-the-framework-calls-your-code.md)

[CWinApp Třída aplikace](../mfc/cwinapp-the-application-class.md)

[Šablony dokumentů a proces vytváření dokumentů/zobrazení](../mfc/document-templates-and-the-document-view-creation-process.md)

[Zpracování a mapování zpráv](../mfc/message-handling-and-mapping.md)

[Objekty oken](../mfc/window-objects.md)

## <a name="see-also"></a>Viz také:

[Použití tříd pro psaní aplikací pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
