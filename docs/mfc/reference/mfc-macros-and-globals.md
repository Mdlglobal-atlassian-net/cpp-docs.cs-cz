---
title: "MFC – makra a globální prvky | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros
dev_langs: C++
helpviewer_keywords:
- MFC, global functions and variables
- MFC, macros
- global functions, MFC
- macros, MFC
- global functions [MFC]
- global variables, MFC
- Afx naming convention
- macros
ms.assetid: add4e33f-0e62-4d27-be14-896cb8675d22
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 71011177634e92b22cce1bc88a2ee711ad9537ed
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-macros-and-globals"></a>MFC – makra a globální prvky
Knihovny Microsoft Foundation Class je možné rozdělit do dvou hlavních částech: (1) MFC – třídy a (2) makra a globální prvky. Pokud funkce nebo proměnná není členem třídy, je globální funkce nebo proměnná.  
  
 Knihovny MFC a knihovny Active šablony (ATL) sdílet makra převodů řetězec. Další informace najdete v tématu [makra převodů řetězec](../../atl/reference/string-conversion-macros.md) v ATL dokumentaci.  
  
 MFC – makra a globální prvky nabízejí funkce v následujících kategorií.  
  
## <a name="general-mfc"></a>Obecné MFC  
  
-   [Datové typy](data-types-mfc.md)  
  
-   [Typ přetypování objektů tříd MFC](type-casting-of-mfc-class-objects.md)  
  
-   [Služby modelu běhového objektu](run-time-object-model-services.md)  
  
-   [Diagnostické služby](diagnostic-services.md)  
  
-   [Zpracování výjimek](exception-processing.md)  
  
-   [Formátování dat CString a zobrazení oken zpráv](cstring-formatting-and-message-box-display.md)  
  
-   [Mapy zpráv](message-map-macros-mfc.md)  

-   [Delegát a rozhraní mapy](delegate-and-interface-maps.md)

-   [Moduly a knihoven DLL](extension-dll-macros.md)
  
-   [Informace o aplikaci a Správa](application-information-and-management.md)  
  
-   [Standardní identifikátory příkazu a okna](standard-command-and-window-ids.md)  
  
-   [Pomocné rutiny třídy kolekce](collection-class-helpers.md)  
  
-   [Funkce gray a dithered pro bitové mapy](gray-and-dithered-bitmap-functions.md)  
  
-   [(DDX) rutiny výměny dat standardního dialogového okna](standard-dialog-data-exchange-routines.md)  
  
-   [Rutiny ověřování (DDV) dat standardního dialogového okna](standard-dialog-data-validation-routines.md)  
  
-   [Afx – zprávy](afx-messages.md)  
  
-   [Styly ovládacího prvku panel nástrojů](toolbar-control-styles.md)  
  
-   [CMFCImagePaintArea::IMAGE_EDIT_MODE – výčet](cmfcimagepaintarea-image-edit-mode-enumeration.md)  

  
## <a name="database"></a>Databáze  
  
-   [Zaznamenejte funkce pole Exchange (RFX)](record-field-exchange-functions.md) a [Hromadná výměna pole záznamu (hromadné RFX) funkce](record-field-exchange-functions.md) pro třídy MFC rozhraní ODBC  
  
-   [Funkce výměny (DFX) polí záznamů](record-field-exchange-functions.md) pro třídy MFC rozhraní DAO  
  
-   [Výměna dat dialogových oken (DDX) funkce pro třídy CRecordView a CDaoRecordView](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md) (třídy knihovny MFC rozhraní ODBC a DAO)  
  
-   [Funkce výměny (DDX) dat dialogových oken pro ovládací prvky OLE](dialog-data-exchange-functions-for-ole-controls.md)  
  
-   [Makra a globální prvky, které pomáhají při přímé volání funkce připojení ODBC (Open Database) rozhraní API](database-macros-and-globals.md)  
  
-   [DAO modul inicializace a ukončování databázového](dao-database-engine-initialization-and-termination.md)  
  
## <a name="internet"></a>Internet  
  
-   [Globální funkce pro analýzu internetových adres URL](internet-url-parsing-globals.md)  
  
## <a name="dhtml--dhtml-event-maps"></a>DHTML / mapy událostí jazyka DHTML  
  
-   [Výměna dialogových dat DHTML makra pomocné rutiny (DDX)](ddx-dhtml-helper-macros.md)  
  
-   [DHTML – mapa událostí](dhtml-event-maps.md)  
  
## <a name="ole"></a>OLE  
  
-   [Inicializace modulu OLE](ole-initialization.md)  
  
-   [Řízení aplikace](application-control.md)  
  
-   [Mapy odesílání](dispatch-maps.md)  
  
 Kromě toho MFC poskytuje funkci s názvem [AfxEnableControlContainer –](ole-initialization.md#afxenablecontrolcontainer) , umožňuje žádné OLE – kontejner vyvinuté pomocí MFC 4.0 pro zajištění plné podpory vložených ovládací prvky OLE.  
  
## <a name="ole-controls"></a>Ovládací prvky OLE  
  
-   [Konstanty variantních typů parametrů](variant-parameter-type-constants.md)  
  
-   [Přístup ke knihovně typů](type-library-access.md)  
  
-   [Stránky vlastností](property-pages-mfc.md)  
  
-   [Mapy událostí](event-maps.md)  
  
-   [Mapy jímek událostí](event-sink-maps.md)  
  
-   [Mapy připojení](connection-maps.md)  
  
-   [Registrace ovládacích prvků OLE](registering-ole-controls.md)  
  
-   [Objekty pro vytváření tříd a licencování](class-factories-and-licensing.md)  
  
-   [Trvalost ovládacích prvků OLE](persistence-of-ole-controls.md)  
  
 První část v této části stručně popisuje každý z předchozích kategorií a uvádí globální funkce a makra v kategorii, společně s stručný popis funkcí. Toto jsou popisy globální funkce, globální proměnné a makra v knihovně MFC.  
  
> [!NOTE]
>  Mnoho globální funkce, které začínají předponou afx "–", ale některé, například funkce exchange (DDX) dat dialogových oken a spoustu funkcí, databáze, neprovádějte touto konvencí. Všechny globální proměnné začínat afx "–" jako předponu. Makra nebudou spuštěny žádné konkrétní předponou, ale jsou zapsány v velká písmena.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../mfc/class-library-overview.md)



