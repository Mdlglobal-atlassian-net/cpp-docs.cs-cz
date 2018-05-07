---
title: ODBC – třídy | Microsoft Docs
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
ms.openlocfilehash: 98ef4509e7e7570d8c07013f0287fe01105e154a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="odbc-classes"></a>ODBC – třídy
Tyto třídy pracovat s další aplikace framework třídy poskytují snadný přístup k široké škále databází, pro které jsou k dispozici ovladače připojení ODBC (Open Database).  
  
 Programy, které používají rozhraní ODBC databáze bude mít alespoň `CDatabase` objektu a `CRecordset` objektu.  
  
 [CDatabase](../mfc/reference/cdatabase-class.md)  
 Zapouzdřuje připojení ke zdroji dat, pomocí kterého lze provozovat na datovém zdroji.  
  
 [CRecordset –](../mfc/reference/crecordset-class.md)  
 Zapouzdří sadu záznamy ze zdroje dat vybraná. Sady záznamů povolte posouvání mezi záznamy, aktualizace záznamů (přidání, úpravy a odstraňování záznamů), kvalifikující výběr s filtrem, řazení výběr a Parametrizace výběr s informacemi o získaných nebo vypočtených za běhu.  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 Nabízí způsob zobrazení přímo připojený k objektu sady záznamů. Výměna dialogových dat (DDX) mechanismus výměnu dat mezi sady záznamů a ovládací prvky zobrazení záznamu. Jako všechna zobrazení formuláře vychází zobrazení záznamu prostředku šablony dialogové okno. Zobrazení záznamů také podporují přesun mezi záznamy v sadě záznamů, aktualizace záznamů a uzavření přidružených záznamů zavře záznam zobrazení.  
  
 [CDBException](../mfc/reference/cdbexception-class.md)  
 Výjimku vyplývající z chyb v přístupu k datům zpracování. Tato třída slouží ke stejnému účelu jako ostatní třídy výjimek ve zpracování výjimek mechanismus knihovny tříd.  
  
 [CFieldExchange](../mfc/reference/cfieldexchange-class.md)  
 Poskytuje kontextové informace pro podporu pole záznamu (exchange – RFX), který výměny dat mezi parametry datových členů objekt sady záznamů a odpovídající sloupce tabulky ve zdroji dat a pole datových členů. Obdobná jako třída [CDataExchange](../mfc/reference/cdataexchange-class.md), který se používá podobně pro výměna dialogových dat (DDX).  
  
## <a name="related-classes"></a>Související třídy  
 [CLongBinary](../mfc/reference/clongbinary-class.md)  
 Zapouzdří popisovač pro úložiště pro binární rozsáhlý objekt (BLOB), jako je například rastrový obrázek. `CLongBinary` objekty se používají ke správě objektů velkého množství dat uložených v tabulkách databáze.  
  
 [CDBVariant](../mfc/reference/cdbvariant-class.md)  
 Umožňuje ukládání hodnotu bez obav, hodnota datového typu. `CDBVariant` sleduje datový typ aktuální hodnota, která je uložena v spojení.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)

