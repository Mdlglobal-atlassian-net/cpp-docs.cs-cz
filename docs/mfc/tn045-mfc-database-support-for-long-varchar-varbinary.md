---
title: 'TN045: Podpora prostředí MFC a databáze pro typy Long Varchar a Varbinary'
ms.date: 11/04/2016
helpviewer_keywords:
- TN045
- Varbinary data type
- Varchar data type
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
ms.openlocfilehash: 55a68ba970d0a26163f426d51818c701c13ed051
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750281"
---
# <a name="tn045-mfcdatabase-support-for-long-varcharvarbinary"></a>TN045: Podpora prostředí MFC a databáze pro typy Long Varchar/Varbinary

> [!NOTE]
> Následující technická poznámka nebyla aktualizována od doby, kdy byla poprvé zahrnuta do online dokumentace. V důsledku toho mohou být některé postupy a témata zastaralé nebo nesprávné. Chcete-li získat nejnovější informace, doporučujeme vyhledat téma zájmu v online indexu dokumentace.

Tato poznámka popisuje, jak načíst a odeslat **SQL_LONGVARCHAR** odbc a **SQL_LONGVARBINARY** datových typů pomocí tříd y databáze knihovny MFC.

## <a name="overview-of-long-varcharvarbinary-support"></a>Přehled podpory Long Varchar/Varbinary

Datové typy **SQL_LONG_VARCHAR** a **SQL_LONGBINARY** ODBC (označované zde jako dlouhé datové sloupce) mohou obsahovat obrovské množství dat. Tato data lze zpracovat 3 způsoby:

- Svázat ji `CString` / `CByteArray`na .

- Svázat ji `CLongBinary`na .

- Nesvazovat vůbec a načíst a odeslat dlouhou hodnotu dat ručně, nezávisle na databázové třídy.

Každá ze tří metod má své výhody a nevýhody.

Dlouhé datové sloupce nejsou podporovány pro parametry dotazu. Jsou podporovány pouze pro outputColumns.

## <a name="binding-a-long-data-column-to-a-cstringcbytearray"></a>Vazba dlouhého datového sloupce na cstring/CByteArray

Výhody:

Tento přístup je jednoduchý na pochopení a pracujete se známými třídami. Rámec poskytuje `CFormView` podporu `CString` `DDX_Text`pro s . Máte spoustu obecné funkce řetězce nebo `CString` kolekce `CByteArray` s a třídy a můžete řídit množství paměti přidělené místně pro uložení hodnoty dat. Rozhraní Framework udržuje starou kopii `Edit` dat `AddNew` pole během volání nebo funkce a rozhraní framework může automaticky rozpoznat změny dat za vás.

> [!NOTE]
> Vzhledem k tomu, `CString` že `CByteArray` je určen pro práci na znakových datech a pro `CString`práci s binárními daty, doporučujeme vložit znaková data (**SQL_LONGVARCHAR**) do aplikace a binární data (**SQL_LONGVARBINARY**) do . `CByteArray`

Funkce RFX `CString` pro `CByteArray` a mají další argument, který umožňuje přepsat výchozí velikost přidělené paměti držet načtenou hodnotu pro sloupec dat. Všimněte si argumentu nMaxLength v následujících deklaracích funkcí:

```cpp
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

Pokud načtete dlouhý datový `CString` `CByteArray`sloupec do nebo , maximální vrácené množství dat je ve výchozím nastavení 255 bajtů. Cokoliv kromě toho je ignorováno. V tomto případě bude rámec vyvolat výjimku **AFX_SQL_ERROR_DATA_TRUNCATED**. Naštěstí můžete explicitně zvýšit nMaxLength na větší hodnoty, až **maxint**.

> [!NOTE]
> Hodnota nMaxLength používá knihovna MFC k nastavení `SQLBindColumn` místní vyrovnávací paměti funkce. Toto je místní vyrovnávací paměť pro ukládání dat a ve skutečnosti nemá vliv na množství dat vrácených ovladačem ODBC. `RFX_Text`a `RFX_Binary` provést pouze `SQLFetch` jedno volání pomocí načíst data z back-end databáze. Každý ovladač ROZHRANÍ ODBC má jiné omezení množství dat, které mohou vrátit v jednom načtení. Toto omezení může být mnohem menší než hodnota nastavená v nMaxLength, v takovém případě bude vyvolána výjimka **AFX_SQL_ERROR_DATA_TRUNCATED.** Za těchto okolností přepněte `RFX_Text` na `RFX_Binary` using `RFX_LongBinary` namísto nebo tak, aby všechna data lze načíst.

ClassWizard sváže **SQL_LONGVARCHAR** `CString`na , nebo `CByteArray` **SQL_LONGVARBINARY** pro vás. Pokud chcete přidělit více než 255 bajtů, do kterých načtete sloupec dlouhých dat, můžete zadat explicitní hodnotu pro nMaxLength.

Pokud je dlouhý datový sloupec `CString` `CByteArray`vázán na nebo , aktualizace pole funguje stejně jako při vazbě na SQL_**VARCHAR** nebo SQL_**VARBINARY**. Během `Edit`, hodnota dat je uložena do `Update` mezipaměti a později porovnány, když je volána ke zjištění změn hodnoty dat a nastavte Dirty a Null hodnoty pro sloupec odpovídajícím způsobem.

## <a name="binding-a-long-data-column-to-a-clongbinary"></a>Vazba dlouhý datový sloupec clongbinary

Pokud váš dlouhý datový sloupec může obsahovat více **bajtů MAXINT** dat, měli byste pravděpodobně zvážit jeho načtení do . `CLongBinary`

Výhody:

Tím se načte celý dlouhý datový sloupec až do dostupné paměti.

Nevýhody:

Data jsou uložena v paměti. Tento přístup je také nepřiměřeně nákladný u velmi velkého množství dat. Musíte volat `SetFieldDirty` vázaného datového člena, abyste zajistili, že pole bude zahrnuto do `Update` operace.

Pokud načtete dlouhé `CLongBinary`datové sloupce do aplikace , budou třídy databáze kontrolovat `HGLOBAL` celkovou velikost dlouhého datového sloupce a pak přidělit dostatečně velký segment paměti, aby byl obsahovat celou hodnotu dat. Třídy databáze pak načíst celou hodnotu dat do přidělené `HGLOBAL`.

Pokud zdroj dat nemůže vrátit očekávanou velikost dlouhého sloupce dat, rozhraní v rámci vyvolá výjimku **AFX_SQL_ERROR_SQL_NO_TOTAL**. Pokud se nezdaří `HGLOBAL` pokus o přidělení, je vyvolána výjimka standardní paměti.

ClassWizard sváže **SQL_LONGVARCHAR** nebo `CLongBinary` **SQL_LONGVARBINARY** na pro vás. V `CLongBinary` dialogovém okně Přidat proměnnou vyberte jako typ proměnné. ClassWizard pak přidá `RFX_LongBinary` volání `DoFieldExchange` do vašeho volání a zvýší celkový počet vázaných polí.

Chcete-li aktualizovat hodnoty dlouhých datových `HGLOBAL` sloupců, nejprve zkontrolujte, zda je přidělená hodnota `CLongBinary`dostatečně velká pro uložení nových dat voláním **::GlobalSize** na *m_hData* člen . Pokud je příliš malý, `HGLOBAL` uvolněte a přidělit jeden odpovídající velikost. Pak nastavte *m_dwDataLength* tak, aby odrážely novou velikost.

V opačném případě, pokud *m_dwDataLength* je větší než velikost dat, které nahrazujete, můžete buď uvolnit a přerozdělit `HGLOBAL`, nebo je nechat přidělené. Nezapomeňte uvést počet bajtů skutečně použitých v *m_dwDataLength*.

## <a name="how-updating-a-clongbinary-works"></a>Jak aktualizace clongbinary works

Není nutné pochopit, jak `CLongBinary` funguje aktualizace, ale může být užitečné jako příklad, jak odeslat dlouhé hodnoty dat do zdroje dat, pokud zvolíte tuto třetí metodu, popsané níže.

> [!NOTE]
> Aby bylo `CLongBinary` pole zahrnuto do aktualizace, musíte `SetFieldDirty` toto pole explicitně volat. Pokud provedete jakoukoli změnu pole, včetně jeho `SetFieldDirty`nastavení Null, musíte volat . Musíte také `SetFieldNull`volat , přičemž druhý parametr je **FALSE**, chcete-li pole označit jako pole s hodnotou.

Při aktualizaci `CLongBinary` pole používají třídy databáze **mechanismus DATA_AT_EXEC** rozhraní `SQLSetPos`ODBC (viz dokumentace od rozhraní ODBC k argumentu rgbValue společnosti ). Když framework připraví příkaz insert nebo update, místo `HGLOBAL` toho, aby ukazoval na `CLongBinary` obsahující data, *adresa* je nastavena jako *hodnota* sloupce a indikátor délky nastaven ý na **SQL_DATA_AT_EXEC**. Později, když je příkaz aktualizace odeslán `SQLExecDirect` do zdroje dat, vrátí **SQL_NEED_DATA**. To upozorní na rámec, že hodnota param pro tento `CLongBinary`sloupec je ve skutečnosti adresa . Rozhraní framework `SQLGetData` volání jednou s malou vyrovnávací paměti, očekává, že ovladač vrátit skutečnou délku dat. Pokud ovladač vrátí skutečnou délku binární velký objekt (BLOB), knihovna MFC přerozdělí tolik místa, jak je potřeba k načtení objektu BLOB. Pokud zdroj dat vrátí **SQL_NO_TOTAL**, což znamená, že nemůže určit velikost objektu BLOB, knihovna MFC vytvoří menší bloky. Výchozí počáteční velikost je 64 kB a následné bloky budou mít dvojnásobnou velikost; například druhý bude 128 kM, třetí je 256 kK a tak dále. Počáteční velikost je konfigurovatelná.

## <a name="not-binding-retrievingsending-data-directly-from-odbc-with-sqlgetdata"></a>Nevazba: Načítání a odesílání dat přímo z ROZHRANÍ ODBC pomocí SQLGetData

Pomocí této metody zcela obejít třídy databáze a vypořádat se s dlouhou datovou sloupec sami.

Výhody:

V případě potřeby můžete data ukládat do mezipaměti na disk nebo dynamicky rozhodnout, kolik dat chcete načíst.

Nevýhody:

Nezískáte rozhraní nebo `Edit` `AddNew` podporu a musíte napsat kód sami k provedení základní`Delete` funkce (funguje i když, protože to není operace na úrovni sloupce).

V tomto případě dlouhý sloupec dat musí být ve výběrovém seznamu sady záznamů, ale nesmí být vázán a rámci. Jedním ze způsobů, jak to provést, `GetDefaultSQL` je zadat vlastní příkaz `CRecordset`SQL `Open` prostřednictvím nebo jako argument lpszSQL do funkce 's a nevázat sloupec navíc s voláním funkce RFX_. Rozhraní ODBC vyžaduje, aby se nevázaná pole zobrazovala vpravo od vázaných polí, proto přidejte nevázaný sloupec nebo sloupce na konec seznamu výběru.

> [!NOTE]
> Vzhledem k tomu, že váš dlouhý sloupec dat není `CRecordset::Update` vázán rámci, změny v něm nebudou zpracovány s voláním. Musíte vytvořit a odeslat požadované příkazy SQL **INSERT** a **UPDATE** sami.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
