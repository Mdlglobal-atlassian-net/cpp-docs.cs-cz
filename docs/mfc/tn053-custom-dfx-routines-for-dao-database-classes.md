---
title: "TN053: Vlastní rutiny DFX pro rozhraní DAO databáze třídy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.dfx
dev_langs: C++
helpviewer_keywords:
- MFC, DAO and
- database classes [MFC], DAO
- DAO [MFC], MFC
- DFX (DAO record field exchange) [MFC], custom routines
- TN053
- DAO [MFC], classes
- DFX (DAO record field exchange) [MFC]
- custom DFX routines [MFC]
ms.assetid: fdcf3c51-4fa8-4517-9222-58aaa4f25cac
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c03c00f6873259ea3fdbf5da0e26f433a855115d
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2017
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053: Vlastní rutiny DFX pro databázové třídy DAO
> [!NOTE]
>  Prostředí Visual C++ a průvodců nepodporují rozhraní DAO (i když jsou zahrnuté třídy DAO a můžete je dál používat). Microsoft doporučuje používat [šablony technologie OLE DB](../data/oledb/ole-db-templates.md) nebo [rozhraní ODBC a MFC](../data/odbc/odbc-and-mfc.md) pro nové projekty. DAO byste měli používat jenom pro údržbu existujících aplikací.  
  
 Tato technická Poznámka popisuje mechanismus výměna pole záznamu exchange (DFX). Pro lepší porozumění tomu, co se děje v rutiny DFX `DFX_Text` funkce budou vysvětleny podrobně jako příklad. Jako další zdroje informací k této technické poznámky můžete zkontrolovat kód pro druhý jednotlivých funkcí DFX. Pravděpodobně nebude nutné vlastní rutiny DFX často může být nutné vlastní rutiny RFX (používá se s třídami databází rozhraní ODBC).  
  
 Obsahuje tato technická Poznámka:  
  
-   DFX – přehled  
  
