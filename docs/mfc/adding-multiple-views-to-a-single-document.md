---
title: "Přidání více zobrazení do jednoho dokumentu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 865b30ac7b4c8910e92d14274f1224c25e7f74d8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="adding-multiple-views-to-a-single-document"></a>Přidání více zobrazení do jednoho dokumentu
V aplikaci (SDI) rozhraní s jedním dokumentem vytvořené pomocí knihovny Microsoft Foundation Class (MFC) každý typ dokumentu je přidružený k typu jednoho zobrazení. V některých případech je třeba mít možnost přepnout aktuální zobrazení objektu na dokument s nové zobrazení.  
  
> [!TIP]
>  Další postupy k implementaci více zobrazení pro jednotlivý dokument najdete v tématu [CDocument::AddView](../mfc/reference/cdocument-class.md#addview) a [SHROMAŽĎOVAT](../visual-cpp-samples.md) MFC ukázka.  
  
 Tuto funkci můžete implementovat přidáním nové `CView`-odvozené třídy a další kód pro přepínání zobrazení dynamicky na existující aplikaci MFC.  
  
 Kroky jsou následující:  
  
-   [Upravit existující třída aplikace](#vcconmodifyexistingapplicationa1)  
  
-   [Vytvořit a upravit nové třídy zobrazení](#vcconnewviewclassa2)  
  
-   [Vytvořte a připojte nové zobrazení](#vcconattachnewviewa3)  
  
-   [Implementace přepínání funkce](#vcconswitchingfunctiona4)  
  
-   [Přidání podpory pro přepínání zobrazení](#vcconswitchingtheviewa5)  
  
 Zbývající část tohoto tématu se předpokládá následující:  
  
-   Název `CWinApp`-odvozené objekt `CMyWinApp`, a `CMyWinApp` definována a je definována v MYWINAPP. H a MYWINAPP. CPP.  
  
-   `CNewView`je název nové `CView`-odvozené objekt, a `CNewView` definována a je definována v NEWVIEW. H a NEWVIEW. CPP.  
  
##  <a name="vcconmodifyexistingapplicationa1"></a>Upravit existující třída aplikace  
 Pro aplikaci pro přepínání mezi zobrazeními budete muset upravit třídy aplikace přidáním členské proměnné pro uložení zobrazení a způsob, jak je přepnout.  
  
 Přidejte následující kód k prohlášení o `CMyWinApp` v MYWINAPP. V:  
  
 [!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]  
  
 Nové proměnné členů `m_pOldView` a `m_pNewView`, přejděte na aktuální zobrazení a nově vytvořený jeden. Metoda new (`SwitchView`) Přepíná zobrazení na žádost uživatele. Těla metody je popsána dále v tomto tématu v [implementovat funkce přepínání](#vcconswitchingfunctiona4).  
  
 Poslední změny třída aplikace vyžaduje, včetně nový soubor hlaviček, který definuje zpráv systému Windows (**WM_INITIALUPDATE**), který se používá v přepínání funkce.  
  
 V části zahrnout MYWINAPP vložte následující řádek. CPP:  
  
 [!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]  
  
 Uložte změny a pokračovat k dalšímu kroku.  
  
##  <a name="vcconnewviewclassa2"></a>Vytvořit a upravit nové třídy zobrazení  
 Vytvoření nové třídy zobrazení je umožněno pomocí **novou třídu** příkaz k dispozici v zobrazení tříd. Pro tuto třídu Jediným požadavkem je, že odvozená z `CView`. Tato nová třída přidáte do aplikace. Konkrétní informace o přidání nové třídy do projektu najdete v tématu [přidání třídy](../ide/adding-a-class-visual-cpp.md).  
  
 Po přidání třídu do projektu, budete muset změnit usnadnění některé členy třídy zobrazení.  
  
 Upravte NEWVIEW. H změnou specifikátor přístup z `protected` k **veřejné** pro konstruktor a destruktor. To umožňuje třídě vytvořen a zničen dynamicky a upravit vzhled zobrazení, aby byl viditelný.  
  
 Uložte změny a pokračovat k dalšímu kroku.  
  
##  <a name="vcconattachnewviewa3"></a>Vytvořte a připojte nové zobrazení  
 A vytvořte nové zobrazení, budete muset upravit `InitInstance` funkce třídě aplikace. Úpravy přidá nový kód, který vytvoří nový objekt zobrazení i pak inicializuje `m_pOldView` a `m_pNewView` s dvěma existující objekty zobrazení.  
  
 Protože je v rámci vytvořit nové zobrazení `InitInstance` funkce, nových nebo stávajících zobrazení zachovat po dobu jeho existence aplikace. Ale aplikace může stejně snadno vytvořit nové zobrazení dynamicky.  
  
 Vložte tento kód po volání `ProcessShellCommand`:  
  
 [!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]  
  
 Uložte změny a pokračovat k dalšímu kroku.  
  
##  <a name="vcconswitchingfunctiona4"></a>Implementace přepínání funkce  
 V předchozím kroku jste přidali kód, který je vytvořen a inicializován nový objekt zobrazení. Poslední hlavní část je implementovat metodu přepínání `SwitchView`.  
  
 Na konci souboru implementace pro vaši aplikaci třídy (MYWINAPP. CPP), přidejte následující definici metody:  
  
 [!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]  
  
 Uložte změny a pokračovat k dalšímu kroku.  
  
##  <a name="vcconswitchingtheviewa5"></a>Přidání podpory pro přepínání zobrazení  
 V posledním kroku, zahrnuje přidání kódu, který volá `SwitchView` metoda, když aplikace potřebuje pro přepínání mezi zobrazeními. To lze provést několika způsoby: Přidání nové položky nabídky k vyberte uživatele nebo přepnutí zobrazení interně při splnění určitých podmínek.  
  
 Další informace o přidání nových položek nabídky a funkce obslužné rutiny příkazů najdete v tématu [obslužné rutiny pro příkazy a oznámení ovládacích prvků](../mfc/handlers-for-commands-and-control-notifications.md).  
  
## <a name="see-also"></a>Viz také  
 [Document/View – architektura](../mfc/document-view-architecture.md)

