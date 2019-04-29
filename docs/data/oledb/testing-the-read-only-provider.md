---
title: Testování zprostředkovatele pouze pro čtení
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, calling
- OLE DB providers, testing
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
ms.openlocfilehash: a9601b2afe40133a5cc88589b530b5ed549ac81e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389226"
---
# <a name="testing-the-read-only-provider"></a>Testování zprostředkovatele pouze pro čtení

Testování zprostředkovatele, budete potřebovat příjemce. Je užitečné, pokud příjemce můžete porovnat s tímto poskytovatelem. Šablony příjemce technologie OLE DB se dynamicky obálku kolem OLE DB a shodovat s objekty COM zprostředkovatele. Protože zdrojem je dodáván s šablonami příjemců, je snadné ladění zprostředkovatele s nimi. Šablony příjemce se také velmi malé a rychlý způsob, jak vyvíjet aplikace pro koncové uživatele.

V příkladu v tomto tématu vytvoří aplikaci výchozí Průvodce aplikací knihovny MFC pro testování příjemce. Testování aplikace je jednoduchá dialogové okno Přidat kód šablony příjemce technologie OLE DB.

## <a name="to-create-the-test-application"></a>Chcete-li vytvořit testovací aplikace

1. Na **souboru** nabídky, klikněte na tlačítko **nový**a potom klikněte na tlačítko **projektu**.

1. V **typy projektů** podokně, vyberte **nainstalováno** > **Visual C++** > **MFC nebo ATL** složky. V **šablony** vyberte **aplikace knihovny MFC**.

1. Název projektu zadejte *TestProv*a potom klikněte na tlačítko **OK**.

   **Aplikace knihovny MFC** průvodce se zobrazí.

1. Na **typ aplikace** stránce **na bázi dialogu**.

1. Na **rozšířené funkce** stránce **automatizace**a potom klikněte na tlačítko **Dokončit**.

> [!NOTE]
> Aplikace nevyžaduje podporu automatizace, pokud chcete přidat `CoInitialize` v `CTestProvApp::InitInstance`.

Můžete zobrazit a upravit **TestProv** dialogové okno (IDD_TESTPROV_DIALOG) tak, že ho vyberete **zobrazení prostředků**. V dialogovém okně umístěte dvě pole se seznamem, jeden pro každý řetězec v dané sadě řádků. Vypnout vlastnost řazení pro oba seznamy stisknutím kombinace kláves **Alt**+**Enter** při výběru pole se seznamem a nastavení **řazení** vlastnost **False**. Také, umístěte **spustit** tlačítko v dialogovém okně Načíst soubor. Dokončené **TestProv** dialogové okno by měl mít dvě pole se seznamem označeny jako "Řetězce 1" a "Řetězec 2"; má také **OK**, **zrušit**, a **spuštění**  tlačítka.

Otevřete soubor hlaviček pro třídu dialogového okna (v tomto případě TestProvDlg.h). Přidejte následující kód do souboru hlaviček (mimo všechny deklarace tříd):

```cpp
////////////////////////////////////////////////////////////////////////
// TestProvDlg.h
#include <atldbcli.h>  

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

Kód představuje záznam uživatele, který definuje, které sloupce budou v dané sadě řádků. Když klient volá `IAccessor::CreateAccessor`, chcete-li určit sloupce, které k vytvoření vazby použije tyto položky. Šablony příjemce technologie OLE DB taky povolit dynamické vazby sloupců. COLUMN_ENTRY makra jsou klientské verze PROVIDER_COLUMN_ENTRY makra. Dvě makra COLUMN_ENTRY určit pořadí, typ, délku a dat členství pro dva řetězce.

Přidat obslužnou rutinu pro **spustit** tlačítko stisknutím kombinace kláves **Ctrl** a dvojitým kliknutím **spustit** tlačítko. Vložte následující kód ve funkci:

```cpp
///////////////////////////////////////////////////////////////////////
// TestProvDlg.cpp

void CTestProvDlg::OnRun()
{
   CCommand<CAccessor<CProvider>> table;
   CDataSource source;
   CSession session;

   if (source.Open("Custom.Custom.1", NULL) != S_OK)
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

`CCommand`, `CDataSource`, A `CSession` třídy, které patří k šablonám příjemců OLE DB. Každá třída napodobuje objekt modelu COM ve zprostředkovateli. `CCommand` Přebírá objekt `CProvider` třídy deklarované v souboru hlaviček, jako parametr šablony. `CProvider` Představuje parametr vazby, které používáte pro přístup k datům od poskytovatele. 

Řádky, které se otevřete každý tříd vytváření každý objekt modelu COM ve zprostředkovateli. Chcete-li vyhledat poskytovatele, použijte `ProgID` poskytovatele. Můžete získat `ProgID` z registru systému nebo nahlédněte do souboru Custom.rgs (otevřete adresář poskytovatele, vyhledejte `ProgID` klíč).

Je součástí souboru MyData.txt `MyProv` vzorku. Vytvořte soubor sami, použití editoru a zadejte sudý počet řetězců, stisknutím klávesy **Enter** mezi každého řetězce. Pokud přesunete soubor, změňte název cesty.

Předat řetězec "c:\\\samples\\\myprov\\\MyData.txt" v `table.Open` řádku. Pokud můžete krokovat s vnořením `Open` volání, uvidíte, že je tento řetězec předat `SetCommandText` metoda ve zprostředkovateli. Všimněte si, `ICommandText::Execute` metodu použít tento řetězec.

Chcete-li načíst data, zavolejte `MoveNext` v tabulce. `MoveNext` volání `IRowset::GetNextRows`, `GetRowCount`, a `GetData` funkce. Pokud neexistují žádné další řádky (to znamená, je větší než aktuální pozici v dané sadě řádků `GetRowCount`), ukončí smyčku.

Pokud neexistují žádné další řádky, vrátí DB_S_ENDOFROWSET. Hodnota DB_S_ENDOFROWSET není chyba. Vždy byste měli zkontrolovat S_OK smyčce načtení dat a není použití makra SUCCEEDED.

Teď by měl být možné vytvářet a testovat program.

## <a name="see-also"></a>Viz také:

[Rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md)