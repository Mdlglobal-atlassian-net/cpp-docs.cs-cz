---
title: 'TN053: Vlastní rutiny DFX pro databázové třídy DAO'
ms.date: 09/17/2019
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
ms.openlocfilehash: f7ad854f4dbb4e90c09e886c69260e4e2eea3be2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365264"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053: Vlastní rutiny DFX pro databázové třídy DAO

> [!NOTE]
> DAO se používá s databázemi Accessu a je podporován prostřednictvím Office 2013. DAO 3.6 je konečná verze, a to je považováno za zastaralé. Prostředí Visual C++ a průvodci nepodporují DAO (i když jsou zahrnuty třídy DAO a můžete je stále používat). Společnost Microsoft doporučuje používat [šablony OLE DB](../data/oledb/ole-db-templates.md) nebo rozhraní [ODBC a knihovnu MFC](../data/odbc/odbc-and-mfc.md) pro nové projekty. DAO byste měli používat pouze při údržbě existujících aplikací.

Tato technická poznámka popisuje mechanismus výměny pole záznamu DAO (DFX). Chcete-li pomoci pochopit, co se děje `DFX_Text` v rutiny DFX, funkce bude podrobně vysvětlena jako příklad. Jako další zdroj informací k této technické poznámce můžete prozkoumat kód pro ostatní funkce DFX. Pravděpodobně nebudete potřebovat vlastní rutinu DFX tak často, jak budete potřebovat vlastní rutinu RFX (používanou s třídami databáze ROZHRANÍ ODBC).

Tato technická poznámka obsahuje:

- Přehled DFX

