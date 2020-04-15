---
title: CDaoException – třída
ms.date: 09/17/2019
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
ms.openlocfilehash: a8a789f4dba06ffe376d8a8e955b026bb23af924
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369001"
---
# <a name="cdaoexception-class"></a>CDaoException – třída

Představuje podmínku výjimky vyplývající z tříd databáze knihovny MFC na základě objektů přístupu k datům (DAO). DAO 3.6 je konečná verze, a to je považováno za zastaralé.

## <a name="syntax"></a>Syntaxe

```
class CDaoException : public CException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[Výjimka CDao::Výjimka CDao](#cdaoexception)|Vytvoří `CDaoException` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Výjimka CDao::GetErrorCount](#geterrorcount)|Vrátí počet chyb v kolekci chyb databázového stroje.|
|[Výjimka CDao::GetErrorInfo](#geterrorinfo)|Vrátí informace o chybě o konkrétní objekt chyby v errors kolekce.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CDaoException::m_nAfxDaoError](#m_nafxdaoerror)|Obsahuje rozšířený kód chyby pro všechny chyby ve třídách Knihovny MFC DAO.|
|[CDaoVýjimka::m_pErrorInfo](#m_perrorinfo)|Ukazatel na objekt [CDaoErrorInfo,](../../mfc/reference/cdaoerrorinfo-structure.md) který obsahuje informace o jednom objektu chyby DAO.|
|[CDaoException::m_scode](#m_scode)|Hodnota [SCODE](#m_scode) přidružená k chybě.|

## <a name="remarks"></a>Poznámky

Třída obsahuje členy veřejných dat, které můžete použít k určení příčiny výjimky. `CDaoException`objekty jsou konstruovány a vyvolány členské funkce tříd databáze DAO.

> [!NOTE]
> Třídy databáze DAO se liší od tříd y databáze knihovny MFC na základě připojení k otevřené databázi (ODBC). Všechny názvy tříd databáze DAO mají předponu "CDao". Stále můžete přistupovat ke zdrojům dat ODBC pomocí tříd DAO. Obecně platí, že třídy Knihovny MFC založené na DAO jsou schopnější než třídy Knihovny MFC založené na rozhraní ODBC; třídy založené na DAO mohou přistupovat k datům, a to i prostřednictvím ovladačů ODBC, prostřednictvím vlastního databázového stroje. Třídy založené na DAO také podporují operace jazyka definice dat (DDL), jako je například přidávání tabulek prostřednictvím tříd, aniž by bylo třeba volat DAO přímo. Informace o výjimkách vyzvacích třídami ODBC naleznete v [tématu CDBException](../../mfc/reference/cdbexception-class.md).

Můžete přistupovat k objektům výjimek v rámci výrazu [CATCH.](../../mfc/reference/exception-processing.md#catch) Můžete také `CDaoException` vyvolat objekty z vlastního kódu s globální funkcí [AfxThrowDaoException.](../../mfc/reference/exception-processing.md#afxthrowdaoexception)

V knihovně MFC jsou všechny chyby DAO `CDaoException`vyjádřeny jako výjimky typu . Při zachycení výjimku tohoto typu, `CDaoException` můžete použít členské funkce k načtení informací z libovolné hod objekty chyb YAO uložené v kolekci chyb databázového stroje. Jako každá chyba dochází, jeden nebo více objektů chyby jsou umístěny v Errors kolekce. (Za normálních okolností kolekce obsahuje pouze jeden objekt chyby; pokud používáte zdroj dat ODBC, je pravděpodobnější, že získáte více objektů chyb.) Když jiná operace DAO generuje chybu, errors kolekce je vymazána a nový objekt chyby je umístěn v Errors kolekce. Operace DAO, které negenerují chybu, nemají žádný vliv na kolekci Errors.

Kódy chyb DAO naleznete v souboru DAOERR. H. Související informace naleznete v tématu "Zachytitelné chyby přístupu k datům" v nápovědě dao.

Další informace o zpracování výjimek `CDaoException` obecně nebo o objektech naleznete v článcích [Zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md) a [Výjimky: Výjimky databáze](../../mfc/exceptions-database-exceptions.md). Druhý článek obsahuje ukázkový kód, který ilustruje zpracování výjimek v DAO.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDaoException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao.h

## <a name="cdaoexceptioncdaoexception"></a><a name="cdaoexception"></a>Výjimka CDao::Výjimka CDao

Vytvoří `CDaoException` objekt.

```
CDaoException();
```

### <a name="remarks"></a>Poznámky

Obvykle rozhraní vytvoří objekty výjimek, když jeho kód vyvolá výjimku. Zřídka potřebujete explicitně vytvořit objekt výjimky. Pokud chcete vyvolat `CDaoException` z vlastního kódu, volejte globální funkce [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception).

Můžete však explicitně vytvořit objekt výjimky, pokud provádíte přímé volání DAO prostřednictvím ukazatelů rozhraní DAO, které jsou zapouzdřeny třídy knihovny MFC. V takovém případě může být nutné načíst informace o chybě z DAO. Předpokládejme, že dojde k chybě v DAO při volání metody DAO prostřednictvím rozhraní DAODatabases do kolekce databáze pracovního prostoru.

##### <a name="to-retrieve-the-dao-error-information"></a>Načtení informací o chybě DAO

1. Vytvořte `CDaoException` objekt.

1. Volání objektu výjimky [GetErrorCount](#geterrorcount) členské funkce k určení, kolik chybové objekty jsou v databázovém stroji Errors kolekce. (Obvykle pouze jeden, pokud nepoužíváte zdroj dat ODBC.)

1. Volání objektu výjimky [GetErrorInfo](#geterrorinfo) členské funkce načíst jeden konkrétní objekt chyby najednou, podle indexu v kolekci, prostřednictvím objektu výjimky. Představte si objekt výjimky jako proxy pro jeden objekt chyby DAO.

1. Zkontrolujte aktuální strukturu [CDaoErrorInfo,](../../mfc/reference/cdaoerrorinfo-structure.md) která `GetErrorInfo` se vrací v [m_pErrorInfo](#m_perrorinfo) datovém členu. Její členové poskytují informace o chybě DAO.

1. V případě zdroje dat ODBC opakujte kroky 3 a 4 podle potřeby pro další objekty chyb.

1. Pokud jste vytvořili objekt výjimky na haldě, odstraňte jej s operátorem **delete** po dokončení.

Další informace o zpracování chyb ve třídách Knihovny MFC DAO naleznete v článku [Výjimky: Výjimky databáze](../../mfc/exceptions-database-exceptions.md).

## <a name="cdaoexceptiongeterrorcount"></a><a name="geterrorcount"></a>Výjimka CDao::GetErrorCount

Volání této členské funkce načíst počet objektů chybDAO v kolekci chyb databázového stroje.

```
short GetErrorCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet objektů chyb YAO v kolekci chyb databázového stroje.

