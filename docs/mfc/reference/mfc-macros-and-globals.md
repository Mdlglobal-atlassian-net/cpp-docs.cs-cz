---
title: MFC – makra a globální prvky
ms.date: 11/04/2016
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
ms.openlocfilehash: 86fbda42d97c9086a3c1d021618a4694cfade7df
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611807"
---
# <a name="mfc-macros-and-globals"></a>MFC – makra a globální prvky

Knihovny Microsoft Foundation Class je možné rozdělit do dvou hlavních částech: (1) třídy knihovny MFC a (2) makra a globální prvky. Pokud funkce nebo proměnná není členem třídy, je globální funkce nebo proměnná.

Knihovna MFC a aktivní šablony knihovny (ATL) sdílejí makra převodu řetězců. Další informace najdete v tématu [makra převodu řetězců](../../atl/reference/string-conversion-macros.md) v dokumentaci knihovny ATL.

MFC – makra a globální prvky nabízejí funkce v následujících kategoriích.

## <a name="general-mfc"></a>Obecné MFC

- [Datové typy](data-types-mfc.md)

- [Přetypování objektů tříd MFC](type-casting-of-mfc-class-objects.md)

- [Služby modelu běhového objektu](run-time-object-model-services.md)

- [Diagnostické služby](diagnostic-services.md)

- [Zpracování výjimek](exception-processing.md)

- [Formátování dat CString a zobrazení oken zpráv](cstring-formatting-and-message-box-display.md)

- [Mapy zpráv](message-map-macros-mfc.md)

- [Delegát a mapy rozhraní](delegate-and-interface-maps.md)

- [Moduly a knihovny DLL](extension-dll-macros.md)

- [Informace o aplikacích a Správa](application-information-and-management.md)

- [Standardní identifikátory příkazů a oken](standard-command-and-window-ids.md)

- [Pomocné rutiny třídy kolekce](collection-class-helpers.md)

- [Funkce gray a dithered pro bitové mapy](gray-and-dithered-bitmap-functions.md)

- [(DDX) rutiny výměny dat standardního dialogového okna](standard-dialog-data-exchange-routines.md)

- [Rutiny ověřování (DDV) dat standardního dialogového okna](standard-dialog-data-validation-routines.md)

- [AFX – zprávy](afx-messages.md)

- [Styly ovládacích prvků panelů nástrojů](toolbar-control-styles.md)

- [CMFCImagePaintArea::IMAGE_EDIT_MODE – výčet](cmfcimagepaintarea-image-edit-mode-enumeration.md)

## <a name="database"></a>Databáze

- [Zaznamenejte výměna pole (RFX) funkce](record-field-exchange-functions.md) a [Hromadná výměna pole záznamu (hromadné funkce RFX) funkce](record-field-exchange-functions.md) pro třídy knihovny MFC rozhraní ODBC

- [Funkce výměny (DFX) polí v záznamu](record-field-exchange-functions.md) pro třídy MFC rozhraní DAO

- [Výměna dat dialogových oken (DDX) funkce pro třídy CRecordView a CDaoRecordView](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md) (třídy knihovny MFC rozhraní ODBC a DAO)

- [Funkce výměny (DDX) dat dialogových oken pro ovládací prvky OLE](dialog-data-exchange-functions-for-ole-controls.md)

- [Makra a globální prvky pro přímé volání funkcí připojení ODBC (Open Database) rozhraní API](database-macros-and-globals.md)

- [DAO – modul inicializace a ukončování databázového](dao-database-engine-initialization-and-termination.md)

## <a name="internet"></a>Internet

- [Globální funkce pro analýzu internetových adres URL](internet-url-parsing-globals.md)

## <a name="dhtml--dhtml-event-maps"></a>DHTML / mapy událostí DHTML

- [Výměna dialogových dat DHTML (DDX) makra pomocné rutiny](ddx-dhtml-helper-macros.md)

- [DHTML – mapa událostí](dhtml-event-maps.md)

## <a name="ole"></a>OLE

- [Inicializace OLE](ole-initialization.md)

- [Řízení aplikací](application-control.md)

- [Mapy odbavení](dispatch-maps.md)

Kromě toho knihovna MFC poskytuje funkci s názvem [AfxEnableControlContainer](ole-initialization.md#afxenablecontrolcontainer) , že umožňuje libovolném kontejneru OLE byly vyvinuty v sadě 4.0 knihovna MFC pro úplnou podporu vložené ovládací prvky OLE.

## <a name="ole-controls"></a>Ovládací prvky OLE

- [Konstanty variantních typů parametrů](variant-parameter-type-constants.md)

- [Přístup ke knihovně typů](type-library-access.md)

- [Stránky vlastností](property-pages-mfc.md)

- [Mapy událostí](event-maps.md)

- [Mapy jímek událostí](event-sink-maps.md)

- [Mapy připojení](connection-maps.md)

- [Registrace ovládacích prvků OLE](registering-ole-controls.md)

- [Objekty pro vytváření tříd a licencování](class-factories-and-licensing.md)

- [Trvalost ovládacích prvků OLE](persistence-of-ole-controls.md)

První část této části stručně popisuje všech předchozích kategorií a seznamy, globální proměnné a makra v kategorii, společně s stručný popis funkcí. Následující jsou popsaná níž globálních funkcí, globálních proměnných a maker v knihovně MFC.

> [!NOTE]
>  Mnoho globálních funkcí začínají předponou "Afx –", ale některé, například funkce exchange (DDX) dat dialogových oken a mnoho z funkcí databáze neřídí Tato konvence. Všechny globální proměnné začínat "afx –" jako předponu. Makra nezačínají žádné konkrétní předponu, ale jsou zapsány v velká písmena.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../mfc/class-library-overview.md)
