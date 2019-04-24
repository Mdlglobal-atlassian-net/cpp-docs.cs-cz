---
title: 'Datové objekty a zdroje dat: Manipulace s'
ms.date: 11/04/2016
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
ms.openlocfilehash: 81dfe911866c4d1ba1720ee2c9854076c499f0a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241546"
---
# <a name="data-objects-and-data-sources-manipulation"></a>Datové objekty a zdroje dat: Manipulace s

Po vytvoření datového objektu nebo zdroj dat, můžete provádět řadu běžných operací na data, jako je například vkládání a odstraňování dat, vytváření výčtu formátů, ve kterém data nachází, a další. Tento článek popisuje postupy nezbytné pro dokončení nejběžnějších operací. Mezi témata patří:

- [Vložení dat do zdroje dat.](#_core_inserting_data_into_a_data_source)

- [Určení formátů v datovém objektu](#_core_determining_the_formats_available_in_a_data_object)

- [Načítání dat z datového objektu](#_core_retrieving_data_from_a_data_object)

##  <a name="_core_inserting_data_into_a_data_source"></a> Vložení dat do zdroje dat.

Jak vložení dat do zdroje dat závisí na okamžitě zadaná data nebo na vyžádání a které střední pochází. Tyto možnosti jsou následující.

### <a name="supplying-data-immediately-immediate-rendering"></a>Zadávání dat okamžitě (okamžité vykreslování)

- Volání `COleDataSource::CacheGlobalData` opakovaně pro každý formát schránky, ve kterém jsou poskytující data. Předejte formát schránky, kterou chcete použít popisovač paměť obsahující data a volitelně **FORMATETC** struktura popisující data.

     -nebo-

- Pokud budete chtít pracovat přímo s **STGMEDIUM** struktury, voláte `COleDataSource::CacheData` místo `COleDataSource::CacheGlobalData` ve výše uvedené možnosti.

### <a name="supplying-data-on-demand-delayed-rendering"></a>Zadávání dat na vyžádání (odložené vykreslování)

Toto je rozšířená.

- Volání `COleDataSource::DelayRenderData` opakovaně pro každý formát schránky, ve kterém jsou poskytující data. Předejte formát schránky, který se má použít a volitelně **FORMATETC** struktura popisující data. Pokud se požaduje data, bude volat rozhraní framework `COleDataSource::OnRenderData`, které je nutné přepsat.

     -nebo-

- Pokud používáte `CFile` objekt slouží k poskytování dat, volání `COleDataSource::DelayRenderFileData` místo `COleDataSource::DelayRenderData` v předchozí možnosti. Pokud se požaduje data, bude volat rozhraní framework `COleDataSource::OnRenderFileData`, které je nutné přepsat.

##  <a name="_core_determining_the_formats_available_in_a_data_object"></a> Určení formátů v datovém objektu

Předtím, než aplikace umožňuje uživatelům dat vložte do něj, je potřeba vědět, pokud jsou formáty schránky, který dokáže zpracovat. K tomuto účelu by měla vaše aplikace postupujte takto:

1. Vytvoření `COleDataObject` objektu a **FORMATETC** struktury.

1. Datový objekt volat `AttachClipboard` členskou funkci na datový objekt přidružit data do schránky.

1. Proveďte jednu z těchto akcí:

   - Datový objekt volat `IsDataAvailable` členskou funkci, pokud existuje pouze jedna nebo dvě formáty, budete potřebovat. Tím se ušetří vám čas v případech, kdy data do schránky podporuje podstatně více formátů než vaší aplikace.

         -or-

   - Datový objekt volat `BeginEnumFormats` členskou funkci začne formáty, které jsou k dispozici do schránky. Poté zavolejte `GetNextFormat` až do schránky vrátí formátu vaše aplikace podporuje nebo neexistují žádné další formáty.

Pokud používáte **ON_UPDATE_COMMAND_UI**, teď můžete povolit vložení a případně i Vložit jinak položky v nabídce Úpravy. K tomuto účelu volání `CMenu::EnableMenuItem` nebo `CCmdUI::Enable`. Další informace o jaké kontejneru by aplikace provést pomocí položky nabídky a když, naleznete v tématu [nabídky a prostředky: Kontejnerové doplňky](../mfc/menus-and-resources-container-additions.md).

##  <a name="_core_retrieving_data_from_a_data_object"></a> Načítání dat z datového objektu

Až se rozhodnete na formát dat už jen zbývá k načtení dat z datového objektu. Provedete to tak, že se uživatel rozhodne kam chcete umístit data a aplikace volá příslušnou funkci. Data budou k dispozici v jednom z následujících médii:

|Střední|Funkce pro volání|
|------------|----------------------|
|Globální paměť (`HGLOBAL`)|`COleDataObject::GetGlobalData`|
|Soubor (`CFile`)|`COleDataObject::GetFileData`|
|**STGMEDIUM** strukturu (`IStorage`)|`COleDataObject::GetData`|

Médium se nejčastěji, zadat společně s jeho formát schránky. Například **CF_EMBEDDEDSTRUCT** objektu je vždy v `IStorage` médium, které vyžaduje **STGMEDIUM** struktury. Proto byste použili `GetData` vzhledem k tomu, že je jenom jedna z těchto funkcí, které může přijmout **STGMEDIUM** struktury.

Pro případy, kdy formát schránky v `IStream` nebo `HGLOBAL` střední, můžete zadat rozhraní framework `CFile` ukazatel, který odkazuje na data. Aplikace pak můžete použít soubor přečíst a získat data prakticky stejně jako ji může import dat ze souboru. To je v podstatě rozhraní na straně klienta `OnRenderData` a `OnRenderFileData` rutiny ve zdroji dat.

Uživatel může nyní vložit data do dokumentu stejně jako u jiných dat ve stejném formátu.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Přetáhnout myší](../mfc/drag-and-drop-ole.md)

- [Schránka](../mfc/clipboard.md)

## <a name="see-also"></a>Viz také:

[Datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject – třída](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource – třída](../mfc/reference/coledatasource-class.md)
