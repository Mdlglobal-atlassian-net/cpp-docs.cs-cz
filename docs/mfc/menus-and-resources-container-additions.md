---
title: 'Nabídky a prostředky: kontejnerové doplňky | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IDP_OLE_INIT_FAILED
- IDP_FAILED_TO_CREATE
- VK_ESCAPE
dev_langs:
- C++
helpviewer_keywords:
- application accelerator table [MFC]
- VK_ESCAPE key [MFC]
- IDP_FAILED_TO_CREATE macro [MFC]
- visual editing, application menus and resources
- OLE containers [MFC], menus and resources
- accelerator tables [MFC], container applications
- IDP_OLE_INIT_FAILED macro [MFC]
- CONTAIN tutorial [MFC]
- Links menu item [MFC]
ms.assetid: 425448be-8ca0-412e-909a-a3a9ce845288
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c71e8a79652a86ba412ef829ac1151256d1bf65
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350650"
---
# <a name="menus-and-resources-container-additions"></a>Nabídky a prostředky: Kontejnerové doplňky
Tento článek vysvětluje změny, které je třeba provést v nabídkách a dalším prostředkům v aplikaci visual úpravy kontejneru.  
  
 V kontejneru aplikace potřeba učinit dvou typů změn: změny se stávajícími prostředky pro podporu úpravy s náhledem OLE a přidání nové prostředky používané pro aktivace na místě. Používáte-li vytvořit aplikaci kontejneru v Průvodce vytvořením aplikace, můžete tyto kroky bude provedeno za vás, ale můžou vyžadovat některé přizpůsobení.  
  
 Pokud použijete Průvodce aplikace, můžete se podívat na OCLIENT. RC, skript prostředků pro OCLIENT ukázkovou aplikaci, pokud chcete zobrazit, jak jsou implementované tyto změny. Viz ukázka MFC OLE [OCLIENT](../visual-cpp-samples.md).  
  
 Témata popsaná v tomto článku:  
  
-   [Přidání do nabídky kontejneru](#_core_container_menu_additions)  
  
-   [Přidání tabulky akcelerátorů](#_core_container_application_accelerator_table_additions)  
  
-   [Přidání tabulky řetězců](#_core_string_table_additions_for_container_applications)  
  
##  <a name="_core_container_menu_additions"></a> Přidání do nabídky kontejneru  
 Do nabídky upravit, je nutné přidat následující položky:  
  
|Položka|Účel|  
|----------|-------------|  
|**Vložit nový objekt**|Otevře dialogové okno Vložit objekt OLE vložit položku propojený nebo vložený do dokumentu.|  
|**Vložit propojení**|Vloží odkaz na položku do schránky do dokumentu.|  
|**Příkaz OLE**|Volá primární požadavek vybranou položku. Text této změny položky nabídky tak, aby odrážela primární požadavek vybrané položky.|  
|**Odkazy**|Otevře dialogové okno OLE upravit odkazy změnit stávající propojené položky.|  
  
 Kromě změn uvedené v tomto článku váš zdrojový soubor musí zahrnovat AFXOLECL. RC, který je nutný k provedení Microsoft Foundation Class Library. Vložit nový objekt je přidání pouze požadované nabídky. Lze přidat další položky, ale které jsou zde uvedeny jsou nejobvyklejší.  
  
 Pokud chcete zajistit podporu aktivace na místě obsažených položek, je nutné vytvořit nové nabídky pro aplikaci kontejneru. Tato nabídka se skládá z stejné nabídka Soubor a používá, když jsou otevřené soubory, ale má dva oddělovače je umístěná mezi oběma místní nabídky okna. Tyto oddělovače jsou slouží k určení, kam položky (součást) (aplikace) by měl být jeho nabídky při aktivaci na místě. Další informace o této technice slučování nabídek najdete v tématu [nabídky a prostředky: sloučení nabídky](../mfc/menus-and-resources-menu-merging.md).  
  
##  <a name="_core_container_application_accelerator_table_additions"></a> Přidání tabulka akcelerátoru aplikace kontejneru  
 Malé změny prostředků tabulky akcelerátorů kontejnerové aplikace jsou nezbytné, pokud podporujete aktivace na místě. První změna umožňuje uživatelům stisknutím klávesy ESC (ESC) zrušit režimu úprav na místě. Přidejte následující položku v tabulce akcelerátorů hlavní:  
  
|ID|Key|Typ|  
|--------|---------|----------|  
|**ID_CANCEL_EDIT_CNTR**|VK_ESCAPE –|**VIRTKEY**|  
  
 Druhý změnou je vytvořit novou tabulku akcelerátoru, která odpovídá nový prostředek nabídky, které jsou vytvořené pro aktivace na místě. Tato tabulka obsahuje záznamy pro nabídky soubor a okno kromě **vk_escape –** výše uvedené položky. V následujícím příkladu je vytvořen aktivace na místě v ukázce MFC tabulka akcelerátoru [KONTEJNERU](../visual-cpp-samples.md):  
  
|ID|Key|Typ|  
|--------|---------|----------|  
|`ID_FILE_NEW`|CTRL + N|**VIRTKEY**|  
|`ID_FILE_OPEN`|CTRL+O|**VIRTKEY**|  
|**ID_FILE_SAVE –**|CTRL+S|**VIRTKEY**|  
|**ID_FILE_PRINT –**|CTRL + P|**VIRTKEY**|  
|**ID_NEXT_PANE –**|VK_F6|**VIRTKEY**|  
|**ID_PREV_PANE –**|SHIFT + VK_F6|**VIRTKEY**|  
|**ID_CANCEL_EDIT_CNTR**|VK_ESCAPE –|**VIRTKEY**|  
  
##  <a name="_core_string_table_additions_for_container_applications"></a> Přidání tabulky řetězec pro aplikace typu kontejner  
 Většinu změn do tabulek řetězců pro aplikace typu kontejner odpovídají položky další nabídky uvedený v [přidání do nabídky kontejneru](#_core_container_menu_additions). Si poskytují text zobrazený ve stavovém řádku při každé položky nabídky se zobrazí. Jako příklad uvádíme položky tabulky řetězců, které generuje Průvodce aplikace:  
  
|ID|String|  
|--------|------------|  
|**IDP_OLE_INIT_FAILED –**|Nepodařilo se inicializovat OLE. Ujistěte se, že jsou knihoven OLE správná verze.|  
|**IDP_FAILED_TO_CREATE –**|Vytvoření objektu se nezdařilo. Ujistěte se, že objekt je zadána v registru systému.|  
  
## <a name="see-also"></a>Viz také  
 [Nabídky a prostředky (OLE)](../mfc/menus-and-resources-ole.md)   
 [Nabídky a prostředky: Serverové doplňky](../mfc/menus-and-resources-server-additions.md)

