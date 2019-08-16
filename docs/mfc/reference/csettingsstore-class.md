---
title: CSettingsStore – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 75d86b81d9651e5892913af5919ae0a78fe6bbc5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502924"
---
# <a name="csettingsstore-class"></a>CSettingsStore – třída

Zabalí funkce rozhraní API systému Windows a poskytuje objektově orientované rozhraní, které používáte pro přístup k registru.

## <a name="syntax"></a>Syntaxe

```
class CSettingsStore : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CSettingsStore::CSettingsStore](#csettingsstore)|`CSettingsStore` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CSettingsStore::Close](#close)|Zavře otevřený klíč registru.|
|[CSettingsStore::CreateKey](#createkey)|Otevře zadaný klíč nebo ho vytvoří, pokud neexistuje.|
|[CSettingsStore::DeleteKey](#deletekey)|Odstraní zadaný klíč a všechny jeho podřízené položky.|
|[CSettingsStore::DeleteValue](#deletevalue)|Odstraní zadanou hodnotu otevřeného klíče.|
|[CSettingsStore::Open](#open)|Otevře zadaný klíč.|
|[CSettingsStore:: Read](#read)|Načte data pro zadanou hodnotu klíče.|
|[CSettingsStore:: Write](#write)|Zapíše hodnotu do registru v rámci otevřeného klíče.|

## <a name="remarks"></a>Poznámky

Členské funkce `CreateKey` a `Open` jsou velmi podobné. Pokud klíč registru již existuje `CreateKey` a `Open` funguje stejným způsobem. Pokud ale klíč registru neexistuje, vytvoří se tím, `CreateKey` že `Open` se vrátí chybová hodnota.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít metody `CSettingsStore` Open a Read třídy. Tento fragment kódu je součástí ukázkové ukázky pro [Popis tlačítka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CSettingsStore`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxsettingsstore. h

##  <a name="close"></a>CSettingsStore:: Close

Zavře otevřený klíč registru.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení je tato metoda volána z destruktoru [třídy CSettingsStore](../../mfc/reference/csettingsstore-class.md).

##  <a name="createkey"></a>CSettingsStore:: CreateKey

Otevře klíč registru nebo ho vytvoří, pokud neexistuje.

```
virtual BOOL CreateKey(LPCTSTR pszPath);
```

### <a name="parameters"></a>Parametry

*pszPath*<br/>
pro Určuje název klíče, který má být vytvořen nebo otevřen.

### <a name="return-value"></a>Návratová hodnota

0, pokud bylo úspěšné; v opačném případě nenulová hodnota.

### <a name="remarks"></a>Poznámky

`CreateKey`používá `m_hKey` se jako kořen dotazů registru. Vyhledá *pszPath* jako podklíč `m_hKey`. Pokud klíč neexistuje, `CreateKey` vytvoří se. V opačném případě otevře klíč. `CreateKey`pak se `m_hKey` nastaví na vytvořený nebo otevřený klíč.

##  <a name="csettingsstore"></a>CSettingsStore::CSettingsStore

`CSettngsStore` Vytvoří objekt.

```
CSettingsStore(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>Parametry

*bAdmin*<br/>
pro Parametr Boolean, který určuje, `CSettingsStore` zda objekt funguje v režimu správce.

*bReadOnly*<br/>
pro Parametr Boolean určující, zda `CSettingsStore` je objekt vytvořen v režimu jen pro čtení.

### <a name="remarks"></a>Poznámky

Pokud je *bAdmin* nastaveno na hodnotu true, `m_hKey` je členská proměnná nastavena na **HKEY_LOCAL_MACHINE**. Pokud nastavíte *bAdmin* na hodnotu false `m_hKey` , bude nastaveno na **HKEY_CURRENT_USER**.

Přístup k zabezpečení závisí na parametru *bReadOnly* . Pokud je *BREADONLY* false, zabezpečení přístupu se nastaví na **KEY_ALL_ACCESS**. Pokud má *bReadyOnly* hodnotu true, zabezpečení přístupu se nastaví na kombinaci **KEY_QUERY_VALUE, KEY_NOTIFY** a **KEY_ENUMERATE_SUB_KEYS**. Další informace o přístupu k zabezpečení spolu s registrem najdete v tématu [zabezpečení klíčů registru a přístupová práva](/windows/win32/SysInfo/registry-key-security-and-access-rights).

Destruktor pro `CSettingsStore` automatické vydaných verzí `m_hKey` .

##  <a name="deletekey"></a>CSettingsStore::D eleteKey

Odstraní klíč a všechny jeho podřízené položky z registru.

```
virtual BOOL DeleteKey(
    LPCTSTR pszPath,
    BOOL bAdmin = FALSE);
