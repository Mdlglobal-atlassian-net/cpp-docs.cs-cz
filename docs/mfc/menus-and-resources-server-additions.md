---
title: 'Nabídky a prostředky: serverové doplňky | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IDP_OLE_INIT_FAILED
dev_langs:
- C++
helpviewer_keywords:
- OLE visual editing servers [MFC]
- accelerator tables [MFC], server applications
- visual editing [MFC], application menus and resources
- server applications [MFC], accelerator table
- string tables [MFC], visual editing applications
- servers [MFC], menu additions
- resources [MFC], server applications
- OLE server applications [MFC], menus and resources
- string editing [MFC], visual editing applications
- IDP_OLE_INIT_FAILED macro [MFC]
- server applications [MFC], OLE menus and resources
- OLE initialization failure [MFC]
ms.assetid: 56ce9e8d-8f41-4db8-8dee-e8b0702d057c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cbcedd8cf217c993511bdb84a89294d7e98d6bab
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930199"
---
# <a name="menus-and-resources-server-additions"></a>Nabídky a prostředky: Serverové doplňky
Tento článek vysvětluje změny, které je třeba provést v nabídkách a dalším prostředkům v aplikaci visual úpravy (součást). Serverová aplikace požaduje mnoho doplňky strukturu nabídky a jiné prostředky, protože může být spuštěno v jednom ze tří režimů: stát samostatného embedded, nebo na místě. Jak je popsáno v [nabídky a prostředky (OLE)](../mfc/menus-and-resources-ole.md) článek, jsou maximálně čtyři sady nabídky. Všechny čtyři se používají pro aplikace MDI úplný server při pouze tři se používají pro miniserver. V Průvodce vytvořením aplikace vytvoří rozložení nabídky potřebné pro typ serveru, který má být. Některé přizpůsobení může být nutné.  
  
 Pokud použijete Průvodce aplikace, můžete se podívat na HIERSVR. RC, skript prostředků pro ukázkovou aplikaci MFC [HIERSVR](../visual-cpp-samples.md), pokud chcete zobrazit, jak jsou implementované tyto změny.  
  
 Témata popsaná v tomto článku:  
  
-   [Přidání serveru do nabídky](#_core_server_menu_additions)  
  
-   [Přidání tabulky akcelerátorů](#_core_server_application_accelerator_table_additions)  
  
-   [Přidání tabulky řetězců](../mfc/menus-and-resources-container-additions.md)  
  
-   [Přidání miniserver](#_core_mini.2d.server_additions)  
  
##  <a name="_core_server_menu_additions"></a> Přidání serveru do nabídky  
 Aplikace serveru (součást) musí mít prostředků nabídky přidaná kvůli podpoře úpravy s náhledem OLE. Není nutné změnit v nabídkách používá při spuštění aplikace v samostatném režimu, ale před vytvořením aplikace musíte přidat dva nové nabídky prostředky: jednu pro podporu aktivace na místě a jeden pro podporu serveru, se plně otevřené. Obě nabídky prostředky jsou používány úplné a miniserver aplikace.  
  
-   Kvůli podpoře aktivace na místě, je nutné vytvořit nabídky prostředek, který je velmi podobný prostředků nabídky použitou při spuštění v samostatném režimu. Rozdíl v této nabídce je, že chybí soubor a okno položky (a všechny ostatní položky nabídky, které pracují s aplikace a nikoli data). Kontejner aplikace bude zadejte tyto položky nabídky. Další informace o a příklad, tato technika slučování nabídek, najdete v článku [nabídky a prostředky: sloučení nabídky](../mfc/menus-and-resources-menu-merging.md).  
  
-   K podpoře plně open aktivace, musíte vytvořit nabídky prostředek, do nabídky prostředek, který používá při spuštění v samostatném režimu. Pouze úpravy pro tento prostředek nabídky je, že některé položky se mění tak, aby odrážela skutečnost, že server pracuje na položku vložených v složeného dokumentu.  
  
 Kromě změn uvedené v tomto článku musí obsahovat AFXOLESV souboru prostředků. RC, který je nutný k provedení Microsoft Foundation Class Library. Tento soubor je v podadresáři MFC\Include.  
  
##  <a name="_core_server_application_accelerator_table_additions"></a> Přidání tabulka akcelerátoru aplikace serveru  
 Dva nové prostředky tabulky akcelerátorů musí být přidaný do serverové aplikace; Tyto nekorespondují přímo do nové nabídky prostředky, které se popisuje výš. První tabulky akcelerátorů se používá, pokud je serverová aplikace aktivován na místě. Obsahuje všechny položky v tabulce akcelerátorů zobrazení s výjimkou těch, které svázané k souboru a okno nabídky.  
  
 Druhá tabulka je téměř přesnou kopii tabulky akcelerátorů tohoto zobrazení. Případné rozdíly paralelní změny provedené ve plně otevřít nabídku uvedený v [přidání serveru do nabídky](#_core_server_menu_additions).  
  
 Příklad těchto změn tabulky akcelerátorů porovnejte tabulky akcelerátoru IDR_HIERSVRTYPE_SRVR_IP a IDR_HIERSVRTYPE_SRVR_EMB s IDR_MAINFRAME v HIERSVR. RC soubor zahrnutý v ukázce MFC OLE [HIERSVR](../visual-cpp-samples.md). Souborová služba a okno akcelerátorů chybí z tabulky na místě a přesné kopie jsou v vložené tabulky.  
  
##  <a name="_core_string_table_additions_for_server_applications"></a> Přidání tabulky řetězec pro serverové aplikace  
 Přidání pouze jeden řetězec tabulky je nutné v serveru aplikace – řetězec tak, aby označily, že inicializace OLE se nezdařila. Jako příklad uvádíme tabulky řetězců položku, která generuje Průvodce aplikací:  
  
|ID|String|  
|--------|------------|  
|IDP_OLE_INIT_FAILED –|Nepodařilo se inicializovat OLE. Ujistěte se, že jsou knihoven OLE správná verze.|  
  
##  <a name="_core_mini.2d.server_additions"></a> Přidání miniserver  
 Přidání stejné platí pro miniservers jako uvedených výše pro úplné servery. Protože miniserver nelze spustit v samostatném režimu, je mnohem menší jeho hlavní nabídky. V hlavní nabídce vytvořené průvodcem aplikací má pouze nabídku souborů, obsahující pouze položky ukončení a o. Vložené a místní nabídky a akcelerátorů pro miniservers jsou stejné jako v případě úplné servery.  
  
## <a name="see-also"></a>Viz také  
 [Nabídky a prostředky (OLE)](../mfc/menus-and-resources-ole.md)   
 [Nabídky a prostředky: Sloučení nabídky](../mfc/menus-and-resources-menu-merging.md)

