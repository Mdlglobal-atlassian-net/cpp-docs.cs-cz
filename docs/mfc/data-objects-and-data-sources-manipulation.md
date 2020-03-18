---
title: 'Datové objekty a zdroje dat: Manipulace'
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
ms.openlocfilehash: adbe2a77fb0069e9874ab20a51b3ab08aabbe1f6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446999"
---
# <a name="data-objects-and-data-sources-manipulation"></a>Datové objekty a zdroje dat: Manipulace

Po vytvoření datového objektu nebo zdroje dat můžete provádět řadu běžných operací s daty, jako je vkládání a odebírání dat, vytváření výčtu formátů dat a další. Tento článek popisuje techniky nezbytné k dokončení nejběžnějších operací. Témata:

- [Vložení dat do zdroje dat](#_core_inserting_data_into_a_data_source)

- [Určení formátů dostupných v datovém objektu](#_core_determining_the_formats_available_in_a_data_object)

- [Načítání dat z datového objektu](#_core_retrieving_data_from_a_data_object)

##  <a name="_core_inserting_data_into_a_data_source"></a>Vložení dat do zdroje dat

Způsob vložení dat do zdroje dat závisí na tom, zda jsou data dodávána okamžitě nebo na vyžádání a v případě, že je dodána. Možnosti jsou následující.

### <a name="supplying-data-immediately-immediate-rendering"></a>Okamžité poskytnutí dat (okamžité vykreslování)

- Pro každý formát schránky, ve kterém jsou data dodávána, zavolejte `COleDataSource::CacheGlobalData` opakovaně. Předejte formát schránky, který se má použít, popisovač paměti obsahující data a volitelně i strukturu **FORMATETC** popisující data.

     -nebo-

- Pokud chcete pracovat přímo s **STGMEDIUM** strukturami, zavoláte `COleDataSource::CacheData` místo `COleDataSource::CacheGlobalData` v možnosti výše.

### <a name="supplying-data-on-demand-delayed-rendering"></a>Zadávání dat na vyžádání (zpožděné vykreslování)

Toto je pokročilé téma.

- Pro každý formát schránky, ve kterém jsou data dodávána, zavolejte `COleDataSource::DelayRenderData` opakovaně. Předejte formát schránky, který se má použít, a volitelně strukturu **FORMATETC** popisující data. Po vyžádání dat rozhraní zavolá `COleDataSource::OnRenderData`, které je nutné přepsat.

     -nebo-

- Použijete-li objekt `CFile` k poskytnutí dat, zavolejte `COleDataSource::DelayRenderFileData` namísto `COleDataSource::DelayRenderData` v předchozí možnosti. Po vyžádání dat rozhraní zavolá `COleDataSource::OnRenderFileData`, které je nutné přepsat.

##  <a name="_core_determining_the_formats_available_in_a_data_object"></a>Určení formátů dostupných v datovém objektu

Předtím, než aplikace umožní uživateli vložit do něj data, musí zjistit, jestli ve schránce existují formáty, které může zpracovat. K tomu by měla aplikace provádět následující akce:

1. Vytvořte objekt `COleDataObject` a strukturu **FORMATETC** .

1. Chcete-li přidružit datový objekt k datům ve schránce, zavolejte `AttachClipboard` členskou funkci datového objektu.

1. Proveďte jednu z těchto akcí:

   - Pokud je k dispozici pouze jeden nebo dva formáty, zavolejte `IsDataAvailable` členskou funkci datového objektu. Ušetříte tím čas v případech, kdy data ve schránce podporují výrazně více formátů než vaše aplikace.

     \-nebo-

   - Chcete-li spustit výčet formátů dostupných ve schránce, zavolejte členskou funkci datového objektu `BeginEnumFormats`. Potom zavolejte `GetNextFormat`, dokud schránka nevrátí formát, který vaše aplikace podporuje, nebo nejsou žádné další formáty.

Pokud používáte **ON_UPDATE_COMMAND_UI**, můžete teď v nabídce Upravit povolit speciální položky vložit a případně vložit. Chcete-li to provést, zavolejte buď `CMenu::EnableMenuItem`, nebo `CCmdUI::Enable`. Další informace o tom, jaké aplikace kontejneru by měly provádět s položkami nabídky a kdy, naleznete v tématech [nabídky a prostředky: Přidání kontejneru](../mfc/menus-and-resources-container-additions.md).

##  <a name="_core_retrieving_data_from_a_data_object"></a>Načítání dat z datového objektu

Jakmile se rozhodnete pro formát dat, vše zůstává k načtení dat z datového objektu. K tomu se uživatel rozhodne, kam se mají data vložit, a aplikace zavolá příslušnou funkci. Data budou k dispozici v jednom z následujících středních údajů:

|Střednědobé používání|Volání funkce|
|------------|----------------------|
|Globální paměť (`HGLOBAL`)|`COleDataObject::GetGlobalData`|
|Soubor (`CFile`)|`COleDataObject::GetFileData`|
|Struktura **STGMEDIUM** (`IStorage`)|`COleDataObject::GetData`|

Obvykle bude médium zadáno spolu s formátem schránky. Například objekt **CF_EMBEDDEDSTRUCT** je vždy v `IStorage`m médiu, které vyžaduje strukturu **STGMEDIUM** . Proto byste použili `GetData`, protože se jedná o jedinou jednu z těchto funkcí, které mohou přijmout strukturu **STGMEDIUM** .

V případech, kdy je formát schránky ve `IStream` nebo `HGLOBAL`m médiu, může rozhraní poskytnout `CFile` ukazatel, který odkazuje na data. Aplikace pak může použít čtení souborů k získání dat v podstatě stejným způsobem, jako by mohla importovat data ze souboru. V podstatě se jedná o rozhraní na straně klienta pro `OnRenderData` a `OnRenderFileData` rutiny ve zdroji dat.

Uživatel teď může do dokumentu vložit data stejně jako pro jiná data ve stejném formátu.

### <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- [Přetažení](../mfc/drag-and-drop-ole.md)

- [Schránka](../mfc/clipboard.md)

## <a name="see-also"></a>Viz také

[Datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject – třída](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource – třída](../mfc/reference/coledatasource-class.md)
