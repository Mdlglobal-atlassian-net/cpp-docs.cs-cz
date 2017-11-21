---
title: 'TN043: Rutiny RFX | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RFX
dev_langs: C++
helpviewer_keywords:
- RFX (record field exchange), architecture
- TN043
- RFX (record field exchange)
ms.assetid: f552d0c1-2c83-4389-b472-42c9940aa713
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8b0435385455b759d16c3d78dfad36bab00f9de8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="tn043-rfx-routines"></a>TN043: Rutiny RFX
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Tato poznámka popisuje architekturu pole záznamu (exchange – RFX). Také popisuje, jak psát **RFX_** postupu.  
  
## <a name="overview-of-record-field-exchange"></a>Přehled výměna pole záznamu  
 Všechny funkce pole sady záznamů se provádějí pomocí kódu C++. Neexistují žádné zvláštní prostředky nebo magic makra. Vysílat mechanismu je virtuální funkce, která musí být přepsána nastaveními v každé třídy odvozené záznamů. Vždy zjistí následujícím způsobem:  
  
```  
void CMySet::DoFieldExchange(CFieldExchange* pFX)  
{ *//{{AFX_FIELD_MAP(CMySet)  
 <recordset exchange field type call>  
 <recordset exchange function call> *//}}AFX_FIELD_MAP  
}  
```  
  
 Afx – komentáře speciální formát povolit ClassWizard pro vyhledání a úpravy kódu v rámci této funkce. Kód, který není kompatibilní s ClassWizard musí být umístěny mimo speciální formát komentáře.  
  
 V předchozím příkladu < recordset_exchange_field_type_call > je ve formátu:  
  
```  
pFX->SetFieldType(CFieldExchange::outputColumn);
```  
  
 a < recordset_exchange_function_call > je ve formátu:  
  
```  
RFX_Custom(pFX, "Col2",
    m_Col2);
```  
  
 Většina **RFX_** funkce mají tři argumenty jako v příkladu nahoře, ale některé (například `RFX_Text` a `RFX_Binary`) mají další volitelné argumenty.  
  
 Více než jeden **RFX_** může být součástí každé `DoDataExchange` funkce.  
  
 Najdete v části "afxdb.h' seznam všech záznamů pole exchange rutiny dodávané s knihovnou MFC.  
  
 Sada záznamů pole volání představují způsob registrace umístění v paměti (obvykle datové členy) k uložení dat pole pro **CMySet** třídy.  
  
## <a name="notes"></a>Poznámky  
 Funkce sady záznamů pole jsou navrženy pro práci jenom s `CRecordset` třídy. Nejsou obecně použitelná pro jiné třídy MFC.  
  
 Počáteční hodnoty dat se nastavují v standardní C++ konstruktoru, obvykle v bloku s `//{{AFX_FIELD_INIT(CMylSet)` a `//}}AFX_FIELD_INIT` komentáře.  
  
 Každý **RFX_** funkce musí podporovat různé operace, od vrácením archivace pole v rámci přípravy pro úpravy pole nevyřízený stav pole.  
  
 Jednotlivé funkce, která volá `DoFieldExchange` (například `SetFieldNull`, `IsFieldDirty`), nemá vlastní inicializaci kolem volání `DoFieldExchange`.  
  
## <a name="how-does-it-work"></a>Jak to funguje  
 Není nutné pochopit následující, abyste mohli používat – record field exchange. Pochopení, jak to funguje na pozadí vám pomůže však napsat vlastní postup exchange.  
  
 `DoFieldExchange` – Členská funkce je podobné jako `Serialize` – členská funkce – je zodpovědná za získání nebo nastavení data do nebo z formuláře externí (v této případu sloupců z výsledek dotazu rozhraní ODBC) z/do data členů v třídě. `pFX` Parametr je kontext provádění výměny dat a je podobná `CArchive` parametru `CObject::Serialize`. `pFX` ( `CFieldExchange` Objektu) má ukazatel operace, které je podobné, ale generalizace z `CArchive` příznak směru. Funkce RFX může mít pro podporu následující operace:  
  
- **BindParam** – uveďte, kde by měl ODBC načtení dat parametru  
  
- **BindFieldToColumn** – označit kde ODBC musí načíst nebo uložení outputColumn dat  
  
- **Oprava** – nastavte **CString/CByteArray** délky, nastavte hodnotu NULL stav bit  
  
- **MarkForAddNew** – označit nesprávné, pokud je hodnota změněna od AddNew volání  
  
- **MarkForUpdate** – označit nesprávné, pokud hodnota změněna od upravit volání  
  
- **Název** – připojit názvy polí pro pole označila jako neaktualizované  
  
- **Názevhodnota** – připojení "\<název sloupce > =" pro pole označila jako neaktualizované  
  
- **Hodnota** – připojení "" následované oddělovače, jako například ',' nebo '.  
  
- `SetFieldDirty`– Nastavte stav bit změny (tj. změněné) pole  
  
- `SetFieldNull`– Nastavte stav bit označující pro pole hodnotu null  
  
- `IsFieldDirty`– Návratová hodnota bit změny stavu  
  
