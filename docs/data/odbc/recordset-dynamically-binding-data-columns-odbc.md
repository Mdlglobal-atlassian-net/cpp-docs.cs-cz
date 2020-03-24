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
ms.openlocfilehash: 456d999a056abc4c15f2dcf3b8774dfc86182272
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212924"
---
# <a name="recordset-dynamically-binding-data-columns-odbc"></a>Sada záznamů: Dynamické vazby datových sloupců (ODBC)

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

Sady záznamů spravují sloupce vazeb vazeb, které zadáte v době návrhu, ale v některých případech můžete chtít svázat sloupce, které byly pro vás v době návrhu neznámy. Toto téma vysvětluje:

- [V případě, že můžete chtít dynamicky navazovat sloupce do sady záznamů](#_core_when_you_might_bind_columns_dynamically).

- [Jak dynamicky navazovat sloupce v době běhu](#_core_how_to_bind_columns_dynamically).

> [!NOTE]
>  Toto téma se vztahuje na objekty odvozené od `CRecordset`, ve kterých nebylo implementováno hromadné načítání řádků. Obecně popsané techniky nejsou doporučovány, pokud používáte hromadné načítání řádků. Další informace o hromadném načítání řádků naleznete v tématu [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="when-you-might-bind-columns-dynamically"></a><a name="_core_when_you_might_bind_columns_dynamically"></a>Když je možné dynamicky navazovat sloupce

> [!NOTE]
> Průvodce příjemcem knihovny MFC rozhraní ODBC není dostupný v aplikaci Visual Studio 2019 a novějším. Příjemce můžete přesto vytvořit ručně.

V době návrhu, Průvodce aplikací knihovny MFC nebo [Průvodce příjemcem rozhraní ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (z **Přidat třídu**) vytvoří třídy sady záznamů založené na známých tabulkách a sloupcích ve zdroji dat. Databáze se mohou měnit mezi návrhem a později, když aplikace používá tyto tabulky a sloupce za běhu. Vy nebo jiný uživatel můžete přidat nebo vyřadit tabulku nebo přidat nebo vyřadit sloupce z tabulky, na které závisí vaše sada záznamů vaší aplikace. To pravděpodobně není obavou pro všechny aplikace pro přístup k datům, ale pokud je pro vás, jak se můžete vypořádat se změnami ve schématu databáze, než přenavrhování a rekompilace? Účelem tohoto tématu je odpovědět na tuto otázku.

Toto téma popisuje nejběžnější případ, ve kterém můžete dynamicky navazovat sloupce, které začaly sadou záznamů založenou na známém schématu databáze, chcete v době běhu zpracovávat další sloupce. Téma dále předpokládá, že další sloupce jsou mapovány na `CString` datových členů, Nejběžnější případ, i když jsou k dispozici návrhy, které vám pomůžou se správou jiných datových typů.

S malým množstvím dalšího kódu můžete:

- [Určete, jaké sloupce jsou k dispozici v době běhu](#_core_how_to_bind_columns_dynamically).

- [Navázání dalších sloupců do vaší sady záznamů dynamicky v době běhu](#_core_adding_the_columns).

Vaše sada záznamů stále obsahuje datové členy pro sloupce, o kterých jste věděli v době návrhu. Obsahuje také malé množství speciálního kódu, který dynamicky určuje, zda byly do cílové tabulky přidány nějaké nové sloupce, a pokud ano, sváže tyto nové sloupce s dynamicky přiděleným úložištěm (nikoli k datovým členům sady záznamů).

Toto téma se nezabývá dalšími případy dynamické vazby, jako jsou například vyřazené tabulky nebo sloupce. V takových případech je nutné použít volání rozhraní API ODBC přímo. Informace najdete v tématu *Referenční příručka programátora* rozhraní ODBC SDK na disku CD knihovny MSDN.

##  <a name="how-to-bind-columns-dynamically"></a><a name="_core_how_to_bind_columns_dynamically"></a>Jak dynamicky navazovat sloupce

Chcete-li dynamicky navazovat sloupce, musíte znát (nebo být schopni určit) názvy dalších sloupců. Pro další pole datových členů musíte také přidělit úložiště, zadat jejich názvy a jejich typy a zadat počet sloupců, které přidáváte.

Následující diskuze uvádí dvě různé sady záznamů. První je hlavní sada záznamů, která vybere záznamy z cílové tabulky. Druhým je speciální sada záznamů, která se používá k získání informací o sloupcích v cílové tabulce.

###  <a name="general-process"></a><a name="_core_the_general_process"></a>Obecný proces

Na nejobecnější úrovni můžete postupovat podle těchto kroků:

1. Sestavte svůj hlavní objekt sady záznamů.

   Volitelně můžete předat ukazatel na otevřený objekt `CDatabase` nebo být schopný dodávat informace o připojení do sloupce sady záznamů jiným způsobem.

1. Proveďte kroky pro dynamické přidání sloupců.

   Podívejte se na proces popsaný v části Přidání sloupců níže.

1. Otevřete svou hlavní sadu záznamů.

   Sada záznamů vybere záznamy a používá výměnu pole záznamu (RFX) pro svázání statických sloupců (mapovaných na datové členy pole sady záznamů) a dynamické sloupce (namapované na dodatečné úložiště, které přidělíte).

###  <a name="adding-the-columns"></a><a name="_core_adding_the_columns"></a>Přidávání sloupců

K dynamickému vázání přidaných sloupců za běhu je potřeba provést následující kroky:

1. Určí čas spuštění, které sloupce jsou v cílové tabulce. Extrahovat z těchto informací seznam sloupců, které byly přidány do tabulky, protože byla vytvořena třída sady záznamů.

   Dobrým přístupem je použití třídy sady záznamů, která je navržena k dotazování zdroje dat na informace o sloupci cílové tabulky (například název sloupce a datový typ).

1. Poskytněte úložiště pro nové datové členy pole. Vzhledem k tomu, že vaše hlavní třída sady záznamů neobsahuje datové členy pole pro neznámé sloupce, je nutné zadat místo pro uložení názvů, výsledných hodnot a případně informací o datovém typu (pokud jsou sloupce různými datovými typy).

   Jedním z možností je vytvořit jeden nebo více dynamických seznamů, jeden pro názvy nových sloupců, druhý pro jejich hodnoty výsledku a třetí pro jejich datové typy (v případě potřeby). Tyto seznamy, zejména seznam hodnot, poskytují informace a nezbytné úložiště pro vazbu. Následující obrázek znázorňuje sestavování seznamů.

   ![Vytváření seznamů sloupců k dynamickému vázání](../../data/odbc/media/vc37w61.gif "Vytváření seznamů sloupců k dynamickému vázání")<br/>
   Vytváření seznamů sloupců k dynamickému vázání

1. Přidejte volání funkce RFX do funkce `DoFieldExchange` vaší hlavní sady záznamů pro každý přidaný sloupec. Tato volání RFX dělají práci při načítání záznamu, včetně dalších sloupců, a navázání sloupců na datové členy sady záznamů nebo na vaše dynamicky dodané úložiště pro ně.

   Jedním z možností je přidat smyčku do funkce `DoFieldExchange` vaší hlavní sady záznamů, která cyklicky projde seznamem nových sloupců, a volat odpovídající funkci RFX pro každý sloupec v seznamu. Při každém volání RFX předejte název sloupce ze seznamu název sloupce a umístění úložiště v příslušném členovi seznamu výsledných hodnot.

###  <a name="lists-of-columns"></a><a name="_core_lists_of_columns"></a>Seznamy sloupců

V následující tabulce jsou uvedeny čtyři seznamy, se kterými potřebujete pracovat.

|||
|-|-|
|**Current-Table-Columns**| (List 1 na obrázku) Seznam sloupců, které jsou aktuálně v tabulce ve zdroji dat. Tento seznam se může shodovat se seznamem sloupců aktuálně vázaných ve vaší sadě záznamů.|
|**Vázané sloupce sady záznamů**| (Seznam 2 na ilustraci) Seznam sloupců vázaných ve vaší sadě záznamů Tyto sloupce již obsahují příkazy RFX ve funkci `DoFieldExchange`.|
|**Sloupce na vázání – dynamicky**| (Seznam 3 na ilustraci) Seznam sloupců v tabulce, ale ne ve vaší sadě záznamů. Jedná se o sloupce, které mají být dynamicky svázány.|
|**Dynamické hodnoty sloupce**| (List 4 na obrázku) Seznam obsahující úložiště pro hodnoty načtené ze sloupců, které svážete dynamicky. Prvky tohoto seznamu odpovídají sloupcům, které jsou vázány dynamicky, jedna k jedné.|

###  <a name="building-your-lists"></a><a name="_core_building_your_lists"></a>Sestavování seznamů

Díky obecné strategii si můžete zapnout podrobnosti. Postupy ve zbývající části tohoto tématu ukazují, jak vytvořit seznamy zobrazené v [seznamech sloupců](#_core_lists_of_columns). Postupy vás provedou těmito kroky:

- [Určení názvů sloupců, které nejsou ve vaší sadě záznamů](#_core_determining_which_table_columns_are_not_in_your_recordset).

- [Poskytování dynamického úložiště pro nově přidané sloupce do tabulky](#_core_providing_storage_for_the_new_columns).

- [Dynamicky přidávají volání RFX pro nové sloupce](#_core_adding_rfx_calls_to_bind_the_columns).

###  <a name="determining-which-table-columns-are-not-in-your-recordset"></a><a name="_core_determining_which_table_columns_are_not_in_your_recordset"></a>Určení, které sloupce tabulky nejsou ve vaší sadě záznamů

Sestavte seznam (vázané sady záznamů-Columns, jako v seznamu 2 na ilustraci), který obsahuje seznam sloupců již vázaných ve vaší hlavní sadě záznamů. Pak Sestavte seznam (sloupce pro vazbu dynamicky, odvozený z aktuálních sloupců tabulky a vázané sady záznamů), které obsahují názvy sloupců, které se nacházejí v tabulce ve zdroji dat, ale ne ve vaší hlavní sadě záznamů.

##### <a name="to-determine-the-names-of-columns-not-in-the-recordset-columns-to-bind-dynamically"></a>Určení názvů sloupců, které nejsou v sadě záznamů (sloupce-do-BIND-Dynamic)

1. Sestavte seznam (Bound-Recordset-Columns) sloupců, které jsou už svázané ve vaší hlavní sadě záznamů.

   Jedním z možností je vytvořit vázané sloupce sady záznamů v době návrhu. Můžete vizuálně kontrolovat volání RFX funkce ve funkci `DoFieldExchange` sady záznamů pro získání těchto názvů. Potom nastavte seznam jako pole inicializované s názvy.

   Například ilustrace znázorňuje Bound-Recordset-Columns (list 2) se třemi prvky. Ve sloupcích vázané na sadu záznamů chybí sloupec telefon zobrazený v aktuálním sloupci tabulky (list 1).

1. Porovnejte sloupce Current-Table-Columns a Bound-Recordset-Columns a sestavte seznam (sloupce pro vazbu – dynamicky) sloupců, které nejsou v hlavní sadě záznamů už vázané.

   Jedním z nich je projít si seznam sloupců v tabulce za běhu (aktuální tabulka-sloupce) a seznam sloupců, které jsou už ve vaší sadě záznamů (Bound-Recordset-Columns) současně vázané. Do sloupců na vazbu – dynamicky umísťujte všechny názvy v aktuálních sloupcích tabulky, které nejsou uvedeny ve sloupcích Bound-Recordset-Columns.

   Například ilustrace zobrazuje sloupce pro vazbu dynamicky (list 3) s jedním prvkem: sloupec telefon nalezen v aktuální tabulce (list 1), ale ne v vázaném-Recordset-Columns (list 2).

1. Sestavte seznam dynamických hodnot sloupce (jako v seznamu 4 na obrázku), ve kterém se mají ukládat hodnoty dat odpovídající každému názvu sloupce uloženému v seznamu sloupců, aby se dynamicky navázala vazba (sloupce na BIND dynamicky).

   Prvky tohoto seznamu hrají roli nových datových členů pole sady záznamů. Jsou to umístění úložiště, do kterých jsou svázané dynamické sloupce. Popisy seznamů najdete v tématu [seznam sloupců](#_core_lists_of_columns).

###  <a name="providing-storage-for-the-new-columns"></a><a name="_core_providing_storage_for_the_new_columns"></a>Poskytování úložiště pro nové sloupce

Potom nastavte umístění úložiště pro dynamicky svázané sloupce. Nápad je poskytnout prvek seznamu, do kterého se uloží hodnota každého sloupce. Tato umístění úložiště jsou rovnoběžné s proměnnými členů sady záznamů, které ukládají běžně vázané sloupce.

#### <a name="to-provide-dynamic-storage-for-new-columns-dynamic-column-values"></a>Poskytnutí dynamického úložiště pro nové sloupce (hodnoty dynamického sloupce)

1. Sestavujte dynamické hodnoty sloupce rovnoběžně se sloupci, aby bylo možné dynamicky vytvořit vazby tak, aby obsahovaly hodnotu dat v jednotlivých sloupcích.

   Například ilustrace zobrazuje dynamické hodnoty sloupce (list 4) s jedním prvkem: `CString` objekt obsahující skutečné telefonní číslo pro aktuální záznam: "555-1212".

   V nejběžnějším případě mají hodnoty dynamického sloupce elementy typu `CString`. Pokud pracujete se sloupci s různými datovými typy, budete potřebovat seznam, který může obsahovat prvky různých typů.

Výsledkem předchozích postupů je dva hlavní seznamy: sloupce pro svázání – dynamicky obsahující názvy sloupců a dynamické sloupce-hodnoty obsahující hodnoty ve sloupcích pro aktuální záznam.

> [!TIP]
> Pokud nejsou nové sloupce stejného datového typu, můžete chtít extra paralelní seznam obsahující položky, které nějakým způsobem definují typ každého odpovídajícího prvku v seznamu sloupců. (Pokud chcete, můžete použít hodnoty AFX_RFX_BOOL, AFX_RFX_BYTE atd.). Tyto konstanty jsou definovány v AFXDB. H.) vyberte typ seznamu založený na způsobu reprezentace datových typů sloupce.

###  <a name="adding-rfx-calls-to-bind-the-columns"></a><a name="_core_adding_rfx_calls_to_bind_the_columns"></a>Přidání volání RFX pro svázání sloupců

Nakonec zajistěte, aby se dynamická vazba nastala vložením volání RFX pro nové sloupce ve funkci `DoFieldExchange`.

##### <a name="to-dynamically-add-rfx-calls-for-new-columns"></a>Pro dynamické přidání volání RFX pro nové sloupce

1. V `DoFieldExchange` členské funkci vaší hlavní sady záznamů přidejte kód, který projde seznamem nových sloupců (sloupce-vazba-Dynamic). V každé smyčce extrahujte název sloupce ze sloupců na BIND – dynamicky a výslednou hodnotu pro sloupec z dynamické hodnoty sloupce. Předejte tyto položky volání funkce RFX vhodné pro datový typ sloupce. Popisy seznamů najdete v tématu [seznam sloupců](#_core_lists_of_columns).

V běžném případě ve vašich voláních funkce `RFX_Text` vyextrahujete `CString` objekty ze seznamů, jako v následujících řádcích kódu, kde sloupce-to-BIND – dynamicky je `CStringList` s názvem `m_listName` a dynamické hodnoty sloupce je `CStringList` s názvem `m_listValue`:

```cpp
RFX_Text( pFX,
            m_listName.GetNext( posName ),
            m_listValue.GetNext( posValue ));
```

Další informace o funkcích RFX naleznete v tématu [makra a Globals](../../mfc/reference/mfc-macros-and-globals.md) v *dokumentaci knihovny tříd*.

> [!TIP]
> Pokud jsou nové sloupce různými datovými typy, použijte příkaz switch ve smyčce pro volání příslušné funkce RFX pro každý typ.

Když rozhraní volá `DoFieldExchange` během procesu `Open`, aby navázala sloupce do sady záznamů, volání RFX pro statické sloupce sváže tyto sloupce. Vaše smyčka pak opakovaně volá RFX funkce pro dynamické sloupce.

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Práce s velkými datovými položkami (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)
