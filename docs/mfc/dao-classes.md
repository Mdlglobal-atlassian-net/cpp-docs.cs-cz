---
title: "Třídy DAO | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.data
dev_langs:
- C++
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c80351071318b88956fa3717875561bdf30232dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="dao-classes"></a>DAO – třídy
Tyto třídy pracovat s další aplikace framework třídy poskytují snadný přístup k databázím objekt DAO (Data Access), které používají stejný databázový stroj Microsoft Visual Basic a Microsoft Access. Třídy DAO můžete také přístup k celé řadě databáze, pro které jsou k dispozici ovladače připojení ODBC (Open Database).  
  
 Programy, které používají rozhraní DAO databáze bude mít alespoň `CDaoDatabase` objektu a `CDaoRecordset` objektu.  
  
> [!NOTE]
>  Prostředí Visual C++ a průvodců již nepodporují rozhraní DAO (i když jsou zahrnuté třídy DAO a můžete je dál používat). Společnost Microsoft doporučuje použití rozhraní ODBC pro nové projekty MFC. DAO byste měli používat jenom pro údržbu existujících aplikací.  
  
 [CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)  
 Spravuje relace s názvem databáze chráněné heslem z přihlášení a odhlášení. Většina programů používá výchozí pracovní prostor.  
  
 [CDaoDatabase](../mfc/reference/cdaodatabase-class.md)  
 Připojení k databázi, pomocí kterého lze provozovat na data.  
  
 [CDaoRecordset](../mfc/reference/cdaorecordset-class.md)  
 Představuje sadu záznamy ze zdroje dat vybraná.  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 Zobrazení, které zobrazuje záznamy databáze v ovládacích prvcích.  
  
 [CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)  
 Představuje definici dotazu, obvykle 1, které jsou uloženy v databázi.  
  
 [CDaoTableDef](../mfc/reference/cdaotabledef-class.md)  
 Představuje definici uložené na základní tabulku nebo připojené tabulky.  
  
 [CDaoException](../mfc/reference/cdaoexception-class.md)  
 Představuje podmínku vyplývající z třídy DAO.  
  
 [CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)  
 Podporuje rutiny výměna pole záznamu exchange (DFX) používá databázové třídy DAO. Nejsou obvykle použijete přímo tuto třídu.  
  
## <a name="related-classes"></a>Související třídy  
 [CLongBinary](../mfc/reference/clongbinary-class.md)  
 Zapouzdří popisovač pro úložiště pro binární rozsáhlý objekt (BLOB), jako je například rastrový obrázek. `CLongBinary`objekty se používají ke správě objektů velkého množství dat uložených v tabulkách databáze.  
  
 [COleCurrency](../mfc/reference/colecurrency-class.md)  
 Obálka pro typ automatizace OLE **MĚNA**, s pevnou desetinnou čárkou aritmetické typu, s 15 číslic od desetinné čárky a po 4 číslice.  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)  
 Obálka pro typ automatizace OLE **datum**. Představuje hodnoty data a času.  
  
 [COleVariant](../mfc/reference/colevariant-class.md)  
 Obálka pro typ automatizace OLE **VARIANT**. Data v **VARIANT**s mohou být uloženy v mnoha různých formátech.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)