### <a name="remarks"></a>Poznámky

Tyto informace jsou užitečné pro opakování prostřednictvím Errors kolekce načíst každý z jednoho nebo více objektů chybY DAO v kolekci. Chcete-li načíst objekt chyby podle indexu nebo čísla chyby DAO, zavolejte člennou funkci [GetErrorInfo.](#geterrorinfo)

> [!NOTE]
> Za normálních okolností je pouze jeden objekt chyby v Errors kolekce. Pokud však pracujete se zdrojem dat ODBC, může existovat více než jeden.

## <a name="cdaoexceptiongeterrorinfo"></a><a name="geterrorinfo"></a>Výjimka CDao::GetErrorInfo

Vrátí informace o chybě o konkrétní objekt chyby v errors kolekce.

```
void GetErrorInfo(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index informací o chybě v kolekci chyb databázového stroje pro vyhledávání podle indexu.

### <a name="remarks"></a>Poznámky

Volání této členské funkce získat následující druhy informací o výjimce:

- Kód chyby

- Zdroj

- Popis

- Soubor nápovědy

- Kontext nápovědy

`GetErrorInfo`ukládá informace v datovém `m_pErrorInfo` členu objektu výjimky. Stručný popis vrácených informací naleznete [v m_pErrorInfo](#m_perrorinfo). Pokud zachytíte výjimku typu `CDaoException` vyzdviženého knihovnou MFC, `m_pErrorInfo` člen již bude vyplněn. Pokud se rozhodnete volat DAO přímo, musíte volat `GetErrorInfo` členské funkce `m_pErrorInfo`objektu výjimky sami vyplnit . Podrobnější popis naleznete ve struktuře [CDaoErrorInfo.](../../mfc/reference/cdaoerrorinfo-structure.md)

Informace o výjimkách DAO a ukázkový kód naleznete v článku [Výjimky: Výjimky databáze](../../mfc/exceptions-database-exceptions.md).

## <a name="cdaoexceptionm_nafxdaoerror"></a><a name="m_nafxdaoerror"></a>CDaoException::m_nAfxDaoError

Obsahuje rozšířený kód chyby knihovny MFC.

### <a name="remarks"></a>Poznámky

Tento kód je dodáván v případech, kdy konkrétní součást tříd y MFC DAO chybně.

Možné hodnoty:

- NO_AFX_DAO_ERROR Poslední operace nevedla k rozšířené chybě knihovny MFC. Operace však mohla způsobit další chyby z DAO nebo OLE, takže byste měli zkontrolovat [m_pErrorInfo](#m_perrorinfo) a případně [m_scode](#m_scode).

- AFX_DAO_ERROR_ENGINE_INITIALIZATION knihovny MFC nelze inicializovat databázový stroj Microsoft Jet. Ole se pravděpodobně nepodařilo inicializovat nebo bylo možné vytvořit instanci objektu databázového stroje DAO. Tyto problémy obvykle naznačují chybnou instalaci dao nebo ole.

- AFX_DAO_ERROR_DFX_BIND Adresa použitá ve volání funkce dao záznamového pole (DFX) neexistuje nebo je neplatná (adresa nebyla použita k vázání dat). Je možné, že jste při volání DFX předali chybnou adresu nebo se adresa stala neplatnou mezi operacemi DFX.

- AFX_DAO_ERROR_OBJECT_NOT_OPEN Pokusili jste se otevřít sadu záznamů na základě querydef nebo tabledef objektu, který nebyl v otevřeném stavu.

## <a name="cdaoexceptionm_perrorinfo"></a><a name="m_perrorinfo"></a>CDaoVýjimka::m_pErrorInfo

Obsahuje ukazatel na `CDaoErrorInfo` strukturu, která poskytuje informace o objektu chyby DAO, který jste naposledy načetli voláním [GetErrorInfo](#geterrorinfo).

### <a name="remarks"></a>Poznámky

Tento objekt obsahuje následující informace:

|Člen CDaoErrorInfo|Informace|Význam|
|--------------------------|-----------------|-------------|
|`m_lErrorCode`|Kód chyby|Kód chyby DAO|
|`m_strSource`|Zdroj|Název objektu nebo aplikace, která původně vygenerovala chybu|
|`m_strDescription`|Popis|Popisný řetězec přidružený k chybě|
|`m_strHelpFile`|Soubor nápovědy|Cesta k souboru nápovědy systému Windows, ve kterém může uživatel získat informace o problému|
|`m_lHelpContext`|Kontext nápovědy|ID kontextu tématu v souboru nápovědy dao|

Podrobné informace o informacích obsažených v objektu `CDaoErrorInfo` naleznete ve struktuře [CDaoErrorInfo.](../../mfc/reference/cdaoerrorinfo-structure.md)

## <a name="cdaoexceptionm_scode"></a><a name="m_scode"></a>CDaoException::m_scode

Obsahuje hodnotu `SCODE` typu, která popisuje chybu.

### <a name="remarks"></a>Poznámky

Toto je kód OLE. Tuto hodnotu budete zřídka potřebovat použít, protože téměř ve všech případech jsou v ostatních `CDaoException` datových členech k dispozici konkrétnější informace o chybě knihovny MFC nebo DAO.

Informace o kódu SCODE naleznete v tématu [Struktura kódů chyb OLE](/windows/win32/com/structure-of-com-error-codes) v sadě Windows SDK. Datový typ SCODE se mapuje na datový typ HRESULT.

## <a name="see-also"></a>Viz také

[CException – třída](../../mfc/reference/cexception-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CException – třída](../../mfc/reference/cexception-class.md)
