---
title: ODBC – třídy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.data
dev_langs:
- C++
helpviewer_keywords:
- database classes [MFC], ODBC
- ODBC classes [MFC]
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97bbdb74d122e633574dcf76876f0907de8ef2c4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400574"
---
# <a name="odbc-classes"></a>ODBC – třídy

Tyto třídy fungují s další aplikace tříd rozhraní framework a poskytovat snadný přístup k široké databází, pro které jsou k dispozici ovladače připojení ODBC (Open Database).

Programy, které používají rozhraní ODBC databáze bude mít alespoň `CDatabase` objektu a `CRecordset` objektu.

[CDatabase](../mfc/reference/cdatabase-class.md)<br/>
Zapouzdřuje připojení ke zdroji dat, pomocí kterého můžete pracovat ve zdroji dat.

[CRecordset –](../mfc/reference/crecordset-class.md)<br/>
Zapouzdřuje sadu záznamů ze zdroje dat vybrané. Sady záznamů povolit posouvání ze záznamu, aktualizují záznamy (přidání, úpravy a odstranění záznamů), výběr kvalifikaci s filtrem, řazení výběr a Parametrizace výběru s informacemi o získaných nebo vypočítat v době běhu.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Formulář obsahuje zobrazení přímo připojen k objektu sady záznamů. Výměna dialogových dat (DDX) mechanizmus výměny dat mezi sady záznamů a ovládací prvky zobrazení záznamů. Stejně jako všechna zobrazení formuláře zobrazení záznamů podle prostředku šablony dialogového okna. Zobrazení záznamů také podporují přesunutí mezi záznamy v sadě záznamů, aktualizace záznamů a zavření přidružené sadě záznamů po zavření zobrazení záznamů.

[CDBException](../mfc/reference/cdbexception-class.md)<br/>
Výjimka výsledkem zpracování chyb v přístupu k datům. Tato třída slouží stejnému účelu jako ostatní třídy výjimek v mechanismus zpracování výjimek knihovny tříd.

[CFieldExchange](../mfc/reference/cfieldexchange-class.md)<br/>
Poskytuje kontextové informace pro podporu výměna pole záznamu (RFX), který vyměňuje data mezi pole datové členy a parametry datových členů objektu sady záznamů a odpovídající sloupce tabulky ve zdroji dat. Obdobná třída [cdataexchange –](../mfc/reference/cdataexchange-class.md), který se používá podobně pro výměna dat dialogových oken (DDX).

## <a name="related-classes"></a>Související třídy

[CLongBinary –](../mfc/reference/clongbinary-class.md)<br/>
Zapouzdřuje popisovač úložiště pro binární velkých objektů (BLOB), jako je například rastrový obrázek. `CLongBinary` objekty se používají ke správě velkých datových objektů uložených v databázových tabulek.

[CDBVariant –](../mfc/reference/cdbvariant-class.md)<br/>
Umožňuje uložit hodnotu bez starostí o datový typ hodnoty. `CDBVariant` sleduje datový typ aktuální hodnotu, která je uložena ve sjednocení.

## <a name="see-also"></a>Viz také

[Přehled tříd](../mfc/class-library-overview.md)

