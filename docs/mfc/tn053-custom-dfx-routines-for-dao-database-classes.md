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
ms.openlocfilehash: 6dde96520d9472726da86f8da295770cccc5d42c
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303432"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053: Vlastní rutiny DFX pro databázové třídy DAO

> [!NOTE]
>  Rozhraní DAO se používá s databázemi Access a je podporované prostřednictvím sady Office 2013. Rozhraní DAO 3,6 je finální verze a je považována za zastaralou. Vizuální C++ prostředí a Průvodci nepodporují rozhraní DAO (i když třídy rozhraní DAO jsou zahrnuty a je možné je nadále používat). Společnost Microsoft doporučuje, abyste pro nové projekty používali [šablony OLE DB](../data/oledb/ole-db-templates.md) nebo [rozhraní ODBC a knihovnu MFC](../data/odbc/odbc-and-mfc.md) . V údržbě stávajících aplikací byste měli používat jenom rozhraní DAO.

Tato technická Poznámka popisuje mechanismus výměny pole záznamu (DFX) DAO. Aby bylo možné pochopit, co se děje v rutinách DFX, funkce `DFX_Text` bude podrobně vysvětlena jako příklad. Jako další zdroj informací k této technické poznámce si můžete prohlédnout kód pro ostatní jednotlivé funkce DFX. Pravděpodobně nebudete potřebovat vlastní rutinu DFX, jak často budete potřebovat vlastní rutinu RFX (používá se u databázových tříd ODBC).

Tato technická Poznámka obsahuje:

- Přehled DFX

