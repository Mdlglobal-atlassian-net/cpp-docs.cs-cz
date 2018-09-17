---
title: Csettingsstore – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::Close
- AFXSETTINGSSTORE/CSettingsStore::CreateKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteValue
- AFXSETTINGSSTORE/CSettingsStore::Open
- AFXSETTINGSSTORE/CSettingsStore::Read
- AFXSETTINGSSTORE/CSettingsStore::Write
dev_langs:
- C++
helpviewer_keywords:
- CSettingsStore [MFC], CSettingsStore
- CSettingsStore [MFC], Close
- CSettingsStore [MFC], CreateKey
- CSettingsStore [MFC], DeleteKey
- CSettingsStore [MFC], DeleteValue
- CSettingsStore [MFC], Open
- CSettingsStore [MFC], Read
- CSettingsStore [MFC], Write
ms.assetid: 0ea181de-a13e-4b29-b560-7c43838223ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1cd37ee2ad7fe09e2838d5e3cecb3488594d2c9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706625"
---
# <a name="csettingsstore-class"></a>Csettingsstore – třída
Zalomí funkce rozhraní API Windows, poskytuje objektově orientovaného rozhraní, které používáte pro přístup k registru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSettingsStore : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSettingsStore::CSettingsStore](#csettingsstore)|Vytvoří `CSettingsStore` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSettingsStore::Close](#close)|Zavře otevřít klíč registru.|  
|[CSettingsStore::CreateKey](#createkey)|Otevře se zadaným klíčem nebo ji vytvoří, pokud neexistuje.|  
|[CSettingsStore::DeleteKey](#deletekey)|Odstraní zadaný klíč a všechny jeho podřízené objekty.|  
|[CSettingsStore::DeleteValue](#deletevalue)|Odstraní zadanou hodnotu otevřít klíč.|  
|[CSettingsStore::Open](#open)|Otevře se zadaným klíčem.|  
|[CSettingsStore::Read](#read)|Načte data pro zadanou hodnotou klíče.|  
|[CSettingsStore::Write](#write)|Zapíše hodnotu registru pod klíčem otevřít.|  
  
## <a name="remarks"></a>Poznámky  
 Členské funkce `CreateKey` a `Open` jsou velmi podobné. Pokud již existuje klíč registru, `CreateKey` a `Open` funkce stejným způsobem. Nicméně, pokud klíč registru neexistuje, `CreateKey` dojde k jejímu vytvoření vzhledem k tomu `Open` vrátí chybovou hodnotu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití metody otevřít a číst `CSettingsStore` třídy. Tento fragment kódu je součástí [nástroj Tip demonstrační ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 `CSettingsStore`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxsettingsstore.h  
  
##  <a name="close"></a>  CSettingsStore::Close  
 Zavře otevřít klíč registru.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, tato metoda je volána z destruktor [csettingsstore – třída](../../mfc/reference/csettingsstore-class.md).  
  
##  <a name="createkey"></a>  CSettingsStore::CreateKey  
 Otevře se klíč registru nebo ji vytvoří, pokud neexistuje.  
  
```  
virtual BOOL CreateKey(LPCTSTR pszPath);
```  
  
### <a name="parameters"></a>Parametry  
*pszPath*<br/>
[in] Určuje název klíče, který má být vytvořen nebo otevřen.  
  
### <a name="return-value"></a>Návratová hodnota  
 0 v případě úspěchu; v opačném případě nenulovou hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 `CreateKey` používá `m_hKey` jako kořen registru dotazy. Vyhledá *pszPath* jako podklíč `m_hKey`. Pokud klíč neexistuje, `CreateKey` ji vytvoří. V opačném případě se otevře klíč. `CreateKey` potom nastaví `m_hKey` na klíč vytvořené nebo je otevřen.  
  
##  <a name="csettingsstore"></a>  CSettingsStore::CSettingsStore  
 Vytvoří `CSettngsStore` objektu.  
  
```  
CSettingsStore(
    BOOL bAdmin,  
    BOOL bReadOnly);
```  
  
### <a name="parameters"></a>Parametry  
*bAdmin*<br/>
[in] Logický parametr, který určuje, zda `CSettingsStore` objekt funguje v režimu správce.  
  
*bReadOnly*<br/>
[in] Logický parametr, který určuje, zda `CSettingsStore` objekt je vytvořen v režimu jen pro čtení.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *bAdmin* nastavena na hodnotu TRUE, `m_hKey` členská proměnná je nastavena na **HKEY_LOCAL_MACHINE**. Pokud nastavíte *bAdmin* na hodnotu FALSE, `m_hKey` je nastavena na **HKEY_CURRENT_USER**.  
  
 Zabezpečený přístup závisí *bReadOnly* parametru. Pokud *bReadonly* má hodnotu FALSE, nastaví se zabezpečený přístup **KEY_ALL_ACCESS**. Pokud *bReadyOnly* má hodnotu TRUE, přístup k zabezpečení se nastaví na kombinaci **KEY_QUERY_VALUE, KEY_NOTIFY** a **KEY_ENUMERATE_SUB_KEYS**. Další informace o zabezpečení přístupu spolu s registru najdete v tématu [zabezpečení klíče registru a přístupová práva](/windows/desktop/SysInfo/registry-key-security-and-access-rights).  
  
 Destruktor `CSettingsStore` uvolní `m_hKey` automaticky.  
  
##  <a name="deletekey"></a>  CSettingsStore::DeleteKey  
 Odstraní klíč a všechny jeho podřízené položky z registru.  
  
```  
virtual BOOL DeleteKey(
    LPCTSTR pszPath,  
    BOOL bAdmin = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
*pszPath*<br/>
[in] Název klíče odstranit.  
  
*bAdmin*<br/>
[in] Přepínač, který určuje umístění klíče odstranit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda se nezdaří, pokud `CSettingsStore` objekt je v režimu jen pro čtení.  
  
 Pokud parametr *bAdmin* je nula, `DeleteKey` vyhledá klíč odstranit v rámci **HKEY_CURRENT_USER**. Pokud *bAdmin* nenulové, `DeleteKey` vyhledá klíč odstranit v rámci **HKEY_LOCAL_MACHINE**.  
  
##  <a name="deletevalue"></a>  CSettingsStore::DeleteValue  
 Odstraní hodnotu z `m_hKey`.  
  
```  
virtual BOOL DeleteValue(LPCTSTR pszValue);
```  
  
### <a name="parameters"></a>Parametry  
*pszValue*<br/>
[in] Určuje hodnotu pole odebrat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
##  <a name="open"></a>  CSettingsStore::Open  
 Otevře se klíč registru.  
  
```  
virtual BOOL Open(LPCTSTR pszPath);
```  
  
### <a name="parameters"></a>Parametry  
*pszPath*<br/>
[in] Název klíče registru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Po této metody úspěšně otevře se zadaným klíčem, nastaví `m_hKey` ke zpracování tohoto klíče.  
  
##  <a name="read"></a>  CSettingsStore::Read  
 Načte hodnotu z klíče registru.  
  
```  
virtual BOOL Read(
    LPCTSTR pszKey,  
    int& iVal);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    DWORD& dwVal);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    CString& sVal);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    CStringList& scStringList);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    CStringArray& scArray);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    CDWordArray& dwcArray);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    CWordArray& wcArray);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    CByteArray& bcArray);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    LPPOINT& lpPoint);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    CRect& rect);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    BYTE** ppData,  
    UINT* pBytes);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    CObList& list);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    CObject& obj);

 
