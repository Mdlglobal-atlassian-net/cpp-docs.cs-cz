---
title: 'Sada záznamů: Dynamické vazby datových sloupců (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets [C++], binding columns dynamically
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- columns [C++], binding to recordsets
ms.assetid: bff67254-d953-4ae4-9716-91c348cb840b
ms.openlocfilehash: e26e62b0e8d613c1a09b077e3bf8d01d1eabba66
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367054"
---
# <a name="recordset-dynamically-binding-data-columns-odbc"></a>Sada záznamů: Dynamické vazby datových sloupců (ODBC)

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

Sady záznamů spravují sloupce tabulky vazeb, které zadáte v době návrhu, ale existují případy, kdy můžete chtít svázat sloupce, které jste v době návrhu neznali. Toto téma vysvětluje:

- [Pokud budete chtít dynamicky svázat sloupce se sadou záznamů](#_core_when_you_might_bind_columns_dynamically).

- [Jak dynamicky svázat sloupce za běhu](#_core_how_to_bind_columns_dynamically).

> [!NOTE]
> Toto téma se vztahuje `CRecordset` na objekty odvozené od, ve kterém hromadné načítání řádků nebyla implementována. Popsané techniky obecně se nedoporučuje, pokud používáte hromadné načítání řádků. Další informace o hromadném načítání řádků naleznete v tématu [Recordset: Fetching Records in Bulk (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

## <a name="when-you-might-bind-columns-dynamically"></a><a name="_core_when_you_might_bind_columns_dynamically"></a>Dynamické vazby sloupců

> [!NOTE]
> Průvodce příjemcem knihovny MFC ODBC není k dispozici v sadě Visual Studio 2019 a novějších. Stále můžete vytvořit příjemce ručně.

V době návrhu průvodce aplikací knihovny MFC nebo [Průvodce vytvořením služby MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (z **přidat třídu)** vytvoří třídy sady záznamů založené na známých tabulkách a sloupcích ve zdroji dat. Databáze můžete změnit mezi při jejich návrhu a později, když vaše aplikace používá tyto tabulky a sloupce za běhu. Vy nebo jiný uživatel můžete přidat nebo přetáhnout tabulku nebo přidat nebo přetáhnout sloupce z tabulky, na kterou závisí sada záznamů vaší aplikace. To pravděpodobně není problém pro všechny aplikace pro přístup k datům, ale pokud je to pro vás, jak se můžete vyrovnat se změnami ve schématu databáze, než redesignem a rekompilací? Účelem tohoto tématu je odpovědět na tuto otázku.

Toto téma popisuje nejběžnější případ, ve kterém můžete svázat sloupce dynamicky – po zahájení sesadou záznamů na základě známého schématu databáze, chcete zpracovat další sloupce za běhu. Téma dále předpokládá, že další `CString` sloupce mapovat na členy dat pole, nejběžnější případ, i když návrhy jsou dodávány, které vám pomohou spravovat jiné datové typy.

S malým množstvím kódu navíc můžete:

- [Určete, jaké sloupce jsou k dispozici za běhu](#_core_how_to_bind_columns_dynamically).

- [Dynamicky spojte další sloupce se sadou záznamů za běhu](#_core_adding_the_columns).

Sada záznamů stále obsahuje datové členy pro sloupce, o kterých jste věděli v době návrhu. Obsahuje také malé množství kódu navíc, který dynamicky určuje, zda byly do cílové tabulky přidány nové sloupce, a pokud ano, sváže tyto nové sloupce s dynamicky přiděleným úložištěm (spíše než pro členy datové sady záznamů).

Toto téma se nevztahuje na jiné případy dynamické vazby, jako jsou například vynechané tabulky nebo sloupce. V těchto případech je třeba použít volání rozhraní API ROZHRANÍ ODBC příměji. Další informace naleznete v příručce ODBC SDK *Programmer's Reference* na disku CD-ROM knihovny MSDN.

## <a name="how-to-bind-columns-dynamically"></a><a name="_core_how_to_bind_columns_dynamically"></a>Dynamické svázání sloupců

Chcete-li sloupce dynamicky svázat, musíte znát (nebo být schopni určit) názvy dalších sloupců. Je také nutné přidělit úložiště pro další datové členy pole, zadat jejich názvy a jejich typy a zadat počet sloupců, které přidáváte.

Následující diskuse zmiňuje dvě různé sady záznamů. První je hlavní sada záznamů, která vybírá záznamy z cílové tabulky. Druhým je speciální sada záznamů sloupců, která slouží k získání informací o sloupcích v cílové tabulce.

### <a name="general-process"></a><a name="_core_the_general_process"></a>Obecný proces

Na nejobecnější úrovni postupujte takto:

1. Vytvořte hlavní objekt sady záznamů.

   Volitelně můžete ukazatel předat `CDatabase` otevřenému objektu nebo být schopen poskytnout informace o připojení k sadě záznamů sloupce jiným způsobem.

1. Přidejte sloupce dynamicky.

   Podívejte se na proces popsaný v části Přidání sloupců níže.

1. Otevřete hlavní sadu záznamů.

   Sada záznamů vybere záznamy a použije výměnu pole záznamů (RFX) k vytvoření vazby jak statických sloupců (namapovaných na datové členy pole sady záznamů), tak dynamických sloupců (mapovaných na další úložiště, které přidělíte).

### <a name="adding-the-columns"></a><a name="_core_adding_the_columns"></a>Přidání sloupců

Dynamicky vazebné přidané sloupce za běhu vyžadují následující kroky:

1. Určete za běhu, jaké sloupce jsou v cílové tabulce. Extrahujte z těchto informací seznam sloupců, které byly přidány do tabulky od doby, kdy byla navržena třída sady záznamů.

   Dobrým přístupem je použití třídy sady záznamů sloupců určené k dotazování zdroje dat na informace o sloupci pro cílovou tabulku (například název sloupce a datový typ).

1. Poskytněte úložiště pro nové datové členy pole. Vzhledem k tomu, že hlavní třída sady záznamů nemá datové členy polí pro neznámé sloupce, je nutné zadat místo pro uložení názvů, hodnot výsledků a případně informací o datovém typu (pokud jsou sloupce různými datovými typy).

   Jedním z přístupů je vytvoření jednoho nebo více dynamických seznamů, jeden pro názvy nových sloupců, jiný pro jejich hodnoty výsledků a třetí pro jejich datové typy (v případě potřeby). Tyto seznamy, zejména seznam hodnot, poskytují informace a nezbytné úložiště pro vazbu. Následující obrázek znázorňuje vytváření seznamů.

   ![Vytváření seznamů sloupců, které mají být dynamicky svázány](../../data/odbc/media/vc37w61.gif "Vytváření seznamů sloupců, které mají být dynamicky svázány")<br/>
   Vytváření seznamů sloupců pro dynamickou vazbu

1. Přidejte volání funkce RFX do `DoFieldExchange` funkce hlavní sady záznamů pro každý přidaný sloupec. Tato volání RFX provést práci načítání záznamu, včetně dalších sloupců a vazby sloupce pro členy datové sady záznamů nebo dynamicky poskytované úložiště pro ně.

   Jedním z přístupů je přidání smyčky do `DoFieldExchange` funkce hlavní sady záznamů, která prochází seznam emitovaných nových sloupců a volá příslušnou funkci RFX pro každý sloupec v seznamu. Při každém volání RFX předejte název sloupce ze seznamu názvů sloupců a umístění úložiště v odpovídajícím členu seznamu hodnot výsledků.

### <a name="lists-of-columns"></a><a name="_core_lists_of_columns"></a>Seznamy sloupců

Čtyři seznamy, se kterými potřebujete pracovat, jsou uvedeny v následující tabulce.

|||
|-|-|
|**Sloupce aktuální tabulky**| (Seznam 1 na obrázku) Seznam sloupců, které jsou aktuálně v tabulce ve zdroji dat. Tento seznam se může shodovat se seznamem sloupců aktuálně vázaných v sadě záznamů.|
|**Vázané sady záznamů-sloupce**| (Seznam 2 na obrázku) Seznam sloupců vázaných v sadě záznamů. Tyto sloupce již mají příkazy RFX ve vaší `DoFieldExchange` funkci.|
|**Sloupce: Svázat dynamicky**| (Seznam 3 na obrázku) Seznam sloupců v tabulce, ale ne v sadě záznamů. Jedná se o sloupce, které chcete dynamicky svázat.|
|**Dynamické hodnoty sloupců**| (Seznam 4 na obrázku) Seznam obsahující úložiště pro hodnoty načtené ze sloupců, které dynamicky svážete. Prvky tohoto seznamu odpovídají těm v sloupce-k-bind-dynamicky, jeden k jednomu.|

### <a name="building-your-lists"></a><a name="_core_building_your_lists"></a>Vytváření seznamů

S ohledem na obecnou strategii se můžete obrátit na detaily. Postupy ve zbývající části tohoto tématu ukazují, jak vytvořit seznamy zobrazené v [seznamu sloupců](#_core_lists_of_columns). Postupy vás provedou:

- [Určení názvů sloupců, které nejsou v sadě záznamů](#_core_determining_which_table_columns_are_not_in_your_recordset).

- [Poskytuje dynamické úložiště pro sloupce nově přidané do tabulky](#_core_providing_storage_for_the_new_columns).

- [Dynamické přidávání RFX vyžaduje nové sloupce](#_core_adding_rfx_calls_to_bind_the_columns).

### <a name="determining-which-table-columns-are-not-in-your-recordset"></a><a name="_core_determining_which_table_columns_are_not_in_your_recordset"></a>Určení sloupců tabulky, které nejsou ve vaší sadě záznamů

Sestavte seznam (Vázaná sada záznamů-sloupce, jako v seznamu 2 na obrázku), který obsahuje seznam sloupců, které jsou již vázány v hlavní sadě záznamů. Pak vytvořte seznam (Sloupce na vazato dynamicky, odvozený z aktuálních sloupců tabulky a vázaných záznamů-sloupců), který obsahuje názvy sloupců, které jsou v tabulce ve zdroji dat, ale ne v hlavní sadě záznamů.

##### <a name="to-determine-the-names-of-columns-not-in-the-recordset-columns-to-bind-dynamically"></a>Chcete-li určit názvy sloupců, které nejsou v sadě záznamů (Sloupce-to-Bind-Dynamically)

1. Sestavte seznam (Vázaná sada záznamů-sloupce) sloupců, které jsou již vázány v hlavní sadě záznamů.

   Jedním z přístupů je vytvoření bound-recordset-columns v době návrhu. Můžete vizuálně prozkoumat volání funkce RFX ve `DoFieldExchange` funkci sady záznamů získat tyto názvy. Potom nastavte seznam jako pole inicializované s názvy.

   Například na obrázku je zobrazenbound-Recordset-Columns (Seznam 2) se třemi prvky. Vázaná sada záznamů-sloupce chybí sloupec Telefon zobrazený v aktuálních sloupcích tabulky (seznam 1).

1. Porovnejte aktuální sloupce tabulky a vázané-recordset-sloupce vytvořit seznam (sloupce-k-bind-dynamicky) sloupců, které již nejsou vázány v hlavní sadě záznamů.

   Jedním z přístupů je procházet seznam sloupců v tabulce za běhu (Aktuální tabulka-sloupce) a seznam sloupců, které jsou již vázány ve vaší sadě záznamů (Vázaná sada záznamů-sloupce) paralelně. Do sloupců na vazbu dynamicky umístit všechny názvy v aktuální tabulka sloupce, které se nezobrazují v Vázané-Recordset-Sloupce.

   Na příklad obrázek znázorňuje sloupce na vazbu dynamicky (seznam 3) s jedním prvkem: sloupec Telefon nalezený v aktuálních sloupcích tabulky (seznam 1), ale ne ve sloupcích vázaná sada záznamů (seznam 2).

1. Sestavte seznam dynamických hodnot sloupců (jako v seznamu 4 na obrázku), ve kterém se budou ukládat datové hodnoty odpovídající každému názvu sloupce uloženému v seznamu sloupců, které mají být dynamicky vvázány (Sloupce s vazbou dynamicky).

   Prvky tohoto seznamu hrají roli nových datových členů pole sady záznamů. Jedná se o umístění úložiště, ke kterým jsou dynamické sloupce vázány. Popis seznamů naleznete v [tématu Seznamy sloupců](#_core_lists_of_columns).

### <a name="providing-storage-for-the-new-columns"></a><a name="_core_providing_storage_for_the_new_columns"></a>Poskytování úložiště pro nové sloupce

Dále nastavte umístění úložiště pro sloupce, které mají být dynamicky vázány. Cílem je poskytnout prvek seznamu, do kterého chcete uložit hodnotu každého sloupce. Tato umístění úložiště paralelně proměnné člena sady záznamů, které ukládají normálně vázané sloupce.

#### <a name="to-provide-dynamic-storage-for-new-columns-dynamic-column-values"></a>Poskytnutí dynamického úložiště pro nové sloupce (dynamic-column-values)

1. Vytvořte dynamicky sloupcové hodnoty, rovnoběžné se sloupci na vaza-dynamicky, aby obsahovaly hodnotu dat v každém sloupci.

   Na příklad znázorněno dynamické hodnoty sloupců (seznam 4) `CString` s jedním elementem: objekt obsahující skutečné telefonní číslo pro aktuální záznam: "555-1212".

   V nejběžnějším případě dynamické hodnoty sloupců má `CString`prvky typu . Pokud máte co do činění se sloupci různých datových typů, potřebujete seznam, který může obsahovat prvky různých typů.

Výsledkem předchozích postupů jsou dva hlavní seznamy: Sloupce s vazbou dynamicky obsahující názvy sloupců a Dynamické hodnoty sloupců obsahující hodnoty ve sloupcích pro aktuální záznam.

> [!TIP]
> Pokud nové sloupce nejsou všechny stejného datového typu, můžete chtít další paralelní seznam obsahující položky, které nějakým způsobem definovat typ každého odpovídajícího prvku v seznamu sloupců. (Můžete použít hodnoty AFX_RFX_BOOL, AFX_RFX_BYTE a tak dále, pokud chcete. Tyto konstanty jsou definovány v AFXDB. H.) Zvolte typ seznamu na základě toho, jak reprezentujete datové typy sloupců.

### <a name="adding-rfx-calls-to-bind-the-columns"></a><a name="_core_adding_rfx_calls_to_bind_the_columns"></a>Přidání volání RFX k vazby sloupců

Nakonec uspořádejte dynamickou vazbu, která má nastat `DoFieldExchange` umístěním volání RFX pro nové sloupce ve vaší funkci.

##### <a name="to-dynamically-add-rfx-calls-for-new-columns"></a>Dynamické přidávání volání RFX pro nové sloupce

1. V `DoFieldExchange` členské funkci hlavní sady záznamů přidejte kód, který prochází seznamem nových sloupců (Sloupce s vazbou dynamicky). V každé smyčce extrahujte název sloupce ze sloupce na vazbu dynamicky a výslednou hodnotu pro sloupec z dynamické hodnoty sloupce. Předejte tyto položky volání funkce RFX odpovídající datovému typu sloupce. Popis seznamů naleznete v [tématu Seznamy sloupců](#_core_lists_of_columns).

V běžném případě `RFX_Text` ve vaší `CString` funkce volání extrahovat objekty ze seznamů, jako v následujících `CStringList` řádcích kódu, kde Columns-to-Bind-Dynamically je volána `m_listName` a dynamic-column-hodnoty je `CStringList` nazývána `m_listValue`:

```cpp
RFX_Text( pFX,
            m_listName.GetNext( posName ),
            m_listValue.GetNext( posValue ));
```

Další informace o funkcích RFX naleznete v [tématu Makra a globální](../../mfc/reference/mfc-macros-and-globals.md) soubory v *odkazu knihovny tříd*.

> [!TIP]
> Pokud nové sloupce jsou různé datové typy, použijte příkaz switch ve smyčce k volání příslušné funkce RFX pro každý typ.

Při volání `DoFieldExchange` rozhraní `Open` během procesu svázat sloupce na sadu záznamů, RFX volání statické sloupce vázat tyto sloupce. Potom smyčka opakovaně volá funkce RFX pro dynamické sloupce.

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Práce s velkými datovými položkami (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)
