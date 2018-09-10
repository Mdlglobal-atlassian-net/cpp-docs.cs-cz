---
title: 'TN043: Rutiny RFX | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- RFX
dev_langs:
- C++
helpviewer_keywords:
- RFX (record field exchange), architecture
- TN043
- RFX (record field exchange)
ms.assetid: f552d0c1-2c83-4389-b472-42c9940aa713
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1266097f9d548630459a3fb45ed75edb811deea
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317339"
---
# <a name="tn043-rfx-routines"></a>TN043: Rutiny RFX

> [!NOTE]
> Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Tato poznámka popisuje architekturu pole záznamu (RFX) systému exchange. Také popisuje, jak psát **RFX_** postup.

## <a name="overview-of-record-field-exchange"></a>Přehled výměna pole záznamu

Všechny funkce polí záznamů se provádějí s kódem jazyka C++. Neexistují žádné zvláštní prostředky nebo magic makra. Srdce mechanismu, který je virtuální funkci, která musí být přepsána nastaveními v každé záznamů odvozené třídy. Vždy nachází v tomto formuláři:

```cpp
void CMySet::DoFieldExchange(CFieldExchange* pFX)
{
    //{{AFX_FIELD_MAP(CMySet)
        <recordset exchange field type call>
        <recordset exchange function call>
    //}}AFX_FIELD_MAP
}
```

Afx – komentáře zvláštní formát umožňují ClassWizard k vyhledání a úpravy kódu v rámci této funkce. Kód, který není kompatibilní s ClassWizard by měl umístit mimo speciální formátu komentáře.

Ve výše uvedeném příkladu \<recordset_exchange_field_type_call > je ve formátu:

```cpp
pFX->SetFieldType(CFieldExchange::outputColumn);
```

a \<recordset_exchange_function_call > je ve formátu:

```cpp
RFX_Custom(pFX, "Col2", m_Col2);
```

Většina **RFX_** funkce mají tři argumenty, jak je uvedeno výše, ale některé (třeba `RFX_Text` a `RFX_Binary`) mají další volitelné argumenty.

Více než jeden **RFX_** může být součástí každého `DoDataExchange` funkce.

Viz "afxdb.h' seznam všech záznamů pole exchange rutiny součástí knihovny MFC.

Volání záznamů pole představují způsob, jak registrace umístění v paměti (obvykle datové členy) k ukládání dat pole `CMySet` třídy.

## <a name="notes"></a>Poznámky

Funkce pole sady záznamů jsou navrženy pro práci jenom s `CRecordset` třídy. Nejsou obecně použitelný pro všechny ostatní třídy knihovny MFC.

Počáteční hodnoty dat jsou nastavené v konstruktoru standard C++, obvykle v bloku s `//{{AFX_FIELD_INIT(CMylSet)` a `//}}AFX_FIELD_INIT` komentáře.

Každý **RFX_** funkci musí podporovat různé operace, od vrácení změny stavu pole k archivaci pole v rámci přípravy pro úpravy pole.

Každá funkce, která volá `DoFieldExchange` (například `SetFieldNull`, `IsFieldDirty`), provádí vlastní inicializaci po volání `DoFieldExchange`.

## <a name="how-does-it-work"></a>Jak to funguje

Nemusíte pochopit následující, abyste mohli používat výměna polí záznamu. Pochopení, jak to funguje na pozadí vám pomůže však zapisovat exchange procedury.

`DoFieldExchange` Členská funkce je stejně jako `Serialize` členské funkce – je zodpovědná za získání nebo nastavení dat do a z externích formuláře (v tomto případu sloupcích z výsledku dotazu ODBC) z/do data členů ve třídě. *PFX* parametr je kontext pro provedení výměny dat a je podobný *CArchive* parametr `CObject::Serialize`. *PFX* ( `CFieldExchange` objekt) má indikátor operace, které je podobné, ale generalizace *CArchive* příznak směru. RFX funkce může mít pro podporu následujících operací:

- `BindParam` – Označuje, kde ODBC, načtěte data parametrů

- `BindFieldToColumn` – Pokud ODBC musí načtení/uložení dat outputColumn označení

- `Fixup` – Nastavte `CString/CByteArray` délky, nastavte hodnotu NULL stav bit

- `MarkForAddNew` – Mark nesprávné, pokud hodnota změnila metodu AddNew volat

- `MarkForUpdate` – Mark nesprávné, pokud hodnota změnila, protože volání úpravy

- `Name` – Přidat názvy polí pro pole označena za nečistá

- `NameValue` – Přidat "\<název sloupce > =" pro pole označena za nečistá

- `Value` – Připojit "" následované oddělovač, jako jsou "," nebo ".

- `SetFieldDirty` – Nastavte stav bit změny (například změněné) pole

- `SetFieldNull` – Nastavte stav verze určující hodnotu null pro pole

