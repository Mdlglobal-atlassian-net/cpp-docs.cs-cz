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
ms.openlocfilehash: a08b6ff274c73d301c156d65aa56fbecca49128c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370555"
---
# <a name="data-objects-and-data-sources-manipulation"></a>Datové objekty a zdroje dat: Manipulace

Po vytvoření datového objektu nebo zdroje dat můžete s daty provést řadu běžných operací, například vložit a odebrat data, vyjmenovat formáty, ve kterých se data nachází, a další. Tento článek popisuje techniky nezbytné k dokončení nejběžnější operace. Témata:

- [Vkládání dat do zdroje dat](#_core_inserting_data_into_a_data_source)

- [Určení formátů dostupných v datovém objektu](#_core_determining_the_formats_available_in_a_data_object)

- [Načítání dat z datového objektu](#_core_retrieving_data_from_a_data_object)

## <a name="inserting-data-into-a-data-source"></a><a name="_core_inserting_data_into_a_data_source"></a>Vložení dat do zdroje dat

Způsob vložení dat do zdroje dat závisí na tom, zda jsou data dodána okamžitě nebo na vyžádání a na jakém médiu jsou zadána. Možnosti jsou následující.

### <a name="supplying-data-immediately-immediate-rendering"></a>Okamžité dodání dat (okamžité vykreslování)

- Opakovaně `COleDataSource::CacheGlobalData` volat pro každý formát schránky, ve kterém zadávajíte data. Předejte formát schránky, který má být použit, popisovač paměti obsahující data a volitelně strukturu **FORMATETC** popisující data.

     -nebo-

- Pokud chcete pracovat přímo s **STGMEDIUM** struktury, `COleDataSource::CacheData` `COleDataSource::CacheGlobalData` volání namísto výše uvedené možnosti.

### <a name="supplying-data-on-demand-delayed-rendering"></a>Poskytování dat na vyžádání (zpožděné vykreslování)

Toto je pokročilé téma.

- Opakovaně `COleDataSource::DelayRenderData` volat pro každý formát schránky, ve kterém zadávajíte data. Předaj formát schránky, který má být použit, a volitelně strukturu **FORMATETC** popisující data. Pokud jsou požadována data, `COleDataSource::OnRenderData`bude volat rozhraní , které je nutné přepsat.

     -nebo-

- Pokud používáte `CFile` objekt k dodání `COleDataSource::DelayRenderFileData` dat, `COleDataSource::DelayRenderData` volání namísto v předchozí možnosti. Pokud jsou požadována data, `COleDataSource::OnRenderFileData`bude volat rozhraní , které je nutné přepsat.

## <a name="determining-the-formats-available-in-a-data-object"></a><a name="_core_determining_the_formats_available_in_a_data_object"></a>Určení formátů dostupných v datovém objektu

Předtím, než aplikace umožňuje uživateli vložit data do něj, musí vědět, zda existují formáty ve schránce, které může zpracovat. Chcete-li to provést, aplikace by měla provést následující akce:

1. Vytvořte `COleDataObject` objekt a strukturu **FORMATETC.**

1. Volání členské funkce `AttachClipboard` datového objektu k přidružení datového objektu k datům ve schránce.

1. Proveďte jednu z těchto akcí:

   - Volání členské funkce `IsDataAvailable` datového objektu, pokud existují pouze jeden nebo dva formáty, které potřebujete. To vám ušetří čas v případech, kdy data ve schránce podporují podstatně více formátů než vaše aplikace.

     \-nebo-

   - Volání členské funkce `BeginEnumFormats` datového objektu začít výčet formátů dostupných ve schránce. Pak `GetNextFormat` volání, dokud schránka vrátí formát aplikace podporuje nebo nejsou k dispozici žádné další formáty.

Pokud používáte **ON_UPDATE_COMMAND_UI**, můžete nyní povolit vložit a případně vložit speciální položky v nabídce Úpravy. Chcete-li to `CMenu::EnableMenuItem` provést, volejte buď nebo `CCmdUI::Enable`. Další informace o tom, co mají aplikace kontejnerů dělat s položkami nabídky a kdy, naleznete v [tématu Nabídky a prostředky: Přidání kontejneru](../mfc/menus-and-resources-container-additions.md).

## <a name="retrieving-data-from-a-data-object"></a><a name="_core_retrieving_data_from_a_data_object"></a>Načítání dat z datového objektu

Jakmile se rozhodnete pro formát dat, vše, co zbývá, je načíst data z datového objektu. Chcete-li to provést, uživatel rozhodne, kam umístit data a aplikace volá příslušnou funkci. Údaje budou k dispozici na jednom z následujících médií:

|Střednědobé používání|Funkce pro volání|
|------------|----------------------|
|Globální paměť`HGLOBAL`( )|`COleDataObject::GetGlobalData`|
|Soubor`CFile`( )|`COleDataObject::GetFileData`|
|**Struktura STGMEDIUM** (`IStorage`)|`COleDataObject::GetData`|

Obvykle bude médium zadáno spolu s formátem schránky. Například **CF_EMBEDDEDSTRUCT** objekt je vždy `IStorage` v médiu, které vyžaduje strukturu **STGMEDIUM.** Proto byste použít, `GetData` protože je pouze jedna z těchto funkcí, které mohou přijmout **stgmedium** strukturu.

V případech, kdy je formát `IStream` `HGLOBAL` schránky v nebo médium, může rozhraní poskytnout `CFile` ukazatel, který odkazuje na data. Aplikace pak může použít soubor číst získat data v podstatě stejným způsobem, jak by mohla importovat data ze souboru. V podstatě se jedná o `OnRenderData` rozhraní `OnRenderFileData` na straně klienta a rutiny ve zdroji dat.

Uživatel nyní může do dokumentu vkládat data stejně jako u jiných dat ve stejném formátu.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Přetažení](../mfc/drag-and-drop-ole.md)

- [Schránka](../mfc/clipboard.md)

## <a name="see-also"></a>Viz také

[Datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject – třída](../mfc/reference/coledataobject-class.md)<br/>
[Třída COleDataSource](../mfc/reference/coledatasource-class.md)