- [Příklady](#_mfcnotes_tn053_examples) použití výměny polí záznamů DAO a dynamické vazby

- [Jak funguje DFX](#_mfcnotes_tn053_how_dfx_works)

- [Co vaše vlastní DFX rutina dělá](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)

- [Podrobnosti o DFX_Text](#_mfcnotes_tn053_details_of_dfx_text)

**Přehled DFX**

Mechanismus výměny pole záznamu DAO (DFX) se používá ke zjednodušení `CDaoRecordset` postupu načítání a aktualizace dat při použití třídy. Proces je zjednodušen pomocí datových členů třídy. `CDaoRecordset` Odvozením z `CDaoRecordset`aplikace můžete přidat datové členy do odvozené třídy představující každé pole v tabulce nebo dotazu. Tento mechanismus "statické vazby" je jednoduchý, ale nemusí to být metoda načítání nebo aktualizace dat pro všechny aplikace. DFX načte každé vázané pole při každé změně aktuálního záznamu. Pokud vyvíjíte aplikaci citlivou na výkon, která nevyžaduje načítání každé pole při `CDaoRecordset::GetFieldValue` `CDaoRecordset::SetFieldValue` změně měny, "dynamická vazba" přes a může být metoda přístupu k datům volby.

> [!NOTE]
> DFX a dynamické vazby se vzájemně nevylučují, takže lze použít hybridní použití statické a dynamické vazby.

## <a name="example-1--use-of-dao-record-field-exchange-only"></a><a name="_mfcnotes_tn053_examples"></a>Příklad 1 – Použití pouze výměny polí záznamů DAO

(předpokládá `CDaoRecordset` – odvozená `CMySet` třída je již otevřená)

```
// Add a new record to the customers table
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```

**Příklad 2 – Použití pouze dynamické vazby**

(předpokládá použití `CDaoRecordset` třídy , `rs`a je již otevřena)

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

**Příklad 3 – Použití výměny pole záznamu DAO a dynamické vazby**

(předpokládá procházení dat `CDaoRecordset`zaměstnanců s `emp`odvozenou třídou)

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

## <a name="how-dfx-works"></a><a name="_mfcnotes_tn053_how_dfx_works"></a>Jak funguje DFX

Mechanismus DFX funguje podobným způsobem jako mechanismus výměny pole záznamu (RFX), který používají třídy Rozhraní MFC ODBC. Principy DFX a RFX jsou stejné, ale existují četné vnitřní rozdíly. Návrh funkcí DFX byl takový, že prakticky veškerý kód je sdílen jednotlivými rutinami DFX. Na nejvyšší úrovni DFX dělá jen pár věcí.

- DFX vytvoří klauzuli SQL **SELECT** a klauzuli SQL **PARAMETERS** v případě potřeby.

- DFX vytvoří strukturu vazby používanou `GetRows` funkcí DAO (více o tom později).

- DFX spravuje vyrovnávací paměť dat používanou ke zjišťování nečistých polí (pokud se používá dvojité ukládání do vyrovnávací paměti)

- DFX spravuje **pole** stavu NULL a **DIRTY** a v případě potřeby nastaví hodnoty pro aktualizace.

Jádrem mechanismu DFX je `CDaoRecordset` `DoFieldExchange` funkce odvozené třídy. Tato funkce odešle volání jednotlivých funkcí DFX vhodného typu operace. Před `DoFieldExchange` voláním interních funkcí knihovny MFC nastavte typ operace. V následujícím seznamu jsou uvedeny různé typy operací a stručný popis.

|Operace|Popis|
|---------------|-----------------|
|`AddToParameterList`|Sestavení klauzule PARAMETERS|
|`AddToSelectList`|Vytvoří klauzuli SELECT|
|`BindField`|Nastaví strukturu vazby|
|`BindParam`|Nastaví hodnoty parametrů.|
|`Fixup`|Nastaví stav NULL|
|`AllocCache`|Přidělí mezipaměť pro nečisté kontroly|
|`StoreField`|Uloží aktuální záznam do mezipaměti.|
|`LoadField`|Obnoví mezipaměť na členské hodnoty.|
|`FreeCache`|Uvolní mezipaměť|
|`SetFieldNull`|Nastaví hodnotu & pole na hodnotu NULL.|
|`MarkForAddNew`|Označí pole neznečištěná, pokud ne PSEUDO NULL.|
|`MarkForEdit`|Označí znečištěná pole, pokud se neshodují s mezipamětí.|
|`SetDirtyField`|Nastaví hodnoty polí označené jako nečisté.|

V další části bude každá operace podrobněji `DFX_Text`vysvětlena pro .

Nejdůležitější funkcí, kterou je třeba porozumět procesu výměny pole `GetRows` záznamů `CDaoRecordset` DAO, je, že používá funkci objektu. Funkce DAO `GetRows` může pracovat několika způsoby. Tato technická poznámka `GetRows` bude pouze stručně popsána, protože je mimo rozsah této technické poznámky.
DAO `GetRows` může pracovat několika způsoby.

- Může načíst více záznamů a více datových polí najednou. To umožňuje rychlejší přístup k datům s komplikací zpracování velké datové struktury a příslušné posuny pro každé pole a pro každý záznam dat ve struktuře. Knihovna MFC nevyužívá tento mechanismus načítání více záznamů.

- Dalším `GetRows` způsobem, jak může fungovat, je umožnit programátorům zadat adresy vazby pro načtená data každého pole pro jeden záznam dat.

- DAO bude také "volat zpět" do volajícího pro sloupce proměnné délky, aby volající mohl přidělit paměť. Tato druhá funkce má tu výhodu, že minimalizuje počet kopií dat a umožňuje přímé ukládání `CDaoRecordset` dat do členů třídy (odvozené třídy). Tento druhý mechanismus je metoda MFC používá `CDaoRecordset` k vazbě na datové členy v odvozených třídách.

## <a name="what-your-custom-dfx-routine-does"></a><a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a>Co vaše vlastní DFX rutina dělá

Z této diskuse je zřejmé, že nejdůležitější operací implementovanou v libovolné funkci DFX musí být `GetRows`schopnost nastavit požadované datové struktury pro úspěšné volání . Existuje řada dalších operací, které musí podporovat funkci DFX, ale žádná tak `GetRows` důležitá nebo složitá jako správná příprava na volání.

Použití DFX je popsáno v online dokumentaci. V podstatě existují dva požadavky. Nejprve musí být členové `CDaoRecordset` přidáni do odvozené třídy pro každé vázané pole a parametr. Po `CDaoRecordset::DoFieldExchange` tomto by měla být přepsána. Všimněte si, že datový typ člena je důležité. Měla by odpovídat datům z pole v databázi nebo by měla být alespoň konvertibilní s tímto typem. Například číselné pole v databázi, například dlouhé celé číslo, lze vždy `CString` převést na text a svázané s členem, ale textové pole v databázi nemusí být nutně převedeno na číselnou reprezentaci, například dlouhé celé číslo a vázané na dlouhý celý člen. DAO a databázový stroj Microsoft Jet jsou zodpovědní za převod (spíše než Knihovna MFC).

## <a name="details-of-dfx_text"></a><a name="_mfcnotes_tn053_details_of_dfx_text"></a>Podrobnosti o DFX_Text

Jak již bylo zmíněno dříve, nejlepší způsob, jak vysvětlit, jak Funguje DFX je pracovat prostřednictvím příkladu. Pro tento účel prochází vnitřní `DFX_Text` by měl fungovat docela dobře pomoci poskytnout alespoň základní pochopení DFX.

- `AddToParameterList`

   Tato operace vytvoří klauzuli SQL`Parameters <param name>, <param type> ... ;` **PARAMETERS** (" ") vyžadožoto jet. Každý parametr je pojmenován a zadán (jak je uvedeno ve volání RFX). Chcete-li `CDaoFieldExchange::AppendParamType` zobrazit názvy jednotlivých typů, podívejte se na funkci funkce. V případě `DFX_Text`, je použitým typem **text**.

- `AddToSelectList`

   Vytvoří klauzuli SQL **SELECT.** To je docela přímočaré, protože název sloupce určený voláním`SELECT <column name>, ...`DFX je jednoduše připojen (" ").

- `BindField`

   Nejsložitější operace. Jak již bylo zmíněno dříve, je zde `GetRows` nastavena struktura vazby DAO používaná. Jak můžete vidět z `DFX_Text` kódu v typech informací ve struktuře patří typ DAO `DFX_Text`použité (**DAO_CHAR** nebo **DAO_WCHAR** v případě ). Kromě toho je také nastaven typ použité vazby. V dřívější `GetRows` části byla popsána pouze krátce, ale stačilo vysvětlit, že typ vazby používané MFC je vždy přímá adresa vazby (**DAOBINDING_DIRECT**). Kromě toho pro vazby sloupce `DFX_Text`proměnné délky (jako) vazba zpětného volání se používá tak, aby knihovna MFC můžete řídit přidělení paměti a zadat adresu správné délky. To znamená, že knihovna MFC může vždy říct DAO "kam" umístit data, což umožňuje vazbu přímo na členské proměnné. Zbytek struktury vazby je vyplněn a další mise jako adresa funkce zpětného volání přidělení paměti a typ vazby sloupce (vazba podle názvu sloupce).

- `BindParam`

   Jedná se o jednoduchou operaci, která volá `SetParamValue` s hodnotou parametru zadanou v členu parametru.

- `Fixup`

   Vyplní stav **NULL** pro každé pole.

- `SetFieldNull`

   Tato operace pouze označí stav každého pole jako **hodnotu NULL** a nastaví hodnotu členské proměnné na **PSEUDO_NULL**.

- `SetDirtyField`

   Volání `SetFieldValue` pro každé pole označené špinavé.

Všechny zbývající operace se zabývají pouze pomocí mezipaměti dat. Mezipaměť dat je další vyrovnávací paměť dat v aktuálním záznamu, která se používá k zjednodušení určitých věcí. Například "špinavá" pole mohou být automaticky detekována. Jak je popsáno v online dokumentaci, lze jej zcela vypnout nebo na úrovni pole. Implementace vyrovnávací paměti využívá mapu. Tato mapa se používá k přizpůsobení dynamicky přidělených kopií dat s adresou `CDaoRecordset` pole "vázané" (nebo odvozeného datového člena).

- `AllocCache`

   Dynamicky přiděluje hodnotu pole uložené v mezipaměti a přidává ji do mapy.

- `FreeCache`

   Odstraní hodnotu pole uložené v mezipaměti a odebere ji z mapy.

- `StoreField`

   Zkopíruje aktuální hodnotu pole do mezipaměti dat.

- `LoadField`

   Zkopíruje hodnotu uloženou v mezipaměti do člena pole.

- `MarkForAddNew`

   Zkontroluje, zda aktuální hodnota pole není**null** a v případě potřeby ji označí znečištěnou.

- `MarkForEdit`

   Porovná aktuální hodnotu pole s mezipamětí dat a v případě potřeby označí znečištěné.

> [!TIP]
> Modelujte vlastní rutiny DFX na stávajících rutinách DFX pro standardní datové typy.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
