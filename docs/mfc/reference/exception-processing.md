---
title: Zpracování výjimek | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.exceptions
dev_langs:
- C++
helpviewer_keywords:
- macros [MFC], exception handling
- DAO (Data Access Objects), exceptions [MFC]
- OLE exceptions [MFC], MFC functions
- exceptions [MFC], processing
- exception macros [MFC]
- termination functions, MFC
- MFC, exceptions
- exceptions [MFC], MFC throwing functions
ms.assetid: 26d4457c-8350-48f5-916e-78f919787c30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a24d78089e468a2020e0ecdb1fba34783965325
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376985"
---
# <a name="exception-processing"></a>Zpracování výjimek
Když je program spuštěn, může dojít, počet nestandardní podmínky a chyby nazývají "výjimky". Ty mohou obsahovat vyčerpání paměti, chyb přidělení prostředků a nepodařilo se najít soubory.  
  
 Knihovny Microsoft Foundation Class používá schématu zpracování výjimek, které je Modelováno úzce jeden navrhované výbor standardy ANSI pro jazyk C++. Obslužné rutiny výjimek musí ho nastavit před voláním funkce, která setkat s neobvyklou situaci. Pokud funkce zaznamená nestandardního stavu, vyvolá výjimku a ovládací prvek předává do obslužné rutiny výjimky.  
  
 Několik makra součástí knihovny Microsoft Foundation Class nastaví obslužné rutiny výjimek. Počet dalších globální funkce pomoci vyvolat specializované výjimky a ukončit programy, v případě potřeby. Tyto makra a globální funkce spadají do následujících kategorií:  
  
- Makra výjimek, které struktury vaší obslužné rutiny výjimky.  
  
- Exception-throwing funkce), který generování výjimek specifické typy.  
  
- Ukončení funkcí, které způsobí ukončení programu.  
  
 Příklady a další podrobnosti najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="exception-macros"></a>Makra výjimek  
  