- [Příklady](#_mfcnotes_tn053_examples) pomocí výměna pole záznamu rozhraní DAO a dynamické vazby  
  
- [Jak funguje DFX](#_mfcnotes_tn053_how_dfx_works)  
  
- [Jaké jsou vaše vlastní DFX rutiny](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)  
  
- [Podrobnosti o dfx_text –](#_mfcnotes_tn053_details_of_dfx_text)  
  
 **DFX – přehled**  
  
 Mechanismus výměny výměna pole záznamu (DFX) se používá ke zjednodušení procesu načítání a aktualizace dat při použití `CDaoRecordset` třídy. Proces je zjednodušený pomocí datových členů `CDaoRecordset` třídy. Odvozené z `CDaoRecordset`, přidáte datové členy do odvozené třídy představující každé pole v tabulce nebo dotazu. Tento mechanismus "statická vazba" je jednoduchá, ale nemusí být metodu načtení nebo aktualizace dat podle volby pro všechny aplikace. DFX načte každé vázané pole pokaždé, když se změní na aktuální záznam. Pokud vyvíjíte aplikace náročné na výkon, která nevyžaduje načítání každé pole při změně měny "dynamické vazby" prostřednictvím `CDaoRecordset::GetFieldValue` a `CDaoRecordset::SetFieldValue` může být metoda přístupu data výběru.  
  
> [!NOTE]
>  DFX a dynamické vazby nejsou vzájemně vylučují, proto je možné použít hybridní statické a dynamické vazby.  
  
## <a name="_mfcnotes_tn053_examples"></a>Příklad 1 – Použití rozhraní DAO výměna pole záznamu pouze  
  
 (předpokládá `CDaoRecordset` – odvozené třídy `CMySet` otevřený)  
  
```  
// Add a new record to the customers table  
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```  
  
 **Příklad 2 – Použití dynamické vazby**  
  
 (předpokládá použití `CDaoRecordset` třídy, `rs`, a je již otevřeno)  
  
```  
// Add a new record to the customers table  
COleVariant  varFieldValue1 (_T("MSFT"),
    VT_BSTRT);

//Note: VT_BSTRT flags string type as ANSI,
    instead of UNICODE default  
COleVariant  varFieldValue2  (_T("Microsoft"),
    VT_BSTRT);

rs.AddNew();

rs.SetFieldValue(_T("Customer_ID"),
    varFieldValue1);

rs.SetFieldValue(_T("Customer_Name"),
    varFieldValue2);

rs.Update();
```  
  
 **Příklad 3 – Použití z rozhraní DAO výměna pole záznamu a dynamické vazby**  
  
 (předpokládá procházení data zaměstnance s `CDaoRecordset`-odvozené třídy `emp`)  
  
```  
// Get the employee's data so that it can be displayed  
emp.MoveNext();

 
// If user wants to see employee's photograph,  
// fetch it  
COleVariant varPhoto;  
if (bSeePicture)  
    emp.GetFieldValue(_T("photo"),
    varPhoto);

 
// Display the data  
PopUpEmployeeData(emp.m_strFirstName,  
    emp.m_strLastName,
    varPhoto);
```  
  
## <a name="_mfcnotes_tn053_how_dfx_works"></a>Jak funguje DFX  
  
 Tento mechanismus DFX funguje podobným způsobem mechanismu pole záznamu (exchange – RFX), který používá třídy knihovny MFC rozhraní ODBC. Zásady DFX a RFX jsou stejné, ale jsou množství interní rozdíly. Návrh DFX funkce se tak, že se jednotlivé rutiny DFX sdílí prakticky všechny kód. Na nejvyšší úrovni DFX pouze nemá pár věcí.  
  
-   DFX vytvoří SQL **vyberte** klauzule a SQL **parametry** klauzule v případě potřeby.  
  
-   DFX vytvoří strukturu vazby používané pro DAO `GetRows` funkce (Další informace o to později).  
  
-   DFX spravuje vyrovnávací paměť dat použít ke zjištění změny pole (Pokud dvojitě ukládání do vyrovnávací paměti se používá)  
  
-   DFX spravuje **NULL** a **DIRTY** stav polí a nastaví hodnoty v případě potřeby na aktualizace.  
  
 Jádrem DFX mechanismus je `CDaoRecordset` odvozené třídy `DoFieldExchange` funkce. Tato funkce odešle zprávu volání jednotlivých funkcí DFX typu příslušnou operaci. Před voláním `DoFieldExchange` interní funkce MFC nastavte typ operace. Následující seznam obsahuje různé typy operací a stručný popis.  
  
|Operace|Popis|  
|---------------|-----------------|  
|**AddToParameterList**|Klauzule parametry sestavení|  
|**AddToSelectList**|Klauzule SELECT sestavení|  
|**BindField**|Nastaví strukturu vazby|  
|**BindParam**|Nastaví hodnoty parametru|  
|**Oprava**|Nastaví stav hodnotu NULL|  
|**AllocCache**|Přidělí mezipaměti pro změny kontroly|  
|**StoreField**|Uloží aktuální záznam do mezipaměti|  
|**LoadField**|Obnovení mezipaměti hodnoty členů|  
|**FreeCache**|Uvolní mezipaměti|  
|`SetFieldNull`|Nastaví pole stavové & hodnotu na hodnotu NULL|  
|**MarkForAddNew**|Označí pole nekonzistence není-li PSEUDO hodnotu NULL.|  
|**MarkForEdit**|Pokud změny pole značky neshodují mezipaměti|  
|**SetDirtyField**|Nastaví pole hodnoty, které jsou označeny jako nečisté|  
  
 V další části, bude každé operace vysvětlené podrobněji pro `DFX_Text`.  
  
 Nejdůležitější funkce zjistit, o procesu výměna pole záznamu exchange je, že používá `GetRows` funkce `CDaoRecordset` objektu. S objektem DAO `GetRows` funkce můžete pracovat několika způsoby. Tato technická Poznámka bude pouze Krátce popište `GetRows` jako je mimo rozsah této technické poznámky.  
  
 DAO `GetRows` můžete pracovat několika způsoby.  
  
-   Ho můžete získat více pole data a více záznamů najednou. To umožňuje rychlejší přístup k datům s problému zpracování velkých objemů dat strukturu a příslušné posunutí pro každé pole a pro každý záznam dat ve struktuře. MFC není využít tento více záznam načítání mechanismus.  
  
-   Dalším způsobem `GetRows` můžete pracovní je umožnit programátorům určena vazba pro načtená data každého pole pro jeden záznam dat.  
  
-   DAO bude také "zpětného volání" do volající pro sloupce s proměnlivou délkou Chcete-li povolit volající přidělit paměť. Tato druhá funkce má výhodu současně minimalizuje počet kopií dat a také umožňuje přímé ukládání dat do členy třídy ( `CDaoRecordset` odvozené třídy). Tento druhý mechanismus je metoda MFC používá k vytvoření vazby datových členů v `CDaoRecordset` odvozených třídách.  
  
##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a>Jaké jsou vaše vlastní DFX rutiny  
 Je zřejmé z toto pojednání, který nejdůležitější operace provedena v žádné DFX funkce musí být možnost nastavit požadované datové struktury úspěšně volat `GetRows`. Existuje řada jiné operace, které musí také podporovat DFX funkce, ale žádný jako důležité nebo komplexní jako správně přípravy `GetRows` volání.  
  
 Použití DFX je popsaná v online dokumentaci. V podstatě existují dva požadavky. Nejprve je třeba přidat členy do `CDaoRecordset` odvozené třídy pro každou vázané pole a parametr. Následující to `CDaoRecordset::DoFieldExchange` by měla být potlačena. Všimněte si, že datový typ člena je důležité. Ho by měla odpovídat data z pole v databázi nebo alespoň být převoditelná na typu. Například číselné pole v databázi, jako je například dlouhých celých čísel, kdykoli můžete převést na text a vázána `CString` člena, ale textové pole v databázi může nemusí být převést na číselnému znázornění, jako je například dlouhé celé číslo a vázaný k dlouho integ Če člen. DAO a databázový stroj Microsoft Jet jsou zodpovědní za převod (nikoli MFC).  
  
##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a>Podrobnosti o dfx_text –  
 Jak je uvedeno nahoře, je nejlepší způsob, jak vysvětlují, jak funguje DFX pro práci v příkladu. Pro tento účel projít interní položky `DFX_Text` by pomáhají alespoň základní znalosti o DFX velmi dobře fungovat.  
  
 **AddToParameterList**  
 Tato operace vytvoří SQL **parametry** – klauzule ("`Parameters <param name>, <param type> ... ;`") vyžaduje Jet. Každý parametr s názvem a zadali (jako je zadaný ve volání RFX). Najdete v části funkce **CDaoFieldExchange::AppendParamType** funkce, které chcete zobrazit názvy jednotlivých typů. U `DFX_Text`, je typu použitého `text`.  
  
 **AddToSelectList**  
 Sestavení SQL **vyberte** klauzule. To je poměrně rovnou předávat název sloupce zadané ve volání DFX je jednoduše připojen ("`SELECT <column name>, ...`").  
  
 **BindField**  
 Nejvíce komplexní operací. Jak je uvedeno nahoře, to je, kde strukturu DAO vazby používané `GetRows` nastavení. Jak vidíte z kódu v `DFX_Text` typy informací ve struktuře zahrnují DAO typu použitého (**DAO_CHAR** nebo **DAO_WCHAR** u `DFX_Text`). Kromě toho typu vazby použít také nastavená. V dřívější části `GetRows` byla pouze stručně popisuje, ale byla dostatečná vysvětlení, že typ vazby využívané prostředím MFC je vždy vazbu přímé adresy (**DAOBINDING_DIRECT**). Kromě toho pro vazbu na sloupec s proměnlivou délkou (jako je `DFX_Text`) zpětného volání vazby se používá, aby MFC můžete řídit přidělování paměti a zadejte adresu správnou délku. To znamená, že MFC vždy poznáte DAO "kde" dat, což umožňuje vazbu přímo do proměnné členů. Zbytek strukturu vazby vyplněno takové věci, jako adresa funkce zpětného volání přidělování paměti a typ vazba sloupce (vazby název sloupce).  
  
 **BindParam**  
 Toto je jednoduchá operace, která volá `SetParamValue` s hodnotou parametru určenou v parametr člena.  
  
 **Oprava**  
 Vyplní **NULL** stav pro každé pole.  
  
 `SetFieldNull`  
 Tato operace pouze označí stav každého pole jako **NULL** a nastaví hodnoty proměnné člena na **PSEUDO_NULL**.  
  
 **SetDirtyField**  
 Volání `SetFieldValue` pro každé pole označila jako neaktualizované.  
  
 Všechny ostatní operace řešit pouze pomocí datové mezipaměti. Mezipaměť dat je navíc vyrovnávací paměť dat v aktuální záznam, který se používá k zajištění některé aspekty jednodušší. Například můžete být automaticky zjišťují "nekonzistence" pole. Jak je popsáno v online dokumentaci ho může být vypnuto zcela nebo na úrovni pole. Implementace vyrovnávací paměti využívá mapy. Tato mapa slouží k přiřazování dynamicky přidělené kopie dat s adresou pole "vázaná" (nebo `CDaoRecordset` odvozené – datový člen).  
  
 **AllocCache**  
 Dynamicky přiděluje hodnota v mezipaměti pole a přidá ji do mapy.  
  
 **FreeCache**  
 Odstraní hodnotu uloženou v mezipaměti pole a odebere ji z mapování.  
  
 **StoreField**  
 Aktuální hodnota pole zkopíruje do mezipaměti data.  
  
 **LoadField**  
 Hodnota uložená v mezipaměti se zkopíruje do pole člena.  
  
 **MarkForAddNew**  
 Ověří, zda je aktuální hodnota pole jinou hodnotu než**NULL** a označí nekonzistence v případě potřeby.  
  
 **MarkForEdit**  
 Porovná aktuální hodnotu pole s datovou mezipaměť a označí nekonzistence v případě potřeby.  
  
> [!TIP]
>  Vaše vlastní rutiny DFX model na existující rutiny DFX pro standardní datové typy.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

