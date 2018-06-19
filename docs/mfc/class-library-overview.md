---
title: Přehled knihovny tříd | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- grouping MFC classes
- MFC, class library
- classes [MFC], MFC
- class libraries, MFC
- class libraries
ms.assetid: 9b0e3152-ac39-4f52-91b4-f20aa3a674aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f144ce4dd6ed9cd29adca27aaff51a79af0abec1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346897"
---
# <a name="class-library-overview"></a>Přehled knihovny tříd
Tento přehled rozděluje a popisuje třídy v Microsoft Foundation Class Library (MFC) verze 9.0. Třídy v MFC, dohromady, představují aplikační – Architektura aplikace napsané pro rozhraní API systému Windows. Programovací úkolu je vyplnit kód, který je specifický pro vaši aplikaci.  
  
 Knihovny tříd jsou zde uvedeny v následujících kategorií:  
  
-   [Kořenová třída: CObject](../mfc/root-class-cobject.md)  
  
-   [Třídy architektury aplikace MFC](../mfc/mfc-application-architecture-classes.md)  
  
    -   [Třídy pro podporu aplikací a vláken](../mfc/application-and-thread-support-classes.md)  
  
    -   [Třídy směrování příkazů](../mfc/command-routing-classes.md)  
  
    -   [Třídy dokumentů](../mfc/document-classes.md)  
  
    -   [Třídy zobrazení (architektura)](../mfc/view-classes-architecture.md)  
  
    -   [Třídy oken s rámečkem (architektura)](../mfc/frame-window-classes-architecture.md)  
  
    -   [Třídy šablony dokumentu](../mfc/document-template-classes.md)  
  
-   [Třídy oken, dialogových oken a ovládacích prvků](../mfc/window-dialog-and-control-classes.md)  
  
    -   [Třídy oken s rámečkem (Windows)](../mfc/frame-window-classes-windows.md)  
  
    -   [Třídy zobrazení (Windows)](../mfc/view-classes-windows.md)  
  
    -   [Třídy dialogových oken](../mfc/dialog-box-classes.md)  
  
    -   [Třídy ovládacích prvků](../mfc/control-classes.md)  
  
    -   [Třídy ovládacích pruhů](../mfc/control-bar-classes.md)  
  
-   [Třídy pro vykreslování a tisk](../mfc/drawing-and-printing-classes.md)  
  
    -   [Výstupní třídy (třídy kontextu zařízení)](../mfc/output-device-context-classes.md)  
  
    -   [Třídy nástrojů pro kreslení](../mfc/drawing-tool-classes.md)  
  
-   [Třídy jednoduchého datového typu](../mfc/simple-data-type-classes.md)  
  
-   [Třídy pole, seznamu a mapy](../mfc/array-list-and-map-classes.md)  
  
    -   [Třídy šablon pro pole, seznamy a mapy](../mfc/template-classes-for-arrays-lists-and-maps.md)  
  
    -   [Hotové třídy polí připravené k použití](../mfc/ready-to-use-array-classes.md)  
  
    -   [Hotové třídy seznamů připravené k použití](../mfc/ready-to-use-list-classes.md)  
  
    -   [Hotové třídy map připravené k použití](../mfc/ready-to-use-map-classes.md)  
  
-   [Souborové a databázové třídy](../mfc/file-and-database-classes.md)  
  
    -   [Třídy I/O souborů](../mfc/file-i-o-classes.md)  
  
    -   [DAO – třídy](../mfc/dao-classes.md)  
  
    -   [ODBC – třídy](../mfc/odbc-classes.md)  
  
    -   [OLE DB – třídy](../mfc/ole-db-classes.md)  
  
-   [Internetové a síťové třídy](../mfc/internet-and-networking-classes.md)  
  
    -   [Windows Sockets – třídy](../mfc/windows-sockets-classes.md)  
  
    -   [Win32 – internetové třídy](../mfc/win32-internet-classes.md)  
  
-   [OLE – třídy](../mfc/ole-classes.md)  
  
    -   [OLE – třídy kontejnerů](../mfc/ole-container-classes.md)  
  
    -   [OLE – třídy serveru](../mfc/ole-server-classes.md)  
  
    -   [Přetahování v rozhraní OLE a třídy přenosu dat](../mfc/ole-drag-and-drop-and-data-transfer-classes.md)  
  
    -   [OLE – třídy společných dialogů](../mfc/ole-common-dialog-classes.md)  
  
    -   [OLE – třídy automatizace](../mfc/ole-automation-classes.md)  
  
    -   [OLE – třídy ovládacích prvků](../mfc/ole-control-classes.md)  
  
    -   [Třídy aktivních dokumentů](../mfc/active-document-classes.md)  
  
    -   [Třídy související s rozhraním OLE](../mfc/ole-related-classes.md)  
  
-   [Třídy ladění a výjimek](../mfc/debugging-and-exception-classes.md)  
  
    -   [Třídy podpory ladění](../mfc/debugging-support-classes.md)  
  
    -   [Třídy výjimek](../mfc/exception-classes.md)  
  
 V části [obecná filosofie návrhu tříd](../mfc/general-class-design-philosophy.md) vysvětluje, jak byl navržen knihovny MFC.  
  
 Přehled architektury, najdete v tématu [použití tříd pro zápis aplikace pro Windows](../mfc/using-the-classes-to-write-applications-for-windows.md). Některé z kategorií uvedených výše jsou pro obecné účely tříd, které můžete použít mimo rozhraní a poskytují užitečné abstrakce, jako jsou kolekce, výjimky, soubory a řetězce.  
  
 Pokud chcete zobrazit dědičnost třídy, použijte [graf hierarchie třídy](../mfc/hierarchy-chart.md).  
  
 Kromě tříd uvedených v tomto přehledu knihovny MFC obsahuje řadu makra, globální funkce a globální proměnné. Je přehled a podrobný výpis z nich v tématu [MFC – makra a globální prvky](../mfc/reference/mfc-macros-and-globals.md), který následuje abecedně řazená referenční dokumentace pro třídy MFC.  
  
## <a name="see-also"></a>Viz také  
 [Desktopové aplikace knihovny MFC](../mfc/mfc-desktop-applications.md)