virtual BOOL Read(
    LPCTSTR pszKey,  
    CObject*& pObj);
```  
  
### <a name="parameters"></a>Parametry  
*pszKey*<br/>
[in] Ukazatel na řetězec zakončený hodnotou null, který obsahuje název hodnoty ke čtení z registru.  
  
*iVal*<br/>
[out] Odkaz na celočíselnou proměnnou, která přijímá hodnotu čtení z klíče registru.  
  
*dwVal*<br/>
[out] Odkaz na proměnnou double word 32-bit, který přijímá hodnotu čtení z klíče registru.  
  
*sVal*<br/>
[out] Odkaz na proměnnou s řetězcem, který přijímá hodnotu čtení z klíče registru.  
  
*scStringList*<br/>
[out] Odkaz na proměnnou s řetězcem seznam, který přijímá hodnotu čtení z klíče registru.  
  
*scArray*<br/>
[out] Odkaz na proměnnou pole řetězce, který přijímá hodnotu čtení z klíče registru.  
  
*dwcArray*<br/>
[out] Odkaz na proměnnou pole double word 32-bit, který přijímá hodnotu čtení z klíče registru.  
  
*wcArray*<br/>
[out] Odkaz na proměnnou pole 16bitových slov, která přijímá hodnotu čtení z klíče registru.  
  
*bcArray*<br/>
[out] Odkaz na proměnnou pole bajtů, který přijímá hodnotu čtení z klíče registru.  
  
*lppoint –*<br/>
[out] Odkaz na ukazatel `POINT` struktura, která přijímá hodnotu čtení z klíče registru.  
  
*Rect*<br/>
[out] Odkaz [crect –](../../atl-mfc-shared/reference/crect-class.md) proměnné, která přijímá hodnotu čtení z klíče registru.  
  
*ppData*<br/>
[out] Ukazatel na ukazatel na data, která přijímá hodnotu čtení z klíče registru.  
  
*pBytes*<br/>
[out] Ukazatel na proměnnou celého čísla bez znaménka. Tato proměnná obdrží velikost vyrovnávací paměti, která *ppData* odkazuje na.  
  
*list*<br/>
[out] Odkaz [coblist –](../../mfc/reference/coblist-class.md) proměnné, která přijímá hodnotu čtení z klíče registru.  
  
*obj*<br/>
[out] Odkaz [CObject](../../mfc/reference/cobject-class.md) proměnné, která přijímá hodnotu čtení z klíče registru.  
  
*pObj*<br/>
[out] Odkaz na ukazatel `CObject` proměnné, která přijímá hodnotu čtení z klíče registru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 `Read` Vyhledá *pszKey* jako podklíč `m_hKey`.  
  
##  <a name="write"></a>  CSettingsStore::Write  
 Zapíše hodnotu registru pod klíčem otevřít.  
  
```  
virtual BOOL Write(
    LPCTSTR pszKey,  
    int iVal);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    DWORD dwVal);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    LPCTSTR pszVal);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    CStringList& scStringList);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    CByteArray& bcArray);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    CStringArray& scArray);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    CDWordArray& dwcArray);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    CWordArray& wcArray);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    const CRect& rect);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    LPPOINT& lpPoint);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    LPBYTE pData,  
    UINT nBytes);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    CObList& list);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    CObject& obj);

 
