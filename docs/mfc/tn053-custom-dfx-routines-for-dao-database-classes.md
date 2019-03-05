---
title: 'TN053: Vlastní rutiny DFX pro databázové třídy DAO'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.dfx
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
ms.openlocfilehash: b610604c1b7a68128dc9eb6fb5515225ed22b16e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282406"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053: Vlastní rutiny DFX pro databázové třídy DAO

> [!NOTE]
>  Prostředí Visual C++ a Průvodce nepodporuje rozhraní DAO (i když jsou součástí třídy DAO a můžete stále použít). Microsoft doporučuje, abyste použili [šablony technologie OLE DB](../data/oledb/ole-db-templates.md) nebo [rozhraní ODBC a MFC](../data/odbc/odbc-and-mfc.md) pro nové projekty. DAO byste měli používat jenom v udržování existujících aplikací.

Tato technická Poznámka popisuje mechanismem výměny (DFX) DAO pole záznamu. Pro lepší porozumění tomu, co se děje v rutiny DFX `DFX_Text` funkce bude podrobně popsaný v jako příklad. Jako další zdroje informací, které mají tato technická Poznámka můžete zkontrolovat kód pro ostatní jednotlivých funkcí DFX. Pravděpodobně nebude nutné vlastní rutiny DFX tak často, jak může být nutné vlastní rutiny RFX (používá se s databázovými třídami rozhraní ODBC).

Tato technická poznámka obsahuje:

- DFX Overview