- [Příklady](#_mfcnotes_tn053_examples) použití výměny pole záznamu rozhraní DAO a dynamické vazby

- [Jak funguje DFX](#_mfcnotes_tn053_how_dfx_works)

- [Co dělá vlastní rutina DFX](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)

- [Podrobnosti o DFX_Text](#_mfcnotes_tn053_details_of_dfx_text)

**DFX Overview**

Mechanismus výměny pole záznamu DAO (DFX) se používá ke zjednodušení postupu načítání a aktualizace dat při použití třídy `CDaoRecordset`. Proces je zjednodušený pomocí datových členů třídy `CDaoRecordset`. Odvozením z `CDaoRecordset`můžete přidat datové členy do odvozené třídy reprezentující každé pole v tabulce nebo dotazu. Tento mechanismus statické vazby je jednoduchý, ale nemusí se jednat o metodu pro načtení nebo aktualizaci dat, kterou si můžete vybrat pro všechny aplikace. DFX načte každé vázané pole pokaždé, když se změní aktuální záznam. Pokud vyvíjíte aplikaci citlivou na výkon, která nevyžaduje načítání každého pole při změně měny, může být "dynamická vazba" prostřednictvím `CDaoRecordset::GetFieldValue` a `CDaoRecordset::SetFieldValue` může být metoda přístupu k datům podle volby.

> [!NOTE]
>  DFX a dynamická vazba se vzájemně nevylučují, takže je možné použít hybridní použití statické a dynamické vazby.

## <a name="_mfcnotes_tn053_examples"></a>Příklad 1 – použití pouze výměny pole záznamu DAO

(předpokládá `CDaoRecordset` – odvozená třída `CMySet` už je otevřená)

```
// Add a new record to the customers table
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```

**Příklad 2 – použití pouze dynamické vazby**

(předpokládá použití třídy `CDaoRecordset` `rs`a je už otevřená)

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

**Příklad 3 – použití výměny pole záznamu DAO a dynamické vazby**

(předpokládá procházení dat zaměstnanců pomocí `emp`třídy odvozené od `CDaoRecordset`)

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

Mechanismus DFX funguje podobným způsobem jako mechanismus výměny pole záznamu (RFX) používaný třídami MFC rozhraní ODBC. Principy DFX a RFX jsou stejné, ale existuje mnoho interních rozdílů. Návrh funkcí DFX byl takový, že prakticky všechen kód sdílí jednotlivé rutiny DFX. Na nejvyšší úrovni DFX jenom pár věcí.

- DFX vytvoří klauzuli **Select** jazyka SQL a klauzuli **Parameters parametrů** SQL, pokud je to nutné.

- DFX vytvoří strukturu vazeb, kterou používá funkce `GetRows` DAO (Další informace najdete později).

- DFX spravuje vyrovnávací paměť, která se používá ke zjišťování nezměněných polí (Pokud se používá dvojité ukládání do vyrovnávací paměti).

- DFX spravuje pole **null** a **Dirty** stav a v případě potřeby nastavuje hodnoty v případě nutnosti aktualizace.

Na srdci mechanismu DFX je `CDaoRecordset` funkce odvozené třídy `DoFieldExchange`. Tato funkce odesílá volání jednotlivých funkcí DFX pro příslušný typ operace. Před voláním `DoFieldExchange` interní MFC funkce nastavily typ operace. V následujícím seznamu jsou uvedeny různé typy operací a stručný popis.

|Operace|Popis|
|---------------|-----------------|
|`AddToParameterList`|Klauzule Build PARAMETERS|
|`AddToSelectList`|Build – klauzule SELECT|
|`BindField`|Nastaví strukturu vazby.|
|`BindParam`|Nastaví hodnoty parametrů|
|`Fixup`|Nastaví stav NULL.|
|`AllocCache`|Přiděluje mezipaměť pro kontrolu nečistých|
|`StoreField`|Uloží aktuální záznam do mezipaměti.|
|`LoadField`|Obnoví hodnoty do mezipaměti členů.|
|`FreeCache`|Volná mezipaměť|
|`SetFieldNull`|Nastaví hodnotu & stav pole na hodnotu NULL.|
|`MarkForAddNew`|Označí nezměněná pole, pokud není PSEUDO NULL.|
|`MarkForEdit`|Označí nezměněná pole, pokud neodpovídají mezipaměti.|
|`SetDirtyField`|Nastaví hodnoty polí označené jako nečisté.|

V další části jsou jednotlivé operace vysvětleny podrobněji pro `DFX_Text`.

Nejdůležitější funkce pro pochopení procesu výměny pole záznamu rozhraní DAO je, že používá funkci `GetRows` objektu `CDaoRecordset`. Funkce `GetRows` DAO může pracovat několika způsoby. Tato technická Poznámka bude stručně popsat `GetRows`, protože je mimo rámec této technické poznámky.
`GetRows` DAO může pracovat několika způsoby.

- Může najednou načíst několik záznamů a více polí dat. To umožňuje rychlejší přístup k datům s komplikací při práci s velkou datovou strukturou a příslušnými posuny pro každé pole a pro každý záznam dat ve struktuře. Knihovna MFC nevyužívá tento mechanismus načítání více záznamů.

- Další způsob, jak `GetRows` může pracovat, je poskytnout programátorům možnost zadat adresy vazeb pro načtená data každého pole pro jeden záznam dat.

- Rozhraní DAO také "volat zpět" do volajícího pro sloupce proměnné délky, aby volajícímu umožnil přidělit paměť. Tato druhá funkce má na paměti minimalizaci počtu kopií dat a umožňuje přímé ukládání dat do členů třídy (`CDaoRecordset` odvozené třídy). Tento druhý mechanismus je metoda, kterou knihovna MFC používá pro vytvoření vazby k datovým členům v `CDaoRecordset` odvozených třídách.

##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a>Co dělá vlastní rutina DFX

Z této diskuze je zřejmé, že nejdůležitější operace implementovaná v jakékoli funkci DFX musí být schopnost nastavit požadované datové struktury k úspěšnému volání `GetRows`. K dispozici je řada dalších operací, které musí funkce DFX podporovat, ale nejsou žádné jako důležité nebo složité jako správné připravení `GetRows` volání.

Použití DFX je popsané v online dokumentaci. V podstatě existují dva požadavky. Nejdříve je nutné přidat členy do odvozené třídy `CDaoRecordset` pro každé vázané pole a parametr. Následující `CDaoRecordset::DoFieldExchange` by se měly přepsat. Všimněte si, že datový typ členu je důležitý. Měl by odpovídat datům z pole v databázi nebo aspoň převést na tento typ. Například číselné pole v databázi, jako je dlouhé celé číslo, může být vždy převedeno na text a svázáno s `CString`m členem, ale textové pole v databázi nemusí být nutně převedeno na číselnou reprezentaci, jako je dlouhé celé číslo a svázáno s datovým členem Long Integer. Rozhraní DAO a databázový stroj Microsoft Jet jsou zodpovědné za převod (nikoli MFC).

##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a>Podrobnosti o DFX_Text

Jak bylo zmíněno dříve, nejlepším způsobem, jak vysvětlit fungování DFX, je využít příklad. Pro účely tohoto účelu by interní `DFX_Text` měla fungovat poměrně dobře, aby bylo možné zajistit nejméně základní porozumění DFX.

- `AddToParameterList`

   Tato operace sestaví klauzuli **Parameters** SQL (`Parameters <param name>, <param type> ... ;`), kterou vyžaduje stroj Jet. Každý parametr má název a je typu (jak je uvedeno v volání RFX). Pokud chcete zobrazit názvy jednotlivých typů, podívejte se na funkci `CDaoFieldExchange::AppendParamType` funkce. V případě `DFX_Text`se používá typ **text**.

- `AddToSelectList`

   Vytvoří klauzuli **Select** jazyka SQL. Tato možnost je poměrně přímá, protože název sloupce určený voláním DFX je jednoduše připojen ("`SELECT <column name>, ...`").

- `BindField`

   Nejsložitější operace. Jak už bylo zmíněno dříve, kde je nastavená struktura vazby rozhraní DAO používaná `GetRows`. Jak vidíte z kódu v `DFX_Text` typy informací ve struktuře zahrnují použit typ DAO (**DAO_CHAR** nebo **DAO_WCHAR** v případě `DFX_Text`). Kromě toho je také nastaven typ použité vazby. V dřívější části `GetRows` bylo popsáno pouze krátce, ale bylo dostačující pro vysvětlení, že typ vazby používaný knihovnou MFC je vždy přímá vazba adres (**DAOBINDING_DIRECT**). Kromě pro vazbu sloupce s proměnlivou délkou (například `DFX_Text`) se používá vazba zpětného volání, aby mohla knihovna MFC řídit přidělování paměti a zadat adresu správné délky. To znamená, že knihovna MFC může vždy sdělit rozhraní DAO "Where" pro vložení dat, čímž umožňuje vazbu přímo na členské proměnné. Zbytek struktury vazby je vyplněn s akcemi, jako je adresa funkce zpětného volání přidělení paměti a typ vazby sloupce (vazba podle názvu sloupce).

- `BindParam`

   Toto je jednoduchá operace, která volá `SetParamValue` s hodnotou parametru zadanou v parametru member.

- `Fixup`

   Vyplní stav **null** pro každé pole.

- `SetFieldNull`

   Tato operace označí pouze všechny stavy pole jako **null** a nastaví hodnotu členské proměnné na **PSEUDO_NULL**.

- `SetDirtyField`

   Volá `SetFieldValue` pro každé pole s označením undirty.

Všechny zbývající operace se týkají pouze používání mezipaměti dat. Mezipaměť dat je dodatečná vyrovnávací paměť dat v aktuálním záznamu, která se používá k jednoduššímu provádění určitých věcí. Například pole "dirty" mohou být automaticky rozpoznána. Jak je popsáno v online dokumentaci, může být úplně vypnutá nebo na úrovni pole. Implementace vyrovnávací paměti využívá mapu. Tato mapa se používá ke spárování dynamicky přidělených kopií dat s adresou "vázaného" pole (nebo `CDaoRecordset` odvozeného datového členu).

- `AllocCache`

   Dynamicky přidělí hodnotu pole v mezipaměti a přidá ji do mapy.

- `FreeCache`

   Odstraní hodnotu pole v mezipaměti a odebere ji z mapy.

- `StoreField`

   Zkopíruje aktuální hodnotu pole do mezipaměti dat.

- `LoadField`

   Zkopíruje hodnotu uloženou v mezipaměti do členu pole.

- `MarkForAddNew`

   Zkontroluje, jestli je hodnota aktuálního pole**nenulová** a v případě potřeby ji označí jako nezměněnou.

- `MarkForEdit`

   Porovná hodnotu aktuálního pole s mezipamětí dat a v případě potřeby označí nečisté.

> [!TIP]
> Modelujte vlastní rutiny DFX na stávajících rutinách DFX pro standardní datové typy.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
