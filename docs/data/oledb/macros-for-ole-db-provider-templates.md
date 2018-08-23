---
title: Makra pro šablony zprostředkovatele OLE DB | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc.templates.ole
- BEGIN_PROPERTY_SET
- BEGIN_PROPERTY_SET_EX
- BEGIN_PROPSET_MAP
- CHAIN_PROPERTY_SET
- END_PROPERTY_SET
- END_PROPSET_MAP
- PROPERTY_INFO_ENTRY
- PROPERTY_INFO_ENTRY_EX
- PROPERTY_INFO_ENTRY_VALUE
- BEGIN_PROVIDER_COLUMN_MAP
- END_PROVIDER_COLUMN_MAP
- PROVIDER_COLUMN_ENTRY
- PROVIDER_COLUMN_ENTRY_FIXED
- PROVIDER_COLUMN_ENTRY_GN
- PROVIDER_COLUMN_ENTRY_LENGTH
- PROVIDER_COLUMN_ENTRY_STR
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
- PROVIDER_COLUMN_ENTRY_WSTR
- BEGIN_SCHEMA_MAP
- END_SCHEMA_MAP
- SCHEMA_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates, macros
- macros, OLE DB Provider Templates
- Provider Template macros (OLE DB)
- OLE DB Provider Template macros
- BEGIN_PROPERTY_SET macro
- BEGIN_PROPERTY_SET_EX macro
- BEGIN_PROPSET_MAP macro
- CHAIN_PROPERTY_SET macro
- END_PROPERTY_SET macro
- END_PROPSET_MAP macro
- PROPERTY_INFO_ENTRY macro
- PROPERTY_INFO_ENTRY_EX macro
- PROPERTY_INFO_ENTRY_VALUE macro
- BEGIN_PROVIDER_COLUMN_MAP macro
- END_PROVIDER_COLUMN_MAP macro
- PROVIDER_COLUMN_ENTRY macro
- PROVIDER_COLUMN_ENTRY_FIXED macro
- PROVIDER_COLUMN_ENTRY_GN macro
- PROVIDER_COLUMN_ENTRY_LENGTH macro
- PROVIDER_COLUMN_ENTRY_STR macro
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH macro
- PROVIDER_COLUMN_ENTRY_WSTR macro
- BEGIN_SCHEMA_MAP macro
- END_SCHEMA_MAP macro
- SCHEMA_ENTRY macro
ms.assetid: 909482c5-64ab-4e52-84a9-1c07091db183
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 747f54e4ae37fe31eeea7540c1531b988d692427
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464630"
---
# <a name="macros-for-ole-db-provider-templates"></a>Makra pro šablony zprostředkovatele OLE DB
Makra poskytovatele šablony technologie OLE DB nabízejí funkce v následujících kategoriích:  
  
## <a name="property-set-map-macros"></a>Makra Map vlastností sady  
  