- `IsFieldDirty` – Návratová hodnota bit změny stavu

- `IsFieldNull` – Vrácení hodnoty null stavu verze

- `IsFieldNullable` – Vrací TRUE, pokud pole může obsahovat hodnoty NULL

- `StoreField` – Hodnota pole archiv

- `LoadField` – Znovu načte hodnota archivované pole

- `GetFieldInfoValue` – Vrátí obecné informace pro pole

- `GetFieldInfoOrdinal` – Vrátí obecné informace pro pole

## <a name="user-extensions"></a>Rozšíření uživatele

Existuje několik způsobů, jak rozšířit mechanismus RFX výchozí. Můžeš

- Přidáte nové datové typy. Příklad:

    ```cpp
    CBookmark
    ```

- Přidáte nové postupy exchange (RFX_).

    ```cpp
    void AFXAPI RFX_Bigint(CFieldExchange* pFX,
        const char *szName,
        BIGINT& value);
    ```

- Máte `DoFieldExchange` členskou funkci podmíněně zahrnout další volání funkce RFX nebo jiné platné příkazy jazyka C++.

    ```cpp
    while (posExtraFields != NULL)
    {
        RFX_Text(pFX,
        m_listName.GetNext(posExtraFields),
        m_listValue.GetNext(posExtraValues));
    }
    ```

> [!NOTE]
> Takový kód nelze upravit pomocí ClassWizard a měli použít pouze vně speciální formátu komentáře.

## <a name="writing-a-custom-rfx"></a>Psaní vlastních RFX

Zápis funkce RFX vlastní, doporučujeme zkopírovat existující funkce RFX a upravit pro vlastní účely. Výběr správné RFX kopírování můžete značně zjednodušují vaši úlohu. Některé funkce RFX mají některé jedinečné vlastnosti, které byste měli vzít v úvahu při rozhodování, kterého chcete kopírovat.

`RFX_Long` a `RFX_Int`: Jedná se o nejjednodušší funkcí RFX. Hodnota dat není nutné žádné speciální interpretaci a velikost dat je pevná.

`RFX_Single` a `RFX_Double`: jako rfx_long – rfx_int – výše, tyto funkce jsou jednoduché a můžete provést pomocí výchozí implementace často. Ukládají se v dbflt.cpp místo dbrfx.cpp, ale povolit načtení modulu runtime s plovoucí desetinnou čárkou bodu knihovny, pouze pokud nejsou explicitně odkaz.

`RFX_Text` a `RFX_Binary`: tyto dvě funkce předběžné přidělení statické vyrovnávací paměť pro uložení řetězce nebo binární informace a zaregistrujte vyrovnávací paměti s ODBC SQLBindCol místo registrace & vá hodnota. Z tohoto důvodu mají tyto dvě funkce velké množství kódu zvláštní případy.

`RFX_Date`: ODBC vrátí informace o datu a času jejich vlastní TIMESTAMP_STRUCT z datové struktury. Tato funkce dynamicky přiděluje TIMESTAMP_STRUCT z jako proxy "server" pro odesílání a přijímání dat Datum čas. Různé operace musí přenášet informace o datu a času mezi C++ `CTime` objektu a TIMESTAMP_STRUCT z proxy serveru. To komplikuje tato funkce výrazně, ale je dobrým příkladem toho, jak používat proxy server pro přenos dat.

`RFX_LongBinary`: Toto je pouze knihovny tříd RFX funkce, která se nepoužívá pro příjem a odesílání dat vazba sloupce. Tato funkce ignoruje BindFieldToColumn operace a místo toho během operace opravy alokují prostor pro příchozí data SQL_LONGVARCHAR nebo SQL_LONGVARBINARY pak provede volání rozhraní SQLGetData k načtení hodnoty do přidělené úložiště. Při přípravě k odesílání dat zpět do zdroje dat (například operace pár Názevhodnota a hodnota), tato funkce využívá funkce DATA_AT_EXEC ODBC. Zobrazit [Technická poznámka 45](../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md) Další informace o práci s SQL_LONGVARBINARY a SQL_LONGVARCHARs.

Při sestavování vlastních **RFX_** funkce, často budete moct používat `CFieldExchange::Default` implementovat danou operaci. Podívejte se na provádění výchozí příslušná operace. Pokud se provádí operace by zápis v vaše **RFX_** můžete delegovat na funkci `CFieldExchange::Default`. Můžete zobrazit příklady volání `CFieldExchange::Default` v dbrfx.cpp

Je potřeba volat `IsFieldType` na začátku funkce RFX a vrátit okamžitě, pokud vrátí hodnotu FALSE. Tento mechanismus udržuje parametr operace prováděné na *outputColumns*a naopak (jako je volání `BindParam` na *outputColumn*). Kromě toho `IsFieldType` automaticky uchovává informace o počet *outputColumns* (*m_nFields*) a params (*m_nParams*).

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)  
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)  
