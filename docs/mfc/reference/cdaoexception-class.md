---
title: "Třída CDaoException | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoException
- AFXDAO/CDaoException
- AFXDAO/CDaoException::CDaoException
- AFXDAO/CDaoException::GetErrorCount
- AFXDAO/CDaoException::GetErrorInfo
- AFXDAO/CDaoException::m_nAfxDaoError
- AFXDAO/CDaoException::m_pErrorInfo
- AFXDAO/CDaoException::m_scode
dev_langs: C++
helpviewer_keywords:
- CDaoException [MFC], CDaoException
- CDaoException [MFC], GetErrorCount
- CDaoException [MFC], GetErrorInfo
- CDaoException [MFC], m_nAfxDaoError
- CDaoException [MFC], m_pErrorInfo
- CDaoException [MFC], m_scode
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6426588df3f671427874550a62da1f767ecbfd8f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdaoexception-class"></a>CDaoException – třída
Představuje podmínku vzniklých třídami databází MFC podle dat přístup k objektům (DAO).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDaoException : public CException  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDaoException::CDaoException](#cdaoexception)|Vytvoří `CDaoException` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDaoException::GetErrorCount](#geterrorcount)|Vrátí počet chyb v kolekci chybách databázového stroje.|  
|[CDaoException::GetErrorInfo](#geterrorinfo)|Vrátí informace o chybě o konkrétní chybě objektu v kolekci chyby.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|Obsahuje podrobné informace o chybě kód pro všechny chyby v tříd MFC rozhraní DAO.|  
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|Ukazatel [cdaoerrorinfo –](../../mfc/reference/cdaoerrorinfo-structure.md) objekt, který obsahuje informace o jeden objekt DAO chyby.|  
|[CDaoException::m_scode](#m_scode)|[Kód SCODE](#m_scode) hodnotu přidruženou k chybě.|  
  
## <a name="remarks"></a>Poznámky  
 Třída zahrnuje veřejná data členů, které vám pomohou zjistit příčinu výjimky. `CDaoException`objekty jsou vytvořená a vyvolané členské funkce databázové třídy DAO.  
  
> [!NOTE]
>  Databázové třídy DAO se liší od třídami databází MFC založené na připojení ODBC (Open Database). Všechny názvy tříd DAO databáze mít předponu "CDao". Můžete i nadále přístup ke zdrojům dat ODBC s třídy DAO. Obecně platí třídy MFC založené na rozhraní DAO schopné více než třídy MFC založené na rozhraní ODBC; třídy založené na rozhraní DAO přístup k datům, včetně prostřednictvím ovladače ODBC prostřednictvím svých vlastních databázového stroje. Třídy založené na rozhraní DAO také podporují jazyka DDL (Data Definition) operace, jako je například přidávání tabulek prostřednictvím třídy, aniž by museli DAO volat přímo. Informace o výjimky generované třídy rozhraní ODBC, najdete v části [CDBException](../../mfc/reference/cdbexception-class.md).  
  
 Dostanete objekty výjimek v rámci oboru [CATCH](../../mfc/reference/exception-processing.md#catch) výraz. Můžete také vyvolat `CDaoException` objekty z vlastního kódu pomocí [afxthrowdaoexception –](../../mfc/reference/exception-processing.md#afxthrowdaoexception) globální funkce.  
  
 V prostředí MFC, jsou všechny chyby DAO vyjádřené jako výjimky, typu `CDaoException`. Pokud jste zachycení výjimek tohoto typu, můžete použít `CDaoException` členské funkce načíst informace z jakékoli DAO chyba objekty uložené v kolekce chyb databázového stroje. Jako dojde každé chybě, jeden nebo více objektů chyby jsou umístěny do kolekce chyb. (Obvykle kolekce obsahuje pouze jeden objekt chyby, pokud používáte zdroje dat ODBC, se pravděpodobně získat více objektů chyba.) Pokud jiná operace DAO vygeneruje chybu, kolekce chyb není zaškrtnuta, a nový objekt chyby se umístí do kolekce chyb. DAO operace, které nevydávají chybu mít žádný vliv na kolekce chyb.  
  
 Kódy chyb rozhraní DAO naleznete v souboru DAOERR. H. Související informace naleznete v tématu "Zachytitelné chyb přístupu k datům" v nápovědě rozhraní DAO.  
  
 Další informace o zpracování výjimek v obecné nebo o `CDaoException` objekty, najdete v článcích [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md) a [výjimky: výjimky databáze](../../mfc/exceptions-database-exceptions.md). Druhý článek obsahuje ukázkový kód, který ukazuje zpracování výjimek v rozhraní DAO.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CDaoException`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
##  <a name="cdaoexception"></a>CDaoException::CDaoException  
 Vytvoří `CDaoException` objektu.  
  
```  
CDaoException();
```  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework normálně, vytvoří objekty výjimek, když jeho kód, vyvolá výjimku. Je málokdy potřeba explicitně vytvořit objekt výjimky. Pokud chcete throw `CDaoException` z vlastního kódu volání globální funkce [afxthrowdaoexception –](../../mfc/reference/exception-processing.md#afxthrowdaoexception).  
  
 Můžete ale chtít explicitně vytvořit objekt výjimky, pokud provádíte přímé volání DAO prostřednictvím ukazatele rozhraní DAO, které zapouzdřují MFC – třídy. V takovém případě budete muset načíst informace o chybě z rozhraní DAO. Předpokládejme, že dojde k chybě v rozhraní DAO při volání rozhraní DAO metody prostřednictvím rozhraní DAODatabases pracovní prostor databáze kolekce.  
  
##### <a name="to-retrieve-the-dao-error-information"></a>Načíst informace o chybě rozhraní DAO  
  
1.  Vytvořit `CDaoException` objektu.  
  
2.  Volání objekt výjimky [GetErrorCount](#geterrorcount) členské funkce k určení, kolik chyba objekty jsou v kolekci chybách databázového stroje. (Obvykle pouze jeden, pokud nepoužíváte zdroje dat ODBC.)  
  
3.  Volání objekt výjimky [GetErrorInfo –](#geterrorinfo) – členská funkce pro získání jeden objekt konkrétní chyby současně, podle indexu v kolekci, prostřednictvím objekt výjimky. Objekt výjimky si můžete představit jako proxy pro jeden objekt DAO chyby.  
  
4.  Zkontrolujte aktuální [cdaoerrorinfo –](../../mfc/reference/cdaoerrorinfo-structure.md) struktury, která `GetErrorInfo` vrátí [m_pErrorInfo](#m_perrorinfo) – datový člen. Její členy poskytují informace o chybě rozhraní DAO.  
  
5.  V případě zdroje dat ODBC zopakujte kroky 3 a 4 podle potřeby pro další objekty chyby.  
  
6.  Pokud jste sestavený objekt výjimky v haldě, odstraňte jej pomocí **odstranit** operátor po dokončení.  
  
 Další informace o zpracování chyb ve třídách knihovny MFC rozhraní DAO, najdete v článku [výjimky: výjimky databáze](../../mfc/exceptions-database-exceptions.md).  
  
##  <a name="geterrorcount"></a>CDaoException::GetErrorCount  
 Volání této funkce člen načíst počet objektů DAO Chyba v kolekci chybách databázového stroje.  
  
```  
short GetErrorCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet objektů chyba DAO v kolekci chybách databázového stroje.  
  
### <a name="remarks"></a>Poznámky  
 Tyto informace jsou užitečné pro ve smyčce přes kolekce chyb pro načtení každou jeden nebo více rozhraní DAO chyba objektů v kolekci. Chcete-li načíst objekt error pomocí indexu nebo číslo chyby DAO, volejte [GetErrorInfo –](#geterrorinfo) – členská funkce.  
  
> [!NOTE]
>  V kolekci chyby je obvykle pouze jeden objekt chyby. Pokud pracujete s zdroje dat ODBC, však může existovat více než jeden.  
  
##  <a name="geterrorinfo"></a>CDaoException::GetErrorInfo  
 Vrátí informace o chybě o konkrétní chybě objektu v kolekci chyby.  
  
```  
void GetErrorInfo(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index založený na informacích o chybě v kolekce chyb databázového stroje, pro vyhledávání podle indexu.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce člen získat následující druh informací o výjimce:  
  
-   Kód chyby  
  
-   Zdroj  
  
-   Popis  
  
-   Soubor nápovědy  
  
-   Kontextové nápovědy  
  
 `GetErrorInfo`ukládá do objekt výjimky `m_pErrorInfo` – datový člen. Stručný popis vrácené informace najdete v tématu [m_pErrorInfo](#m_perrorinfo). Pokud catch k výjimce typu `CDaoException` vyvolané MFC, `m_pErrorInfo` člen bude již být vyplněna. Pokud zvolíte možnost DAO volat přímo, musí volat objekt výjimky `GetErrorInfo` – členská funkce sami k vyplnění `m_pErrorInfo`. Podrobnější popis najdete v tématu [cdaoerrorinfo –](../../mfc/reference/cdaoerrorinfo-structure.md) struktura.  
  
 Informace o rozhraní DAO výjimky a ukázkový kód, najdete v článku [výjimky: výjimky databáze](../../mfc/exceptions-database-exceptions.md).  
  
##  <a name="m_nafxdaoerror"></a>CDaoException::m_nAfxDaoError  
 Obsahuje knihovny MFC Rozšířený kód chyby.  
  
### <a name="remarks"></a>Poznámky  
 Tento kód je zadána v případech, kde má zmýlila pro konkrétní součást tříd MFC rozhraní DAO.  
  
 Možné hodnoty jsou:  
  
- **NO_AFX_DAO_ERROR** poslední operaci nevedly MFC rozšířená chyba. Ale operaci může je tvořen dalších chyb z rozhraní DAO nebo OLE, takže byste měli zkontrolovat [m_pErrorInfo](#m_perrorinfo) a případně [m_scode](#m_scode).  
  
- **AFX_DAO_ERROR_ENGINE_INITIALIZATION** MFC nelze inicializovat databázový stroj Microsoft Jet. OLE může došlo k chybě při inicializaci, nebo je pravděpodobně bylo možné vytvořit instanci třídy DAO databázový stroj objekt. Tyto problémy obvykle zjistíte chybná instalace DAO nebo OLE.  
  
- **AFX_DAO_ERROR_DFX_BIND** adresa použitá ve volání funkce Výměna pole záznamu exchange (DFX) neexistuje nebo je neplatný (adresu nebyl použit k vytvoření vazby dat). Chybná adresa může mít předán v DFX volání nebo adresu může mít zneplatní mezi operacemi DFX.  
  
- **AFX_DAO_ERROR_OBJECT_NOT_OPEN** jste se pokusili otevřít sadu záznamů na základě querydef nebo tabledef objekt, který nebyl v otevřeném stavu.  
  
##  <a name="m_perrorinfo"></a>CDaoException::m_pErrorInfo  
 Obsahuje odkazy `CDaoErrorInfo` struktura, která poskytuje informace o objektu DAO chyba, která poslední načten voláním [GetErrorInfo –](#geterrorinfo).  
  
### <a name="remarks"></a>Poznámky  
 Tento objekt obsahuje následující informace:  
  
|Cdaoerrorinfo – člen|Informace o|Význam|  
|--------------------------|-----------------|-------------|  
|**m_lErrorCode**|Kód chyby|Kód chyby rozhraní DAO|  
|`m_strSource`|Zdroj|Název objektu nebo aplikace, který původně vytvořil chybu|  
|`m_strDescription`|Popis|Popisný řetězec spojené s chybou|  
|`m_strHelpFile`|Soubor nápovědy|Cesta k souboru nápovědy pro Windows, ve kterém může uživatel získat informace o problému|  
|**m_lHelpContext**|Kontextové nápovědy|ID kontextu pro téma v souboru nápovědy rozhraní DAO|  
  
 Úplné informace o informace obsažené v `CDaoErrorInfo` objektu, najdete v článku [cdaoerrorinfo –](../../mfc/reference/cdaoerrorinfo-structure.md) struktura.  
  
##  <a name="m_scode"></a>CDaoException::m_scode  
 Obsahuje hodnotu typu `SCODE` , který popisuje chybu.  
  
### <a name="remarks"></a>Poznámky  
 Toto je zadání kódu OLE. Je potřeba málokdy tuto hodnotu použijte, protože ve většině případů, je k dispozici v dalších konkrétnější DAO knihovny MFC nebo informace o chybě `CDaoException` datových členů.  
  
 Informace o `SCODE`, podívejte se na téma [struktura z OLE kódy chyb](http://msdn.microsoft.com/library/windows/desktop/ms690088) ve Windows SDK. `SCODE` Datový typ mapuje `HRESULT` datového typu.  
  
## <a name="see-also"></a>Viz také  
 [CException – třída](../../mfc/reference/cexception-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CException – třída](../../mfc/reference/cexception-class.md)
