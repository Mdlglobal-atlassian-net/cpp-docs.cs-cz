---
title: Třída CSettingsStore | Microsoft Docs
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
ms.openlocfilehash: f5ed7d1dad634d330ac857f52d6ef35ef36c9c9a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="csettingsstore-class"></a>CSettingsStore – třída
Zabalí funkcí rozhraní API systému Windows, poskytnutím objektově orientované rozhraní, které používáte pro přístup k registru.  
  
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
|[CSettingsStore::DeleteKey](#deletekey)|Odstraní zadaný klíč a všechny její podřízené položky.|  
|[CSettingsStore::DeleteValue](#deletevalue)|Odstraní zadanou hodnotu otevřít klíč.|  
|[CSettingsStore::Open](#open)|Otevře se zadaným klíčem.|  
|[CSettingsStore::Read](#read)|Načte data pro zadanou hodnotou klíče.|  
|[CSettingsStore::Write](#write)|Zapíše hodnotu registru pod klíčem otevřete.|  
  
## <a name="remarks"></a>Poznámky  
 Členské funkce `CreateKey` a `Open` jsou velmi podobné. Pokud již existuje klíč registru, `CreateKey` a `Open` funkce stejným způsobem. Ale pokud klíč registru neexistuje, `CreateKey` dojde k jejímu vytvoření zatímco `Open` vrátí chybovou hodnotu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat metody otevřete a čtení z `CSettingsStore` třídy. Tento fragment kódu je součástí [nástroj Tip Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CSettingsStore`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxsettingsstore.h  
  
##  <a name="close"></a>  CSettingsStore::Close  
 Zavře otevřít klíč registru.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, tato metoda je volána z destruktoru objektu [CSettingsStore třída](../../mfc/reference/csettingsstore-class.md).  
  
##  <a name="createkey"></a>  CSettingsStore::CreateKey  
 Otevře se klíč registru nebo ji vytvoří, pokud neexistuje.  
  
```  
virtual BOOL CreateKey(LPCTSTR pszPath);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pszPath`  
 Určuje název klíče pro vytvořit nebo otevřít.  
  
### <a name="return-value"></a>Návratová hodnota  
 0 v případě úspěšného; v opačném případě nenulovou hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 `CreateKey` používá `m_hKey` jako kořen registru dotazy. Vyhledá `pszPath` jako podklíč `m_hKey`. Pokud klíč neexistuje, `CreateKey` ji vytvoří. Jinak otevře se klíč. `CreateKey` potom nastaví `m_hKey` ke klíči vytvořený nebo je otevřen.  
  
##  <a name="csettingsstore"></a>  CSettingsStore::CSettingsStore  
 Vytvoří `CSettngsStore` objektu.  
  
```  
CSettingsStore(
    BOOL bAdmin,  
    BOOL bReadOnly);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bAdmin`  
 Logický parametr, který určuje, zda `CSettingsStore` objekt funguje v režimu správce.  
  
 [v] `bReadOnly`  
 Logický parametr, který určuje, zda `CSettingsStore` objekt se vytvoří v režimu jen pro čtení.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `bAdmin` je nastaven na `true`, `m_hKey` člen proměnná je nastavená na `HKEY_LOCAL_MACHINE`. Pokud nastavíte `bAdmin` k `false`, `m_hKey` je nastaven na `HKEY_CURRENT_USER`.  
  
 Zabezpečený přístup závisí na `bReadOnly` parametr. Pokud `bReadonly` je `false`, nastaví se zabezpečený přístup `KEY_ALL_ACCESS`. Pokud `bReadyOnly` je `true`, zabezpečený přístup bude nastavena pro kombinaci `KEY_QUERY_VALUE, KEY_NOTIFY` a `KEY_ENUMERATE_SUB_KEYS`. Další informace o zabezpečení přístupu spolu s registru najdete v tématu [zabezpečení klíč registru a přístupová práva](http://msdn.microsoft.com/library/windows/desktop/ms724878).  
  
 Destruktor pro `CSettingsStore` uvolní `m_hKey` automaticky.  
  
##  <a name="deletekey"></a>  CSettingsStore::DeleteKey  
 Odstraní klíče a všechny její podřízené položky z registru.  
  
```  
virtual BOOL DeleteKey(
    LPCTSTR pszPath,  
    BOOL bAdmin = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pszPath`  
 Název klíče, který se odstranit.  
  
 [v] `bAdmin`  
 Přepínač, který určuje umístění klíč, který chcete odstranit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda se nezdaří, pokud `CSettingsStore` objekt je v režimu jen pro čtení.  
  
 Pokud parametr `bAdmin` rovná nule, `DeleteKey` vyhledá klíč, který chcete odstranit v rámci `HKEY_CURRENT_USER`. Pokud `bAdmin` nenulový, `DeleteKey` vyhledá klíč, který chcete odstranit v rámci `HKEY_LOCAL_MACHINE`.  
  
##  <a name="deletevalue"></a>  CSettingsStore::DeleteValue  
 Odstraní hodnotu z `m_hKey`.  
  
```  
virtual BOOL DeleteValue(LPCTSTR pszValue);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pszValue`  
 Určuje hodnotu pole, které chcete odebrat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
##  <a name="open"></a>  CSettingsStore::Open  
 Otevře se klíč registru.  
  
```  
virtual BOOL Open(LPCTSTR pszPath);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pszPath`  
 Název klíče registru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Když se tato metoda úspěšně otevře okno se zadaným klíčem, nastaví `m_hKey` k popisovači tohoto klíče.  
  
##  <a name="read"></a>  CSettingsStore::Read  
 Načte hodnotu z klíče v registru.  
  
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
 [v] `pszKey`  
 Ukazatel na řetězec ukončené hodnotou null, který obsahuje název hodnoty ke čtení z registru.  
  
 [out] `iVal`  
 Odkaz na proměnnou celé číslo, která přijímá hodnotu čtení z klíče registru.  
  
 [out] `dwVal`  
 Odkaz na 32-bit dvojité slovo proměnné, která obdrží hodnotu čtení z klíče registru.  
  
 [out] `sVal`  
 Odkaz na proměnnou string, který obdrží hodnotu čtení z klíče registru.  
  
 [out] `scStringList`  
 Odkaz na proměnnou string seznamu, která přijímá hodnotu čtení z klíče registru.  
  
 [out] `scArray`  
 Odkaz na proměnnou string pole, která přijímá hodnotu čtení z klíče registru.  
  
 [out] `dwcArray`  
 Odkaz na proměnné pole 32-bit dvojitou slova, která obdrží hodnotu čtení z klíče registru.  
  
 [out] `wcArray`  
 Odkaz na proměnné pole 16bitové slova, která obdrží hodnotu čtení z klíče registru.  
  
 [out] `bcArray`  
 Odkaz na proměnné pole bajtů, která obdrží hodnotu čtení z klíče registru.  
  
 [out] `lpPoint`  
 Odkaz na ukazatel na `POINT` struktura, která přijímá hodnota čtení z klíče registru.  
  
 [out] `rect`  
 Odkaz na [CRect](../../atl-mfc-shared/reference/crect-class.md) proměnné, která obdrží hodnotu čtení z klíče registru.  
  
 [out] `ppData`  
 Ukazatel na ukazatel na data, která obdrží hodnotu čtení z klíče registru.  
  
 [out] `pBytes`  
 Ukazatel na proměnnou celé číslo bez znaménka. Tato proměnná obdrží velikost vyrovnávací paměti, `ppData` odkazuje na.  
  
 [out] `list`  
 Odkaz na [CObList](../../mfc/reference/coblist-class.md) proměnné, která obdrží hodnotu čtení z klíče registru.  
  
 [out] `obj`  
 Odkaz na [CObject](../../mfc/reference/cobject-class.md) proměnné, která obdrží hodnotu čtení z klíče registru.  
  
 [out] `pObj`  
 Odkaz na ukazatel na `CObject` proměnné, která obdrží hodnotu čtení z klíče registru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 `Read` zkontroluje `pszKey` jako podklíč `m_hKey`.  
  
##  <a name="write"></a>  CSettingsStore::Write  
 Zapíše hodnotu registru pod klíčem otevřete.  
  
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
 [v] `pszKey`  
 Ukazatel na řetězec, který obsahuje název hodnota k nastavení.  
  
 [v] `iVal`  
 Odkaz na proměnnou celé číslo, který obsahuje data k uložení.  
  
 [v] `dwVal`  
 Odkaz na 32-bit dvojité slovo proměnné, která obsahuje data k uložení.  
  
 [v] `pszVal`  
 Ukazatel na proměnnou string ukončené hodnotou null, který obsahuje data k uložení.  
  
 [v] `scStringList`  
 Odkaz na [CStringList](../../mfc/reference/cstringlist-class.md) proměnné, která obsahuje data k uložení.  
  
 [v] `bcArray`  
 Odkaz na proměnnou pole bajtů obsahující data k uložení.  
  
 [v] `scArray`  
 Odkaz na proměnnou string pole, která obsahuje data k uložení.  
  
 [v] `dwcArray`  
 Odkaz na 32-bit double aplikace word proměnné pole, která obsahuje data k uložení.  
  
 [v] `wcArray`  
 Odkaz na proměnné pole 16bitové slova, která obsahuje data k uložení.  
  
 [v] `rect`  
 Odkaz na [CRect](../../atl-mfc-shared/reference/crect-class.md) proměnné, která obsahuje data k uložení.  
  
 [v] `lpPoint`  
 Odkaz na ukazatel na `POINT` proměnné, která obsahuje data k uložení.  
  
 [v] `pData`  
 Ukazatel na vyrovnávací paměť, která obsahuje data k uložení.  
  
 [v] `nBytes`  
 Určuje velikost v bajtech, dat, ke kterému `pData` parametr body.  
  
 [v] `list`  
 Odkaz na [CObList](../../mfc/reference/coblist-class.md) proměnné, která obsahuje data k uložení.  
  
 [v] `obj`  
 Odkaz na [CObject](../../mfc/reference/cobject-class.md) proměnné, která obsahuje data k uložení.  
  
 [v] `pObj`  
 Ukazatel na ukazatel na `CObject` proměnné, která obsahuje data k uložení.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` v případě úspěšného; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Aby bylo možné zapsat do registru, je nutné nastavit `bReadOnly` nenulovou hodnotu, při vytváření [CSettingsStore](../../mfc/reference/csettingsstore-class.md) objektu. Další informace najdete v tématu [CSettingsStore::CSettingsStore](#csettingsstore).  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)
