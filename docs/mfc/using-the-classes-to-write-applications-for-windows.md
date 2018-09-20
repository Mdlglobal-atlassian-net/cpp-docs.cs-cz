---
title: Použití tříd pro psaní aplikací pro Windows | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows applications [MFC], MFC application framework
- MFC, application development
- applications [OLE], MFC application framework
- MFC ActiveX controls [MFC], creating
- OLE applications [MFC], MFC application framework
- database applications [MFC], creating
ms.assetid: 73f63470-857d-43dd-9a54-b38b7be0f1b7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c60cf5d6f61f16aac18524e8b6e75638ec13d27e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433332"
---
# <a name="using-the-classes-to-write-applications-for-windows"></a>Použití tříd pro psaní aplikací pro Windows

Dohromady třídy do knihovny Microsoft Foundation Class (MFC) tvoří "aplikační architekturu," k vytváření aplikace operačního systému Windows. Na velmi obecné úrovni rozhraní definuje kostra aplikace a poskytuje implementace standardní uživatelské rozhraní, které mohou být umístěny na kostra. Úlohy jako programátor je tak, aby vyplnil ve zbývající části kostra, které jsou tyto věci, které jsou specifické pro vaši aplikaci. Získejte výhodu pomocí Průvodce aplikací knihovny MFC pro vytvoření souborů pro aplikace s velmi důkladné starter. Implementace logiky specifické pro aplikaci pomocí Microsoft Visual C++ editory prostředků pro návrh vašich prvků uživatelského rozhraní vizuálně, zobrazení tříd příkazy pro připojení tyto prvky kódu a knihovny tříd.

Verze 3.0 a novějších rozhraní MFC Framework podporuje programování pro platformy Win32, včetně systému Microsoft Windows 95 a novějším a Windows NT verze 3.51 a vyšší. Podpora knihovny MFC Win32 zahrnuje multithreadingu. Použijte verzi 1.5*x* Pokud musíte udělat programování 16 bitů.

Tato řada článků představuje komplexní přehled aplikační platformu. Také popisuje hlavní objekty, které tvoří vaši aplikaci a jak se vytvářejí. Mezi témata v těchto článcích jsou následující:

- [Rozhraní framework](../mfc/framework-mfc.md).

- Rozdělení práce mezi rozhraní a kódu, jak je popsáno v [sestavení v rámci](../mfc/building-on-the-framework.md).

- [Třída aplikace](../mfc/cwinapp-the-application-class.md), která zapouzdřuje funkce na úrovni aplikace.

- Jak [šablony](../mfc/document-templates-and-the-document-view-creation-process.md) vytvoření a Správa dokumentů a jejich přidružené zobrazení a rámečku systému windows.

- Třída [CWnd](../mfc/window-objects.md), kořenová základní třída všechny systémy windows.

- [Grafické objekty](../mfc/graphic-objects.md), jako je například pera a stopy.

Ostatní části rozhraní framework patří:

- [Objekty oken: Přehled](../mfc/window-objects.md)

- [Zpracování a mapování zpráv](../mfc/message-handling-and-mapping.md)

- [CObject – kořenová základní třída v prostředí MFC](../mfc/using-cobject.md)

- [Document/View – architektura](../mfc/document-view-architecture.md)

- [Dialogová okna](../mfc/dialog-boxes.md)

- [Ovládací prvky](../mfc/controls-mfc.md)

- [Ovládací pruhy](../mfc/control-bars.md)

- [OLE](../mfc/ole-in-mfc.md)

- [Správa paměti](../mfc/memory-management.md)

     Kromě získáte výhody při psaní aplikací pro operační systém Windows, MFC také umožňuje snazší psát aplikace, které se konkrétně používají propojování a vkládání technologie OLE. Dokážete aplikaci prvku OLE vizuálních úprav kontejneru a vizuální úpravy serveru OLE a automatizace můžete přidat tak, aby další aplikace můžete použít objekty z vaší aplikace nebo dokonce jednotku vzdáleně.

- [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

     Sada ovládacího prvku OLE (CDK) je teď plně integrovaná s použitím rozhraní framework. Tato řada článek poskytuje přehled o vývoj ovládacích prvků ActiveX pomocí knihovny MFC. (Ovládací prvky ActiveX dříve označované jako ovládací prvky OLE.)

- [Programování databáze](../data/data-access-programming-mfc-atl.md)

     MFC také poskytuje dvě sady databázové třídy, které zjednodušují psaní přístup k datům aplikace. Použití databázových tříd rozhraní ODBC, můžete připojit se k nim prostřednictvím ovladače rozhraní Open Database Connectivity (ODBC), vyberte záznamy z tabulek a zobrazit informace o záznamu v formuláři na obrazovce. Použití tříd objektů DAO (Data Access), můžete pracovat s databázemi na databázovém stroji Microsoft Jet nebo externích (bez Jet) zdrojů dat, včetně zdroje dat ODBC.

     Kromě toho MFC se plně podporují psaní aplikací, které používají kódování Unicode a vícebajtových znakových sad (MBCS), konkrétně dvoubajtové znakové sady (DBCS).

Obecné pokyny k dokumentace knihovny MFC, naleznete v tématu [obecná témata MFC](../mfc/general-mfc-topics.md).

## <a name="see-also"></a>Viz také

[Obecná témata MFC](../mfc/general-mfc-topics.md)

