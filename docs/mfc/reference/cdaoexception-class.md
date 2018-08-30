---
title: Cdaoexception – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
helpviewer_keywords:
- CDaoException [MFC], CDaoException
- CDaoException [MFC], GetErrorCount
- CDaoException [MFC], GetErrorInfo
- CDaoException [MFC], m_nAfxDaoError
- CDaoException [MFC], m_pErrorInfo
- CDaoException [MFC], m_scode
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 15719f93fbcfde8e6684373f99c924132af9d288
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215437"
---
# <a name="cdaoexception-class"></a>Cdaoexception – třída
Představuje podmínku výjimky vyplývající z databázových tříd MFC založených na datový přístup k objektům (DAO).  
  
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
|[CDaoException::GetErrorCount](#geterrorcount)|Vrátí počet chyb do kolekce chyb databázový stroj.|  
|[CDaoException::GetErrorInfo](#geterrorinfo)|Vrátí informace o chybě o určité chybové objektu do kolekce chyb.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|Obsahuje rozšířený kód chyby pro všechny chyby v tříd DAO knihovny MFC.|  
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|Ukazatel [cdaoerrorinfo –](../../mfc/reference/cdaoerrorinfo-structure.md) objekt, který obsahuje informace o jeden objekt DAO chyby.|  
|[CDaoException::m_scode](#m_scode)|[SCODE](#m_scode) hodnotu přidruženou k chybě.|  
  
## <a name="remarks"></a>Poznámky  
 Třída zahrnuje veřejné datové členy, která vám pomůže určit příčinu chyby. `CDaoException` objekty jsou vytvořena a vyvolána členským funkcím databázové třídy DAO.  
  
> [!NOTE]
>  Databázové třídy DAO se liší od databázových tříd MFC založených na připojení ODBC (Open Database). Všechny názvy tříd DAO databáze mají předponu "CDao". Je možné i nadále přístup ke zdrojům dat ODBC s tříd DAO. Obecně třídy knihovny MFC rozhraní DAO podle podporují více než třídy knihovny MFC založená na rozhraní ODBC; třídy založené na rozhraní DAO můžou přistupovat k datům, včetně prostřednictvím ovladače rozhraní ODBC, prostřednictvím vlastní databázového stroje. Třídy založené na rozhraní DAO také podporu jazyka DDL (Data Definition) operace, jako je například přidávání tabulek prostřednictvím třídy rozhraní, aniž byste museli DAO volat přímo. Informace o výjimkách vygenerovaných ODBC – třídy naleznete v tématu [CDBException](../../mfc/reference/cdbexception-class.md).  
  
 Můžete přistupovat objektech výjimek v rámci oboru [CATCH](../../mfc/reference/exception-processing.md#catch) výrazu. Můžete také vyvolat `CDaoException` objekty z vlastního kódu s využitím [afxthrowdaoexception –](../../mfc/reference/exception-processing.md#afxthrowdaoexception) globální funkce.  
  
 V knihovně MFC, jsou všechny chyby DAO vyjádřený jako výjimky typu `CDaoException`. Pokud při zachycení výjimky tohoto typu, můžete použít `CDaoException` členské funkce k načtení informací z jakékoli rozhraní DAO chyba objektů uložených v modulu databáze kolekce chyb. Jak dojde k každé chybě, jeden nebo více objektů chyby jsou umístěny do kolekce chyb. (Obvykle kolekce obsahuje pouze jeden objekt error, pokud používáte zdroji dat rozhraní ODBC, jste pravděpodobněji získáte více objektů chyba) Pokud jiná operace DAO vygeneruje chybu, se vymaže kolekci chyby a nový objekt chyby se umístí do kolekce chyb. Operace rozhraní DAO, které nejsou generovány chybu nemají žádný vliv na kolekce chyb.  
  
 DAO – kódy chyb naleznete v souboru DAOERR. H. Související informace naleznete v tématu "Zachytitelné chyb přístupu k datům" v nápovědě k DAO.  
  
 Další informace o zpracování výjimek v obecné, nebo o `CDaoException` objekty, najdete v článcích [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md) a [výjimky: výjimky databáze](../../mfc/exceptions-database-exceptions.md). Druhý článek obsahuje ukázkový kód, který znázorňuje zpracování výjimek v rozhraní DAO.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cexception –](../../mfc/reference/cexception-class.md)  
  
 `CDaoException`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
##  <a name="cdaoexception"></a>  CDaoException::CDaoException  
 Vytvoří `CDaoException` objektu.  
  
```  
CDaoException();
```  
  
### <a name="remarks"></a>Poznámky  
 Obvykle rozhraní vytvoří objekty výjimka při jeho kód vyvolá výjimku. Potřebujete jen zřídka explicitně vytvořit objekt výjimky. Pokud chcete vyvolat `CDaoException` z vlastního kódu, zavolejte funkci globální [afxthrowdaoexception –](../../mfc/reference/exception-processing.md#afxthrowdaoexception).  
  
 Můžete však explicitně vytvořit objekt výjimky, pokud provádíte přímá volání rozhraní DAO prostřednictvím ukazatele rozhraní DAO, které zapouzdřují třídy knihovny MFC. V takovém případě můžete potřebovat načíst informace o chybě z rozhraní DAO. Předpokládejme, že dojde k chybě v rozhraní DAO při volání metody rozhraní DAO prostřednictvím rozhraní DAODatabases pracovní prostor databáze kolekce.  
  
##### <a name="to-retrieve-the-dao-error-information"></a>Načíst informace o chybě rozhraní DAO  
  
1.  Vytvoření `CDaoException` objektu.  
  
2.  Volání objektu výjimky [GetErrorCount](#geterrorcount) členskou funkci k určení, kolik chyb objekty jsou do kolekce chyb databázový stroj. (Obvykle pouze jeden, pokud nepoužíváte zdroje dat ODBC.)  
  
3.  Volání objektu výjimky [GetErrorInfo –](#geterrorinfo) členské funkce lze získat jeden objekt konkrétní chyba najednou, podle indexu v kolekci, prostřednictvím objektu výjimky. Objekt výjimky můžete představit jako proxy pro jeden objekt DAO chyby.  
  
4.  Zkontrolujte aktuální [cdaoerrorinfo –](../../mfc/reference/cdaoerrorinfo-structure.md) struktury, která `GetErrorInfo` vrátí [m_pErrorInfo](#m_perrorinfo) datový člen. Jeho členy poskytují informace o chybě rozhraní DAO.  
  
5.  V případě zdroji dat rozhraní ODBC zopakujte kroky 3 a 4 podle potřeby pro více objektů chyby.  
  
6.  Pokud je vytvořen objekt výjimky v haldě, odstraňte ho pomocí **odstranit** operátor po dokončení.  
  
 Další informace o zpracování chyb v třídách knihovny MFC rozhraní DAO, najdete v článku [výjimky: výjimky databáze](../../mfc/exceptions-database-exceptions.md).  
  
##  <a name="geterrorcount"></a>  CDaoException::GetErrorCount  
 Voláním této členské funkce se načíst počet objektů DAO Chyba v kolekci chyby databázový stroj.  
  
```  
short GetErrorCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet objektů DAO Chyba v kolekci chyby databázový stroj.  
  
### <a name="remarks"></a>Poznámky  
 Tyto informace jsou užitečné pro opakování ve smyčce přes kolekce chyb pro načtení všech jeden nebo více rozhraní DAO chyba objektů v kolekci. Chcete-li načíst objekt error, index nebo podle čísla chyby rozhraní DAO, zavolejte [GetErrorInfo –](#geterrorinfo) členskou funkci.  
  
> [!NOTE]
>  V kolekci chyby je obvykle pouze jeden objekt error. Při práci se zdroji dat rozhraní ODBC, však může existovat více než jeden.  
  
##  <a name="geterrorinfo"></a>  CDaoException::GetErrorInfo  
 Vrátí informace o chybě o určité chybové objektu do kolekce chyb.  
  
```  
void GetErrorInfo(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Index s informacemi o chybě v kolekci chyby databázový stroj, pro vyhledávání podle indexu.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této členské funkce získat následující druh informací o výjimce:  
  
-   Kód chyby:  
  
-   Zdroj  
  
-   Popis  
  
-   Soubor nápovědy  
  
-   Kontextové nápovědy  
  
 `GetErrorInfo` ukládá informace v objektu výjimky `m_pErrorInfo` datový člen. Stručný popis informací, najdete v tématu [m_pErrorInfo](#m_perrorinfo). Při zachycení výjimky typu `CDaoException` vyvolané knihovny MFC, `m_pErrorInfo` člen už bude vyplněno. Pokud budete chtít přímo volat rozhraní DAO, musí volat objekt výjimky `GetErrorInfo` členskou funkci sami tak, aby vyplnil `m_pErrorInfo`. Podrobnější popis najdete v tématu [cdaoerrorinfo –](../../mfc/reference/cdaoerrorinfo-structure.md) struktury.  
  
 Informace o výjimkách rozhraní DAO a ukázkový kód, naleznete v článku [výjimky: výjimky databáze](../../mfc/exceptions-database-exceptions.md).  
  
##  <a name="m_nafxdaoerror"></a>  CDaoException::m_nAfxDaoError  
 Obsahuje knihovny MFC rozšířené kód chyby.  
  
### <a name="remarks"></a>Poznámky  
 Tento kód je zadána v případech, kdy má zmýlila konkrétní součást tříd DAO knihovny MFC.  
  
 Možné hodnoty jsou:  
  
- NO_AFX_DAO_ERROR, které poslední operaci nezpůsobil ztrátu v MFC rozšířená chyba. Ale operace může je tvořen jiné chyby z rozhraní DAO nebo OLE, takže byste měli počítač zkontrolovat [m_pErrorInfo](#m_perrorinfo) a případně [m_scode](#m_scode).  
  
- AFX_DAO_ERROR_ENGINE_INITIALIZATION MFC nebylo možné inicializovat databázový stroj Microsoft Jet. OLE – může se nepodařilo inicializovat nebo mohlo být možné vytvořit instanci databázového stroje objektu rozhraní DAO. Tyto problémy obvykle naznačují chybný instalace DAO nebo OLE.  
  
- AFX_DAO_ERROR_DFX_BIND adresu použít ve volání funkce exchange (DFX) DAO pole záznamu neexistuje nebo je neplatný (adresu nebyl použit k vytvoření vazby dat). Chybná adresa může být uplynulo ve volání DFX nebo adresa může být staly neplatnými mezi operacemi DFX.  
  
- AFX_DAO_ERROR_OBJECT_NOT_OPEN jste se pokusili otevřít sadu záznamů na základě querydef nebo tabledef objekt, který není v otevřeném stavu.  
  
##  <a name="m_perrorinfo"></a>  CDaoException::m_pErrorInfo  
 Obsahuje ukazatel `CDaoErrorInfo` struktura, která poskytuje informace o objektu Chyba rozhraní DAO, který naposledy načten voláním [GetErrorInfo –](#geterrorinfo).  
  
### <a name="remarks"></a>Poznámky  
 Tento objekt obsahuje následující informace:  
  
|Cdaoerrorinfo – člen|Informace o|Význam|  
|--------------------------|-----------------|-------------|  
|`m_lErrorCode`|Kód chyby|Kód chyby rozhraní DAO|  
|`m_strSource`|Zdroj|Název objektu nebo aplikaci, která původně vytvořil chybu|  
|`m_strDescription`|Popis|Popisný řetězec přidružený k chybě|  
|`m_strHelpFile`|Soubor nápovědy|Cesta k souboru nápovědy Windows ve kterém může uživatel získat informace o tomto problému|  
|`m_lHelpContext`|Kontextové nápovědy|ID kontextu pro téma v souboru nápovědy k rozhraní DAO|  
  
 Úplné podrobnosti o informace obsažené v `CDaoErrorInfo` objektu, najdete v článku [cdaoerrorinfo –](../../mfc/reference/cdaoerrorinfo-structure.md) struktury.  
  
##  <a name="m_scode"></a>  CDaoException::m_scode  
 Obsahuje hodnotu typu `SCODE` popisující chybu.  
  
### <a name="remarks"></a>Poznámky  
 Toto je kód OLE. Je potřeba zřídka použít tuto hodnotu, protože v téměř všech případech je k dispozici v jiném konkrétnější informace o chybě rozhraní DAO knihovny MFC nebo `CDaoException` datové členy.  
  
 Informace o SCODE, naleznete v tématu [struktury z OLE kódy chyb](/windows/desktop/com/structure-of-com-error-codes) v sadě Windows SDK. Datový typ SCODE mapuje na datový typ HRESULT.  
  
## <a name="see-also"></a>Viz také  
 [Cexception – třída](../../mfc/reference/cexception-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CException – třída](../../mfc/reference/cexception-class.md)
