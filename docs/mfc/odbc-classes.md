---
title: ODBC – třídy
ms.date: 11/04/2016
helpviewer_keywords:
- database classes [MFC], ODBC
- ODBC classes [MFC]
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
ms.openlocfilehash: a4cfa0d7afa197de7b65b6a0bd6b881a09534ef6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447693"
---
# <a name="odbc-classes"></a>ODBC – třídy

Tyto třídy pracují s ostatními třídami rozhraní aplikace a poskytují snadný přístup k široké škále databází, pro které jsou k dispozici ovladače rozhraní ODBC (Open Database Connectivity).

Programy, které používají databáze ODBC, budou mít alespoň objekt `CDatabase` a objekt `CRecordset`.

[CDatabase](../mfc/reference/cdatabase-class.md)<br/>
Zapouzdřuje připojení ke zdroji dat, pomocí kterého můžete pracovat na zdroji dat.

[CRecordset](../mfc/reference/crecordset-class.md)<br/>
Zapouzdřuje sadu záznamů vybraných ze zdroje dat. Sady záznamů umožňují posouvání záznamu na záznam, aktualizaci záznamů (přidávání, upravování a odstraňování záznamů), kvalifikaci výběru s filtrem, řazení výběru a Parametrizace výběru o informace získané nebo počítané v době běhu.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Poskytuje zobrazení formuláře přímo připojené k objektu sady záznamů. Mechanismus pro výměnu dat dialogových oken (DDX) vyměňuje data mezi sadou záznamů a ovládacími prvky zobrazení záznamu. Podobně jako u všech zobrazení formulářů je zobrazení záznamu založené na prostředku šablony dialogového okna. Zobrazení záznamů také podporují přesun ze záznamu na záznam v sadě záznamů, aktualizaci záznamů a zavření přidružené sady záznamů při zavření zobrazení záznamu.

[CDBException](../mfc/reference/cdbexception-class.md)<br/>
Výjimka způsobená chybami při zpracování přístupu k datům. Tato třída slouží stejnému účelu jako jiné třídy výjimek v mechanismu zpracování výjimek knihovny tříd.

[CFieldExchange](../mfc/reference/cfieldexchange-class.md)<br/>
Poskytuje kontextové informace pro podporu výměny pole záznamu (RFX), která vyměňuje data mezi poli datových členů a parametrem datových členů objektu Recordset a odpovídající sloupce tabulky ve zdroji dat. Analogické ke třídě [CDataExchange –](../mfc/reference/cdataexchange-class.md), která se používá podobně pro výměnu dialogových dat (DDX).

## <a name="related-classes"></a>Související třídy

[CLongBinary –](../mfc/reference/clongbinary-class.md)<br/>
Zapouzdřuje popisovač do úložiště pro binární rozsáhlý objekt (BLOB), jako je například rastrový obrázek. objekty `CLongBinary` se používají ke správě rozsáhlých datových objektů uložených v databázových tabulkách.

[CDBVariant –](../mfc/reference/cdbvariant-class.md)<br/>
Umožňuje uložit hodnotu bez obav o datový typ hodnoty. `CDBVariant` sleduje datový typ aktuální hodnoty, který je uložen ve sjednocení.

## <a name="see-also"></a>Viz také

[Přehled třídy](../mfc/class-library-overview.md)
