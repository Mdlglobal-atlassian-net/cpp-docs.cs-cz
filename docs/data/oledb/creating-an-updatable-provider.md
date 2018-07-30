---
title: Vytvoření aktualizovatelného zprostředkovatele | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e9ee36d2300ed1e86c1f867012ed54c85692f5bd
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340635"
---
# <a name="creating-an-updatable-provider"></a>Vytvoření aktualizovatelného zprostředkovatele

Jazyk Visual C++ podporuje aktualizovatelné zprostředkovatele nebo zprostředkovatele, které můžete aktualizovat (zápis do) úložiště. Toto téma popisuje, jak vytvořit aktualizovatelní zprostředkovatelé pomocí šablony technologie OLE DB.  
  
 Toto téma předpokládá, že začínáte s funkční zprostředkovatele. Existují dva kroky k vytvoření aktualizovatelného zprostředkovatele. Nejprve musíte rozhodnout, jak poskytovatel provede změny úložiště dat; Určuje, zda konkrétně změny jsou okamžitě provést nebo odložena až do vydání příkazu k aktualizaci. V části "[provádění aktualizovat poskytovatele](#vchowmakingprovidersupdatable)" popisuje změny a nastavení, musíte udělat v kódu zprostředkovatele.  
  
 V dalším kroku je nutné zajistit, aby že váš poskytovatel obsahuje všechny funkce pro podporu všechno, co ho může požádat příjemce. Pokud chce aktualizujte úložiště dat příjemce, musí obsahovat kód, který přenese data do úložiště dat zprostředkovatele. Například můžete provádět tyto operace na zdroj dat použít knihovny Run-Time jazyka C nebo MFC. V části "[zápisu do zdroje dat](#vchowwritingtothedatasource)" popisuje, jak zapsat do zdroje dat, řešení s hodnotou NULL a výchozí hodnoty a nastavit příznaky sloupce.  
  
> [!NOTE]
>  UpdatePV je příkladem aktualizovatelného zprostředkovatele. UpdatePV je stejný jako MyProv, ale s podporou.  
  
##  <a name="vchowmakingprovidersupdatable"></a> Vytváření zprostředkovatelů aktualizovat  

 Klíčem k tvorbě aktualizovatelného zprostředkovatele se ke zjištění, jaké operace, které má váš poskytovatel provádět v úložišti dat a jak chcete poskytovatele provádět tyto operace. Konkrétně je závažný problém, jestli jsou aktualizace do úložiště dat provést okamžitě, nebo odloženo (dávkované) až do vydání příkazu k aktualizaci.  
  
 Je třeba nejprve rozhodnout, jestli se má dědit z `IRowsetChangeImpl` nebo `IRowsetUpdateImpl` ve své třídě sady řádků. V závislosti na tom, který z nich rozhodnete implementovat, bude mít vliv funkce tři metody: `SetData`, `InsertRows`, a `DeleteRows`.  
  
- Pokud je zděděn z [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md), tyto tři metody volání okamžitě změní úložišti.  
  
- Pokud je zděděn z [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md), metody odložit změny do úložiště dat, dokud nezavoláte `Update`, `GetOriginalData`, nebo `Undo`. Pokud aktualizace zahrnuje několik změn, jsou provedeny v dávkovém režimu (Poznámka: dávkování změny můžete přidat režijní náklady na značnou paměť).  
  
 Všimněte si, že `IRowsetUpdateImpl` je odvozena z `IRowsetChangeImpl`. Proto `IRowsetUpdateImpl` umožňuje změnit možnosti a funkce služby batch.  
  
#### <a name="to-support-updatability-in-your-provider"></a>Chcete-li podporovat ve zprostředkovateli  
  
1. Ve své třídě řádků dědit z `IRowsetChangeImpl` nebo `IRowsetUpdateImpl`. Tyto třídy poskytují vhodné rozhraní pro Změna úložiště dat:  
  
     **Přidání IRowsetChange**  
  
     Přidat `IRowsetChangeImpl` k použití této formy řetězec dědičnosti:  
  
    ```cpp  
    IRowsetChangeImpl< rowset-name, storage-name >  
    ```  
  
     Přidejte také `COM_INTERFACE_ENTRY(IRowsetChange)` k `BEGIN_COM_MAP` oddílu ve své třídě sady řádků.  
  
     **Přidání IRowsetUpdate**  
  
     Přidat `IRowsetUpdate` k použití této formy řetězec dědičnosti:  
  
    ```cpp  
    IRowsetUpdateImpl< rowset-name, storage>  
    ```  
  
    > [!NOTE]
    >  Měli byste odebrat `IRowsetChangeImpl` řádek z vašeho řetězu dědičnosti. Jedinou výjimkou je to výše zmíněné musí obsahovat kód `IRowsetChangeImpl`.  
  
