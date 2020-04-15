---
title: Třída CSettingsStore
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
ms.openlocfilehash: b1acf959c371aa23ac55ace7fea9466f0e20813f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318458"
---
# <a name="csettingsstore-class"></a>Třída CSettingsStore

Zalomí funkce rozhraní API systému Windows a poskytne objektově orientované rozhraní, které používáte pro přístup k registru.

## <a name="syntax"></a>Syntaxe

```
class CSettingsStore : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CSettingsStore::CSettingsStore](#csettingsstore)|Vytvoří `CSettingsStore` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSettingsStore::Zavřít](#close)|Zavře otevřený klíč registru.|
|[CSettingsStore::Vytvořit klíč](#createkey)|Otevře zadaný klíč nebo jej vytvoří, pokud neexistuje.|
|[CSettingsStore::DeleteKey](#deletekey)|Odstraní zadaný klíč a všechny jeho podřízené položky.|
|[CSettingsStore::DeleteValue](#deletevalue)|Odstraní zadanou hodnotu otevřeného klíče.|
|[CSettingsStore::Otevřít](#open)|Otevře zadaný klíč.|
|[CSettingsStore::Číst](#read)|Načte data pro zadanou hodnotu klíče.|
|[CSettingsStore::Zápis](#write)|Zapíše hodnotu do registru pod otevřeným klíčem.|

## <a name="remarks"></a>Poznámky

Člen funguje `CreateKey` `Open` a jsou velmi podobné. Pokud klíč registru již `CreateKey` existuje `Open` a funguje stejným způsobem. Pokud však klíč registru neexistuje, vytvoří jej, `CreateKey` zatímco `Open` vrátí chybovou hodnotu.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat Open a `CSettingsStore` Read metody třídy. Tento fragment kódu je součástí [ukázky ukázky ukázky tipu nástroje](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CSettingsStore`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxsettingsstore.h

## <a name="csettingsstoreclose"></a><a name="close"></a>CSettingsStore::Zavřít

Zavře otevřený klíč registru.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení je tato metoda volána z destruktoru [třídy CSettingsStore](../../mfc/reference/csettingsstore-class.md).

## <a name="csettingsstorecreatekey"></a><a name="createkey"></a>CSettingsStore::Vytvořit klíč

Otevře klíč registru nebo jej vytvoří, pokud neexistuje.

```
virtual BOOL CreateKey(LPCTSTR pszPath);
```

### <a name="parameters"></a>Parametry

*pszPath*<br/>
[v] Určuje název klíče, který má být vytvořen nebo otevřen.

### <a name="return-value"></a>Návratová hodnota

0 v případě úspěchu; jinak nenulová hodnota.

### <a name="remarks"></a>Poznámky

`CreateKey`jako `m_hKey` kořen dotazů registru. Hledá *pszPath* jako podklíč . `m_hKey` Pokud klíč neexistuje, `CreateKey` vytvoří jej. V opačném případě se otevře klíč. `CreateKey`pak `m_hKey` nastaví na vytvořený nebo otevřený klíč.

## <a name="csettingsstorecsettingsstore"></a><a name="csettingsstore"></a>CSettingsStore::CSettingsStore

Vytvoří `CSettngsStore` objekt.

