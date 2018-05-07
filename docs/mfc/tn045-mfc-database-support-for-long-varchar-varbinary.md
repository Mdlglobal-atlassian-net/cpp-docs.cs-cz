---
title: 'TN045: Podpora MFC databáze pro Long Varchar Varbinary | Microsoft Docs'
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
ms.openlocfilehash: bd5201661afcdf6f4ae9676323f3f644817bcf7d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="tn045-mfcdatabase-support-for-long-varcharvarbinary"></a>TN045: Podpora prostředí MFC a databáze pro typy Long Varchar/Varbinary
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Tato poznámka popisuje, jak načíst a odeslat ODBC **SQL_LONGVARCHAR** a **SQL_LONGVARBINARY** datové typy pomocí knihovny MFC databáze třídy.  
  
## <a name="overview-of-long-varcharvarbinary-support"></a>Přehled podpory Long Varchar/Varbinary  
 ODBC **SQL_LONG_VARCHAR** a **SQL_LONGBINARY** obrovské objemy dat mohou být uloženy datové typy (označována jako dlouho datových sloupců). Tato data můžete řešit 3 způsoby:  
  
-   Vytvořte mu vazbu k `CString` / `CByteArray`.  
  
-   Vytvořte mu vazbu k `CLongBinary`.  
  
-   Není navázat jej na všech a načítají a posílají long – datový hodnotu ručně, nezávislé databázové třídy.  
  
 Každý ze tří metod má výhody a nevýhody.  
  
 Long – datový sloupce nejsou podporovány pro parametry dotazu. Jsou podporovány pouze pro outputColumns.  
  
## <a name="binding-a-long-data-column-to-a-cstringcbytearray"></a>Vytvoření vazby Long – datový sloupec CString/CByteArray  
 Výhody:  
  
 Tento přístup je srozumitelný a práci s známé třídy. Poskytuje rozhraní `CFormView` podporu pro `CString` s `DDX_Text`. Máte spoustu obecné řetězec nebo kolekce funkce s `CString` a `CByteArray` třídy a můžete řídit množství paměti přidělené místně pro uložení dat hodnota. Rozhraní framework udržuje staré kopii dat pole během **upravit** nebo `AddNew` volání funkcí a můžete framework, který je pro vás automaticky zjišťovat změny v datech.  
  
> [!NOTE]
>  Vzhledem k tomu `CString` je určená pro práci na textová data a `CByteArray` pro práci na binární data, je doporučeno, vložit textová data (**SQL_LONGVARCHAR**) do `CString`a binární data ( **SQL_LONGVARBINARY**) do `CByteArray`.  
  
 Funkce RFX pro `CString` a `CByteArray` mají další argument, které lze přepsat výchozí velikost přidělené paměti pro uložení načtené hodnoty pro sloupec data. Poznámka: argument nMaxLength v deklaracích následující funkce:  
  
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
  
 Pokud načtení long – datový sloupec do `CString` nebo `CByteArray`, vrátí maximální množství dat, je ve výchozím nastavení, 255 bajtů. Nic nad tuto hranici se ignoruje. V takovém případě rozhraní vyvolá výjimku **AFX_SQL_ERROR_DATA_TRUNCATED**. Naštěstí můžete explicitně zvýšit nMaxLength větší hodnoty, až **MAXINT**.  
  
> [!NOTE]
>  Hodnota nMaxLength je využívané prostředím MFC nastavit místní vyrovnávací paměti **SQLBindColumn** funkce. Toto je místní vyrovnávací paměti pro úložiště dat a nemá vliv na ve skutečnosti množství dat vrácených ovladač ODBC. `RFX_Text` a `RFX_Binary` pouze si ho volat pomocí **SQLFetch** k načtení dat z databáze back-end. Každý ovladač ODBC má jiné omezení na množství dat, které vracejí v jednoho načtení. Tento limit, může být mnohem menší než hodnotu nastavenou v nMaxLength, ve kterém případ výjimka **AFX_SQL_ERROR_DATA_TRUNCATED** bude vyvolána. Za těchto okolností, přejít k používání `RFX_LongBinary` místo `RFX_Text` nebo `RFX_Binary` tak, aby se nedají načíst všechna data.  
  
 Vytvoří vazbu ClassWizard **SQL_LONGVARCHAR** k `CString`, nebo **SQL_LONGVARBINARY** k `CByteArray` za vás. Pokud chcete přidělit více než 255 bajtů, do kterých načíst vaše long – datový sloupec, potom můžete zadat explicitní hodnotu pro nMaxLength.  
  
 Long – datový sloupec je vázána k `CString` nebo `CByteArray`, aktualizace pole funguje stejně jako když je vázána na SQL_**VARCHAR** nebo SQL_**VARBINARY**. Během **upravit**, hodnota dat je uložený v mezipaměti ji okamžitě a později při porovnání **aktualizace** nazývá ke zjištění změny dat hodnotu nastavit Dirty a hodnoty pro sloupec správně Null.  
  