2.  Přidejte následující do mapy modelu COM (`BEGIN_COM_MAP ... END_COM_MAP`):  
  
    |Pokud se rozhodnete implementovat|Přidejte do mapy modelu COM.|  
    |----------------------|--------------------|  
    |`IRowsetChangeImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)`|  
    |`IRowsetUpdateImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)COM_INTERFACE_ENTRY(IRowsetUpdate)`|  
  
3.  V příkazu, přidejte následující mapy set vlastnosti (`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`):  
  
    |Pokud se rozhodnete implementovat|Přidejte do mapy sady vlastností|  
    |----------------------|-----------------------------|  
    |`IRowsetChangeImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`|  
    |`IRowsetUpdateImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)`|  
  
4.  V mapě sadu vlastností měli byste také zahrnout všechna následující nastavení, jak se objeví pod:  
  
    ```cpp  
    PROPERTY_INFO_ENTRY_VALUE(UPDATABILITY, DBPROPVAL_UP_CHANGE |   
      DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)  
    PROPERTY_INFO_ENTRY_VALUE(CHANGEINSERTEDROWS, VARIANT_TRUE)  
    PROPERTY_INFO_ENTRY_VALUE(IMMOBILEROWS, VARIANT_TRUE)  
  
    PROPERTY_INFO_ENTRY_EX(OWNINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OWNUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OTHERINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OTHERUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(REMOVEDELETED, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_FALSE, 0)  
    ```  
  
     Můžete najít hodnoty použité v těchto volání makra vyhledáváním v Atldb.h identifikátory vlastnosti a hodnoty (Pokud Atldb.h se liší v online dokumentaci ke službě, nahrazuje Atldb.h dokumentaci).  
  
    > [!NOTE]
    >  Mnoho `VARIANT_FALSE` a `VARIANT_TRUE` vyžaduje nastavení šablony technologie OLE DB; specifikaci OLE DB uvádí, že můžou být r/w, ale šablony technologie OLE DB podporuje pouze jednu hodnotu.  
  
     **Pokud se rozhodnete implementovat IRowsetChangeImpl**  
  
     Pokud se rozhodnete implementovat `IRowsetChangeImpl`, musíte nastavit následující vlastnosti ve zprostředkovateli služby. Tyto vlastnosti se primárně používají k žádosti rozhraní prostřednictvím `ICommandProperties::SetProperties`.  
  
    - `DBPROP_IRowsetChange`: Nastavení tomto automaticky nastaví `DBPROP_IRowsetChange`.  
  
    - `DBPROP_UPDATABILITY`: Bitová maska zadání podporovaných metod na `IRowsetChange`: `SetData`, `DeleteRows`, nebo `InsertRow`.  
  
    - `DBPROP_CHANGEINSERTEDROWS`: Příjemce může volat `IRowsetChange::DeleteRows` nebo `SetData` nově vložených řádků.  
  
    - `DBPROP_IMMOBILEROWS`: Sada řádků nebude pořadí vložené nebo aktualizované řádky.  
  
     **Pokud se rozhodnete implementovat IRowsetUpdateImpl**  
  
     Pokud se rozhodnete implementovat `IRowsetUpdateImpl`, musíte nastavit následující vlastnosti ve zprostředkovateli služby, navíc k nastavením vlastností pro `IRowsetChangeImpl` výše uvedených:  
  
    - `DBPROP_IRowsetUpdate`.  
  
    - `DBPROP_OWNINSERT`: Musí být a VARIANT_TRUE READ_ONLY.  
  
    - `DBPROP_OWNUPDATEDELETE`: Musí být a VARIANT_TRUE READ_ONLY.  
  
    - `DBPROP_OTHERINSERT`: Musí být a VARIANT_TRUE READ_ONLY.  
  
    - `DBPROP_OTHERUPDATEDELETE`: Musí být a VARIANT_TRUE READ_ONLY.  
  
    - `DBPROP_REMOVEDELETED`: Musí být a VARIANT_TRUE READ_ONLY.  
  
    - `DBPROP_MAXPENDINGROWS`.  
  
        > [!NOTE]
        >  Pokud podporujete oznámení, může být také některé také další vlastnosti; naleznete v části `IRowsetNotifyCP` pro tento seznam.  
  
##  <a name="vchowwritingtothedatasource"></a> Zápis do zdroje dat.  
 Chcete-li načíst ze zdroje dat, zavolejte `Execute` funkce. Chcete-li zapsat do zdroje dat, zavolejte `FlushData` funkce. (V obecném smyslu vyprázdněte znamená, že se uložit změny provedené u tabulky nebo indexu na disk.)  

