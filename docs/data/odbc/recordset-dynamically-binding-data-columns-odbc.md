---
title: 'Sada záznamů: Dynamické vazby datových sloupců (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets [C++], binding columns dynamically
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- columns [C++], binding to recordsets
ms.assetid: bff67254-d953-4ae4-9716-91c348cb840b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9fe71707de20ba02228039e5693cab9c9401d560
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-dynamically-binding-data-columns-odbc"></a>Sada záznamů: Dynamické vazby datových sloupců (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Vazba sloupce tabulky, které zadáte v době návrhu spravovat sady záznamů, ale existují případy, pokud chcete vytvořit vazbu sloupce, které neznámé vám v době návrhu. Toto téma vysvětluje:  
  
-   [Pokud chcete dynamicky navázat sloupce do sady záznamů](#_core_when_you_might_bind_columns_dynamically).  
  
-   [Jak vytvořit vazbu sloupců dynamicky za běhu](#_core_how_to_bind_columns_dynamically).  
  
> [!NOTE]
>  Toto téma se vztahuje na objekty, které jsou odvozené z `CRecordset` v který řádek hromadné načítání se neimplementovala. Technik popsaných obecně není vhodné, pokud používáte hromadné načítání řádků. Další informace o hromadné načítání řádků najdete v tématu [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_when_you_might_bind_columns_dynamically"></a> Když může svázat sloupců dynamicky  
 V době návrhu, Průvodce aplikací knihovny MFC nebo [průvodce příjemcem knihovny MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (z **přidat třídu**) vytváří na základě známých tabulek a sloupců na zdroj dat třídy sady záznamů. Databáze může změnit při návrhu a pokud vaše aplikace používá tyto tabulky a sloupce v době běhu později. Vy nebo jiný uživatel může přidat nebo vyřadit tabulku nebo přidat nebo vyřadit sloupce z tabulky, která vychází sada záznamů vaší aplikace. To pravděpodobně není důležité pro všechny aplikace, přístup k datům, ale pokud je pro vaše, jak můžete vypořádat s změny ve schématu databáze, jiné než přepracování a nutnosti rekompilace? Účelem tohoto tématu je odpověď na tuto otázku.  
  
 Toto téma popisuje nejběžnější případ, ve kterém můžete dynamicky vázat sloupce – zahájené se záznamů založené na schéma známé databáze, chcete zpracovávat další sloupce v době běhu. Další téma předpokládá, že mapování dalších sloupců do `CString` pole datových členů, nejběžnější případ, i když jsou dodávány návrhy, které vám pomohou spravovat jiné datové typy.  
  
 Malé množství kódu navíc můžete:  
  
-   [Zjistit, jaké sloupce jsou dostupná v době běhu](#_core_how_to_bind_columns_dynamically).  
  
-   [Svázat další sloupce do sady záznamů dynamicky za běhu](#_core_adding_the_columns).  
  
 Sady záznamů stále obsahuje datové členy pro sloupce, které znáte v době návrhu. Také obsahuje malé množství další kód, který dynamicky určuje, zda byly přidány žádné nové sloupce do cílové tabulky a, pokud ano, váže tyto nové sloupce do dynamicky přidělené úložiště (nikoli do datových členů sady záznamů).  
  
 Toto téma nepopisuje ostatních případech dynamické vazby, například vynechaných tabulky nebo sloupce. Pro případy budete muset použít rozhraní API ODBC volání více přímo. Informace najdete v tématu ODBC SDK *referenční informace pro programátory* na disku CD knihovny MSDN.  
  
##  <a name="_core_how_to_bind_columns_dynamically"></a> Jak vytvořit vazbu sloupců dynamicky  
 Pokud chcete vytvořit vazbu sloupců dynamicky, musíte vědět, (nebo být schopní určit) názvy dalších sloupců. Musíte také přidělit úložiště pro další pole datových členů, zadejte jejich názvy a jejich typy a zadat počet sloupců, který chcete přidat.  
  
 Následující diskuse uvádí dvě různé sady záznamů. První je hlavní sada záznamů, který vybere záznamy z cílové tabulky. Druhá je speciální sloupec sady záznamů použít k získání informací o sloupcích v cílové tabulce.  
  
###  <a name="_core_the_general_process"></a> Obecné procesu  
 Nejvýše obecné úrovni, postupujte takto:  
  
1.  Sestavení objektu sady hlavní záznamů.  
  
     Volitelně můžete předat ukazatel otevřenou `CDatabase` objektu nebo moci poskytnout informace o připojení na sloupec sady záznamů jiným způsobem.  
  
2.  Proveďte kroky k přidání sloupců dynamicky.  
  
     Viz proces popsaný v přidání sloupců níže.  
  
3.  Otevřete hlavní sady záznamů.  
  
     Sady záznamů vybere záznamy a používá pole záznamu (exchange – RFX) pro vazbu statické sloupce (ty jsou mapovány na sadu záznamů pole datových členů) a dynamické sloupce (mapovat do dalšího úložiště, které přidělíte).  
  
###  <a name="_core_adding_the_columns"></a> Přidání sloupců  
 Dynamické vazby přidat sloupce v době běhu vyžaduje následující kroky:  
  
1.  V době běhu zjistěte, co jsou sloupce v cílové tabulce. Extrahuje z těchto informací seznam sloupců, které byly přidány do tabulky vzhledem k tomu, že byl navržen třídu sady záznamů.  
  
     Dobrý přístupů je použít třídu sady záznamů sloupec, který je navržený tak, aby dotazy na zdroj dat pro informace o sloupci pro cílové tabulky (například název a datový typ sloupce).  
  
2.  Poskytování úložiště pro nové pole datových členů. Protože vaše třída hlavní sady záznamů nemá pole datových členů pro neznámé sloupce, je třeba zadat místo, kam můžete ukládat názvy, hodnoty výsledek a pravděpodobně informace o typu dat (pokud jsou různé datové typy sloupce).  
  
     Jeden z přístupů je vytvořit jeden nebo více dynamických seznamů, jeden pro nové sloupce názvy, jiné pro své hodnoty výsledek a třetí pro jejich datové typy (v případě potřeby). Tyto seznamy, zejména seznam hodnot, zadejte informace a potřebné úložiště pro vazbu. Následující obrázek ukazuje, vytváření seznamů.  
     ![Vytváření seznamů sloupců pro vazbu dynamicky](../../data/odbc/media/vc37w61.gif "vc37w61")  
Vytváření seznamů sloupců pro vazbu dynamicky  
  
3.  Přidejte volání funkce RFX v hlavní záznamů `DoFieldExchange` funkce pro každý přidaný sloupec. Tato RFX volání práci načítání záznamu, včetně dalších sloupců a vazba sloupce záznamů datových členů nebo vámi zadané dynamické úložiště pro ně.  
  
     Jeden z přístupů je přidání smyčky do hlavní sady záznamů `DoFieldExchange` funkce, který projde seznam nových sloupců, voláním příslušné RFX funkce pro každý sloupec v seznamu. Při každém volání RFX předejte název sloupce ze seznamu sloupců název a umístění úložiště v odpovídající členem hodnota seznam výsledků.  
  
###  <a name="_core_lists_of_columns"></a> Seznam sloupců  
 V následující tabulce jsou uvedeny čtyři seznamy, které potřebujete k práci s.  
  
 **Aktuální sloupců tabulky (seznam 1 na obrázku)** seznam sloupce v tabulce ve zdroji dat. Tento seznam může odpovídat seznam sloupců, které jsou aktuálně provázána ve vaší sadě záznamů.  
  
 **Hranice sloupce sad záznamů (seznam 2 na obrázku)**  
 Seznam sloupců hranice ve vaší sadě záznamů. Tyto sloupce již obsahují RFX příkazy ve vaší `DoFieldExchange` funkce.  
  
 **Sloupce pro dynamickou vazby (seznam 3 na obrázku)**  
 Seznam sloupců v tabulce, ale není ve vaší sadě záznamů. Jedná se o sloupce, které chcete vytvořit vazbu dynamicky.  
  
 **Dynamické hodnoty sloupce (seznam 4 na obrázku)**  
 Seznam obsahující úložiště pro hodnoty ze sloupce, které můžete vytvořit vazbu dynamicky načíst. Prvky tohoto seznamu odpovídají sloupcům v sloupce do dynamickou vazbu, 1.  
  
###  <a name="_core_building_your_lists"></a> Vytváření seznamů  
 S strategie Obecné v paměti můžete zapnout na podrobnosti. Postupy v zbývající část tohoto tématu ukazují, jak vytvářet seznamy ukazuje [seznamy sloupců](#_core_lists_of_columns). Podle pokynů Průvodce vás provede:  
  
-   [Určení názvy sloupců nejsou ve vaší sadě záznamů](#_core_determining_which_table_columns_are_not_in_your_recordset).  
  
-   [Poskytování dynamického úložiště pro sloupce do tabulky přidat nově](#_core_providing_storage_for_the_new_columns).  
  
-   [Dynamické přidávání RFX volání pro nové sloupce](#_core_adding_rfx_calls_to_bind_the_columns).  
  
###  <a name="_core_determining_which_table_columns_are_not_in_your_recordset"></a> Určení, které jsou sloupce tabulky nejsou v sady záznamů  
 Sestavte seznam (vázané sloupce sady záznamů, jako v seznamu 2 na obrázku), který obsahuje seznam sloupců, již je svázaná vaší hlavní sady záznamů. Potom můžete vytvoříte seznam (sloupce do dynamickou vazbu, odvozená od aktuální sloupců tabulky a sloupce sad záznamů hranice) obsahující názvy sloupců, které jsou v tabulce ve zdroji dat, ale ne v hlavní sady záznamů.  
  
##### <a name="to-determine-the-names-of-columns-not-in-the-recordset-columns-to-bind-dynamically"></a>Chcete-li zjistit názvy sloupců nejsou v sadě záznamů (sloupce pro dynamickou vazby)  
  
1.  Sestavte seznam sloupců, již je svázaná vaší hlavní sady záznamů (vázané sloupce sady záznamů).  
  
     Jeden ze způsobů je vytvoření hranice sloupce sad záznamů v době návrhu. Můžete vizuálně zkoumat funkce RFX v sadě záznamů `DoFieldExchange` funkce získat tyto názvy. Potom nastavte si na seznam jako pole inicializován s názvy.  
  
     Například na obrázku hranice sloupce sad záznamů (seznam 2) s tři prvky. Sloupce sad záznamů hranice chybí sloupci Phone ukazuje aktuální sloupců tabulky (seznam 1).  
  
2.  Porovnejte Aktuální sloupce tabulky a sloupce sad záznamů mez, jak sestavit seznam sloupců, není již je svázaná vaší hlavní sady záznamů (sloupce pro dynamickou vazby).  
  
     Jeden z přístupů je můžete procházet seznam sloupců v tabulce za běhu (aktuální sloupce tabulky) a seznam sloupců, již je svázaná ve vaší sadě záznamů (vázané sloupce sady záznamů) paralelně. Do sloupce pro dynamickou vazby dávat žádné názvy v aktuální-sloupců tabulky, které se nezobrazí v sloupce sad záznamů hranice.  
  
     Například obrázek zobrazuje sloupce pro dynamickou vazby (seznam 3) s jedním prvkem: sloupec Phone se nachází v aktuální sloupců tabulky (seznam 1), ale není v hranice sloupce sad záznamů (seznam 2).  
  
3.  Vytvořit seznam dynamické hodnoty sloupce (jako v seznamu 4 na obrázku) pro uložení hodnoty dat, odpovídající každému názvu sloupce, uložené v seznamu sloupců pro dynamickou vazbu (sloupce pro dynamickou vazby).  
  
     Prvky tohoto seznamu Přehrát roli nové sady záznamů pole datových členů. Jsou umístění úložiště, na které jsou vázány dynamické sloupce. Popis seznamů najdete v tématu [seznamy sloupců](#_core_lists_of_columns).  
  
###  <a name="_core_providing_storage_for_the_new_columns"></a> Poskytování úložiště pro nové sloupce  
 Potom si nastavte umístění úložiště pro sloupce, které mají být dynamicky vázána. Cílem je zajistit element seznamu pro uložení každá hodnota sloupce. Tato umístění úložiště paralelní členské proměnné sady záznamů, které ukládají obvyklé vázané sloupce.  
  
##### <a name="to-provide-dynamic-storage-for-new-columns-dynamic-column-values"></a>K poskytování dynamické úložiště pro nové sloupce (dynamické hodnoty sloupce)  
  
1.  Vytvořte dynamické hodnoty sloupce, paralelní k sloupce do dynamickou vazbu, tak, aby obsahovala hodnota dat v každém sloupci.  
  
     Například obrázek zobrazuje dynamické hodnoty sloupce (seznam 4) s jedním prvkem: `CString` objekt obsahující skutečné telefonní číslo pro aktuální záznam: "555-1212".  
  
     V případě nejběžnějších dynamické hodnoty sloupce má elementy typu `CString`. Pokud chcete pracovat s různými datovými typy sloupců, je třeba seznam, který může obsahovat elementy celou řadu typů.  
  
 Výsledek předchozí postupy jsou dva hlavní seznamy: sloupce pro vazby-dynamickou obsahující názvy sloupců a dynamických sloupec hodnot obsahující hodnoty ve sloupcích pro aktuální záznam.  
  
> [!TIP]
>  Pokud nové sloupce nejsou všechny stejného typu dat, můžete chtít extra paralelní seznam obsahující položky, které nějakým způsobem definování typu jednotlivých odpovídající element v seznamu sloupců. (Můžete použít hodnoty **AFX_RFX_BOOL**, **AFX_RFX_BYTE**a tak dále, pokud chcete. Tyto konstanty jsou definovány v AFXDB. H.) Vyberte typ seznamu založené na tom, jak představují datové typy sloupce.  
  
###  <a name="_core_adding_rfx_calls_to_bind_the_columns"></a> Přidání volání RFX pro vazbu sloupců  
 Nakonec uspořádat dynamické vazby provádí umístění RFX volání pro nové sloupce ve vaší `DoFieldExchange` funkce.  
  
##### <a name="to-dynamically-add-rfx-calls-for-new-columns"></a>Chcete-li dynamicky přidat volání RFX pro nové sloupce  
  
1.  V hlavní záznamů `DoFieldExchange` členské funkce, přidejte kód který projde seznam nové sloupce (sloupce pro dynamickou vazby). V každé smyčce ze sloupce pro dynamickou vazby a výslednou hodnotu pro sloupec z hodnot sloupce dynamické extrahujte název sloupce. Předejte tyto položky funkce RFX podle typu dat sloupce. Popis seznamů najdete v tématu [seznamy sloupců](#_core_lists_of_columns).  
  
 V případě běžných v vaše `RFX_Text` extrahujete volání funkce `CString` ze seznamů, podobně jako v následujícím kódu, kde je sloupce pro dynamickou vazby `CStringList` názvem `m_listName` a dynamické hodnoty sloupce `CStringList` názvem `m_listValue`:  
  
```  
RFX_Text( pFX,   
            m_listName.GetNext( posName ),   
            m_listValue.GetNext( posValue ));  
```  
  
 Další informace o funkce RFX najdete v tématu [makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md) v *knihovny tříd*.  
  
> [!TIP]
>  Pokud nové sloupce jsou různé datové typy, využít k volání příslušné RFX funkce pro každý typ příkazu switch ve vaší smyčce.  
  
 Když volá framework `DoFieldExchange` během **otevřete** proces navázat sloupce do sady záznamů, volání RFX pro statické sloupce vazby tyto sloupce. Potom volá Vaše smyčka opakovaně funkce RFX pro dynamické sloupce.  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Práce s velkými datovými položkami (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)