```
CSettingsStore(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>Parametry

*bAdmin*<br/>
[v] Logický parametr, který určuje, `CSettingsStore` zda objekt pracuje v režimu správce.

*bReadOnly*<br/>
[v] Logický parametr, který určuje, zda je `CSettingsStore` objekt vytvořen v režimu jen pro čtení.

### <a name="remarks"></a>Poznámky

Pokud je *hodnota bAdmin* `m_hKey` nastavena na hodnotu TRUE, je proměnná člena nastavena na **HKEY_LOCAL_MACHINE**. Pokud nastavíte *bAdmin* na HODNOTU NEPRAVDA, `m_hKey` je nastavena na **HKEY_CURRENT_USER**.

Přístup k zabezpečení závisí na parametru *bReadOnly.* Pokud *bReadonly* je FALSE, přístup k zabezpečení bude nastavena na **KEY_ALL_ACCESS**. Pokud *je hodnota bReadyOnly* true, bude přístup k zabezpečení nastaven na kombinaci **KEY_QUERY_VALUE, KEY_NOTIFY** a **KEY_ENUMERATE_SUB_KEYS**. Další informace o přístupu k zabezpečení spolu s registrem naleznete v [tématu Zabezpečení klíčů registru a přístupová práva](/windows/win32/SysInfo/registry-key-security-and-access-rights).

Destruktor `CSettingsStore` pro `m_hKey` uvolnění automaticky.

## <a name="csettingsstoredeletekey"></a><a name="deletekey"></a>CSettingsStore::DeleteKey

Odstraní klíč a všechny jeho podřízené z registru.

```
virtual BOOL DeleteKey(
    LPCTSTR pszPath,
    BOOL bAdmin = FALSE);