```

### <a name="parameters"></a>Parametry

*pszPath*<br/>
pro Název klíče, který se má odstranit

*bAdmin*<br/>
pro Přepínač, který určuje umístění klíče, který se má odstranit.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato metoda se nezdaří, pokud `CSettingsStore` je objekt v režimu jen pro čtení.

Pokud je parametr *bAdmin* nula, `DeleteKey` vyhledá klíč, který se má odstranit pod **HKEY_CURRENT_USER**. Pokud je *bAdmin* nenulového `DeleteKey` , vyhledá klíč, který se má v **HKEY_LOCAL_MACHINE**odstranit.

##  <a name="deletevalue"></a>CSettingsStore::D eleteValue

Odstraní hodnotu z `m_hKey`.

```
virtual BOOL DeleteValue(LPCTSTR pszValue);
```

### <a name="parameters"></a>Parametry

*pszValue*<br/>
pro Určuje pole hodnoty, které se má odebrat.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

##  <a name="open"></a>CSettingsStore:: Open

Otevře klíč registru.

```
virtual BOOL Open(LPCTSTR pszPath);
```

### <a name="parameters"></a>Parametry

*pszPath*<br/>
pro Název klíče registru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Po úspěšném spuštění této metody se zadaný klíč nastaví `m_hKey` na popisovač tohoto klíče.

##  <a name="read"></a>CSettingsStore:: Read

Přečte hodnotu z klíče v registru.

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
pro Ukazatel na řetězec zakončený hodnotou null, který obsahuje název hodnoty, která má být načtena z registru.

*iVal*<br/>
mimo Odkaz na proměnnou typu Integer, která přijímá hodnotu načtenou z klíče registru.

*dwVal*<br/>
mimo Odkaz na 32 proměnnou s dvojitým slovem, která přijímá hodnotu načtenou z klíče registru.

*sVal*<br/>
mimo Odkaz na řetězcovou proměnnou, která přijímá hodnotu načtenou z klíče registru.

*scStringList*<br/>
mimo Odkaz na proměnnou seznamu řetězců, která přijímá hodnotu čtenou z klíče registru.

*scArray*<br/>
mimo Odkaz na proměnnou pole řetězce, která přijímá hodnotu načtenou z klíče registru.

*dwcArray*<br/>
mimo Odkaz na proměnnou pole dvojitého slova (32), která přijímá hodnotu načtenou z klíče registru.

*wcArray*<br/>
mimo Odkaz na 16bitová proměnnou pole aplikace Word, která přijímá hodnotu načtenou z klíče registru.

*bcArray*<br/>
mimo Odkaz na proměnnou bajtového pole, která přijímá hodnotu načtenou z klíče registru.

*lpPoint*<br/>
mimo Odkaz na ukazatel na `POINT` strukturu, která přijímá hodnotu načtenou z klíče registru.

*OBD*<br/>
mimo Odkaz na proměnnou [CRect](../../atl-mfc-shared/reference/crect-class.md) , která přijímá hodnotu načtenou z klíče registru.

*ppData*<br/>
mimo Ukazatel na ukazatel na data, která obdrží hodnotu načtenou z klíče registru.

*pBytes*<br/>
mimo Ukazatel na unsigned integer proměnnou. Tato proměnná přijímá velikost vyrovnávací paměti, na kterou odkazuje *ppData* .

*list*<br/>
mimo Odkaz na proměnnou [CObList](../../mfc/reference/coblist-class.md) , která přijímá hodnotu načtenou z klíče registru.

*obj*<br/>
mimo Odkaz na proměnnou [CObject](../../mfc/reference/cobject-class.md) , která přijímá hodnotu načtenou z klíče registru.

*pObj*<br/>
mimo Odkaz na ukazatel na `CObject` proměnnou, která přijímá hodnotu načtenou z klíče registru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

`Read`kontroluje *pszKey* jako podklíč `m_hKey`.

##  <a name="write"></a>CSettingsStore:: Write

Zapíše hodnotu do registru v rámci otevřeného klíče.

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
pro Ukazatel na řetězec, který obsahuje název hodnoty, která se má nastavit.

*iVal*<br/>
pro Odkaz na celočíselnou proměnnou obsahující data, která mají být uložena.

*dwVal*<br/>
pro Odkaz na proměnnou s dvojitým slovem 32, která obsahuje data, která se mají uložit.

*pszVal*<br/>
pro Ukazatel na řetězcovou proměnnou zakončenou hodnotou null, která obsahuje data, která mají být uložena.

*scStringList*<br/>
pro Odkaz na [CStringList](../../mfc/reference/cstringlist-class.md) proměnnou obsahující data, která mají být uložena.

*bcArray*<br/>
pro Odkaz na proměnnou bajtového pole obsahující data, která mají být uložena.

*scArray*<br/>
pro Odkaz na proměnnou pole řetězce obsahující data, která mají být uložena.

*dwcArray*<br/>
pro Odkaz na proměnnou pole dvojitého slova (32), která obsahuje data, která mají být uložena.

*wcArray*<br/>
pro Odkaz na 16bitová proměnnou pole aplikace Word obsahující data, která mají být uložena.

*OBD*<br/>
pro Odkaz na [CRect](../../atl-mfc-shared/reference/crect-class.md) proměnnou obsahující data, která mají být uložena.

*lpPoint*<br/>
pro Odkaz na ukazatel na `POINT` proměnnou, která obsahuje data, která mají být uložena.

*pData*<br/>
pro Ukazatel na vyrovnávací paměť obsahující data, která mají být uložena.

*nBytes*<br/>
pro Určuje velikost dat, na která odkazuje parametr *PDATA* (v bajtech).

*list*<br/>
pro Odkaz na [CObList](../../mfc/reference/coblist-class.md) proměnnou obsahující data, která mají být uložena.

*obj*<br/>
pro Odkaz na [CObject](../../mfc/reference/cobject-class.md) proměnnou obsahující data, která mají být uložena.

*pObj*<br/>
pro Ukazatel na ukazatel na `CObject` proměnnou, která obsahuje data, která mají být uložena.

### <a name="return-value"></a>Návratová hodnota

TRUE v případě úspěchu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Aby bylo možné zapisovat do registru, je nutné při vytváření objektu [CSettingsStore](../../mfc/reference/csettingsstore-class.md) nastavit *bReadOnly* na nenulovou hodnotu. Další informace najdete v tématu [CSettingsStore:: CSettingsStore](#csettingsstore).

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)