|||  
|-|-|  
|[BEGIN_PROPERTY_SET](#begin_property_set)|Označuje začátek toho sadu vlastností.|  
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|Označuje začátek toho sadu vlastností.|  
|[BEGIN_PROPSET_MAP](#begin_propset_map)|Značky na začátek vlastnost nastavena, které můžete skrytý nebo definované mimo obor poskytovatele.|  
|[CHAIN_PROPERTY_SET](#chain_property_set)|Vlastnosti skupiny zřetězí společně.|  
|[END_PROPERTY_SET](#end_property_set)|Označuje konec sady vlastností.|  
|[END_PROPSET_MAP](#end_propset_map)|Označuje konec mapy sady vlastností.|  
|[PROPERTY_INFO_ENTRY](#property_info_entry)|Určité vlastnosti nastaví ve vlastnosti nastavit na výchozí hodnotu.|  
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|Určité vlastnosti nastaví ve vlastnosti nastavit na hodnotu vámi zadané. Také vám umožní nastavit příznaky a možnosti.|  
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|Určité vlastnosti nastaví ve vlastnosti nastavit na hodnotu vámi zadané.|  
  
## <a name="column-map-macros"></a>Makra Map sloupec  
  
|||  
|-|-|  
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|Označuje začátek položky mapování sloupce zprostředkovatele.|  
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|Označuje konec položky mapování sloupce zprostředkovatele.|  
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|Představuje konkrétní sloupec podporována zprostředkovatelem.|  
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|Představuje konkrétní sloupec podporována zprostředkovatelem. Můžete zadat datový typ sloupce.|  
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|Představuje konkrétní sloupec podporována zprostředkovatelem. Můžete zadat velikost sloupce, datový typ, přesnost, měřítko a identifikátor GUID sady řádků schématu.|  
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|Představuje konkrétní sloupec podporována zprostředkovatelem. Můžete zadat velikost sloupce.|  
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|Představuje konkrétní sloupec podporována zprostředkovatelem. Předpokládá se, že typ sloupce není řetězec.|  
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|Představuje konkrétní sloupec podporována zprostředkovatelem. PROVIDER_COLUMN_ENTRY_LENGTH, jako jsou, ale také umožňuje určit typ sloupce dat, jakož i velikost.|  
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|Představuje konkrétní sloupec podporována zprostředkovatelem. Předpokládá se, že typ sloupce je řetězec znaků Unicode.|  
  
## <a name="schema-rowset-macros"></a>Makra sady řádků schématu  
  
|||  
|-|-|  
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|Označuje začátek toho mapy schémat.|  
|[END_SCHEMA_MAP](#end_schema_map)|Označuje konec mapování schématu.|  
|[SCHEMA_ENTRY](#schema_entry)|Přiřadí identifikátor GUID s třídou.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  

### <a name="begin_property_set"></a> BEGIN_PROPERTY_SET
Značky, které od vlastnosti nastavte do vlastnosti nastavit mapování.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
BEGIN_PROPERTY_SET(guid)  
```  
  
#### <a name="parameters"></a>Parametry  
 *identifikátor GUID*  
 [in] Vlastnost identifikátor GUID.  
  
#### <a name="example"></a>Příklad  
 Zobrazit [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="begin_property_set_ex"></a> BEGIN_PROPERTY_SET_EX
Značky, které od vlastnosti nastavte do vlastnosti nastavit mapování.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
BEGIN_PROPERTY_SET_EX(guid, flags)  
```  
  
#### <a name="parameters"></a>Parametry  
 *identifikátor GUID*  
 [in] Vlastnost identifikátor GUID.  
  
 *příznaky*  
 [in] UPROPSET_HIDDEN pro všechny sady vlastností, které nechcete zveřejnit nebo UPROPSET_PASSTHROUGH zprostředkovatele vystavení vlastností, které jsou definovány mimo obor poskytovatele.  
  
#### <a name="example"></a>Příklad  
 Zobrazit [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="begin_propset_map"></a> BEGIN_PROPSET_MAP
Značky na začátek vlastnosti nastavte položky mapy.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
BEGIN_PROPSET_MAP(Class)  
```  
  
#### <a name="parameters"></a>Parametry  
 *Třída*  
 [in] Je zadána třída, ve kterém tuto vlastnost nastavit. V následující objekty OLE DB lze zadat sadu vlastností:  
  
-   [Objekty zdroje dat](/previous-versions/windows/desktop/ms721278\(v=vs.85\))  
  
-   [Objekty relace](/previous-versions/windows/desktop/ms711572\(v=vs.85\))  
  
-   [Příkazy](/previous-versions/windows/desktop/ms724608\(v=vs.85\))  
  
#### <a name="example"></a>Příklad  
 Tady je mapy sady vlastností vzorku:  
  
 [!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]  

### <a name="chain_property_set"></a> CHAIN_PROPERTY_SET
Toto makro zřetězí společně skupiny vlastností.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
CHAIN_PROPERTY_SET(ChainClass)  
```  
  
#### <a name="parameters"></a>Parametry  
 *ChainClass*  
 [in] Název třídy pro vlastnosti řetězce. Toto je třída generované průvodcem knihovnou ATL projektu, který již obsahuje mapu (například relaci, příkaz nebo datového zdroje objektu třídy).  
  
#### <a name="remarks"></a>Poznámky  
 Můžete zřetězit nastavenou vlastnost z jiné třídy do své vlastní třídy a pak přístup k vlastnostem přímo z vaší třídy.  
  
> [!CAUTION]
>  Toto makro používejte opatrně. Nesprávné použití může způsobit příjemce selhání testů shodnosti technologie OLE DB.  

### <a name="end_property_set"></a> END_PROPERTY_SET
Označuje konec sady vlastností.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
END_PROPERTY_SET(guid)  
```  
  
#### <a name="parameters"></a>Parametry  
 *identifikátor GUID*  
 [in] Vlastnost identifikátor GUID.  
  
#### <a name="example"></a>Příklad  
 Zobrazit [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="end_propset_map"></a> END_PROPSET_MAP
Značky konec vlastnosti nastavte položky mapy.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
END_PROPSET_MAP()  
```  
  
#### <a name="example"></a>Příklad  
 Zobrazit [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="property_info_entry"></a> PROPERTY_INFO_ENTRY
Představuje konkrétní vlastnost sady vlastností.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
PROPERTY_INFO_ENTRY(dwPropID)  
```  
  
#### <a name="parameters"></a>Parametry  
 *dwPropID*  
 [in] A [DBPROPID](/previous-versions/windows/desktop/ms723882\(v=vs.85\)) identifikátor GUID k identifikaci vlastnost nastavit hodnotu, kterou můžete použít ve spojení s vlastností.  
  
#### <a name="remarks"></a>Poznámky  
 Toto makro nastaví hodnotu vlastnosti typu `DWORD` na výchozí hodnotu definovanou v ATLDB. H. Chcete-li nastavit vlastnost na hodnotu podle vašeho výběru, použijte [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md). Chcete-li nastavit [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) a [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342\(v=vs.85\)) pro vlastnost ve stejnou dobu, použijte [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).  
  
#### <a name="example"></a>Příklad  
 Zobrazit [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="property_info_entry_ex"></a> PROPERTY_INFO_ENTRY_EX
Představuje konkrétní vlastnost sady vlastností.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID, vt, dwFlags, value, options)  
```  
  
#### <a name="parameters"></a>Parametry  
 *dwPropID*  
 [in] A [DBPROPID](/previous-versions/windows/desktop/ms723882\(v=vs.85\)) identifikátor GUID k identifikaci vlastnost nastavit hodnotu, kterou můžete použít ve spojení s vlastností.  
  
 *vt*  
 [in] [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) této vlastnosti položky.  
  
 *dwFlags*  
 [in] A [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342\(v=vs.85\)) hodnotu popisující tuto položku Vlastnosti.  
  
 *value*  
 [in] Hodnota vlastnosti typu `DWORD`.  
  
 *Možnosti*  
 DBPROPOPTIONS_REQUIRED nebo DBPROPOPTIONS_SETIFCHEAP. Za normálních okolností není nutné nastavit zprostředkovatele *možnosti* protože je nastaven uživatelem.  
  
#### <a name="remarks"></a>Poznámky  
 Tímto makrem můžete přímo zadat hodnotu vlastnosti typu `DWORD` a také možnosti a příznaky. Nastavení pro výchozí hodnotu definovanou v ATLDB pouze vlastnosti. H, použijte [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Chcete-li nastavit vlastnost na hodnotu dle vlastního výběru, bez možnosti nastavení nebo příznaky, použijte [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md).  
  
#### <a name="example"></a>Příklad  
 Zobrazit [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="property_info_entry_value"></a> PROPERTY_INFO_ENTRY_VALUE
Představuje konkrétní vlastnost sady vlastností.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID, value)  
```  
  
#### <a name="parameters"></a>Parametry  
 *dwPropID*  
 [in] A [DBPROPID](/previous-versions/windows/desktop/ms723882\(v=vs.85\)) identifikátor GUID k identifikaci vlastnost nastavit hodnotu, kterou můžete použít ve spojení s vlastností.  
  
 *value*  
 [in] Hodnota vlastnosti typu `DWORD`.  
  
#### <a name="remarks"></a>Poznámky  
 Tímto makrem můžete přímo zadat hodnotu vlastnosti typu `DWORD`. Chcete-li nastavit vlastnost na výchozí hodnotu definovanou v ATLDB. H, použijte [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Chcete-li nastavit hodnotu, příznaky a možnosti pro vlastnost, použijte [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).  
  
#### <a name="example"></a>Příklad  
 Zobrazit [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="begin_provider_column_map"></a> BEGIN_PROVIDER_COLUMN_MAP
Označuje začátek položky mapování sloupce zprostředkovatele.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)  
```  
  
#### <a name="parameters"></a>Parametry  
 *theClass*  
 [in] Název třídy, do které patří toto mapování.  
  
#### <a name="example"></a>Příklad  
 Tady je ukázkové mapování sloupce zprostředkovatele:  
  
 [!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]  

### <a name="end_provider_column_map"></a> END_PROVIDER_COLUMN_MAP
Označuje konec položky mapování sloupce zprostředkovatele.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
END_PROVIDER_COLUMN_MAP()  
```  
  
#### <a name="example"></a>Příklad  
 Zobrazit [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).  

### <a name="provider_column_entry"></a> PROVIDER_COLUMN_ENTRY
Představuje konkrétní sloupec podporována zprostředkovatelem.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
PROVIDER_COLUMN_ENTRY (name, ordinal, member)  
```  
  
#### <a name="parameters"></a>Parametry  
 *Jméno*  
 [in] Název sloupce.  
  
 *Pořadí*  
 [in] Číslo sloupce. Pokud sloupec není sloupec záložky, číslo sloupce nesmí být 0.  
  
 *Člen*  
 [in] Členské proměnné v `dataClass` odpovídající sloupec.  

### <a name="provider_column_entry_fixed"></a> PROVIDER_COLUMN_ENTRY_FIXED
Představuje konkrétní sloupec podporována zprostředkovatelem.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name, ordinal, dbtype, member)  
```  
  
#### <a name="parameters"></a>Parametry  
 *Jméno*  
 [in] Název sloupce.  
  
 *Pořadí*  
 [in] Číslo sloupce. Pokud sloupec není sloupec záložky, číslo sloupce nesmí být 0.  
  
 *Hodnota DbType*  
 [in] Datový typ v [DBTYPE](/previous-versions/windows/desktop/ms711251\(v=vs.85\)).  
  
 *Člen*  
 [in] Členské proměnné v `dataClass` , který ukládá data.  
  
#### <a name="remarks"></a>Poznámky  
 Umožňuje zadat datový typ sloupce.  
  
#### <a name="example"></a>Příklad  
 Zobrazit [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).  

### <a name="provider_column_entry_gn"></a> PROVIDER_COLUMN_ENTRY_GN
Představuje konkrétní sloupec podporována zprostředkovatelem.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
PROVIDER_COLUMN_ENTRY_GN (name, ordinal, flags, colSize, dbtype, precision, scale, guid)  
```  
  
#### <a name="parameters"></a>Parametry  
 *Jméno*  
 [in] Název sloupce.  
  
 *Pořadí*  
 [in] Číslo sloupce. Pokud sloupec není sloupec záložky, číslo sloupce nesmí být 0.  
  
 *příznaky*  
 [in] Určuje, jak se data vrací. Zobrazit `dwFlags` popis v [DBBINDING struktury](/previous-versions/windows/desktop/ms716845\(v=vs.85\)).  
  
 *colSize*  
 [in] Velikost sloupce.  
  
 *Hodnota DbType*  
 [in] Určuje datový typ hodnoty. Zobrazit `wType` popis v [DBBINDING struktury](/previous-versions/windows/desktop/ms716845\(v=vs.85\)).  
  
 *Přesnost*  
 [in] Určuje přesnost pro použití při získávání dat, pokud *dbType* DBTYPE_NUMERIC nebo DBTYPE_DECIMAL. Zobrazit `bPrecision` popis v [DBBINDING struktury](/previous-versions/windows/desktop/ms716845\(v=vs.85\)).  
  
 *Škálování*  
 [in] Označuje chcete použít při získávání dat, pokud je hodnota dbType DBTYPE_NUMERIC nebo DBTYPE_DECIMAL. Zobrazit `bScale` popis v [DBBINDING struktury](/previous-versions/windows/desktop/ms716845\(v=vs.85\)).  
  
 *identifikátor GUID*  
 Sadu řádků schématu identifikátoru GUID. Zobrazit [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\)) v *OLE DB referenční informace pro programátory* seznam sad řádků schématu a jejich identifikátory GUID.  
  
#### <a name="remarks"></a>Poznámky  
 Umožňuje zadat velikost sloupce, datový typ, přesnost, měřítko a identifikátor GUID sady řádků schématu.  

### <a name="provider_column_entry_length"></a> PROVIDER_COLUMN_ENTRY_LENGTH
Představuje konkrétní sloupec podporována zprostředkovatelem.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name, ordinal, size, member)  
```  
  
#### <a name="parameters"></a>Parametry  
 *Jméno*  
 [in] Název sloupce.  
  
 *Pořadí*  
 [in] Číslo sloupce. Pokud sloupec není sloupec záložky, číslo sloupce nesmí být 0.  
  
 *Velikost*  
 [in] Velikost sloupce v bajtech.  
  
 *Člen*  
 [in] Členské proměnné v `dataClass` , který ukládá data sloupce.  
  
#### <a name="remarks"></a>Poznámky  
 Umožňuje zadat velikost sloupce.  
  
#### <a name="example"></a>Příklad  
 Zobrazit [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md). 

### <a name="provider_column_entry_str"></a> PROVIDER_COLUMN_ENTRY_STR
Představuje konkrétní sloupec podporována zprostředkovatelem.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
PROVIDER_COLUMN_ENTRY_STR(name, ordinal, member)  
```  
  
#### <a name="parameters"></a>Parametry  
 *Jméno*  
 [in] Název sloupce.  
  
 *Pořadí*  
 [in] Číslo sloupce. Pokud sloupec není sloupec záložky, číslo sloupce nesmí být 0.  
  
 *Člen*  
 [in] Členské proměnné v datové třídě, která ukládá data.  
  
#### <a name="remarks"></a>Poznámky  
 Použijte toto makro, když sloupec data je považován za [typem DBTYPE_STR](/previous-versions/windows/desktop/ms711251\(v=vs.85\)).  
  
#### <a name="example"></a>Příklad  
 Zobrazit [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).   

### <a name="provider_column_entry_type_length"></a> PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
Představuje konkrétní sloupec podporována zprostředkovatelem.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name, ordinal, dbtype, size, member)  
```  
  
#### <a name="parameters"></a>Parametry  
 *Jméno*  
 [in] Název sloupce.  
  
 *Pořadí*  
 [in] Číslo sloupce. Pokud sloupec není sloupec záložky, číslo sloupce nesmí být 0.  
  
 *Hodnota DbType*  
 [in] Datový typ v [DBTYPE](/previous-versions/windows/desktop/ms711251\(v=vs.85\)).  
  
 *Velikost*  
 [in] Velikost sloupce v bajtech.  
  
 *Člen*  
 [in] Členské proměnné v datové třídě, která ukládá data.  
  
#### <a name="remarks"></a>Poznámky  
 Podobně jako [PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md) , ale také umožňuje určit typ sloupce dat, jakož i velikost.  

### <a name="provider_column_entry_wstr"></a> PROVIDER_COLUMN_ENTRY_WSTR
Představuje konkrétní sloupec podporována zprostředkovatelem.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name, ordinal, member)  
```  
  
#### <a name="parameters"></a>Parametry  
 *Jméno*  
 [in] Název sloupce.  
  
 *Pořadí*  
 [in] Číslo sloupce. Pokud sloupec není sloupec záložky, číslo sloupce nesmí být 0.  
  
 *Člen*  
 [in] Členské proměnné v datové třídě, která ukládá data.  
  
#### <a name="remarks"></a>Poznámky  
 Když sloupec data s hodnotou null byl ukončen řetězec znaků Unicode, použijte toto makro [DBTYPE_WSTR](/previous-versions/windows/desktop/ms711251\(v=vs.85\)).  

### <a name="begin_schema_map"></a> BEGIN_SCHEMA_MAP
Označuje začátek mapování schématu.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
BEGIN_SCHEMA_MAP(SchemaClass);  
```  
  
#### <a name="parameters"></a>Parametry  
 *SchemaClass*  
 Třída, která obsahuje MAPU. Obvykle bude třídu relace.  
  
#### <a name="remarks"></a>Poznámky  
 Zobrazit [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\)) v sadě Windows SDK pro další informace o sad řádků schématu.  

### <a name="end_schema_map"></a> END_SCHEMA_MAP
Označuje konec mapování schématu.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
END_SCHEMA_MAP()  
```  
  
#### <a name="see-also"></a>Viz také  
 [IDBSchemaRowsetImpl – třída](../../data/oledb/idbschemarowsetimpl-class.md)

### <a name="schema_entry"></a> SCHEMA_ENTRY
Přiřadí identifikátor GUID s třídou.  
  
#### <a name="syntax"></a>Syntaxe  
  
```cpp
SCHEMA_ENTRY(guid,  
   rowsetClass);   
```  
  
#### <a name="parameters"></a>Parametry  
 *identifikátor GUID*  
 Sadu řádků schématu identifikátoru GUID. Zobrazit [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\)) v *OLE DB referenční informace pro programátory* seznam sad řádků schématu a jejich identifikátory GUID.  
  
 *RowsetClass*  
 Třída, která bude vytvořena a představují sadu řádků schématu.  
  
#### <a name="remarks"></a>Poznámky  
 [IDBSchemaRowsetImpl –](../../data/oledb/idbschemarowsetimpl-class.md) pak může dotaz na mapě seznamu identifikátorů GUID, nebo je možné vytvořit sadu řádků, pokud se klíči přiřadí identifikátor GUID. Sada řádků schématu `IDBSchemaRowsetImpl` vytvoří je podobná standardní `CRowsetImpl`-odvozené třídy, s výjimkou musí poskytovat `Execute` metodu, která má následující podpis:  
  
```cpp  
HRESULT Execute (LONG* pcRowsAffected,  
    ULONG cRestrictions,  
    const VARIANT* rgRestrictions);  
```  
  
 To `Execute` funkce provede naplnění dat v sadě řádků. Průvodce projektem ATL vytvoří, jak je popsáno v [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\)) v *OLE DB referenční informace pro programátory*, tři počáteční sad řádků schématu v projektu pro všechny tři povinné schémat OLE DB:  
  
-   DBSCHEMA_TABLES  
  
-   DBSCHEMA_COLUMNS  
  
-   DBSCHEMA_PROVIDER_TYPES  
  
 Průvodce také přidá tři odpovídající položky v mapování schématu. Zobrazit [vytváření poskytovatele šablony technologie OLE DB](../../data/oledb/creating-an-ole-db-provider.md) Další informace o používání průvodce k vytvoření poskytovatele.  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)   
 [Reference šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)    
 [Makra pro šablony zprostředkovatele OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   