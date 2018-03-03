---
title: "Datové objekty a zdroje dat: manipulace s | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- data objects [MFC], manipulating
- data sources [MFC], data operations
- data sources [MFC], inserting data
- Clipboard [MFC], determining available formats
- OLE [MFC], data objects
- Clipboard [MFC], passing format information
- data sources [MFC], determining available formats
- delayed rendering [MFC]
- OLE [MFC], data sources
ms.assetid: f7f27e77-bb5d-4131-b819-d71bf929ebaf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 40bd83b2e472ff1b1e5d277c27a801b0750fb160
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="data-objects-and-data-sources-manipulation"></a>Datové objekty a zdroje dat: Manipulace
Po vytvoření objektu dat nebo zdroj dat, můžete provést několik běžných operací na data, jako je například vkládání a odstraňování dat, vytváření výčtu formáty, které je v datech, a další. Tento článek popisuje techniky, které jsou potřebné k dokončení většiny běžných operací. Témata zahrnují:  
  
-   [Vložení dat do zdroje dat](#_core_inserting_data_into_a_data_source)  
  
-   [Zjišťování k dispozici v objektu data formátů](#_core_determining_the_formats_available_in_a_data_object)  
  
-   [Načítání dat z dat objektu](#_core_retrieving_data_from_a_data_object)  
  
##  <a name="_core_inserting_data_into_a_data_source"></a>Vložení dat do zdroje dat  
 Jak data se vloží do zdroje dat závisí na okamžitě zadaná data nebo na vyžádání a které střední pochází. Možnosti jsou následující.  
  
### <a name="supplying-data-immediately-immediate-rendering"></a>Zadávání dat okamžitě (okamžitou vykreslování)  
  
-   Volání `COleDataSource::CacheGlobalData` opakovaně pro každý formát schránky, ve kterém jsou zadávání data. Předat schránky formát, který se použije, popisovač pro paměť obsahující data a volitelně **FORMATETC** struktura popisující data.  
  
     -nebo-  
  
-   Pokud chcete pracovat přímo s **STGMEDIUM** struktury, zavoláte `COleDataSource::CacheData` místo `COleDataSource::CacheGlobalData` v výše uvedené možnosti.  
  
### <a name="supplying-data-on-demand-delayed-rendering"></a>Zadávání dat na vyžádání (odložené vykreslování)  
 To je rozšířená.  
  
-   Volání `COleDataSource::DelayRenderData` opakovaně pro každý formát schránky, ve kterém jsou zadávání data. Předat formát schránky má být použit a volitelně **FORMATETC** struktura popisující data. Pokud se požaduje data, bude volat rozhraní `COleDataSource::OnRenderData`, které je nutné přepsat.  
  
     -nebo-  
  
-   Pokud používáte `CFile` objekt, který chcete zadat data, volání `COleDataSource::DelayRenderFileData` místo `COleDataSource::DelayRenderData` v předchozí možnosti. Pokud se požaduje data, bude volat rozhraní `COleDataSource::OnRenderFileData`, které je nutné přepsat.  
  
##  <a name="_core_determining_the_formats_available_in_a_data_object"></a>Zjišťování k dispozici v objektu Data formátů  
 Předtím, než aplikace umožňuje uživatelům vkládat data do ní, je nutné vědět, pokud se do schránky, který může zpracovat formáty. K tomu, vaše aplikace by měla takto:  
  
1.  Vytvoření `COleDataObject` objektu a **FORMATETC** struktura.  
  
2.  Volání datový objekt `AttachClipboard` – členská funkce na datový objekt přidružit data do schránky.  
  
3.  Proveďte jednu z těchto akcí:  
  
    -   Volání datový objekt `IsDataAvailable` – členská funkce, pokud máte pouze jeden nebo dva formáty, je nutné. Tím se ušetřit čas v případech, kdy data do schránky podporuje podstatně více formátů, než aplikace.  
  
         -nebo-  
  
    -   Volání datový objekt `BeginEnumFormats` – členská funkce začne formáty, které jsou k dispozici do schránky. Potom zavolejte `GetNextFormat` dokud schránky vrátí podporuje formátu aplikace nebo neexistují žádné další formáty.  
  
 Pokud používáte `ON_UPDATE_COMMAND_UI`, teď můžete povolit vložení a případně i Vložit jinak položky v nabídce Upravit. Chcete-li to provést, volejte buď `CMenu::EnableMenuItem` nebo `CCmdUI::Enable`. Další informace o jaké kontejneru by měla aplikace provést pomocí položky nabídky a když, najdete v části [nabídky a prostředky: kontejnerové doplňky](../mfc/menus-and-resources-container-additions.md).  
  
##  <a name="_core_retrieving_data_from_a_data_object"></a>Načítání dat z dat objektu  
 Jakmile jste se rozhodli formát dat, zbývá k načtení dat z datového objektu. K tomuto účelu se uživatel rozhodne kam umístit data a aplikace volá odpovídající funkce. Data budou k dispozici v jednom z následujících médií:  
  
|Střední|Funkce pro volání|  
|------------|----------------------|  
|Globální paměť (`HGLOBAL`)|`COleDataObject::GetGlobalData`|  
|Soubor (`CFile`)|`COleDataObject::GetFileData`|  
|**STGMEDIUM** struktury (`IStorage`)|`COleDataObject::GetData`|  
  
 Médium se nejčastěji, zadat společně s jeho formát schránky. Například **CF_EMBEDDEDSTRUCT** objekt je vždy `IStorage` střední, která vyžaduje **STGMEDIUM** struktura. Proto byste použili `GetData` protože se jedná pouze jeden z těchto funkcí, které může přijmout **STGMEDIUM** struktury.  
  
 Pro případy, kdy formát schránky v `IStream` nebo `HGLOBAL` střední, můžete zadat rozhraní `CFile` ukazatele, který se odkazuje na data. Aplikace pak můžete použít soubor přečíst a získat data prakticky stejně jako ho může import dat ze souboru. To je v podstatě rozhraní na straně klienta `OnRenderData` a `OnRenderFileData` rutiny v datovém zdroji.  
  
 Uživatel může nyní vložení dat do dokumentu stejně jako pro ostatní data ve stejném formátu.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Přetažení](../mfc/drag-and-drop-ole.md)  
  
-   [Schránka](../mfc/clipboard.md)  
  
## <a name="see-also"></a>Viz také  
 [Datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md)   
 [COleDataObject – třída](../mfc/reference/coledataobject-class.md)   
 [COleDataSource – třída](../mfc/reference/coledatasource-class.md)