- `IsFieldNull`– Vrátit hodnotu null stav bit  
  
- `IsFieldNullable`– Vrací hodnotu TRUE, pokud pole může obsahovat hodnoty NULL  
  
- **StoreField** – archivu hodnota pole  
  
- **LoadField** – opětovného načtení archivovat hodnota pole  
  
- **GetFieldInfoValue** – vrátí obecné informace na pole  
  
- **GetFieldInfoOrdinal** – vrátí obecné informace na pole  
  
## <a name="user-extensions"></a>Tato rozšíření  
 Existuje několik způsobů, jak rozšířit výchozí mechanismus RFX. Můžeš  
  
-   Přidáte nové datové typy. Příklad:  
  
 ```  
    CBookmark 
 ```  
  
-   Přidáte nové postupy exchange (RFX_).  
  
 ```  
    void AFXAPI RFX_Bigint(CFieldExchange* pFX,
    const char *szName,  
    BIGINT& value);

 ```  
  
-   Máte `DoFieldExchange` – členská funkce podmíněně zahrnovat další volání RFX nebo jiné platné příkazy C++.  
  
 ```  
    while (posExtraFields != NULL)  
 {  
    RFX_Text(pFX,
    m_listName.GetNext(posExtraFields),   
    m_listValue.GetNext(posExtraValues));

 }  
 ```  
  
> [!NOTE]
>  Takový kód ClassWizard se nedá upravit a měli použít pouze mimo speciální formát komentáře.  
  
## <a name="writing-a-custom-rfx"></a>Psaní vlastních RFX  
 Zápis funkce RFX vlastní, je doporučeno zkopírovat existující funkce RFX a upravit ho na vlastní účely. Výběr správné RFX kopírování můžete nastavit, vaše úlohy mnohem jednodušší. Některé funkce RFX mít některé jedinečné vlastnosti, které byste měli vzít v úvahu při rozhodování, kam chcete zkopírovat.  
  
 **Rfx_long – a rfx_int –**:  
 Jedná se o nejjednodušší funkce RFX. Hodnota dat není nutné žádné speciální interpretace a velikost dat vyřešen.  
  
 **Rfx_single – a rfx_double –**:  
 Jako rfx_long – a rfx_int – výše, tyto funkce jsou jednoduché a ujistěte se, můžete použít výchozí implementace hojně. Jsou uložené ve dbflt.cpp místo dbrfx.cpp, ale chcete-li povolit načítání modulu runtime plovoucí bodu knihovny jenom v případě, že jsou explicitně odkaz.  
  
 **RFX_Text – a RFX_Binary –**:  
 Tyto dvě funkce předem přidělit statické vyrovnávací paměti pro uložení řetězců nebo binární informace a musíte zaregistrovat tyto vyrovnávací paměti s ODBC SQLBindCol místo registrace & hodnota. Z tohoto důvodu se tyto dvě funkce máte spoustu zvláštní případ kódu.  
  
 `RFX_Date`:  
 ODBC vrátí informace o datu a času ve své vlastní TIMESTAMP_STRUCT z datové struktury. Tato funkce dynamicky přiděluje TIMESTAMP_STRUCT z jako "proxy" pro odesílání a příjmu dat Datum čas. Různé operace musíte přenést informace o datu a času mezi C++ `CTime` objekt a TIMESTAMP_STRUCT z proxy serveru. To výrazně komplikuje tuto funkci, ale je dobrým příkladem toho, jak použít server proxy pro přenos dat.  
  
 `RFX_LongBinary`:  
 Toto je pouze knihovny tříd RFX funkce, která nepoužívá pro příjem a odesílání dat vazba sloupce. Tato funkce ignoruje operaci BindFieldToColumn a místo toho v průběhu operace oprava přiděluje úložiště pro uložení příchozích dat SQL_LONGVARCHAR nebo SQL_LONGVARBINARY pak provede volání SQLGetData k načtení hodnoty do úložiště přidělené. Když se připravuje na odeslání, že hodnoty dat zpět do zdroje dat (například Názevhodnota a hodnotu operations), tato funkce využívá DATA_AT_EXEC fungování rozhraní ODBC je. V tématu [Technická poznámka 45](../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md) Další informace o práci s SQL_LONGVARBINARY a SQL_LONGVARCHARs.  
  
 Při zápisu vlastní **RFX_** funkce, často bude moci používat **CFieldExchange::Default** implementovat danou operaci. Podívejte se na provádění výchozí pro operace. Pokud se provede operaci by zápis do vaší **RFX_** funkce můžete delegovat na **CFieldExchange::Default.** Vidíte příklady volání **CFieldExchange::Default** v dbrfx.cpp  
  
 Je důležité k volání `IsFieldType` na začátku funkce RFX a vraťte se okamžitě, pokud vrátí hodnotu FALSE. Tento mechanismus udržuje parametr operací z provádí na **outputColumns**a naopak (jako je volání **BindParam** na **outputColumn**). Kromě toho `IsFieldType` automaticky uchovává informace o počtu **outputColumns** (`m_nFields`) a parametry (`m_nParams`).  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

