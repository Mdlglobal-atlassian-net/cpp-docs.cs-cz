---
title: 'Recordset: Dynamické vazby datových sloupců (ODBC)'
ms.date: 11/19/2018
helpviewer_keywords:
- ODBC recordsets [C++], binding columns dynamically
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- columns [C++], binding to recordsets
ms.assetid: bff67254-d953-4ae4-9716-91c348cb840b
ms.openlocfilehash: c2f2a6a6696f46fb5b8f2777c6c911269c9e7a80
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397894"
---
# <a name="recordset-dynamically-binding-data-columns-odbc"></a>Recordset: Dynamické vazby datových sloupců (ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

Spravovat sady záznamů vazeb sloupců tabulky, které zadáte v době návrhu, ale existují případy, kdy můžete chtít vytvořit vazbu sloupce, které neznámé vám v době návrhu. Toto téma vysvětluje:

- [Když se můžete chtít dynamické vazby sloupců do sady záznamů](#_core_when_you_might_bind_columns_dynamically).

- [Jak vytvořit vazbu sloupců dynamicky za běhu](#_core_how_to_bind_columns_dynamically).

> [!NOTE]
>  Toto téma se vztahuje na objekty odvozené z `CRecordset` v který řádek hromadné načítání není implementovaná. Technik popsaných obecně se doporučuje, pokud používáte hromadné načítání řádků. Další informace o hromadném načítání řádků naleznete v tématu [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="_core_when_you_might_bind_columns_dynamically"></a> Když může svázat sloupců dynamicky

V době návrhu, Průvodce aplikací knihovny MFC nebo [průvodce příjemcem MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (z **přidat třídu**) vytváří na základě známých tabulek a sloupců ve zdroji dat. třídy sady záznamů. Databáze může změnit při návrhu a pokud vaše aplikace používá tyto tabulky a sloupce v době spuštění později. Vy nebo jiný uživatel může přidat nebo vyřadit tabulku nebo přidat nebo odebrat sloupce z tabulky záznamů vaší aplikace závislou na. To pravděpodobně není žádný problém pro všechny aplikace přístup k datům, ale pokud je pro vás, jak můžete vypořádat se změny ve schématu databáze, jiné než realizace a rekompilace? Účelem tohoto tématu je odpověď na tuto otázku.

Toto téma popisuje nejběžnější případ, ve kterém můžete dynamicky navázat sloupce – zahájené se na sadu záznamů na základě schématu databáze známé, chcete zpracovávat další sloupce v době běhu. Další téma předpokládá, že další sloupce mapovat na `CString` pole datových členů, nejběžnější případ, i když se poskytne návrhy vám pomohou při správě jiných datových typů.

S menším objemem kódu navíc můžete:

- [Určete, jaké sloupce jsou k dispozici v době běhu](#_core_how_to_bind_columns_dynamically).

- [Svázat s další sloupce sady záznamů dynamicky za běhu](#_core_adding_the_columns).

Sady záznamů stále obsahuje datových členů pro sloupce, které znáte v době návrhu. Také obsahuje malé množství kódu navíc, která dynamicky určí, zda byly přidány všechny nové sloupce do cílové tabulky a, pokud ano, váže tyto nové sloupce do dynamicky přidělené úložiště (nikoli do datové členy sady záznamů).

Toto téma nepopisuje ostatních případech dynamické vazby, jako jsou vyřazené tabulky nebo sloupce. Pro případy budete muset použít volání rozhraní API ODBC přímo. Informace najdete v tématu ODBC SDK *referenční informace pro programátory* na disku CD knihovny MSDN.

##  <a name="_core_how_to_bind_columns_dynamically"></a> Jak vytvořit vazbu sloupců dynamicky

K vytvoření dynamické vazby sloupců, musíte vědět, (nebo být schopní určit) názvy další sloupce. Musíte také přidělení úložiště pro datové členy další pole, zadejte jejich názvy a jejich typy a zadat počet sloupců, které chcete přidat.

Následující diskuse uvádí dvě různé sady záznamů. První je hlavní záznamů, který vybírá záznamy z cílové tabulky. Druhý je speciální sloupec sady záznamů použít k získání informací o sloupcích v cílové tabulce.

###  <a name="_core_the_general_process"></a> Obecné procesu

Nanejvýš obecná úroveň, postupujte takto:

1. Vytvoření objektu hlavní sady záznamů.

   Volitelně můžete předat ukazatel na otevřený `CDatabase` objektu nebo moct zadat informace o připojení k sloupec sady záznamů jiným způsobem.

1. Kroky k přidání sloupců dynamicky.

   V tématu proces popsaný v přidávání sloupců níže.

1. Otevřete hlavní sady záznamů.

   Sada záznamů vybírá záznamy a výměna pole záznamu (RFX) používá k vytvoření vazby statické sloupce (ty jsou mapovány na datové členy polí záznamů) a dynamické sloupce (namapované na přidělíte dodatečné úložiště).

###  <a name="_core_adding_the_columns"></a> Přidání sloupců

Dynamické vazby přidat sloupce za běhu vyžaduje následující kroky:

1. V době běhu zjistěte, co jsou sloupce v cílové tabulce. Extrahuje z těchto informací seznam sloupců, které jsou přidané do tabulky, protože byla navržena vaší třídy sady záznamů.

   Dobrý nápad, je použít třídu sloupec záznamů navržené tak, aby dotazy na zdroj dat pro informace o sloupci pro cílové tabulky (jako je například název a datový typ sloupce).

1. Poskytují úložiště pro nové pole datových členů. Protože vaše hlavní sada záznamů třída nemá pole datových členů pro neznámý sloupců, je nutné zadat místo k uložení jména, výsledné hodnoty a pravděpodobně informace o typu dat (Pokud sloupce, které jsou různé datové typy).

   Jedním z přístupů je vytvořit jeden nebo více dynamických seznamů, jeden pro názvy nových sloupců, jiné pro jejich výsledné hodnoty a třetí pro jejich datové typy (v případě potřeby). Tyto seznamy, zejména seznam hodnot, zadejte informace a potřebné úložiště pro vazbu. Následující obrázek ukazuje vytváření seznamů.

   ![Vytváření seznamů sloupce, které chcete vytvořit vazbu dynamicky](../../data/odbc/media/vc37w61.gif "vytváření seznamů sloupce, které chcete vytvořit vazbu dynamicky")<br/>
   Vytváření seznam sloupců k vytvoření dynamické vazby

1. Přidejte volání funkce RFX v hlavních záznamů `DoFieldExchange` funkci pro každý přidaný sloupec. Tato volání funkce RFX práci načítání záznam, včetně dalších sloupců a vazba sloupce na sadu záznamů datové členy nebo do úložiště dynamicky zadaný pro ně.

   Jedním z přístupů je přidání smyčky do hlavních záznamů `DoFieldExchange` funkce, která prochází seznam nové sloupce, voláním příslušné funkce RFX pro každý sloupec v seznamu. Při každém volání funkce RFX předejte název sloupce z seznam názvů sloupců a umístění úložiště v odpovídající člen hodnotu seznamu výsledků.

###  <a name="_core_lists_of_columns"></a> Seznam sloupců

V následující tabulce jsou uvedeny čtyři seznamy, které potřebujete k práci s.

|||
|-|-|
|**Aktuální sloupců tabulky**| (Seznam 1 na obrázku) Seznam sloupce v tabulce ve zdroji dat. Tento seznam může odpovídat seznam sloupců, které jsou aktuálně vázána ve vaší sadě záznamů.|
|**Sloupce sad záznamů s vazbou**| (Obrázek seznamu 2) Seznam sloupců hranice ve vaší sadě záznamů. Tyto sloupce již RFX příkazy ve vašich `DoFieldExchange` funkce.|
|**Sloupce pro dynamickou vazbu**| (Obrázek seznamu 3) Seznam sloupců v tabulce, ale ne do sady záznamů. Jedná se o sloupce, které chcete vytvořit vazbu dynamicky.|
|**Dynamické hodnoty sloupců**| (Obrázek seznamu 4) Seznam obsahující úložiště pro hodnoty ze sloupce, které můžete vytvořit vazbu dynamicky načíst. Elementy tohoto seznamu odpovídají těm v sloupce do dynamickou vazbu, 1: 1.|

###  <a name="_core_building_your_lists"></a> Vytváření seznamů

Díky obecné strategii na paměti můžete zapnout v podrobnostech. Postupy ve zbývající části tohoto tématu ukazují, jak vytvářet seznamy ukazuje [seznamy sloupců](#_core_lists_of_columns). Postupy vás prostřednictvím:

- [Určení názvy sloupců nejsou ve vaší sadě záznamů](#_core_determining_which_table_columns_are_not_in_your_recordset).

- [U sloupců nově přidané do tabulky poskytují úložiště pro dynamické](#_core_providing_storage_for_the_new_columns).

- [Dynamické přidání RFX volání pro nové sloupce](#_core_adding_rfx_calls_to_bind_the_columns).

###  <a name="_core_determining_which_table_columns_are_not_in_your_recordset"></a> Určení, které sloupce je tabulka není v sady záznamů

Sestavte seznam (mez sloupce sad záznamů, stejně jako v seznamu 2 na obrázku), který obsahuje seznam sloupců již vázán v hlavních záznamů. Potom sestavte seznam (sloupců na dynamickou vazbu, odvozený od aktuálního sloupce tabulky a sloupce s vazbou sad záznamů), který obsahuje názvy sloupců, které jsou v tabulce na zdroj dat, ale ne v hlavní sady záznamů.

##### <a name="to-determine-the-names-of-columns-not-in-the-recordset-columns-to-bind-dynamically"></a>Chcete-li zjistit názvy sloupců nejsou v sadě záznamů (sloupce pro dynamickou vazbu)

1. Sestavte seznam (mez sloupce sad záznamů) sloupce již vázán v hlavních záznamů.

   Jedním z přístupů je vytvoření sloupce s vazbou sad záznamů v době návrhu. Volání funkcí RFX v sadě záznamů můžete vizuálně zkoumat `DoFieldExchange` funkce získáte tyto názvy. Potom nastavte seznamu jako pole inicializována s názvy.

   Obrázek příkladu s vazbou sloupce sad záznamů (seznam 2) s tři elementy. Sloupce sad záznamů s vazbou chybí sloupec Phone podle aktuální sloupce tabulky (seznam 1).

1. Porovnání aktuálního sloupce tabulky a sloupce sad záznamů s vazbou sestavení seznamu sloupců, které ještě nejsou vázány v hlavních záznamů (sloupce pro dynamickou Bind).

   Jedním z přístupů je můžete projít seznam sloupců v tabulce v době běhu (aktuální sloupce tabulky) a v seznamu sloupců již vázán v sady záznamů (mez sloupce sad záznamů) paralelně. Do sloupce pro dynamickou vazbu umístěte všechny názvy v aktuální tabulce sloupce, které nejsou v vázaný na sloupce sad záznamů.

   Například na obrázku znázorňuje sloupce pro dynamickou vazbu (seznam 3) s jedním prvkem: sloupec Phone se nachází v aktuální sloupců tabulky (seznam 1), ale ne v vázaný na sloupce sad záznamů (seznam 2).

1. Sestavte seznam dynamické hodnoty sloupců (jako v seznamu 4 na obrázku), do kterého k ukládání hodnot data odpovídající názvy jednotlivých sloupců uložené v seznamu sloupců pro vazbu dynamicky (sloupce pro dynamickou vazbu).

   Elementy tohoto seznamu hrají roli nové sady záznamů datové členy. Jsou umístění úložiště, na které jsou vázány dynamické sloupce. Popisy seznamů, naleznete v tématu [seznamy sloupců](#_core_lists_of_columns).

###  <a name="_core_providing_storage_for_the_new_columns"></a> Poskytování úložiště pro nové sloupce

Potom si nastavte umístění úložiště pro sloupce, které mají být vázaný dynamicky. Cílem je poskytovat prvek seznamu, ve kterém pro ukládání hodnoty horní každý sloupec. Tato umístění úložiště paralelní proměnné členů sady záznamů, které ukládají běžně svázané sloupce.

#### <a name="to-provide-dynamic-storage-for-new-columns-dynamic-column-values"></a>Zajištění dynamickou paměť pro nové sloupce (dynamické hodnoty sloupců)

1. Vytvářejte dynamické hodnoty sloupce, paralelní do sloupce do – dynamickou vazbu, aby obsahovalo hodnotu data v jednotlivých sloupcích.

   Například na obrázku ukazuje dynamické hodnoty sloupců (seznam 4) s jedním prvkem: `CString` objekt, který obsahuje skutečné telefonní číslo pro požadovaný aktuální záznam: "555-1212".

   V případě nejběžnějších dynamické hodnoty sloupce s prvky typu `CString`. Pokud pracujete s různými datovými typy sloupců, potřebujete seznam, který může obsahovat prvky různých typů.

Výsledek předchozích postupů jsou dva hlavní seznamy: Sloupce na dynamickou vazbu obsahující názvy sloupců a dynamických sloupec hodnot obsahující hodnoty ve sloupcích pro požadovaný aktuální záznam.

> [!TIP]
> Pokud nové sloupce nejsou všechny stejného typu dat, můžete navíc paralelní seznam obsahující položky, které nějakým způsobem definování typu každý odpovídající element v seznamu sloupců. (Můžete použít hodnoty AFX_RFX_BOOL AFX_RFX_BYTE, a tak dále, pokud chcete. Tyto konstanty jsou definovány v AFXDB. H.) Vyberte typ seznamu závislosti na tom, jak reprezentaci datové typy sloupce.

###  <a name="_core_adding_rfx_calls_to_bind_the_columns"></a> Přidání volání RFX vazba sloupce

Nakonec uspořádat pro dynamické vazby dojde k umístěním volání RFX pro nové sloupce ve vaší `DoFieldExchange` funkce.

##### <a name="to-dynamically-add-rfx-calls-for-new-columns"></a>Chcete-li dynamicky přidat volání RFX pro nové sloupce

1. V hlavním záznamů `DoFieldExchange` členské funkci, přidejte kód který projde seznam nových sloupců (sloupce pro dynamickou Bind). V každé smyčce extrahujte název sloupce ze sloupce pro dynamickou vazbu a výslednou hodnotu pro sloupec z dynamické hodnoty sloupců. Předejte tyto položky volání funkce RFX odpovídající datový typ sloupce. Popisy seznamů, naleznete v tématu [seznamy sloupců](#_core_lists_of_columns).

V obvyklém případě v vaše `RFX_Text` extrahujete volání funkce `CString` objekty ze seznamů, stejně jako v následující řádky kódu, ve kterém se sloupce pro dynamickou vazbu `CStringList` volá `m_listName` a dynamické hodnoty sloupců je `CStringList` volá `m_listValue`:

```cpp
RFX_Text( pFX,
            m_listName.GetNext( posName ),
            m_listValue.GetNext( posValue ));
```

Další informace o funkce RFX najdete v tématu [makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md) v *knihovny tříd*.

> [!TIP]
> Pokud nové sloupce jsou různé datové typy, voláním příslušné funkce RFX pro každý typ pomocí příkazu switch v smyčku.

Když volá framework `DoFieldExchange` během `Open` procesu vazba sloupce na sadu záznamů, volání funkce RFX pro statické sloupce svázat těchto sloupců. Potom smyčku opakovaně volání funkcí RFX pro dynamické sloupce.

## <a name="see-also"></a>Viz také:

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Práce s velkými datovými položkami (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)