- [Příklady](#_mfcnotes_tn053_examples) pomocí záznamu – Record Field Exchange a dynamické vazby

- [Jak funguje DFX](#_mfcnotes_tn053_how_dfx_works)

- [Co dělá váš vlastní DFX rutina](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)

- [Podrobnosti o dfx_text –](#_mfcnotes_tn053_details_of_dfx_text)

**DFX Overview**

DAO mechanismem výměny pole záznamu (DFX) slouží ke zjednodušení procesu načítání a aktualizace dat při použití `CDaoRecordset` třídy. Proces je zjednodušeno pomocí datové členy `CDaoRecordset` třídy. Odvozením z `CDaoRecordset`, můžete přidat datové členy odvozené třídy, představující každé pole v tabulce nebo dotazu. Tento mechanismus "statická vazba" je jednoduchý, ale nemusí být metodu načtení nebo aktualizace dat podle výběru pro všechny aplikace. DFX načte všechny vázané pole pokaždé, když se změní aktuální záznam. Pokud vyvíjíte aplikace náročné na výkon, který nevyžaduje načítání každé pole při změně měny "dynamická vazba" prostřednictvím `CDaoRecordset::GetFieldValue` a `CDaoRecordset::SetFieldValue` mohou být data metody přístupu podle výběru.

> [!NOTE]
>  DFX a dynamické vazby se vzájemně nevylučují, aby mohly využívat hybridní použití statické a dynamické vazby.

## <a name="_mfcnotes_tn053_examples"></a> Příklad 1 – Použití záznamu – Record Field Exchange pouze

(předpokládá `CDaoRecordset` – odvozené třídy `CMySet` otevřen)

```
// Add a new record to the customers table
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```

**Příklad 2: Použití dynamické vazby**

(předpokládá použití `CDaoRecordset` třídy `rs`, a je již otevřen)

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

**Příklad 3 – Používání z rozhraní DAO výměna pole záznamu a dynamické vazby**

(předpokládá procházení daty o zaměstnancích s `CDaoRecordset`-odvozené třídy `emp`)

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

## <a name="_mfcnotes_tn053_how_dfx_works"></a> Jak funguje DFX

Mechanismus DFX funguje podobným způsobem jako pole záznamu mechanismem výměny (RFX) používané v rámci tříd knihovny MFC rozhraní ODBC. Principy DFX a RFX jsou stejné, ale existují mnoho rozdíly interní. Návrh DFX – funkce byla tak, aby jednotlivé rutiny DFX sdílí prakticky veškerému kódu. Na nejvyšší úrovni DFX pouze se několik věcí.

- DFX konstrukce SQL **vyberte** klauzule a SQL **parametry** klauzule v případě potřeby.

- DFX vytvoří strukturu vazby používá pro rozhraní DAO `GetRows` – funkce (podrobněji dále).

- DFX spravuje vyrovnávací paměť dat, které slouží ke zjištění změny pole (Pokud se právě používá dvojité ukládání do vyrovnávací paměti)

- DFX spravuje **NULL** a **čistý** stav pole a nastaví hodnoty v případě potřeby na aktualizace.

V srdci DFX mechanismus je `CDaoRecordset` odvozené třídy `DoFieldExchange` funkce. Tato funkce odesílá volání jednotlivých DFX – funkce typu příslušné operace. Před voláním `DoFieldExchange` vnitřní funkce MFC nastaví typ operace. Následující seznam obsahuje různé typy operací a stručný popis.

|Operace|Popis|
|---------------|-----------------|
|`AddToParameterList`|Klauzule parametry sestavení|
|`AddToSelectList`|Klauzule SELECT sestavení|
|`BindField`|Nastaví strukturu vazby|
|`BindParam`|Nastaví hodnoty parametru|
|`Fixup`|Nastaví stav hodnotu NULL|
|`AllocCache`|Přidělí mezipaměti změny kontroly|
|`StoreField`|Uloží aktuální záznam do mezipaměti|
|`LoadField`|Obnovení mezipaměti, aby hodnoty členů|
|`FreeCache`|Uvolní mezipaměti|
|`SetFieldNull`|Nastaví pole stavu & hodnota, která má hodnotu NULL|
|`MarkForAddNew`|Označí pole nezapsané není-li PSEUDO NULL|
|`MarkForEdit`|Pokud změny pole značky neshodují mezipaměti|
|`SetDirtyField`|Nastaví pole hodnoty, které jsou označeny jako nečisté|

V další části, bude se každá operace vysvětlené podrobněji pro `DFX_Text`.

Nejdůležitější funkce pochopit o procesu DAO pole záznamu exchange je, že používá `GetRows` funkce `CDaoRecordset` objektu. Rozhraní DAO `GetRows` funkce funguje v několika způsoby. Tato technická Poznámka bude pouze Krátce popište `GetRows` je mimo rozsah této Technická poznámka.

DAO `GetRows` můžete pracovat několika způsoby.

- To můžete načíst více polí dat a více záznamů najednou. To umožňuje rychlejší přístup k datům s komplikace pro řešení problémů s strukturu velkých objemů dat a příslušný posun k jednotlivým polím a pro každý záznam dat ve struktuře. MFC nevyužívá tohoto více záznamu načítání mechanismus.

- Dalším způsobem `GetRows` můžete umožňující programátorům zadejte adresy vazby pro načtená data každého pole pro jeden záznam dat je práce.

- DAO – bude také "zpětné volání" do volajícího pro sloupce s proměnlivou délkou aby volající přidělení paměti. Tato druhá funkce má výhodu, že minimalizovat počet kopií dat, stejně jako umožňuje přímé ukládání dat do členy třídy ( `CDaoRecordset` odvozené třídy). Tento druhý mechanismus je metoda knihovna MFC používá k vytvoření vazby na datové členy v `CDaoRecordset` odvozené třídy.

##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a> Co dělá váš vlastní DFX rutina

Je zřejmé z této diskuse nejdůležitější operace implementované ve všech funkcích DFX musí zajistit možnost upravit požadované datové struktury tak, aby úspěšně volat `GetRows`. Existuje mnoho dalších operací, které funkce DFX musí podporovat i, ale žádný jako důležité nebo komplexního, jako správně Příprava `GetRows` volání.

Použití DFX je popsaný v online dokumentaci. V podstatě existují dva požadavky. Nejprve musí být členy přidané do `CDaoRecordset` odvozené třídy pro každou vázané pole a parametrů. Následující `CDaoRecordset::DoFieldExchange` by měla být potlačena. Všimněte si, že datový typ člena je důležité. Ji by měl odpovídat data z pole v databázi nebo alespoň být převeden na tento typ. Můžete například číselná pole v databázi, jako je long integer, vždy převedeno na text a vázán na `CString` člen, ale textové pole v databázi může nemusí být převést na číselnou reprezentaci, jako je například dlouhé celé číslo a vázaný k dlouhé integ ER člena. Rozhraní DAO a databázový stroj Microsoft Jet zodpovídají za převod (spíše než knihovny MFC).

##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a> Podrobnosti o dfx_text –

Jak již bylo zmíněno dříve, je nejlepší způsob, jak popisují, jak funguje DFX projít si příklad. Pro tento účel prostřednictvím interních dat `DFX_Text` měl by být dostačující poměrně pomáhají aspoň základní znalosti o DFX.

- `AddToParameterList`

   Tato operace vytvoří SQL **parametry** – klauzule ("`Parameters <param name>, <param type> ... ;`") vyžaduje Jet. Každý parametr je s názvem a typem (jak je uvedeno ve volání funkce RFX). Podívat se na funkci `CDaoFieldExchange::AppendParamType` funkci zobrazíte názvy jednotlivých typů. V případě třídy `DFX_Text`, je typ použitý **text**.

- `AddToSelectList`

   Sestavení SQL **vyberte** klauzuli. To je poměrně jasný název sloupce zadané ve volání DFX je jednoduše připojit ("`SELECT <column name>, ...`").

- `BindField`

   Nejvíce komplexní operací. Jak je uvedeno nahoře, to je, kde struktura vazby DAO používané `GetRows` nastaven. Jak je vidět z kódu v `DFX_Text` typy informací ve struktuře, které zahrnují DAO typ použitý (**DAO_CHAR** nebo **DAO_WCHAR** v případě třídy `DFX_Text`). Kromě toho typ vazby používá se také nastavit. V předchozím oddílu `GetRows` byla pouze stručně popisuje, ale je dostatečná k vysvětlení, že typ vazby využívané prostředím MFC je vždy vazbu s přímým přístupem adresy (**DAOBINDING_DIRECT**). Kromě toho pro vazbu na sloupec proměnné délky (jako je `DFX_Text`) zpětné vazby se používá tak, aby knihovny MFC můžete řídit přidělování paměti a zadejte adresu správnou délku. Co to znamená, že knihovny MFC můžete vždy jasně určit DAO "kde" umístění dat, což umožní vazbu přímo do proměnné členů. Zbytek struktury vazby se vyplní věci, jako je adresa funkce zpětného volání přidělení paměti a typ vazby sloupce (vazby podle názvu sloupce).

- `BindParam`

   Toto je jednoduchá operace, která volá `SetParamValue` se parametr hodnoty zadané v parametr člena.

- `Fixup`

   Vyplní **NULL** stav pro každé pole.

- `SetFieldNull`

   Tato operace označí pouze stav každé pole jako **NULL** a nastaví hodnotu proměnné člena na **PSEUDO_NULL**.

- `SetDirtyField`

   Volání `SetFieldValue` pro každé pole označena za nečistá.

Všechny zbývající operace řešit pouze pomocí datové mezipaměti. Mezipaměť dat je další vyrovnávací paměť dat v aktuální záznam, který se využívá k Prognózování některé aspekty jednodušší. Například je možné automaticky detekovat "nezapsané" pole. Jak je popsáno v online dokumentaci ho vypnete zcela nebo na úrovni pole. Provádění vyrovnávací paměti využívá mapu. Toto mapování se používá shodu se dynamicky přidělené kopie dat s adresou "vázané" pole (nebo `CDaoRecordset` odvozené datový člen).

- `AllocCache`

   Dynamicky přiděluje hodnotu pole v mezipaměti a přidá jej do mapy.

- `FreeCache`

   Odstraní hodnotu pole v mezipaměti a odebere ji z mapy.

- `StoreField`

   Zkopíruje aktuální hodnotu pole do datové mezipaměti.

- `LoadField`

   Hodnota uložená v mezipaměti se zkopíruje do členu pole.

- `MarkForAddNew`

   Zkontroluje, zda je aktuální hodnota pole není**NULL** a označí změny v případě potřeby.

- `MarkForEdit`

   Porovná aktuální hodnotu pole s mezipaměť dat a označí změny v případě potřeby.

> [!TIP]
> Vlastní rutiny DFX model na existující rutiny DFX pro standardní datových typů.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
