---
title: "Podpora sad řádků schématu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- schema rowsets
- OLE DB consumer templates, schema rowsets
- OLE DB providers, schema rowsets
- OLE DB, schema rowsets
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d3cd1a75df607678546c53b53df134f45eb87026
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="supporting-schema-rowsets"></a>Podpora sad řádků schématu
Schéma sad řádků umožňují spotřebitelům získat informace o úložišti dat bez znalosti jeho podkladová struktura nebo schéma. Úložiště dat, které může mít například tabulky, které jsou uspořádány do uživatelem definované hierarchie, takže by být žádný způsob, jak zajistit, aby znalosti o schématu s výjimkou jeho čtení. (Například Upozorňujeme, že průvodci Visual C++ použít sady řádků schématu pro generování přístupových objektů pro spotřebitele.) Povolit příjemce k tomu, vystavuje objekt relace poskytovatele metody na [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) rozhraní. V aplikacích Visual C++, můžete použít [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) třídu pro implementaci **IDBSchemaRowset**.  
  
 `IDBSchemaRowsetImpl`podporuje následující metody:  
  
-   [CheckRestrictions –](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md) kontroluje platnost omezení proti sadě řádků schématu.  
  
-   [CreateSchemaRowset –](../../data/oledb/idbschemarowsetimpl-createschemarowset.md) implementuje COM objekt funkci pro daný objekt zadaný parametrem šablony.  
  
-   [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) určuje omezení, které podporují pro sadu řádků schématu konkrétní.  
  
-   [IDBSchemaRowset::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) vrací sadu řádků schématu (zděděno z rozhraní).  
  
-   [GetSchemas –](../../data/oledb/idbschemarowsetimpl-getschemas.md) vrátí seznam sad řádků schématu přístupný `IDBSchemaRowsetImpl::GetRowset` (zděděno z rozhraní).  
  
## <a name="atl-ole-db-provider-wizard-support"></a>Podpora průvodce pro zprostředkovatele ATL OLE DB  
 Průvodce zprostředkovatele OLE DB ATL vytvoří tři třídy schématu v záhlaví souboru relace:  
  
-   **C** *ShortName* **SessionTRSchemaRowset**  
  
-   **C** *ShortName* **SessionColSchemaRowset**  
  
-   **C** *ShortName* **SessionPTSchemaRowset**  
  
 Tyto třídy reagovat na požadavky příjemce pro informace o schématu; Všimněte si, že specifikace OLE DB vyžaduje podporovat tyto tři schéma sad řádků:  
  
-   **C** *ShortName* **SessionTRSchemaRowset** zpracovává požadavky pro informace o tabulce ( `DBSCHEMA_TABLES` sada řádků schématu).  
  
-   **C** *ShortName* **SessionColSchemaRowset** zpracovává požadavky pro informace o sloupcích ( **DBSCHEMA_COLUMNS** sada řádků schématu). Průvodce poskytuje vzorové implementace pro tyto třídy, které vrací informace o schématu pro poskytovatele DOS.  
  
-   **C** *ShortName* **SessionPTSchemaRowset** zpracovává požadavky na schéma informace o typu poskytovatele ( **DBSCHEMA_PROVIDER_TYPES** Sada řádků schématu). Vrátí výchozí implementace zadaným průvodcem `S_OK`.  
  
 Můžete přizpůsobit tyto třídy pro zpracování informací o schématu na základě vašeho poskytovatele:  
  
-   V **C***ShortName***SessionTRSchemaRowset**, musíte vyplnit pole katalog, tabulky a popis (**trData.m_szType**, **trData.m_szTable**, a **trData.m_szDesc**). Příklad generované v Průvodci používá jenom jeden řádek (tabulky). Ostatní poskytovatele může vrátit více než jedna tabulka.  
  
-   V **C***ShortName***SessionColSchemaRowset**, předáte název tabulky jako **DBID**.  
  
## <a name="setting-restrictions"></a>Nastavení omezení  
 Důležitou koncepcí v Podpora sad řádků schématu je nastavení omezení, které provedete pomocí `SetRestrictions`. Omezení umožňují spotřebitelům načítat pouze odpovídající řádky (třeba najít všechny sloupce v tabulce "MyTable"). Omezení jsou volitelné a v případě, ve které žádný není podporována (výchozí), vždycky vrátí se všechna data. Příklad poskytovatele, který nepodporuje omezení, naleznete v části [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) ukázka.  
  
