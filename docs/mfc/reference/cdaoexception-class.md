---
title: CDaoException – třída
ms.date: 11/04/2016
f1_keywords:
- CDaoException
- AFXDAO/CDaoException
- AFXDAO/CDaoException::CDaoException
- AFXDAO/CDaoException::GetErrorCount
- AFXDAO/CDaoException::GetErrorInfo
- AFXDAO/CDaoException::m_nAfxDaoError
- AFXDAO/CDaoException::m_pErrorInfo
- AFXDAO/CDaoException::m_scode
helpviewer_keywords:
- CDaoException [MFC], CDaoException
- CDaoException [MFC], GetErrorCount
- CDaoException [MFC], GetErrorInfo
- CDaoException [MFC], m_nAfxDaoError
- CDaoException [MFC], m_pErrorInfo
- CDaoException [MFC], m_scode
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
ms.openlocfilehash: e5f28b8896fc9e7e5c6a656a64b938cd7af39f42
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507066"
---
# <a name="cdaoexception-class"></a>CDaoException – třída

Představuje podmínku výjimky vyplývající z databázových tříd knihovny MFC založených na objektech DAO (Data Access Objects).

## <a name="syntax"></a>Syntaxe

```
class CDaoException : public CException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CDaoException::CDaoException](#cdaoexception)|`CDaoException` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CDaoException::GetErrorCount](#geterrorcount)|Vrátí počet chyb v kolekci chyb databázového stroje.|
|[CDaoException::GetErrorInfo](#geterrorinfo)|Vrátí informace o chybě týkající se konkrétního objektu chyby v kolekci Errors.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|Obsahuje rozšířený chybový kód pro jakoukoli chybu v třídách knihovny MFC rozhraní DAO.|
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|Ukazatel na objekt [CDaoErrorInfo –](../../mfc/reference/cdaoerrorinfo-structure.md) , který obsahuje informace o jednom objektu Error objektu DAO.|
|[CDaoException::m_scode](#m_scode)|Hodnota [Code](#m_scode) přidružená k chybě.|

## <a name="remarks"></a>Poznámky

Třída obsahuje veřejné datové členy, které lze použít k určení příčiny výjimky. `CDaoException`objekty jsou vytvářeny a vyvolány členskými funkcemi třídy databáze DAO.

> [!NOTE]
>  Databázové třídy DAO se liší od databázových tříd knihovny MFC založených na rozhraní ODBC (Open Database Connectivity). Všechny názvy databázových tříd DAO mají předponu "CDao". Ke zdrojům dat rozhraní ODBC můžete přistupovat i s třídami DAO. Obecně jsou třídy knihovny MFC založené na rozhraní DAO větší, než třídy knihovny MFC založené na rozhraní ODBC; třídy založené na rozhraní DAO mají přístup k datům, včetně přes ovladače rozhraní ODBC, prostřednictvím vlastního databázového stroje. Třídy založené na rozhraní DAO také podporují operace DDL (Data Definition Language), jako je například přidávání tabulek přes třídy, aniž by bylo nutné volat rozhraní DAO přímo. Informace o výjimkách vyvolaných třídami rozhraní ODBC naleznete v tématu [CDBException](../../mfc/reference/cdbexception-class.md).

Můžete přistupovat k objektům výjimek v rámci rozsahu výrazu [catch](../../mfc/reference/exception-processing.md#catch) . Můžete také vyvolat `CDaoException` objekty z vlastního kódu s globální funkcí [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception) .

V knihovně MFC jsou všechny chyby rozhraní DAO vyjádřeny jako výjimky typu `CDaoException`. Při zachycení výjimky tohoto typu lze pomocí `CDaoException` členských funkcí načíst informace ze všech objektů s chybou DAO uložených v kolekci chyb databázového stroje. Při výskytu každé chyby jsou některé objekty chyb umístěny v kolekci Errors. (Obvykle kolekce obsahuje pouze jeden objekt chyby. Pokud používáte zdroj dat ODBC, je pravděpodobnější, že získáte více objektů chyby.) Když jiná operace rozhraní DAO vygeneruje chybu, kolekce chyb je vymazána a nový objekt Error je umístěn v kolekci Errors. Operace DAO, které negenerují chybu, nemají žádný vliv na kolekci Errors.

Kódy chyb DAO najdete v souboru DAOERR. Y. Související informace najdete v nápovědě k rozhraní DAO v tématu "chyby při přístupu k datům v tomto případě".

Další informace o zpracování výjimek v obecné nebo o `CDaoException` objektech naleznete v článcích [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md) a [výjimky: Výjimky](../../mfc/exceptions-database-exceptions.md)databáze. Druhý článek obsahuje příklad kódu, který ilustruje zpracování výjimek v rozhraní DAO.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CException –](../../mfc/reference/cexception-class.md)

`CDaoException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