|||  
|-|-|  
|[ZKUSTE](#try)|Označí blok kódu pro zpracování výjimky.|  
|[CATCH](#catch)|Označí blok kódu pro zachytávání výjimku z předchozí **zkuste** bloku.|  
|[CATCH_ALL –](#catch_all)|Označí blok kódu pro zachytávání všechny výjimky z předchozí **zkuste** bloku.|  
|[AND_CATCH –](#and_catch)|Označí blok kódu pro zachytávání výjimek další typy z předchozí **zkuste** bloku.|  
|[AND_CATCH_ALL –](#and_catch_all)|Označí blok kódu pro zachytávání všechny ostatní typy další výjimka vyvolána v předchozích **zkuste** bloku.|  
|[END_CATCH –](#end_catch)|Končí poslední **CATCH** nebo `AND_CATCH` blok kódu.|  
|[END_CATCH_ALL –](#end_catch_all)|Končí poslední `CATCH_ALL` blok kódu.|  
|[THROW](#throw)|Vyvolá zadanou výjimkou.|  
|[THROW_LAST –](#throw_last)|Vyvolá aktuálně zpracování výjimek na další vnější obslužnou rutinu.|  
  
### <a name="exception-throwing-functions"></a>Funkce vyvolávání výjimek  
  
|||  
|-|-|  
|[Afxthrowarchiveexception –](#afxthrowarchiveexception)|Vyvolá výjimku archivu.|  
|[Afxthrowfileexception –](#afxthrowfileexception)|Vyvolá výjimku souborů.|  
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|Vyvolá výjimku neplatný argument.|
|[Afxthrowmemoryexception –](#afxthrowmemoryexception)|Vyvolá výjimku paměti.|  
|[Afxthrownotsupportedexception –](#afxthrownotsupportedexception)|Vyhodí výjimku není podporována.|  
|[Afxthrowresourceexception –](#afxthrowresourceexception)|Vyhodí výjimku Windows prostředek není nalezen.|  
|[Afxthrowuserexception –](#afxthrowuserexception)|V rámci akce zahájená uživatelem program vyvolá výjimku.|  
  
 MFC poskytuje dvě funkce vyvolávání výjimek speciálně pro OLE – výjimky:  
  
### <a name="ole-exception-functions"></a>Funkce výjimky OLE  
  
|||  
|-|-|  
|[Afxthrowoledispatchexception –](#afxthrowoledispatchexception)|Vyvolá výjimku, v rámci funkce automatizace OLE.|  
|[Afxthrowoleexception –](#afxthrowoleexception)|Vyvolá výjimku OLE.|  
  
 Pro podporu výjimky databáze, databázové třídy poskytují dvě třídy výjimek, `CDBException` a `CDaoException`a globální funkce pro podporu výjimka:  
  
### <a name="dao-exception-functions"></a>Funkce Výjimka rozhraní DAO  
  
|||  
|-|-|  
|[Afxthrowdaoexception –](#afxthrowdaoexception)|Vyvolá [CDaoException](../../mfc/reference/cdaoexception-class.md) z vlastního kódu.|  
|[Afxthrowdbexception –](#afxthrowdbexception)|Vyvolá [CDBException](../../mfc/reference/cdbexception-class.md) z vlastního kódu.|  
  
 MFC poskytuje následující funkce ukončení:  
  
### <a name="termination-functions"></a>Funkce ukončování  
  
|||  
|-|-|  
|[Afxabort –](#afxabort)|Volá se ukončit aplikaci po závažné chybě dochází.|  
  
##  <a name="try"></a>  ZKUSTE  
 Nastaví **zkuste** bloku.  
  
```   
TRY   
```  
  
### <a name="remarks"></a>Poznámky  
 A **zkuste** bloku identifikuje blok kódu, který může vyvolat výjimky. Tyto výjimky jsou zpracovávány v následujícím **CATCH** a `AND_CATCH` bloky. Rekurze je povoleno: výjimky může být předán vnější **zkuste** bloku, buď pomocí je ignorována, nebo pomocí `THROW_LAST` makro. End **zkuste** blokovat s `END_CATCH` nebo `END_CATCH_ALL` makro.  
  
 Další informace najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CATCH](#catch).  

### <a name="requirements"></a>Požadavky
Záhlaví: afx.h

##  <a name="catch"></a>  CATCH  
 Definuje blok kódu, který zachytí první typ výjimky vyvolány v předchozím **zkuste** bloku.  
  
```   
CATCH(exception_class, exception_object_pointer_name)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *exception_class*  
 Určuje typ výjimky, které chcete otestovat. Seznam tříd standardní výjimek najdete v tématu třídy [CException](../../mfc/reference/cexception-class.md).  
  
 *exception_object_pointer_name*  
 Určuje název ukazatele objekt výjimky vytvořené makro. Název ukazatele můžete použít pro přístup k objektu výjimka v rámci **CATCH** bloku. Tato proměnná je deklarovaná za vás.  
  
### <a name="remarks"></a>Poznámky  
 Kód zpracování výjimek můžete objekt výjimky, zjistěte, pokud je to vhodné, chcete-li získat další informace o konkrétní příčina výjimky. Vyvolání `THROW_LAST` makro se posunou zpracování do dalšího rámečku vnější výjimka. End **zkuste** blokovat s `END_CATCH` makro.  
  
 Pokud *exception_class* je třída `CException`, pak bude místo zachycení všechny typy výjimek. Můžete použít [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof) – členská funkce k určení, které konkrétní výjimku. Lepší způsob, jak zachytit několik druhy výjimek je použití sekvenční `AND_CATCH` příkazy, každý typ různé výjimky.  
  
 Makro vytvoří ukazatele na objekt výjimky. Není nutné deklarovat sami.  
  
> [!NOTE]
>  **CATCH** bloku je definován jako obor C++, vymezeny hranatými závorkami. Pokud deklarujete proměnné v tomto rozsahu, které jsou přístupné pouze v rámci tohoto oboru. To platí také pro *exception_object_pointer_name*.  
  
 Další informace o výjimky a **CATCH** makro, najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]  
  
##  <a name="catch_all"></a>  CATCH_ALL –  
 Definuje blok kódu, který zachytí všechny typy výjimka vyvolána v předchozím **zkuste** bloku.  
  
```   
CATCH_ALL(exception_object_pointer_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *exception_object_pointer_name*  
 Určuje název ukazatele objekt výjimky vytvořené makro. Název ukazatele můžete použít pro přístup k objektu výjimka v rámci `CATCH_ALL` bloku. Tato proměnná je deklarovaná za vás.  
  
### <a name="remarks"></a>Poznámky  
 Kód zpracování výjimek můžete objekt výjimky, zjistěte, pokud je to vhodné, chcete-li získat další informace o konkrétní příčina výjimky. Vyvolání `THROW_LAST` makro se posunou zpracování do dalšího rámečku vnější výjimka. Pokud používáte `CATCH_ALL`, end **zkuste** blokovat s `END_CATCH_ALL` makro.  
  
> [!NOTE]
>  `CATCH_ALL` Bloku je definován jako obor C++, vymezeny hranatými závorkami. Pokud deklarujete proměnné v tomto rozsahu, které jsou přístupné pouze v rámci tohoto oboru.  
  
 Další informace o výjimky, najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CFile::Abort](../../mfc/reference/cfile-class.md#abort).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afx.h  

##  <a name="and_catch"></a>  AND_CATCH –  
 Definuje blok kódu pro zachytávání typy další výjimka vyvolána v předchozích **zkuste** bloku.  
  
```   
AND_CATCH(exception_class, exception_object_pointer_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *exception_class*  
 Určuje typ výjimky, které chcete otestovat. Seznam tříd standardní výjimek najdete v tématu třídy [CException](../../mfc/reference/cexception-class.md).  
  
 *exception_object_pointer_name*  
 Název ukazatele objekt výjimky vytvořené makro. Název ukazatele můžete použít pro přístup k objektu výjimka v rámci `AND_CATCH` bloku. Tato proměnná je deklarovaná za vás.  
  
### <a name="remarks"></a>Poznámky  
 Použití **CATCH** makro k zachycení jeden typ výjimky, pak se `AND_CATCH` makro k zachycení každý další typ. End **zkuste** blokovat s `END_CATCH` makro.  
  
 Kód zpracování výjimek můžete objekt výjimky, zjistěte, pokud je to vhodné, chcete-li získat další informace o konkrétní příčina výjimky. Volání `THROW_LAST` makro v rámci `AND_CATCH` zablokujte shift zpracování do dalšího rámečku vnější výjimka. `AND_CATCH` označuje konec předchozím **CATCH** nebo `AND_CATCH` bloku.  
  
> [!NOTE]
>  `AND_CATCH` Bloku je definován jako obor C++ (vymezeny hranatými složené závorky). Pokud je deklarovat proměnné v tomto rozsahu, mějte na paměti, že jsou přístupné pouze v rámci tohoto oboru. To platí také pro *exception_object_pointer_name* proměnné.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CATCH](#catch).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afx.h  
##  <a name="and_catch_all"></a>  AND_CATCH_ALL –  
 Definuje blok kódu pro zachytávání typy další výjimka vyvolána v předchozích **zkuste** bloku.  
  
```   
AND_CATCH_ALL(exception_object_pointer_name)  
```  
  
### <a name="parameters"></a>Parametry  
 *exception_object_pointer_name*  
 Název ukazatele objekt výjimky vytvořené makro. Název ukazatele můžete použít pro přístup k objektu výjimka v rámci `AND_CATCH_ALL` bloku. Tato proměnná je deklarovaná za vás.  
  
### <a name="remarks"></a>Poznámky  
 Použití **CATCH** makro k zachycení jeden typ výjimky, pak se `AND_CATCH_ALL` makro k zachycení všech ostatních dalších typů. Pokud používáte `AND_CATCH_ALL`, end **zkuste** blokovat s `END_CATCH_ALL` makro.  
  
 Kód zpracování výjimek můžete objekt výjimky, zjistěte, pokud je to vhodné, chcete-li získat další informace o konkrétní příčina výjimky. Volání `THROW_LAST` makro v rámci `AND_CATCH_ALL` zablokujte shift zpracování do dalšího rámečku vnější výjimka. `AND_CATCH_ALL` označuje konec předchozím **CATCH** nebo `AND_CATCH_ALL` bloku.  
  
> [!NOTE]
>  `AND_CATCH_ALL` Bloku je definován jako obor C++ (vymezeny hranatými závorkami). Pokud je deklarovat proměnné v tomto rozsahu, mějte na paměti, že jsou přístupné pouze v rámci tohoto oboru.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afx.h  
  
##  <a name="end_catch"></a>  END_CATCH –  
 Označuje konec posledního **CATCH** nebo `AND_CATCH` bloku.  
  
```   
END_CATCH  
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace o `END_CATCH` makro, najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afx.h  
  
##  <a name="end_catch_all"></a>  END_CATCH_ALL –  
 Označuje konec posledního `CATCH_ALL` nebo `AND_CATCH_ALL` bloku.  
  
```   
END_CATCH_ALL  
```  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afx.h  
  
##  <a name="throw"></a>  THROW (MFC)  
 Vyvolá zadanou výjimkou.  
  
```   
THROW(exception_object_pointer) 
```  
  
### <a name="parameters"></a>Parametry  
 *exception_object_pointer*  
 Odkazuje na objekt výjimky odvozené z `CException`.  
  
### <a name="remarks"></a>Poznámky  
 **THROW** přerušení programu provádění předání přidruženého ovládacího prvku **CATCH** blokovat v programu. Pokud jste nezadali **CATCH** blokovat, pak ovládací prvek předává do Microsoft Foundation Class Library modul, který výtisků se chyba zpráva a bude ukončen.  
  
 Další informace najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afx.h  
  
##  <a name="throw_last"></a>  THROW_LAST –  
 Vyvolá výjimku zpět na další vnější **CATCH** bloku.  
  
```   
THROW_LAST()   
```  
  
### <a name="remarks"></a>Poznámky  
 Toto makro umožňuje místně vytvořené výjimku vyvolat. Pokud se pokusíte způsobí výjimku, který jste právě zachycena, bude se za normálních okolností dostala mimo rozsah a odstranit. S `THROW_LAST`, výjimka je předána správně na další **CATCH** obslužné rutiny.  
  
 Další informace najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CFile::Abort](../../mfc/reference/cfile-class.md#abort).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afx.h  
  
##  <a name="afxthrowarchiveexception"></a>  Afxthrowarchiveexception –  
 Vyvolá výjimku archivu.  
  
```   
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName); 
```  
  
### <a name="parameters"></a>Parametry  
 `cause`  
 Určuje celé číslo, které označuje důvod výjimky. Seznam možných hodnot najdete v tématu [CArchiveException::m_cause](../../mfc/reference/carchiveexception-class.md#m_cause).  
  
 `lpszArchiveName`  
 Odkazuje na řetězec obsahující název `CArchive` objekt, který způsobil výjimku (Pokud je k dispozici).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afx.h  
  
##  <a name="afxthrowfileexception"></a>  Afxthrowfileexception –  
 Vyvolá výjimku souborů.  
  
```   
void AfxThrowFileException(
    int cause,  
    LONG lOsError = -1,  
    LPCTSTR lpszFileName = NULL); 
```  
  
### <a name="parameters"></a>Parametry  
 `cause`  
 Určuje celé číslo, které označuje důvod výjimky. Seznam možných hodnot najdete v tématu [CFileException::m_cause](../../mfc/reference/cfileexception-class.md#m_cause).  
  
 `lOsError`  
 Obsahuje číslo chyby operačního systému (Pokud je k dispozici), stavy z důvodu výjimky. V příručce k operačního systému pro seznam kódy chyb.  
  
 `lpszFileName`  
 Odkazuje na řetězec, který obsahuje název souboru, který způsobil výjimku (Pokud je k dispozici).  
  
### <a name="remarks"></a>Poznámky  
 Jste zodpovědní za určení příčina podle kód chyby operačního systému.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afx.h  

## <a name="afxthrowinvalidargexception"></a>  AfxThrowInvalidArgException
Vyvolá výjimku neplatný argument.  
   
### <a name="syntax"></a>Syntaxe    
```
void AfxThrowInvalidArgException( );  
```  
   
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána, když se používají neplatné argumenty.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [CInvalidArgException – třída](cinvalidargexception-class.md)   
 [THROW](#throw)
  
  
##  <a name="afxthrowmemoryexception"></a>  Afxthrowmemoryexception –  
 Vyvolá výjimku paměti.  
  
```   
void AfxThrowMemoryException(); 
```  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce, pokud volání základní alokátorů paměti systému (například `malloc` a [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) funkce systému Windows) nezdaří. Není potřeba ho volání **nové** protože **nové** vyvolá výjimku výjimka paměti automaticky pokud selže přidělení paměti.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afx.h  
  
##  <a name="afxthrownotsupportedexception"></a>  Afxthrownotsupportedexception –  
 Vyvolá výjimku, která je výsledkem požadavku nepodporované funkce.  
  
```  
void AfxThrowNotSupportedException(); 
```  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afx.h  
  
##  <a name="afxthrowresourceexception"></a>  Afxthrowresourceexception –  
 Vyvolá výjimku prostředků.  
  
```   
void  AfxThrowResourceException(); 
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána obvykle, když prostředek systému Windows nelze načíst.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afx.h  
  
##  <a name="afxthrowuserexception"></a>  Afxthrowuserexception –  
 Vyvolá výjimku pro ukončení operace koncového uživatele.  
  
```   
void AfxThrowUserException(); 
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je obvykle volána hned po `AfxMessageBox` ohlásilo chybu pro uživatele.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afx.h  
  
##  <a name="afxthrowoledispatchexception"></a>  Afxthrowoledispatchexception –  
 Pomocí této funkce můžete vyvolat výjimku v rámci funkce automatizace OLE.  
  
```   
void AFXAPI AfxThrowOleDispatchException(
    WORD wCode ,  
    LPCSTR lpszDescription,  
    UINT nHelpID = 0);

void AFXAPI AfxThrowOleDispatchException(
    WORD wCode,  
    UINT nDescriptionID,  
    UINT nHelpID = -1); 
```  
  
### <a name="parameters"></a>Parametry  
 `wCode`  
 Kód chyby specifický pro vaši aplikaci.  
  
 `lpszDescription`  
 Slovní popis chyby.  
  
 `nDescriptionID`  
 ID prostředku pro popis ústní chyby.  
  
 `nHelpID`  
 Kontextové nápovědy nápovědu k vaší aplikace (. Soubor HLP).  
  
### <a name="remarks"></a>Poznámky  
 Informace o zadaný pro tuto funkci lze zobrazit řízení aplikací (Microsoft Visual Basic nebo jiná aplikace klienta automatizace OLE).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afx.h  
  
##  <a name="afxthrowoleexception"></a>  Afxthrowoleexception –  
 Vytvoří objekt typu `COleException` a vyvolá výjimku.  
  
``` 
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr); 
```  
  
### <a name="parameters"></a>Parametry  
 `sc`  
 Stavový kód OLE, určující důvod výjimky.  
  
 `hr`  
 Popisovač kód výsledku, který označuje důvod výjimky.  
  
### <a name="remarks"></a>Poznámky  
 Verze, která přebírá `HRESULT` jako argument k odpovídající položce převede tento kód výsledku `SCODE`. Další informace o `HRESULT` a `SCODE`, najdete v části [struktura kódy chyb COM](http://msdn.microsoft.com/library/windows/desktop/ms690088) ve Windows SDK.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdao.h  
  
##  <a name="afxthrowdaoexception"></a>  Afxthrowdaoexception –  
 Volání této funkce můžete vyvolat výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md) z vlastního kódu.  
  
```   
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,  
    SCODE scode = S_OK); 
```  
  
### <a name="parameters"></a>Parametry  
 `nAfxDaoError`  
 Celočíselná hodnota představující DAO, Rozšířený kód chyby, které může být jedna z hodnot uvedený v části [CDaoException::m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror).  
  
 *kód SCODE*  
 Kód chyby OLE z rozhraní DAO typu `SCODE`. Informace najdete v tématu [CDaoException::m_scode](../../mfc/reference/cdaoexception-class.md#m_scode).  
  
### <a name="remarks"></a>Poznámky  
 Také volá framework `AfxThrowDaoException`. Ve volání můžete předat jeden z parametrů nebo obojí. Například pokud chcete zvýšit jeden z chyby, které se definované v **CDaoException::nAfxDaoError** , ale nechcete o *kód scode* parametr, předejte platný kód v `nAfxDaoError` parametr a přijměte Výchozí hodnota pro *kód scode*.  
  
 Informace o výjimky související s tříd MFC rozhraní DAO najdete v tématu třídy `CDaoException` v této příručce a v článku [výjimky: výjimky databáze](../../mfc/exceptions-database-exceptions.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdb.h  
  
##  <a name="afxthrowdbexception"></a>  Afxthrowdbexception –  
 Volání této funkce můžete vyvolat výjimku typu `CDBException` z vlastního kódu.  
  
```  
void AfxThrowDBException(
    RETCODE nRetCode,  
    CDatabase* pdb,  
    HSTMT hstmt);  
```  
  
### <a name="parameters"></a>Parametry  
 `nRetCode`  
 Hodnotu typu **RETCODE**, definování typu chyby, která způsobila vyvolání výjimky.  
  
 `pdb`  
 Ukazatel `CDatabase` objekt, který reprezentuje připojení zdroje dat, ke kterému je přiřazeno výjimku.  
  
 `hstmt`  
 ODBC **HSTMT** popisovač, který určuje popisovač příkazu, ke kterému je přiřazeno výjimku.  
  
### <a name="remarks"></a>Poznámky  
 Volání framework `AfxThrowDBException` při přijetí ODBC **RETCODE** volání rozhraní API ODBC funkce a interpretuje **RETCODE** jako podmínku výjimečných, nikoli expectable chybu. Například operace přístupu k datům může selhat z důvodu chyby čtení disku.  
  
 Informace o **RETCODE** hodnoty definované rozhraní ODBC, naleznete v kapitole 8, "Načítání stavu a informace o chybě," v sadě Windows SDK. Informace o rozšíření MFC tyto kódy najdete v tématu třídy [CDBException](../../mfc/reference/cdbexception-class.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afx.h  
  
##  <a name="afxabort"></a>  Afxabort –  
 Výchozí funkce ukončení poskytl MFC.  
  
```   
void  AfxAbort(); 
```  
  
### <a name="remarks"></a>Poznámky  
 `AfxAbort` je volána interně členské funkce MFC po závažné chybě, jako je například nezachycenou výjimku, která nelze zpracovat. Můžete volat `AfxAbort` v případě výjimečných, když dojde k závažné chybě ze kterého nelze obnovit.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CATCH](#catch).  

### <a name="requirements"></a>Požadavky  
  **Záhlaví** afx.h   
  
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)   
 [CException – třída](../../mfc/reference/cexception-class.md)
