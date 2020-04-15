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
ms.openlocfilehash: ed45fc7014bda18887be6dc8fbcdff8ba9a9c5f1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373047"
---
# <a name="mfc-macros-and-globals"></a>MFC – makra a globální prvky

Knihovnu tříd Microsoft Foundation lze rozdělit do dvou hlavních částí: (1) tříd knihovny MFC a (2) makra a globální. Pokud funkce nebo proměnná není členem třídy, je globální funkce nebo proměnná.

Knihovna knihovny MFC a knihovna knihovny šablon (ATL) sdílejí makra převodu řetězců. Další informace naleznete v [tématu Makra převodu řetězců](../../atl/reference/string-conversion-macros.md) v dokumentaci k atl.

Makra a globální soubory knihovny MFC nabízejí funkce v následujících kategoriích.

## <a name="general-mfc"></a>Obecné knihovny MFC

- [Datové typy](data-types-mfc.md)

- [Typ ové obsazení objektů třídy MFC](type-casting-of-mfc-class-objects.md)

- [Služby objektového modelu run-time](run-time-object-model-services.md)

- [Diagnostické služby](diagnostic-services.md)

- [Zpracování výjimek](exception-processing.md)

- [Formátování dat CString a zobrazení oken zpráv](cstring-formatting-and-message-box-display.md)

- [Mapy zpráv](message-map-macros-mfc.md)

- [Mapy delegátů a rozhraní](delegate-and-interface-maps.md)

- [Moduly a knihovny DLL](extension-dll-macros.md)

- [Informace o aplikaci a správa](application-information-and-management.md)

- [Standardní ID příkazů a oken](standard-command-and-window-ids.md)

- [Pomocné rutiny třídy kolekce](collection-class-helpers.md)

- [Šedé a roztíralé bitmapové funkce](gray-and-dithered-bitmap-functions.md)

- [Standardní rutiny výměny dialogových dat (DDX)](standard-dialog-data-exchange-routines.md)

- [Rutiny ověřování standardních dialogových dat (DDV)](standard-dialog-data-validation-routines.md)

- [Zprávy AFX](afx-messages.md)

- [Styly ovládacích prvků panelu nástrojů](toolbar-control-styles.md)

- [CMFCImagePaintArea::IMAGE_EDIT_MODE – výčet](cmfcimagepaintarea-image-edit-mode-enumeration.md)

## <a name="database"></a>databáze

- [Funkce Výměny dat záznamu (RFX)](record-field-exchange-functions.md) a [funkce hromadné výměny polí (hromadné RFX)](record-field-exchange-functions.md) pro třídy MFC ODBC

- [Funkce výměny pole záznamu (DFX)](record-field-exchange-functions.md) pro třídy MFC DAO

- [Dialogová výměna dat (DDX) pro crecordview a CDaoRecordView](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md) (třídy MFC ODBC a DAO)

- [Dialogová výměna dat (DDX) pro ovládací prvky OLE](dialog-data-exchange-functions-for-ole-controls.md)

- [Makra a globální prostředí pro přímé volání funkcí rozhraní API připojení k otevřené databázi (ODBC)](database-macros-and-globals.md)

- [Inicializace a ukončení databázového stroje DAO](dao-database-engine-initialization-and-termination.md)

## <a name="internet"></a>Internet

- [Globální analýzy adres URL v Internetu](internet-url-parsing-globals.md)

## <a name="dhtml--dhtml-event-maps"></a>Mapy událostí DHTML / DHTML

- [Pomocná makra dialogu DHTML (DDX)](ddx-dhtml-helper-macros.md)

- [DHTML – mapy událostí](dhtml-event-maps.md)

## <a name="ole"></a>OLE

- [Inicializace OLE](ole-initialization.md)

- [Řízení aplikací](application-control.md)

- [Mapy odeslání](dispatch-maps.md)

Kromě toho knihovna MFC poskytuje funkci nazvanou [AfxEnableControlContainer,](ole-initialization.md#afxenablecontrolcontainer) která umožňuje libovolný kontejner OLE vyvinutý pomocí knihovny MFC 4.0 plně podporovat vložené ovládací prvky OLE.

## <a name="ole-controls"></a>Ovládací prvky OLE

- [Konstanty typu parametru varianty](variant-parameter-type-constants.md)

- [Přístup k knihovně typů](type-library-access.md)

- [Stránky vlastností](property-pages-mfc.md)

- [Mapy událostí](event-maps.md)

- [Mapy jímky událostí](event-sink-maps.md)

- [Mapy připojení](connection-maps.md)

- [Registrace ovládacích prvků OLE](registering-ole-controls.md)

- [Třídní továrny a licencování](class-factories-and-licensing.md)

- [Trvalost ovládacích prvků OLE](persistence-of-ole-controls.md)

První část této části stručně popisuje každou z předchozích kategorií a uvádí globální a makra v kategorii spolu se stručným popisem funkcí. Za tímto způsobem jsou uvedeny popisy globálních funkcí, globálních proměnných a maker v knihovně knihovny Knihovny MFC.

> [!NOTE]
> Mnoho globálních funkcí začíná předponou "Afx", ale některé, například funkce výměny dialogových dat (DDX) a mnoho databázových funkcí, nedodržují tuto konvenci. Všechny globální proměnné začínají "afx" jako předponou. Makra nezačínají žádnou konkrétní předponou, ale jsou napsána velkými písmeny.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../mfc/class-library-overview.md)