## <a name="binding-a-long-data-column-to-a-clongbinary"></a>Vytvoření vazby Long – datový sloupec CLongBinary  
 Pokud vaše long – datový sloupec může obsahovat více **MAXINT** bajtů dat, pravděpodobně zvažte načítání do aplikace `CLongBinary`.  
  
 Výhody:  
  
 To načte na celý long – datový sloupec až dostupné paměti.  
  
 Nevýhody:  
  
 Data je udržována v paměti. Tento přístup je také výtažkovými u velmi velkých objemů dat. Je třeba volat `SetFieldDirty` pro vázaných dat je součástí člen zajistit pole **aktualizace** operaci.  
  
 Pokud načtení dlouho datových sloupců do `CLongBinary`, databázové třídy zkontrolujte celková velikost long – datový sloupec a potom přidělit `HGLOBAL` dostatečně velký pro uložení je hodnota celého datového segmentu paměti. Databázové třídy pak načíst hodnotu celého dat do přidělená `HGLOBAL`.  
  
 Pokud zdroj dat nelze vrátit očekávané velikosti long – datový sloupec, rozhraní vyvolá výjimku **AFX_SQL_ERROR_SQL_NO_TOTAL**. Pokud se pokus o přidělení `HGLOBAL` selže, je vyvolána výjimka standardní paměti.  
  
 Vytvoří vazbu ClassWizard **SQL_LONGVARCHAR** nebo **SQL_LONGVARBINARY** k `CLongBinary` za vás. Vyberte `CLongBinary` jako typ proměnné v dialogovém okně Přidat proměnnou člen. Poté přidá ClassWizard `RFX_LongBinary` volání do vaší `DoFieldExchange` volání a zvýšit celkový počet vázané pole.  
  
 Pokud chcete aktualizovat dlouhé hodnoty sloupců dat, nejprve zkontrolujte přidělená `HGLOBAL` je dostatečně velký pro uložení nová data voláním **:: GlobalSize** na `m_hData` členem `CLongBinary`. Pokud je příliš malá, vydání `HGLOBAL` a přidělte jednu správnou velikost. Nastavte `m_dwDataLength` tak, aby odrážely novou velikost.  
  
 Jinak Pokud `m_dwDataLength` je větší než velikost dat nahrazujete, můžete buď volné a znovu přidělte `HGLOBAL`, nebo ponechte přidělené. Nezapomeňte určit počet bajtů použitých ve skutečnosti v `m_dwDataLength`.  
  
## <a name="how-updating-a-clongbinary-works"></a>Jak aktualizací CLongBinary funguje  
 Není nutné pochopit, jak aktualizací `CLongBinary` funguje, ale můžou být užitečné jako příklad o tom, jak poslat hodnoty long – datový zdroj dat, pokud zvolíte tuto třetí metodu popsané dole.  
  
> [!NOTE]
>  Aby `CLongBinary` pole, které mají být zahrnuty v aktualizaci, musí explicitně volat `SetFieldDirty` pro pole. Pokud jste provedli jakékoli změny pro pole, včetně jeho nastavení na hodnotu Null, musí volat `SetFieldDirty`. Musíte také zavolat `SetFieldNull`, s druhý parametr je **FALSE**, označit pole tak, že má hodnotu.  
  
 Při aktualizaci `CLongBinary` pole, použijte rozhraní ODBC pro databázové třídy **DATA_AT_EXEC** mechanismus (naleznete v dokumentaci k rozhraní ODBC na **SQLSetPos**na rgbValue argument). Když rozhraní připraví příkaz insert nebo update místo odkazující na `HGLOBAL` obsahující data, *adresu* z `CLongBinary` je nastaven jako *hodnotu* sloupce Místo toho a indikátoru délka nastavena na **SQL_DATA_AT_EXEC**. Později při odeslání příkazu update ke zdroji dat **SQLExecDirect** vrátí **SQL_NEED_DATA**. Toto upozornění rozhraní, že hodnota parametru pro tento sloupec je ve skutečnosti adresa `CLongBinary`. Volání framework **SQLGetData** jednou s malou vyrovnávací pamětí, byla očekávána ovladač vrátit skutečné délce dat. Pokud ovladač vrátí skutečné délce binární rozsáhlý objekt (objektů BLOB), přidělí MFC tolik místa nezbytný k načtení objektu BLOB. Pokud zdroj dat, vrátí **SQL_NO_TOTAL**, která určuje, že ho nelze určit velikost objektu BLOB, MFC vytvoří menší bloky. Výchozí počáteční velikost je 64 kB a následné bloky budou double velikost; například druhý bude 128 kb / s, třetí je 256 kB a tak dále. Počáteční velikost je možné konfigurovat.  
  
## <a name="not-binding-retrievingsending-data-directly-from-odbc-with-sqlgetdata"></a>Vazba není: Načítání nebo odesílání dat přímo z rozhraní ODBC se SQLGetData  
 Pomocí této metody můžete zcela vynechat databázové třídy a řešit long – datový sloupec.  
  
 Výhody:  
  
 Mezipaměti můžete ukládat data na disku v případě potřeby nebo rozhodnout dynamicky, kolik dat pro načtení.  
  
 Nevýhody:  
  
 Nezískávat rozhraní framework **upravit** nebo `AddNew` podporu a vy musíte napsat kód sami provádět základní funkce (**odstranit** funguje, když, protože se nejedná o úrovni operaci sloupce).  
  
 Long – datový sloupec v takovém případě musí být v seznamu select sady záznamů, ale nesmí být vázán k rozhraní. Jeden ze způsobů, jak provést jde zadat vlastní příkaz jazyka SQL prostřednictvím `GetDefaultSQL` nebo jako lpszSQL argument `CRecordset`na **otevřete** funkce a další sloupec s volání funkce RFX_ vazba není. ODBC vyžaduje, aby nevázaný pole se zobrazí vpravo od pole vázané, takže přidání nepřipojeného sloupce nebo sloupce na konec seznamu příkazu select.  
  
> [!NOTE]
>  Protože vaše long – datový sloupec není vázán rámcem, změny k němu nebude zpracována s `CRecordset::Update` volání. Musíte vytvořit a odeslat požadované SQL **vložit** a **aktualizace** příkazy sami.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