## <a name="setting-up-the-schema-map"></a>Nastavení schématu Map  
 Nastavte mapa schématu, jako je tato v Session.h v UpdatePV:  
  
```  
BEGIN_SCHEMA_MAP(CUpdateSession)  
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)  
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)  
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)  
END_SCHEMA_MAP()  
```  
  
 Pro podporu **IDBSchemaRowset**, musí podporovat `DBSCHEMA_TABLES`, **DBSCHEMA_COLUMNS**, a **DBSCHEMA_PROVIDER_TYPES**. Můžete přidat další sady řádků schématu svého uvážení.  
  
 Deklarování třídy sady řádků schématu s `Execute` metoda jako `CUpdateSessionTRSchemaRowset` v UpdatePV:  
  
```  
class CUpdateSessionTRSchemaRowset :   
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,   
                              CTABLESRow, CUpdateSession >  
...  
// Execute looks like this; what pointers does the consumer use?  
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,   
                    ULONG cRestrictions, const VARIANT* rgRestrictions)  
```  
  
 Všimněte si, že `CUpdateSession` dědí z `IDBSchemaRowsetImpl`, takže má všechny metody zpracování omezení. Pomocí `CSchemaRowsetImpl`, deklarovat tři podřízené třídy (uvedené v mapě schématu výše): `CUpdateSessionTRSchemaRowset`, `CUpdateSessionColSchemaRowset`, a `CUpdateSessionPTSchemaRowset`. Každá z těchto tříd podřízené má `Execute` metoda, která zpracovává jeho odpovídající sadu omezení (kritéria vyhledávání). Každý `Execute` metoda srovnává hodnoty `cRestrictions` a `rgRestrictions` parametry. Popis těchto parametrů v [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md).  
  
 Další informace o tom, které odpovídají omezení konkrétní sadě řádků schématu, naleznete v tabulce GUID sad řádků schématu v [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) v *referenční příručka programátora technologie OLE DB* v Windows SDK.  
  
 Například, pokud je podporována **TABLE_NAME** omezení `DBSCHEMA_TABLES`, by postupujte takto:  
  
 Nejprve vyhledat `DBSCHEMA_TABLES` a zjistěte, zda podporuje čtyři omezení (v pořadí).  
  
|Omezení sady řádků schématu|Hodnota omezení|  
|-------------------------------|-----------------------|  
|**TABLE_CATALOG**|0x1 (binární 1)|  
|**TABLE_SCHEMA**|0x2 (binární 10)|  
|**TABLE_NAME**|0x4 (binární 100)|  
|**TABLE_TYPE**|0x8 (binární 1000)|  
  
 V dalším kroku Všimněte si, že jeden bit pro každý omezení. Vzhledem k tomu, že chcete podporovat **TABLE_NAME** pouze by vrátit 0x4 v `rgRestrictions` elementu. Pokud je podporovaná **TABLE_CATALOG** a **TABLE_NAME**, vrátili byste 0x5 (binární 101).  
  
 Ve výchozím nastavení implementace, vrátí hodnotu 0 (nepodporuje žádné omezení) pro každou žádost. UpdatePV je příkladem zprostředkovatele, který nepodporuje omezení.  
  
### <a name="example"></a>Příklad  
 Tento kód je převzat ze [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) ukázka. UpdatePv podporuje tři požadované schéma sad řádků: `DBSCHEMA_TABLES`, **DBSCHEMA_COLUMNS**, a **DBSCHEMA_PROVIDER_TYPES**. Jako příklad toho, jak implementovat podporu schématu ve zprostředkovateli Toto téma vás provede implementace **DBSCHEMA_TABLE** sady řádků.  
  
> [!NOTE]
>  Ukázkový kód se může lišit od co je uveden zde; měli byste považovat ukázkový kód jako aktuální verze.  
  
 Prvním krokem při přidání podpory schématu je určit omezení, které chcete podporovat. Pokud chcete zjistit, která omezení jsou k dispozici pro vaše sada řádků schématu, podívejte se na specifikace OLE DB pro definici **IDBSchemaRowset**. Následující definici hlavní zobrazí tabulku obsahující název sady řádků schématu, počet omezení a omezení sloupce. Vyberte sadu řádků schématu, které chcete podporovat a poznamenejte si počet omezení a omezení sloupce. Například `DBSCHEMA_TABLES` podporuje čtyři omezení (**TABLE_CATALOG**, **TABLE_SCHEMA**, **TABLE_NAME**, a **TABLE_TYPE** ):  
  
