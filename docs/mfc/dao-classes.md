---
title: DAO – třídy
ms.date: 11/04/2016
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: 238aab0a1948f16a85b8ea16719b75b49f5e69c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241598"
---
# <a name="dao-classes"></a>DAO – třídy

Tyto třídy fungují s další aplikace tříd rozhraní framework a poskytovat snadný přístup k databázím objekt přístup k datům (DAO), které používají stejný databázový stroj jako Microsoft Visual Basic a aplikace Microsoft Access. DAO – třídy se dostanete také širokou škálu databází, pro které jsou k dispozici ovladače připojení ODBC (Open Database).

Programy, které používají rozhraní DAO databáze bude mít alespoň `CDaoDatabase` objektu a `CDaoRecordset` objektu.

> [!NOTE]
>  Prostředí Visual C++ a průvodců už nebude podporovat rozhraní DAO (i když jsou součástí třídy DAO a můžete stále použít). Společnost Microsoft doporučuje použití rozhraní ODBC pro nové projekty MFC. DAO byste měli používat jenom v udržování existujících aplikací.

[CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)<br/>
Spravuje relace s názvem databáze chráněné heslem od přihlášení po odhlášení. Většina aplikací pomocí výchozího pracovního prostoru.

[CDaoDatabase](../mfc/reference/cdaodatabase-class.md)<br/>
Připojení k databázi, pomocí které můžete pracovat s daty.

[CDaoRecordset](../mfc/reference/cdaorecordset-class.md)<br/>
Představuje sadu záznamů ze zdroje dat vybrané.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Zobrazení, které zobrazuje záznamy databáze v ovládacích prvcích.

[CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)<br/>
Představuje definici dotazu, obvykle jeden uložený v databázi.

[CDaoTableDef](../mfc/reference/cdaotabledef-class.md)<br/>
Představuje uloženou definici základní tabulky nebo připojené tabulky.

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
Představuje podmínku výjimky vyplývající z tříd DAO.

[CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)<br/>
Podporuje rutiny (DFX) systému exchange pole záznamu DAO používané databázové třídy DAO. Obvykle použijete přímo do této třídy.

## <a name="related-classes"></a>Související třídy

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
Zapouzdřuje popisovač úložiště pro binární velkých objektů (BLOB), jako je například rastrový obrázek. `CLongBinary` objekty se používají ke správě velkých datových objektů uložených v databázových tabulek.

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
Obálka pro typ automatizace OLE **měny**, s pevnou desetinnou čárkou aritmetického typu, s 15 číslic od desetinné čárky a po 4 číslice.

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Obálka pro typ automatizace OLE **datum**. Představuje hodnoty data a času.

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
Obálka pro typ automatizace OLE **VARIANT**. Data v **VARIANT**s mohou být uloženy v mnoha formátech.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../mfc/class-library-overview.md)
