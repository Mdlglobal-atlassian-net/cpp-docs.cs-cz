---
title: 'TN045: Podpora prostředí MFC a databáze pro Long Varchar a Varbinary | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.data
dev_langs:
- C++
helpviewer_keywords:
- TN045
- Varbinary data type
- Varchar data type
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d22080532f36be18d32d29a24da9c5e3738fb275
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068980"
---
# <a name="tn045-mfcdatabase-support-for-long-varcharvarbinary"></a>TN045: Podpora prostředí MFC a databáze pro typy Long Varchar/Varbinary

> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Tato poznámka popisuje, jak načíst a odeslat rozhraní ODBC **SQL_LONGVARCHAR** a **SQL_LONGVARBINARY** databáze tříd datových typů pomocí knihovny MFC.

## <a name="overview-of-long-varcharvarbinary-support"></a>Přehled podpory Long Varchar/Varbinary

Rozhraní ODBC **SQL_LONG_VARCHAR** a **SQL_LONGBINARY** datové typy (dále jako dlouho datových sloupců do tohoto místa) může obsahovat velké objemy dat. Tato data můžete zpracovávat 3 způsoby:

- Vytvořte mu vazbu k `CString` / `CByteArray`.

- Vytvořte mu vazbu k `CLongBinary`.

- Nelze vytvořit vazbu na všech a načíst a odesílání hodnotu long – datový ručně, nezávisle na databázové třídy.

Každá ze tří metod obsahuje výhody a nevýhody.

Long – datový sloupce nejsou podporovány pro parametry dotazu. Jsou podporovány pouze pro outputColumns.

## <a name="binding-a-long-data-column-to-a-cstringcbytearray"></a>Vazba na CString/CByteArray – Long – datový sloupec

Výhody:

Tento přístup je srozumitelný a práci s známé třídy. Poskytuje rozhraní `CFormView` podporu `CString` s `DDX_Text`. Máte spoustu obecné řetězec nebo kolekce funkcí pomocí `CString` a `CByteArray` třídy kde můžete určit množství paměti přidělené místně pro uchování hodnoty data. Rozhraní framework udržuje staré kopii dat pole během `Edit` nebo `AddNew` volání funkce a rozhraní framework může automaticky rozpoznat změny dat za vás.

> [!NOTE]
>  Protože `CString` je navržená pro práci s daty znak a `CByteArray` ke zpracování binárních dat, doporučujeme umístit znaková data (**SQL_LONGVARCHAR**) do `CString`a binárních dat ( **SQL_LONGVARBINARY**) do `CByteArray`.

Pro funkce RFX `CString` a `CByteArray` mají další argument, který umožní přepsat výchozí velikost přidělené paměti pro uložení načtené hodnoty pro sloupec data. Poznámka: argument nMaxLength v deklaracích následující funkce:

```
void AFXAPI RFX_Text(CFieldExchange* pFX,
    const char *szName,
    CString& value,
    int nMaxLength = 255,
    int nColumnType =
    SQL_VARCHAR);

void AFXAPI RFX_Binary(CFieldExchange* pFX,
    const char *szName,
    CByteArray& value,
    int nMaxLength = 255);
```

Pokud načtete long – datový sloupec do `CString` nebo `CByteArray`, vrátí maximální množství dat je ve výchozím nastavení, 255 bajtů. Nic nad tuto hranici se ignoruje. V tomto případě rozhraní vyvolá výjimku **AFX_SQL_ERROR_DATA_TRUNCATED**. Naštěstí můžete explicitně zvýšit nMaxLength vyšší hodnoty, až **MAXINT**.

> [!NOTE]
>  Je hodnota nMaxLength využívané prostředím MFC se nastavit místní vyrovnávací paměť `SQLBindColumn` funkce. Toto je místní vyrovnávací paměti pro ukládání dat a nemá vliv na skutečně množství dat vrácených ovladač ODBC. `RFX_Text` a `RFX_Binary` pouze si ho volat pomocí `SQLFetch` k načtení dat z databáze back-end. Každý ovladač ODBC má jiné omezení množství dat, která může vrátit do jednoho načtení. Toto omezení může být mnohem menší než hodnotu nastavenou v nMaxLength, ve kterémžto případě výjimku **AFX_SQL_ERROR_DATA_TRUNCATED** bude vyvolána výjimka. Za těchto okolností, přejít k používání `RFX_LongBinary` místo `RFX_Text` nebo `RFX_Binary` tak, aby se dá načíst všechna data.

Vytvoří vazbu ClassWizard **SQL_LONGVARCHAR** k `CString`, nebo **SQL_LONGVARBINARY** k `CByteArray` za vás. Pokud chcete přidělit víc než 255 bajtů, do kterých můžete získat vaše long – datový sloupec, můžete potom zadejte explicitní hodnotu pro nMaxLength.

Long – datový sloupec je vázána k `CString` nebo `CByteArray`, aktualizuje pole funguje stejně jako když je vázán na SQL_**VARCHAR** nebo SQL_**VARBINARY**. Během `Edit`, hodnota dat se uloží do mezipaměti okamžitě a později při porovnání `Update` je volána k zjištění změny v datech hodnotu a nastavit čistý a odpovídajícím způsobem Null hodnoty pro sloupec.

## <a name="binding-a-long-data-column-to-a-clongbinary"></a>Vazba Long – datový sloupec CLongBinary

Pokud vaše long – datový sloupec může obsahovat více **MAXINT** bajtů dat, měli byste pravděpodobně zvážit načítání do `CLongBinary`.

Výhody:

To obnoví na celý long – datový sloupec až dostupné paměti.

Nevýhody:

Jsou data uložená v paměti. Tento přístup je také pro opravdu velké objemy dat nepřekonatelně drahé. Je nutné volat `SetFieldDirty` vázaných dat člen zajistit, pole je součástí `Update` operace.

Pokud načtete dlouhé datových sloupců do `CLongBinary`, databázové třídy zkontrolujte celková velikost long – datový sloupec a potom přidělit `HGLOBAL` dostatečně velký pro uložení je hodnota celého datového segmentu paměti. Databázové třídy pak načíst hodnotu všechna data do přidělená `HGLOBAL`.

Pokud zdroj dat nelze očekávanou velikost long – datový sloupec, rozhraní vyvolá výjimku **AFX_SQL_ERROR_SQL_NO_TOTAL**. Pokud se pokus o přidělení `HGLOBAL` selže, je vyvolána výjimka standardní paměti.

Vytvoří vazbu ClassWizard **SQL_LONGVARCHAR** nebo **SQL_LONGVARBINARY** k `CLongBinary` za vás. Vyberte `CLongBinary` jako typ proměnné v dialogovém okně Přidat členskou proměnnou. Poté přidá ClassWizard `RFX_LongBinary` volání vaše `DoFieldExchange` volání a zvýšit celkový počet vázaného pole.

K aktualizaci dlouho hodnoty dat sloupců, nejdřív Ujistěte se, že přidělená `HGLOBAL` je dostatečně velký pro nová data voláním **:: GlobalSize** na *m_hData* člena `CLongBinary`. Pokud je příliš malá, uvolněte `HGLOBAL` a přidělte jednu odpovídající velikost. Potom nastavte *m_dwDataLength* tak, aby odrážely novou velikost.

Jinak, pokud *m_dwDataLength* je větší než velikost dat, kterého nahrazujete, můžete zdarma a přidělit jinému uživateli `HGLOBAL`, nebo ponechat přiděleny. Ujistěte se, že označující počet bajtů v skutečně spotřebujete *m_dwDataLength*.

## <a name="how-updating-a-clongbinary-works"></a>Jak aktualizovat CLongBinary funguje

Není nutné pochopit, jak aktualizovat `CLongBinary` funguje, ale může být užitečné například o tom, jak odeslat hodnoty long – datový zdroj dat, pokud se rozhodnete tento třetí způsob popsaný níže.

> [!NOTE]
>  Aby se `CLongBinary` pole mají být zahrnuty v aktualizaci, musí explicitně volat `SetFieldDirty` pro pole. Pokud provedete změny pole, včetně nastavení jeho hodnoty Null, musí volat `SetFieldDirty`. Musíte také zavolat `SetFieldNull`, s druhý parametr je **FALSE**, označte pole tak, že má hodnotu.

Při aktualizaci `CLongBinary` pole, ODBC pro databázové třídy použít **DATA_AT_EXEC** mechanismus (na najdete v dokumentaci k rozhraní ODBC `SQLSetPos`společnosti rgbValue argument). Když rozhraní připraví příkazu insert nebo update místo přejdete `HGLOBAL` obsahující data, *adresu* z `CLongBinary` je nastaven jako *hodnotu* sloupce Místo toho a délka indikátor nastavena na **SQL_DATA_AT_EXEC**. Později, při odesílání příkazu update ke zdroji dat `SQLExecDirect` vrátí **SQL_NEED_DATA**. Toto upozornění rozhraní framework, že hodnota parametru pro tento sloupec je ve skutečnosti adresu `CLongBinary`. Rámec volá `SQLGetData` jednou očekává ovladač vrátit skutečná délka dat s malou vyrovnávací pamětí. Pokud ovladač vrátí skutečná délka binární velkých objektů (BLOB), znovu alokuje MFC tolik místa potřebného k načtení objektu BLOB. Pokud zdroj dat vrátí **SQL_NO_TOTAL**, označující, že nelze určit velikost objektu BLOB, budou knihovny MFC vytvořte menší bloky. Výchozí počáteční velikost je 64 kB a následné bloky bude dvojnásobek velikosti; například druhá bude 128 kb / s, třetí je 256 kB a tak dále. Počáteční velikost je možné konfigurovat.

## <a name="not-binding-retrievingsending-data-directly-from-odbc-with-sqlgetdata"></a>Vazba není: Načítání/odesílat Data přímo z rozhraní ODBC s SQLGetData

Pomocí této metody můžete úplně obejít databázové třídy a řešil long – datový sloupec.

Výhody:

Můžete ukládat do mezipaměti dat na disk v případě potřeby nebo rozhodnout dynamicky, kolik dat k načtení.

Nevýhody:

Neobdržíte rozhraní framework `Edit` nebo `AddNew` podpory který musíte napsat kód sami sebe k provádění základních funkcí (`Delete` funguje, protože se nejedná o úrovni operace sloupce).

Long – datový sloupec v tomto případě musí být v seznamu pro výběr sady záznamů, ale by neměl být vázán na rozhraním. Můžete provést například jde zadat vlastní příkaz jazyka SQL přes `GetDefaultSQL` nebo jako argument Ipszsql `CRecordset`společnosti `Open` funkce a další sloupec s volání funkce rozhraní RFX_ vazbu. ODBC vyžaduje nevázaný pole, které se zobrazí napravo od vázaného pole, proto přidat nevázaný sloupec nebo sloupce na konec seznamu příkazu select.

> [!NOTE]
>  Protože dlouhý datový sloupec není vázán v rámci rozhraní, změny k němu nebude zpracován s `CRecordset::Update` volání. Musíte vytvořit a odeslat vyžaduje SQL **vložit** a **aktualizace** příkazy sami.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