```

### <a name="parameters"></a>Parametry

*pszPath*<br/>
[v] Název klíče, který chcete odstranit.

*bAdmin*<br/>
[v] Přepínač, který určuje umístění klíče k odstranění.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda se `CSettingsStore` nezdaří, pokud je objekt v režimu jen pro čtení.

Pokud je parametr *bAdmin* nulový, `DeleteKey` vyhledá klíč, který chcete odstranit v **části HKEY_CURRENT_USER**. Pokud *je bAdmin* `DeleteKey` nenulový, vyhledá klíč, který chcete odstranit v **části HKEY_LOCAL_MACHINE**.

## <a name="csettingsstoredeletevalue"></a><a name="deletevalue"></a>CSettingsStore::DeleteValue

Odstraní hodnotu `m_hKey`z .

```
virtual BOOL DeleteValue(LPCTSTR pszValue);
```

### <a name="parameters"></a>Parametry

*pszValue*<br/>
[v] Určuje pole hodnoty, které chcete odebrat.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

## <a name="csettingsstoreopen"></a><a name="open"></a>CSettingsStore::Otevřít

Otevře klíč registru.

```
virtual BOOL Open(LPCTSTR pszPath);
```

### <a name="parameters"></a>Parametry

*pszPath*<br/>
[v] Název klíče registru.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Poté, co tato metoda úspěšně otevře `m_hKey` zadaný klíč, nastaví na popisovač tohoto klíče.

## <a name="csettingsstoreread"></a><a name="read"></a>CSettingsStore::Číst

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

*pszKey*<br/>
[v] Ukazatel na řetězec s ukončeným hodnotou null, který obsahuje název hodnoty pro čtení z registru.

*iVal*<br/>
[out] Odkaz na celou proměnnou, která přijímá hodnotu přečtenou z klíče registru.

*dwVal řekl:*<br/>
[out] Odkaz na 32bitovou proměnnou dvojitého slova, která přijímá hodnotu přečtenou z klíče registru.

*sVal*<br/>
[out] Odkaz na proměnnou řetězce, která přijímá hodnotu přečtenou z klíče registru.

*seznam scStringList*<br/>
[out] Odkaz na proměnnou seznamu řetězců, která přijímá hodnotu přečtenou z klíče registru.

*pole scArray*<br/>
[out] Odkaz na proměnnou pole řetězce, která přijímá hodnotu přečtenou z klíče registru.

*pole dwcArray*<br/>
[out] Odkaz na 32bitovou proměnnou dvojitého pole slov, která přijímá hodnotu přečtenou z klíče registru.

*wcArray*<br/>
[out] Odkaz na 16bitovou proměnnou pole slov, která přijímá hodnotu přečtenou z klíče registru.

*pole bcArray*<br/>
[out] Odkaz na proměnnou bajtového pole, která přijímá hodnotu přečtenou z klíče registru.

*lpPoint*<br/>
[out] Odkaz na ukazatel `POINT` na strukturu, která přijímá hodnotu přečtenou z klíče registru.

*Rect*<br/>
[out] Odkaz na proměnnou [CRect,](../../atl-mfc-shared/reference/crect-class.md) která přijímá hodnotu přečtenou z klíče registru.

*ppData*<br/>
[out] Ukazatel na ukazatel na data, která obdrží hodnotu přečtenou z klíče registru.

*pBytes*<br/>
[out] Ukazatel na nepodepsanou integer ovou proměnnou. Tato proměnná obdrží velikost vyrovnávací paměti, která *ppData* odkazuje na.

*list*<br/>
[out] Odkaz na proměnnou [CObList,](../../mfc/reference/coblist-class.md) která přijímá hodnotu přečtenou z klíče registru.

*Obj*<br/>
[out] Odkaz na proměnnou [CObject,](../../mfc/reference/cobject-class.md) která přijímá hodnotu přečtenou z klíče registru.

*pObj*<br/>
[out] Odkaz na ukazatel `CObject` na proměnnou, která obdrží hodnotu přečtenou z klíče registru.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

`Read`zkontroluje *pszKey* jako podklíč . `m_hKey`

## <a name="csettingsstorewrite"></a><a name="write"></a>CSettingsStore::Zápis

Zapíše hodnotu do registru pod otevřeným klíčem.

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
[v] Ukazatel na řetězec, který obsahuje název hodnoty, která má být nastavena.

*iVal*<br/>
[v] Odkaz na celou proměnnou, která obsahuje data k uložení.

*dwVal řekl:*<br/>
[v] Odkaz na 32bitovou proměnnou dvojitého slova, která obsahuje data, která mají být ukládána.

*pszVal*<br/>
[v] Ukazatel na proměnnou řetězce ukončenou hodnotou null, která obsahuje data, která mají být ukládat.

*seznam scStringList*<br/>
[v] Odkaz na [proměnnou CStringList,](../../mfc/reference/cstringlist-class.md) která obsahuje data k uložení.

*pole bcArray*<br/>
[v] Odkaz na proměnnou bajtového pole, která obsahuje data k uložení.

*pole scArray*<br/>
[v] Odkaz na proměnnou pole řetězce, která obsahuje data k uložení.

*pole dwcArray*<br/>
[v] Odkaz na 32bitovou proměnnou dvojitého pole slov, která obsahuje data, která mají být ukládat.

*wcArray*<br/>
[v] Odkaz na 16bitovou proměnnou pole slov, která obsahuje data, která mají být ukládána.

*Rect*<br/>
[v] Odkaz na [cRect](../../atl-mfc-shared/reference/crect-class.md) proměnné, která obsahuje data k uložení.

*lpPoint*<br/>
[v] Odkaz na ukazatel `POINT` na proměnnou, která obsahuje data k uložení.

*Pdata*<br/>
[v] Ukazatel na vyrovnávací paměť, která obsahuje data k uložení.

*nBajtu bajtů*<br/>
[v] Určuje velikost dat, na která odkazuje parametr *pData* v bajtech.

*list*<br/>
[v] Odkaz na [CObList](../../mfc/reference/coblist-class.md) proměnné, která obsahuje data k uložení.

*Obj*<br/>
[v] Odkaz na proměnnou [CObject,](../../mfc/reference/cobject-class.md) která obsahuje data k uložení.

*pObj*<br/>
[v] Ukazatel na ukazatel `CObject` na proměnnou, která obsahuje data, která mají být ukládat.

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu; jinak FALSE.

### <a name="remarks"></a>Poznámky

Chcete-li zapisovat do registru, musíte nastavit *bReadOnly* na nenulovou hodnotu při vytváření objektu [CSettingsStore.](../../mfc/reference/csettingsstore-class.md) Další informace naleznete v tématu [CSettingsStore::CSettingsStore](#csettingsstore).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CWinAppEx](../../mfc/reference/cwinappex-class.md)
