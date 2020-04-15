---
title: DAO – třídy
ms.date: 09/17/2019
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: 7ae85cbeb7790cadb8c26dfbdb7a5163dbcd47c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373519"
---
# <a name="dao-classes"></a>DAO – třídy

DAO se používá s databázemi Accessu a je podporován prostřednictvím Office 2013. DAO 3.6 je konečná verze, a to je považováno za zastaralé.

Tyto třídy pracují s ostatními třídami architektury aplikace a poskytují snadný přístup k databázím DAO (Data Access Object), které používají stejný databázový stroj jako aplikace Microsoft Visual Basic a Microsoft Access. Třídy DAO mohou také přistupovat k široké škále databází, pro které jsou k dispozici ovladače připojení k otevřené databázi (ODBC).

Programy, které používají databáze DAO, `CDaoDatabase` budou `CDaoRecordset` mít alespoň objekt a objekt.

> [!NOTE]
> Prostředí Visual C++ a průvodci již nepodporují DAO (i když jsou zahrnuty třídy DAO a můžete je stále používat). Společnost Microsoft doporučuje použít rozhraní ODBC pro nové projekty knihovny MFC. DAO byste měli používat pouze při údržbě existujících aplikací.

[CDaoPracovní prostor](../mfc/reference/cdaoworkspace-class.md)<br/>
Spravuje pojmenované, heslem chráněné relace databáze od přihlášení k odhlášení. Většina programů používá výchozí pracovní prostor.

[Cdaodatabase](../mfc/reference/cdaodatabase-class.md)<br/>
Připojení k databázi, pomocí které můžete pracovat s daty.

[Cdaorecordset](../mfc/reference/cdaorecordset-class.md)<br/>
Představuje sadu záznamů vybraných ze zdroje dat.

[Cdaorecordview](../mfc/reference/cdaorecordview-class.md)<br/>
Zobrazení, které zobrazuje záznamy databáze v ovládacích prvcích.

[CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)<br/>
Představuje definici dotazu, obvykle jednu uloženou v databázi.

[CDaoTableDef](../mfc/reference/cdaotabledef-class.md)<br/>
Představuje uloženou definici základní tabulky nebo připojené tabulky.

[Výjimka CDao](../mfc/reference/cdaoexception-class.md)<br/>
Představuje podmínku výjimky vyplývající z tříd DAO.

[CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)<br/>
Podporuje rutiny výměny dat záznamu DAO (DFX) používané třídou databáze DAO. Obvykle nebudete přímo používat tuto třídu.

## <a name="related-classes"></a>Související třídy

[Clongbinary](../mfc/reference/clongbinary-class.md)<br/>
Zapouzdřuje popisovač do úložiště pro binární velký objekt (BLOB), například rastrový obrázek. `CLongBinary`objekty se používají ke správě velkých datových objektů uložených v databázových tabulkách.

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
Obálka pro typ automatizace OLE **CURRENCY**, aritmetický typ s pevnou desetinnou čárkou, s 15 číslicemi před desetinnou čárkou a 4 číslicemi za ním.

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Obálka pro automatizaci OLE typu **DATE**. Představuje hodnoty data a času.

[Varianta COle](../mfc/reference/colevariant-class.md)<br/>
Obálka pro automatizaci OLE typu **VARIANT**. Data v **variantách**s mohou být uložena v mnoha formátech.

## <a name="see-also"></a>Viz také

[Přehled třídy](../mfc/class-library-overview.md)
