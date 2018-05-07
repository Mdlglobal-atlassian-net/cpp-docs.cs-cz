---
title: Testování zprostředkovatele pouze pro čtení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, calling
- OLE DB providers, testing
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 703d33f44fae534b206050e85086edb1ccc816f9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="testing-the-read-only-provider"></a>Testování zprostředkovatele pouze pro čtení
Chcete-li otestovat poskytovatele, musíte příjemce. Je užitečné, pokud příjemce může shodovat s poskytovatelem. Šablony příjemce technologie OLE DB jsou dynamické obálku kolem OLE DB a shodovat s objekty COM zprostředkovatele. Vzhledem k tomu, že je zdroj dodáván s šablonami příjemců, je snadné ladění zprostředkovatele s nimi. Šablony příjemce jsou také velmi malé a rychlý způsob, jak vyvíjet aplikace příjemce.  
  
 Příklad v tomto tématu vytvoří výchozí aplikaci MFC – Průvodce aplikací pro testování příjemce. Testování aplikace je jednoduché dialogové okno s přidaným kódem šablony příjemce technologie OLE DB.  
  
### <a name="to-create-the-test-application"></a>Chcete-li vytvořit testovací aplikace  
  
1.  Na **soubor** nabídky, klikněte na tlačítko **nový**a potom klikněte na **projektu**.  
  
2.  V podokně typy projektů, vyberte **projekty Visual C++** složky. V podokně šablon vyberte **aplikace knihovny MFC**.  
  
3.  Název projektu zadejte **TestProv**a potom klikněte na **OK**.  
  
     Zobrazí se Průvodce aplikací MFC.  
  
4.  Na **typ aplikace** vyberte **založená na dialogovém okně**.  
  
5.  Na **upřesňující funkce** vyberte **automatizace**a potom klikněte na **Dokončit**.  
  
> [!NOTE]
>  Aplikace nevyžaduje podporu automatizace, pokud přidáte **funkce CoInitialize** v **CTestProvApp::InitInstance**.  
  
 Můžete zobrazit a upravit dialogové okno TestProv (IDD_TESTPROV_DIALOG) tak, že ho vyberete v zobrazení zdrojů. V dialogovém okně umístěte dva seznamy, jeden pro každou řetězec v dané sadě řádků. Vypnout vlastnosti řazení pro oba seznamy stisknutím ALT + Enter když je vybraný seznam, kliknutím **styly** kartě a vymazání **řazení** zaškrtávací políčko. Navíc umístit **spustit** tlačítka v dialogovém okně se načíst soubor. Dialogové okno dokončení TestProv by měl mít dva seznamy s označením "Řetězec 1" a "String 2", v uvedeném pořadí; je také **OK**, **zrušit**, a **spustit** tlačítka.  
  
 Otevřete soubor hlaviček pro třídy dialogového okna (v tomto případě TestProvDlg.h). Přidejte následující kód do souboru hlaviček (mimo všechny deklarace tříd):  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// TestProvDlg.h  
  
class CProvider   
{  
// Attributes  
public:  
   char   szField1[16];  
   char   szField2[16];  
  
   // Binding Maps  
BEGIN_COLUMN_MAP(CProvider)  
   COLUMN_ENTRY(1, szField1)  
   COLUMN_ENTRY(2, szField2)  
END_COLUMN_MAP()  
};  
```  
  
 Kód představuje záznam uživatele, který definuje, které sloupce budou v dané sadě řádků. Když klient volá **IAccessor::CreateAccessor**, použije tyto položky a určete sloupce pro vazbu. Šablony příjemce technologie OLE DB také umožňují dynamické vazby sloupců. Makra COLUMN_ENTRY jsou verze klienta makra PROVIDER_COLUMN_ENTRY. Dvě makra COLUMN_ENTRY určují pořadí, typ, délku a data člena pro dva řetězce.  
  
 Přidat obslužnou rutinu pro **spustit** stisknutím klávesy CTRL a dvakrát klikněte na tlačítko **spustit** tlačítko. Vložte následující kód funkce:  
  
```cpp
///////////////////////////////////////////////////////////////////////  
// TestProvDlg.cpp  
  
void CtestProvDlg::OnRun()  
{  
   CCommand<CAccessor<CProvider>> table;  
   CDataSource source;  
   CSession   session;  
  
   if (source.Open("MyProvider.MyProvider.1", NULL) != S_OK)  
      return;  
  
   if (session.Open(source) != S_OK)  
      return;  
  
   if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)  
      return;  
  
   while (table.MoveNext() == S_OK)  
   {  
      m_ctlString1.AddString(table.szField1);  
      m_ctlString2.AddString(table.szField2);  
   }  
}  
```  
  
 `CCommand`, `CDataSource`, A `CSession` tříd všechny patřit do šablony příjemce technologie OLE DB. Každá třída napodobuje objektu COM ve zprostředkovateli. `CCommand` Objektu trvá `CProvider` třídy, deklarované v záhlaví souboru, jako parametr šablony. `CProvider` Představuje parametr vazby, které používáte pro přístup k datům ze zprostředkovatele. Tady je `Open` kód pro zdroj dat, relace a příkaz:  
  
```  
if (source.Open("MyProvider.MyProvider.1", NULL) != S_OK)  
   return;  
  
if (session.Open(source) != S_OK)  
   return;  
  
if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)  
   return;  
```  
  
 Řádky určené k otevírání jednotlivých tříd vytvořit každého objektu COM ve zprostředkovateli. Chcete-li vyhledejte poskytovatele, použijte ProgID zprostředkovatele. Identifikátor ProgID můžete získat z registru systému nebo nahlédněte do souboru MyProvider.rgs (otevřete adresář a vyhledejte klíč ProgID poskytovatele).  
  
 Soubor MyData.txt je součástí MyProv vzorku. Chcete-li vytvořit vlastní soubor, pomocí editoru a zadejte sudý počet řetězců, stisknutím klávesy ENTER mezi každý řetězec. Pokud přesunete soubor, změňte název cesty.  
  
 Předejte v řetězci "c:\\\samples\\\myprov\\\MyData.txt" v `table.Open` řádku. Pokud jste přesunuli do `Open` volání, uvidíte, že tento řetězec je předán do `SetCommandText` metoda ve zprostředkovateli. Všimněte si, že `ICommandText::Execute` metodu použít tento řetězec.  
  
 Chcete-li načíst data, volejte `MoveNext` v tabulce. `MoveNext` volání **IRowset::GetNextRows**, `GetRowCount`, a `GetData` funkce. Pokud nejsou zjištěny žádné další řádky (to znamená, je větší než aktuální pozici v dané sadě řádků `GetRowCount`), ukončí smyčka:  
  
```  
while (table.MoveNext() == S_OK)  
{  
   m_ctlString1.AddString(table.szField1);  
   m_ctlString2.AddString(table.szField2);  
}  
```  
  
 Všimněte si, že pokud nejsou zjištěny žádné další řádky, vrátí **DB_S_ENDOFROWSET**. **DB_S_ENDOFROWSET** hodnota není k chybě. Vždy byste měli zkontrolovat proti `S_OK` zrušit smyčku načtení dat a nepoužívat makro bylo úspěšné.  
  
 Teď by měla být možnost pro sestavení a otestování program.  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md)