virtual BOOL Write(
    LPCTSTR pszKey,  
    CObject* pObj);
```  
  
### <a name="parameters"></a>Parametry  
*pszKey*<br/>
[in] Ukazatel na řetězec, který obsahuje název má být nastavena hodnota.  
  
*iVal*<br/>
[in] Odkaz na celočíselnou proměnnou, která obsahuje data k uložení.  
  
*dwVal*<br/>
[in] Odkaz na proměnnou double word 32-bit, který obsahuje data k uložení.  
  
*pszVal*<br/>
[in] Ukazatel na řetězec zakončený hodnotou null proměnné, která obsahuje data k uložení.  
  
*scStringList*<br/>
[in] Odkaz [CStringList](../../mfc/reference/cstringlist-class.md) proměnnou, která obsahuje data k uložení.  
  
*bcArray*<br/>
[in] Odkaz na proměnnou pole bajtů, který obsahuje data k uložení.  
  
*scArray*<br/>
[in] Odkaz na proměnnou pole řetězce, který obsahuje data k uložení.  
  
*dwcArray*<br/>
[in] Odkaz na proměnnou pole double word 32-bit, který obsahuje data k uložení.  
  
*wcArray*<br/>
[in] Odkaz na proměnnou pole 16bitových slov, která obsahuje data k uložení.  
  
*Rect*<br/>
[in] Odkaz [crect –](../../atl-mfc-shared/reference/crect-class.md) proměnnou, která obsahuje data k uložení.  
  
*lppoint –*<br/>
[in] Odkaz na ukazatel `POINT` proměnnou, která obsahuje data k uložení.  
  
*pData*<br/>
[in] Ukazatel do vyrovnávací paměti, která obsahuje data k uložení.  
  
*nBytes*<br/>
[in] Určuje velikost v bajtech, dat, ke kterému *pData* parametr body.  
  
*list*<br/>
[in] Odkaz [coblist –](../../mfc/reference/coblist-class.md) proměnnou, která obsahuje data k uložení.  
  
*obj*<br/>
[in] Odkaz [CObject](../../mfc/reference/cobject-class.md) proměnnou, která obsahuje data k uložení.  
  
*pObj*<br/>
[in] Ukazatel na ukazatel `CObject` proměnnou, která obsahuje data k uložení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE v případě úspěchu; v opačném případě FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Aby bylo možné zapsat do registru, je nutné nastavit *bReadOnly* na nenulovou hodnotu, když vytvoříte [csettingsstore –](../../mfc/reference/csettingsstore-class.md) objektu. Další informace najdete v tématu [CSettingsStore::CSettingsStore](#csettingsstore).  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)
