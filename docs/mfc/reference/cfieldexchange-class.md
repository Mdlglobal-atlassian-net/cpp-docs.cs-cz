---
title: "Třída CFieldExchange | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFieldExchange
- AFXDB/CFieldExchange
- AFXDB/CFieldExchange::IsFieldType
- AFXDB/CFieldExchange::SetFieldType
dev_langs: C++
helpviewer_keywords:
- CFieldExchange [MFC], IsFieldType
- CFieldExchange [MFC], SetFieldType
ms.assetid: 24c5c0b3-06a6-430e-9b6f-005a2c65e29f
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d20a89e48475a0226d76ac719459b1b99cc4e355
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cfieldexchange-class"></a>CFieldExchange – třída
Podporuje pole záznamu (exchange – RFX) a rutiny exchange (Bulk RFX) pole záznamu hromadné používá databázové třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFieldExchange  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CFieldExchange::IsFieldType](#isfieldtype)|Vrátí nenulové hodnoty, pokud aktuální operace je vhodné pro typ pole aktualizované.|  
|[CFieldExchange::SetFieldType](#setfieldtype)|Určuje typ člena data sady záznamů – sloupec nebo parametr – reprezentována všechny následující volání funkce RFX až další volání `SetFieldType`.|  
  
## <a name="remarks"></a>Poznámky  
 `CFieldExchange`nemá základní třídu.  
  
 Tuto třídu použít, pokud píšete rutiny výměny dat pro vlastní datové typy nebo když jsou implementace hromadné načítání řádků; jinak nebudete používat přímo tuto třídu. RFX a Bulk RFX výměnu dat mezi pole datových členů z objektu sady záznamů a odpovídající pole ve zdroji dat na aktuální záznam.  
  
> [!NOTE]
>  Pokud pracujete s třídy objektů DAO (Data Access), nikoli třídy připojení ODBC (Open Database), použijte třídu [CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md) místo. Další informace najdete v článku [programování přehled: databáze](../../data/data-access-programming-mfc-atl.md).  
  
 A `CFieldExchange` objekt poskytuje kontextové informace potřebné pro – record field exchange nebo hromadná výměna pole záznamu provést umístit. `CFieldExchange`objekty podporují několik operací, včetně vázané parametry a pole datových členů a nastavení různé příznaky na pole na aktuální záznam. RFX a Bulk RFX operací na členy třídy sady záznamů dat typy definované `enum` **typ pole** v `CFieldExchange`. Možné **typ pole** hodnoty jsou:  
  
- **CFieldExchange::outputColumn** pro pole datových členů.  
  
- **CFieldExchange::inputParam** nebo **CFieldExchange::param** pro vstupní parametry datových členů.  
  
- **CFieldExchange::outputParam** pro výstupní parametry datových členů.  
  
- **CFieldExchange::inoutParam** pro vstupní a výstupní parametry datových členů.  
  
 Většina funkcí a data členy člena třídy jsou uvedené pro psaní vlastního vlastní rutiny RFX. Budete používat `SetFieldType` často. Další informace najdete v článcích [výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md) a [záznamů (ODBC)](../../data/odbc/recordset-odbc.md). Informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Podrobnosti o globální funkce RFX a hromadně RFX najdete v tématu [funkce výměny polí v záznamu](../../mfc/reference/record-field-exchange-functions.md) v části MFC – makra a globální prvky tohoto odkazu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CFieldExchange`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  
  
##  <a name="isfieldtype"></a>CFieldExchange::IsFieldType  
 Pokud píšete funkce RFX, zavolejte `IsFieldType` na začátku funkce k určení, zda aktuální operaci lze provést na konkrétní pole nebo parametr data člena typu ( **CFieldExchange::outputColumn**, **CFieldExchange::inputParam**, **CFieldExchange::param**, **CFieldExchange::outputParam**, nebo **CFieldExchange::inoutParam** ).  
  
```  
BOOL IsFieldType(UINT* pnField);
```  
  
### <a name="parameters"></a>Parametry  
 *pnField*  
 V tomto parametru je vrácen sekvenční počet datový člen pole nebo parametr. Toto číslo odpovídá pořadí datového člena [CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) nebo [CRecordset::DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) funkce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud aktuální operaci lze provést v aktuální typ pole nebo parametr.  
  
### <a name="remarks"></a>Poznámky  
 Postupujte podle modelu existující funkce RFX.  
  
##  <a name="setfieldtype"></a>CFieldExchange::SetFieldType  
 Je třeba volání `SetFieldType` ve třídě sady záznamů [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) nebo [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) přepsat.  
  
```  
void SetFieldType(UINT nFieldType);
```  
  
### <a name="parameters"></a>Parametry  
 `nFieldType`  
 Hodnota **výčtu typ pole**, deklarované v `CFieldExchange`, který může být jedna z následujících akcí:  
  
- **CFieldExchange::outputColumn**  
  
- **CFieldExchange::inputParam**  
  
- **CFieldExchange::param**  
  
- **CFieldExchange::outputParam**  
  
- **CFieldExchange::inoutParam**  
  
### <a name="remarks"></a>Poznámky  
 Pole datových členů, musí volat `SetFieldType` s parametrem **CFieldExchange::outputColumn**, za nímž následují volání funkcí RFX nebo Bulk RFX. Pokud jste to ještě implementována hromadné načítání řádků, pak ClassWizard umístí to `SetFieldType` volání můžete v části mapy pole `DoFieldExchange`.  
  
 Pokud jste Parametrizace vaší třídy sady záznamů, musí volat `SetFieldType` znovu mimo oddíl žádné pole mapy, následuje volání RFX pro všechny členy parametr data. Každý typ parametru – datový člen musí mít svůj vlastní `SetFieldType` volání. V následující tabulce slouží k rozlišení různé hodnoty, které lze předat `SetFieldType` představují parametry datových členů vaší třídy:  
  
|Hodnota parametru SetFieldType|Typ parametru – datový člen|  
|----------------------------------|-----------------------------------|  
|**CFieldExchange::inputParam**|Vstupní parametr. Hodnota, která je předána do sady záznamů dotazu nebo uložené proceduře.|  
|**CFieldExchange::param**|Stejné jako **CFieldExchange::inputParam**.|  
|**CFieldExchange::outputParam**|Výstupní parametr. Vrácená hodnota sady záznamů uložené procedury.|  
|**CFieldExchange::inoutParam**|Vstupní a výstupní parametr. Hodnota, která je předán do a, kterou vrátil uloženou proceduru sady záznamů.|  
  
 Obecně platí, každou skupinu funkce RFX přidružené pole datových členů nebo parametry datových členů musí předcházet volání `SetFieldType`. `nFieldType` Parametr jednotlivých `SetFieldType` volání jsou uvedeny typy datových členů reprezentována funkce RFX, které následují `SetFieldType` volání.  
  
 Další informace o zpracování výstupní a vstupní a výstupní parametry, najdete v článku `CRecordset` – členská funkce [FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset). Další informace o funkcích RFX a Bulk RFX, naleznete v tématu [funkce výměny polí v záznamu](../../mfc/reference/record-field-exchange-functions.md). Související informace o hromadné načítání řádků, najdete v článku [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje několik volání funkce RFX s doplňujícími volání `SetFieldType`. Všimněte si, že `SetFieldType` nazývá prostřednictvím `pFX` ukazatel na `CFieldExchange` objektu.  
  
 [!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CRecordset – třída](../../mfc/reference/crecordset-class.md)
