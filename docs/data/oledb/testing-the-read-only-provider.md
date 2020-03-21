---
title: Testování zprostředkovatele pouze pro čtení
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, calling
- OLE DB providers, testing
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
ms.openlocfilehash: a173e1466179dfb40a33d7bdb4a94eabdbf23cc0
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079051"
---
# <a name="testing-the-read-only-provider"></a>Testování zprostředkovatele pouze pro čtení

K otestování poskytovatele potřebujete příjemce. Pomáhá, pokud se příjemce může shodovat s poskytovatelem. Šablony příjemce OLE DB jsou tenkou obálkou kolem OLE DB a odpovídají objektům COM poskytovatele. Vzhledem k tomu, že je zdroj dodán se šablonami příjemců, je snadné ho ladit pomocí těchto poskytovatelů. Šablony spotřebitelů představují také velmi malý a rychlý způsob vývoje zákaznických aplikací.

Příklad v tomto tématu vytvoří výchozí aplikaci Průvodce aplikací knihovny MFC pro testovacího příjemce. Testovací aplikace je jednoduchý dialog s přidaným OLE DBm kódem šablony příjemce.

## <a name="to-create-the-test-application"></a>Vytvoření testovací aplikace

1. V nabídce **soubor** klikněte na příkaz **Nový**a potom klikněte na **projekt**.

1. V podokně **typy projektů** vyberte složku **Installed** > **Visual C++**  > **MFC/ATL** . V podokně **šablony** vyberte možnost **aplikace MFC**.

1. Jako název projektu zadejte *TestProv*a pak klikněte na **OK**.

   Zobrazí se průvodce **aplikací knihovny MFC** .

1. Na stránce **Typ aplikace** vyberte možnost **založeno na dialogovém okně**.

1. Na stránce **Pokročilé funkce** vyberte možnost **Automatizace**a pak klikněte na tlačítko **Dokončit**.

> [!NOTE]
> Pokud přidáte `CoInitialize` do `CTestProvApp::InitInstance`, aplikace nevyžaduje podporu automatizace.

Dialog **TestProv** (IDD_TESTPROV_DIALOG) můžete zobrazit a upravit tak, že ho vyberete v **prostředky**. Umístěte dvě pole seznamu, jednu pro každý řetězec v sadě řádků v dialogovém okně. Vypněte vlastnost Sort pro obě pole seznamu stisknutím klávesy **Alt**+**Zadejte** , když je vybráno pole se seznamem, a nastavením vlastnosti **Sort** na **hodnotu false (NEPRAVDA**). Také umístěte tlačítko **Spustit** do dialogového okna pro načtení souboru. Dialogové okno dokončený **TestProv** by mělo mít dva seznamy označené "String 1" a "String 2", v uvedeném pořadí; má také tlačítka **OK**, **Zrušit**a **Spustit** .

Otevřete hlavičkový soubor pro třídu dialogového okna (v tomto případě TestProvDlg. h). Do hlavičkového souboru přidejte následující kód (mimo deklarace třídy):

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

Kód představuje záznam uživatele definující, které sloupce budou v sadě řádků. Když klient volá `IAccessor::CreateAccessor`, používá tyto záznamy k určení, které sloupce se mají vytvořit. Šablony příjemce OLE DB také umožňují dynamicky navazovat sloupce. Makra COLUMN_ENTRY jsou verze PROVIDER_COLUMN_ENTRY maker na straně klienta. Dvě COLUMN_ENTRY makra určují pořadové číslo, typ, délku a datový člen pro dva řetězce.

Stisknutím klávesy **CTRL** a dvojitým kliknutím na tlačítko **Spustit** Přidejte funkci obslužné rutiny pro tlačítko **Spustit** . Do funkce vložte následující kód:

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

Třídy `CCommand`, `CDataSource`a `CSession` patří do šablon OLE DB příjemce. Každá třída napodobuje objekt COM ve zprostředkovateli. Objekt `CCommand` přebírá třídu `CProvider`, která je deklarována v hlavičkovém souboru jako parametr šablony. Parametr `CProvider` představuje vazby, které používáte pro přístup k datům od poskytovatele.

Řádky, které mají být otevřeny každou ze tříd, vytvoří každý objekt COM ve zprostředkovateli. Chcete-li vyhledat poskytovatele, použijte `ProgID` poskytovatele. `ProgID` můžete získat z systémového registru nebo tak, že si vyhledáte vlastní soubor. rgs (otevřete adresář poskytovatele a vyhledejte `ProgID` klíč).

Soubor Mojedata. txt je součástí ukázky `MyProv`. Chcete-li vytvořit vlastní soubor, použijte Editor a zadejte sudý počet řetězců a stiskněte klávesu **ENTER** mezi každým řetězcem. Pokud soubor přesunete, změňte název cesty.

Do `table.Open` řádku předejte řetězec "c:\\\Samples\\\myprov\\\MyData.txt". Pokud zadáte krok do `Open` volání, uvidíte, že tento řetězec je předán metodě `SetCommandText` ve zprostředkovateli. Všimněte si, že metoda `ICommandText::Execute` použila tento řetězec.

Chcete-li načíst data, zavolejte `MoveNext` v tabulce. `MoveNext` volá funkce `IRowset::GetNextRows`, `GetRowCount`a `GetData`. Pokud neexistují žádné další řádky (to znamená, že aktuální pozice v sadě řádků je větší než `GetRowCount`), smyčka skončí.

Pokud nejsou k dispozici žádné další řádky, zprostředkovatelé vrátí DB_S_ENDOFROWSET. Hodnota DB_S_ENDOFROWSET není chyba. Vždy byste měli kontrolovat S_OK, abyste zrušili smyčku načítání dat a nepoužili makro SUCCEEDED.

Nyní byste měli být schopni sestavit a otestovat program.

## <a name="see-also"></a>Viz také

[Rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md)