```  
void SetRestrictions(ULONG cRestrictions, GUID* rguidSchema,   
   ULONG* rgRestrictions)  
{  
    for (ULONG l=0; l<cRestrictions; l++)  
    {  
        if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))  
            rgRestrictions[l] = 0x0C;  
        else if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_COLUMNS))  
                 rgRestrictions[l] = 0x04;  
             else if (InlineIsEqualGUID(rguidSchema[l],  
                                        DBSCHEMA_PROVIDER_TYPES))  
                      rgRestrictions[l] = 0x00;  
   }  
}  
```  
  
 Bit představuje každý sloupec omezení. Pokud chcete zajistit podporu omezení (to znamená, můžete dát dotaz tímto), nastavte tento bit na 1. Pokud nechcete pro podporu omezení, nastavte tento bit na nulu. V řádku výše uvedený kód UpdatePV podporuje **TABLE_NAME** a **TABLE_TYPE** omezení `DBSCHEMA_TABLES` sady řádků. Jsou to třetí (bitová maska 100) a čtvrtý omezení (bitová maska 1000). Proto je bitové masky pro UpdatePv 1100 (nebo 0x0C):  
  
```  
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))  
    rgRestrictions[l] = 0x0C;  
```  
  
 Následující `Execute` funkce je podobná těm v pravidelných sady řádků. Máte tři argumenty: `pcRowsAffected`, `cRestrictions`, a `rgRestrictions`. `pcRowsAffected` Proměnné je výstupní parametr, může poskytovatel vrátit počet řádků v sadě řádků schématu. `cRestrictions` Parametr je vstupní parametr, obsahující počet omezení předána zprostředkovateli uživatelem. `rgRestrictions` Parametr je pole **VARIANT** hodnoty, které obsahují hodnoty omezení.  
  
```  
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,   
                const VARIANT* rgRestrictions)  
```  
  
 `cRestrictions` Proměnné je na základě celkového počtu omezení pro sadu řádků schématu, bez ohledu na to, jestli je zprostředkovatel podporuje. Protože UpdatePv podporuje dvě omezení (třetí a čtvrté), tento kód jenom vyhledá `cRestrictions` hodnotu větší než nebo rovnou na tři.  
  
 Hodnota **TABLE_NAME** omezení je uložen v `rgRestrictions[2]` (znovu, třetí omezení v pole s nulovým základem je 2). Je potřeba zkontrolovat, že omezení není `VT_EMPTY` podporu. Všimněte si, že **VT_NULL** se nerovná `VT_EMPTY`. **VT_NULL** Určuje platnou hodnotu omezení.  
  
 Definice UpdatePv název tabulky je plně kvalifikovanou cestu jméno do textového souboru. Rozbalte hodnotu omezení a pak pokus o otevření souboru a ujistěte se, že soubor skutečně existuje. Pokud soubor neexistuje, vrátí `S_OK`. Může se to zdát trochu zpětné ale co kód skutečně sděluje příjemce je, že neexistují žádné podporované tabulky pomocí zadaného názvu. `S_OK` Vrátit znamená, že se kód spustil správně.  
  
```  
USES_CONVERSION;  
enum {  
            sizeOfszFile = 255  
};  
CTABLESRow  trData;  
FILE        *pFile = NULL;  
TCHAR       szFile[ sizeOfszFile ];  
errcode     err = 0;  
  
// Handle any restrictions sent to us. This only handles  
// the TABLE_NAME & TABLE_TYPE restictions (the 3rd and 4th   
// restrictions in DBSCHEMA_TABLES...look in IDBSchemaRowsets   
// in part 2 of the prog. ref) so your restrictions are 0x08 & 0x04   
// for a total of (0x0C)  
if (cRestrictions >= 3 && rgRestrictions[2].vt != VT_EMPTY)  
{  
    CComBSTR bstrName = rgRestrictions[2].bstrVal;  
    if ((rgRestrictions[2].vt == VT_BSTR) && (bstrName != (BSTR)NULL))  
    {  
        // Check to see if the file exists  
        _tcscpy_s(&szFile[0], sizeOfszFile, OLE2T(bstrName));  
        if (szFile[0] == _T('\0') ||   
           ((err = _tfopen(&pFile, &szFile[0], _T("r"))) == 0))  
        {  
            return S_OK;// Their restriction was invalid return no data  
        }  
        else  
        {  
            fclose(pFile);  
        }  
    }  
}  
```  
  
 Podpora čtvrtého omezení (**TABLE_TYPE**) je podobná třetí omezení. Zkontrolujte, zda hodnota není `VT_EMPTY`. Toto omezení pouze vrací typ tabulky **tabulky**. K určení platné hodnoty pro `DBSCHEMA_TABLES`, vyhledejte v dodatku B *referenční příručka programátora technologie OLE DB* v **tabulky** části sady řádků.  
  
