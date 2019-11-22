---
title: DAO – třídy
ms.date: 09/17/2019
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: cdd3fd9a733df73d36441693d049724878219df5
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303398"
---
# <a name="dao-classes"></a>DAO – třídy

Rozhraní DAO se používá s databázemi Access a je podporované prostřednictvím sady Office 2013. Rozhraní DAO 3,6 je finální verze a je považována za zastaralou.

Tyto třídy pracují s ostatními třídami aplikačního rozhraní a poskytují snadný přístup k databázím DAO (Data Access Object), které používají stejný databázový stroj jako Microsoft Visual Basic a Microsoft Access. Třídy DAO mají přístup také k široké škále databází, pro které jsou k dispozici ovladače rozhraní ODBC (Open Database Connectivity).

Programy, které používají databáze DAO, budou mít alespoň objekt `CDaoDatabase` a objekt `CDaoRecordset`.

> [!NOTE]
>  Vizuální C++ prostředí a průvodci už rozhraní DAO nepodporují (i když třídy DAO jsou zahrnuté a pořád je můžete používat). Microsoft doporučuje používat rozhraní ODBC pro nové projekty knihovny MFC. V údržbě stávajících aplikací byste měli používat jenom rozhraní DAO.

[CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)<br/>
Spravuje pojmenovanou relaci databáze chráněné heslem od přihlášení k odhlášení. Většina programů používá výchozí pracovní prostor.

[CDaoDatabase](../mfc/reference/cdaodatabase-class.md)<br/>
Připojení k databázi, pomocí které můžete pracovat s daty.

[CDaoRecordset](../mfc/reference/cdaorecordset-class.md)<br/>
Představuje sadu záznamů vybraných ze zdroje dat.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Zobrazení, které zobrazuje záznamy databáze v ovládacích prvcích.

[CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)<br/>
Představuje definici dotazu, obvykle uloženou v databázi.

[CDaoTableDef](../mfc/reference/cdaotabledef-class.md)<br/>
Představuje uloženou definici základní tabulky nebo připojené tabulky.

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
Představuje podmínku výjimky vyplývající z tříd DAO.

[CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)<br/>
Podporuje rutiny pro výměnu záznamů pole (DFX) DAO používané databázovými třídami DAO. Tuto třídu obvykle nebudete používat přímo.

## <a name="related-classes"></a>Související třídy

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
Zapouzdřuje popisovač do úložiště pro binární rozsáhlý objekt (BLOB), jako je například rastrový obrázek. objekty `CLongBinary` se používají ke správě rozsáhlých datových objektů uložených v databázových tabulkách.

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
Obálka pro typ automatizace OLE **, typ aritmetického typu s**pevnou desetinnou čárkou, s 15 číslicemi před desetinnou čárkou a 4 číslicemi.

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Obálka pro **Datum**typu automatizace OLE Představuje hodnoty data a času.

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
Obálka pro **variantu**typu automatizace OLE Data v **variantě**se dají ukládat v mnoha formátech.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../mfc/class-library-overview.md)