##  <a name="cdaoexception"></a>CDaoException::CDaoException

`CDaoException` Vytvoří objekt.

```
CDaoException();
```

### <a name="remarks"></a>Poznámky

Rozhraní obvykle vytvoří objekty výjimek, když kód vyvolá výjimku. Není zřídka nutné vytvořit objekt výjimky explicitně. Pokud chcete vyvolat `CDaoException` z vlastního kódu, zavolejte globální funkci [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception).

Nicméně můžete chtít explicitně vytvořit objekt výjimky, pokud provádíte Přímá volání rozhraní DAO prostřednictvím ukazatelů rozhraní DAO, které třídy MFC zapouzdřují. V takovém případě může být nutné načíst informace o chybě z rozhraní DAO. Předpokládejme, že v rozhraní DAO dojde k chybě při volání metody DAO prostřednictvím rozhraní DAODatabases do kolekce databází v pracovním prostoru.

##### <a name="to-retrieve-the-dao-error-information"></a>Načtení informací o chybě DAO

1. Sestavte `CDaoException` objekt.

1. Voláním členské funkce [GetErrorCount](#geterrorcount) objektu výjimky určíte, kolik objektů chyby je v kolekci chyb databázového stroje. (Obvykle pouze jeden, pokud nepoužíváte zdroj dat ODBC.)

1. Volání členské funkce GetErrorInfo [](#geterrorinfo) objektu výjimky pro načtení jednoho konkrétního objektu chyby v čase, index v kolekci, prostřednictvím objektu výjimky. Objekt výjimky si popřemýšlejte jako proxy pro jeden objekt Error objektu DAO.

1. Prověřte aktuální strukturu [CDaoErrorInfo –](../../mfc/reference/cdaoerrorinfo-structure.md) , `GetErrorInfo` která se vrací v datovém členu [m_pErrorInfo](#m_perrorinfo) . Jeho členové poskytují informace o chybě rozhraní DAO.

1. V případě zdroje dat ODBC opakujte podle potřeby kroky 3 a 4 pro objekty s dalšími chybami.

1. Pokud jste objekt výjimky vyvolali v haldě, odstraňte jej pomocí operátoru **Delete** po dokončení.

Další informace o zpracování chyb v třídách knihovny MFC rozhraní DAO naleznete v článku [výjimky: Výjimky](../../mfc/exceptions-database-exceptions.md)databáze.

##  <a name="geterrorcount"></a>CDaoException::GetErrorCount

Zavolejte tuto členskou funkci pro načtení počtu objektů chyb DAO v kolekci chyb databázového stroje.

```
short GetErrorCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet objektů chyb DAO v kolekci chyb databázového stroje.

### <a name="remarks"></a>Poznámky

Tyto informace jsou užitečné k tomu, aby se v kolekci chyb přečetly všechny objekty chyb DAO v kolekci. Chcete-li načíst chybový objekt podle indexu nebo čísla chyby DAO, zavolejte členskou [](#geterrorinfo) funkci GetErrorInfo.

> [!NOTE]
>  V kolekci chyb obvykle existuje pouze jeden objekt Error. Pokud pracujete se zdrojem dat ODBC, může se jednat o více než jeden.

##  <a name="geterrorinfo"></a>CDaoException:: GetErrorInfo

Vrátí informace o chybě týkající se konkrétního objektu chyby v kolekci Errors.

```
void GetErrorInfo(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index informací o chybě v kolekci chyb databázového stroje pro vyhledávání podle indexu.

### <a name="remarks"></a>Poznámky

Zavolejte tuto členskou funkci pro získání následujících typů informací o výjimce:

- Kód chyby

- Source

- Popis

- Soubor Help

- Kontext kontextové nápovědě

`GetErrorInfo`ukládá informace v `m_pErrorInfo` datovém členu objektu výjimky. Stručný popis vrácených informací naleznete v tématu [m_pErrorInfo](#m_perrorinfo). Pokud zachytíte výjimku typu `CDaoException` vyvolanou knihovnou MFC `m_pErrorInfo` , člen již bude vyplněn. Pokud se rozhodnete volat rozhraní DAO přímo, je nutné zavolat `GetErrorInfo` členskou funkci objektu Exception sami k vyplnění. `m_pErrorInfo` Podrobnější popis najdete ve struktuře [CDaoErrorInfo –](../../mfc/reference/cdaoerrorinfo-structure.md) .

Informace o výjimkách rozhraní DAO a příklady kódu naleznete v článku [výjimky: Výjimky](../../mfc/exceptions-database-exceptions.md)databáze.

##  <a name="m_nafxdaoerror"></a>  CDaoException::m_nAfxDaoError

Obsahuje rozšířený kód chyby MFC.

### <a name="remarks"></a>Poznámky

Tento kód je dodán v případech, kde má erred konkrétní součást tříd knihovny MFC rozhraní DAO.

Možné hodnoty jsou:

- NO_AFX_DAO_ERROR poslední operace nevedla k rozšířené chybě MFC. Tato operace ale mohla z rozhraní DAO nebo OLE vyprodukovat jiné chyby, takže byste měli ověřit [m_pErrorInfo](#m_perrorinfo) a případně [m_scode](#m_scode).

- AFX_DAO_ERROR_ENGINE_INITIALIZATION MFC nemohl inicializovat databázový stroj Microsoft Jet. Inicializace OLE se pravděpodobně nezdařila, nebo nebylo možné vytvořit instanci objektu databázového stroje DAO. Tyto problémy obvykle naznačují špatnou instalaci rozhraní DAO nebo OLE.

- AFX_DAO_ERROR_DFX_BIND adresa, která se používá ve volání funkce pro výměnu pole záznamu DAO (DFX), neexistuje nebo je neplatná (adresa nebyla použita pro svázání dat). Je možné, že jste ve volání DFX prošli chybnou adresu, nebo je možné, že se tato adresa v rámci operací DFX nezdařila.

- AFX_DAO_ERROR_OBJECT_NOT_OPEN jste se pokusili otevřít sadu záznamů založenou na objektu querydef nebo objektu tabledef, který není v otevřeném stavu.

##  <a name="m_perrorinfo"></a>  CDaoException::m_pErrorInfo

Obsahuje ukazatel na `CDaoErrorInfo` strukturu, která poskytuje informace o objektu chyby DAO, který jste naposledy načetli voláním metody GetErrorInfo. [](#geterrorinfo)

### <a name="remarks"></a>Poznámky

Tento objekt obsahuje následující informace:

|Člen CDaoErrorInfo –|Informace o|Význam|
|--------------------------|-----------------|-------------|
|`m_lErrorCode`|Kód chyby|Kód chyby rozhraní DAO|
|`m_strSource`|Source|Název objektu nebo aplikace, které původně vygenerovaly chybu|
|`m_strDescription`|Popis|Popisný řetězec přidružený k chybě|
|`m_strHelpFile`|Soubor Help|Cesta k souboru Nápověda systému Windows, ve kterém může uživatel získat informace o problému|
|`m_lHelpContext`|Kontext kontextové nápovědě|ID kontextu pro téma v souboru nápovědy pro rozhraní DAO|

Úplné podrobnosti o informacích obsažených v `CDaoErrorInfo` objektu naleznete v tématu struktura [CDaoErrorInfo –](../../mfc/reference/cdaoerrorinfo-structure.md) .

##  <a name="m_scode"></a>  CDaoException::m_scode

Obsahuje hodnotu typu `SCODE` , která popisuje chybu.

### <a name="remarks"></a>Poznámky

Toto je kód OLE. Tuto hodnotu nebudete používat zřídka, protože v téměř všech případech jsou k dispozici konkrétnější informace o chybě MFC nebo DAO v ostatních `CDaoException` datových členech.

Informace o Code naleznete v tématu [Struktura kódů chyb OLE](/windows/win32/com/structure-of-com-error-codes) v Windows SDK. Datový typ Code se mapuje na datový typ HRESULT.

## <a name="see-also"></a>Viz také:

[CException – třída](../../mfc/reference/cexception-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CException – třída](../../mfc/reference/cexception-class.md)