```  
// TABLE_TYPE restriction:  
if (cRestrictions >=4 && rgRestrictions[3].vt != VT_EMPTY)  
{  
    CComBSTR bstrType = rgRestrictions[3].bstrVal;  
    if ((rgRestrictions[3].vt == VT_BSTR) && (bstrType != (BSTR)NULL))  
    {  
        // This is kind of a blind restriction.  
        // This only actually supports  
        // TABLES so if you get anything else,   
        // just return an empty rowset.  
        if (_tcscmp(_T("TABLE"), OLE2T(bstrType)) != 0)  
            return S_OK;  
    }  
}  
```  
  
 Toto je ve skutečnosti vytvoříte položku řádku v sadě řádků. Proměnná `trData` odpovídá **CTABLESRow**, struktuře definované v šablony zprostředkovatele technologie OLE DB. **CTABLESRow** odpovídá **tabulky** definice řádků v příloha B specifikace OLE DB. Můžete mít pouze jeden řádek přidat, protože jedna tabulka může podporovat pouze v čase.  
  
```  
// Bring over the data:  
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);  
wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);  
wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());  
```  
  
 UpdatePV nastaví jenom tři sloupce: **TABLE_NAME**, **TABLE_TYPE**, a **popis**. Měli byste si poznamenejte sloupce, pro které vracíte informace, protože tyto informace jsou potřeba při implementaci `GetDBStatus`:  
  
```  
    _ATLTRY  
    {  
        m_rgRowData.Add(trData);  
    }  
    _ATLCATCHALL()  
    {  
        return E_OUTOFMEMORY;  
    }  
    //if (!m_rgRowData.Add(trData))  
    //    return E_OUTOFMEMORY;  
    *pcRowsAffected = 1;  
    return S_OK;  
}  
```  
  
 `GetDBStatus` Funkce je velmi důležité pro správné fungování sady řádků schématu. Protože nevracejí data pro každý sloupec v **tabulky** řádků, je třeba zadat sloupce, které vrací data pro a které ne.  
  
```  
virtual DBSTATUS GetDBStatus(CSimpleRow* , ATLCOLUMNINFO* pColInfo)  
{  
    ATLASSERT(pColInfo != NULL);  
  
    switch(pColInfo->iOrdinal)  
    {  
    case 3:     // TABLE_NAME  
    case 4:     // TABLE_TYPE  
    case 6:     // DESCRIPTION  
        return DBSTATUS_S_OK;  
        break;  
    default:  
        return DBSTATUS_S_ISNULL;  
    break;  
    }  
}  
```  
  
 Protože vaše `Execute` funkce vrací data **TABLE_NAME**, **TABLE_TYPE**, a **popis** pole z **tabulky**řádků, můžete hledat v příloha B specifikace OLE DB a určit (podle počítání shora), že jsou pořadová čísla, 3, 4 a 6. Pro každý z těchto sloupců vrátí **DBSTATUS_S_OK**. U všech ostatních sloupců vrátit **DBSTATUS_S_ISNULL**. Je důležité vrátit tento stav, protože příjemce nemusí pochopit, že hodnota vrátíte je **NULL** nebo něco jiného. Znovu, Všimněte si, že **NULL** není ekvivalentní prázdný.  
  
 Další informace o rozhraní sady řádků schématu OLE DB, najdete v článku [IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md) rozhraní v OLE DB referenční informace pro programátory.  
  
 Informace o tom, jak mohou příjemci použít **IDBSchemaRowset** metody, najdete v části [získávání metadat pomocí sad řádků schématu](../../data/oledb/obtaining-metadata-with-schema-rowsets.md).  
  
 Příklad poskytovatele, který podporuje sady řádků schématu, naleznete v části [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) ukázka.  
  
## <a name="see-also"></a>Viz také  
 [Pokročilé techniky zprostředkování](../../data/oledb/advanced-provider-techniques.md)